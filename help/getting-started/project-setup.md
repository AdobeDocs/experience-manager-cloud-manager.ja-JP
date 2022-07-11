---
title: プロジェクトのセットアップ
description: Cloud Manager でプロジェクトを管理およびデプロイできるようにプロジェクトを設定する方法について説明します。
exl-id: ed994daf-0195-485a-a8b1-87796bc013fa
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '1432'
ht-degree: 77%

---


# プロジェクトのセットアップ {#setting-up-your-project}

Cloud Manager でプロジェクトを管理およびデプロイできるようにプロジェクトを設定する方法について説明します。

## 既存のプロジェクトの変更 {#modifying-project-setup-details}

既存のAEMプロジェクトを Cloud Manager で正常にビルドおよびデプロイするには、いくつかの基本ルールに従う必要があります。

* プロジェクトは Apache Maven を使用してビルドする必要があります。
* 必ず `pom.xml` ファイルを git リポジトリのルートに配置します。
   * この `pom.xml` ファイルでは、必要な数のサブモジュールを参照できます（それらのサブモジュールでさらに他のサブモジュールを参照している場合もあります）。
   * 追加の Maven アーティファクトリポジトリーへの参照を `pom.xml` ファイルに追加できます。
   * 設定時には、[パスワードで保護されたアーティファクトリポジトリー](#password-protected-maven-repositories)へのアクセスがサポートされます。ただし、ネットワークで保護されたアーティファクトリポジトリーへのアクセスはサポートされていません。
* デプロイ可能なコンテンツパッケージは、という名前のディレクトリに含まれているコンテンツパッケージ.zip ファイルをスキャンすることで検出されます `target`.
   * 任意の数のサブモジュールでコンテンツパッケージを作成することもできます。
* デプロイ可能な Dispatcher アーティファクトは、 `zip` のサブディレクトリを含むファイル `target` 名前付き `conf` および `conf.d`.
* 複数のコンテンツパッケージがある場合、パッケージデプロイメントの順序は保証されません。
* 特定の順序が必要な場合は、コンテンツパッケージの依存関係を使用して順序を定義できます。
* パッケージはデプロイメントから[スキップ](#skipping-content-packages)できます。

## Cloud Manager での Maven プロファイルのアクティブ化 {#activating-maven-profiles-in-cloud-manager}

ごく一部のケースでは、開発用ワークステーションで実行する場合とは異なり、Cloud Manager 内で実行する場合にはビルドプロセスを少し変える必要が出ることもあります。この場合は、[Maven プロファイル](https://maven.apache.org/guides/introduction/introduction-to-profiles.html)を使用して、Cloud Manager を含む環境ごとのビルドの違いを定義できます。

Cloud Manager ビルド環境内での Maven プロファイルのアクティベーションは、 `CM_BUILD` [環境変数](/help/getting-started/build-environment.md#environment-variables) 環境変数。 逆に、Cloud Manager ビルド環境以外でのみ使用するためのプロファイルは、この変数がないかどうかを調べることでアクティブ化する必要があります。

例えば、Cloud Manager 内でビルドが実行されたときにのみ簡単なメッセージを出力する場合は、次のようにします。

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                  <property>
                        <name>env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running inside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

>[!NOTE]
>
>開発用ワークステーションでこのプロファイルをテストするには、（`-PcmBuild` を付けた）コマンドラインまたは統合開発環境（IDE）でプロファイルを有効にします。

Cloud Manager 以外でビルドが実行されたときにのみ簡単なメッセージを出力する場合は、次のようにします。

```xml
        <profile>
            <id>notCMBuild</id>
            <activation>
                  <property>
                        <name>!env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running outside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

## パスワードで保護された Maven リポジトリーのサポート {#password-protected-maven-repositories}

パスワードで保護された Maven リポジトリーのアーティファクトは、慎重に使用する必要があります。これは、Cloud Manager の品質ゲートに実装されているすべての品質ルールを通じてデプロイされるコードが実行されるわけではないからです。 Java ソース、およびプロジェクトのソースコード全体もバイナリとともにデプロイすることをお勧めします。

>[!TIP]
>
>パスワードで保護された Maven リポジトリーのアーティファクトは、まれに、AEMに結び付けられていないコードに対してのみ使用する必要があります。

パスワードで保護された Maven リポジトリーを Cloud Manager から使用するには、パスワード（および任意でユーザー名）を秘密の[パイプライン変数](/help/getting-started/build-environment.md#pipeline-variables)として指定し、Git リポジトリーの `.cloudmanager/maven/settings.xml` という名前のファイル内でその秘密を参照します。このファイルは、[Maven Settings File](https://maven.apache.org/settings.html) スキーマに従います。

Cloud Manager のビルドプロセス開始時に、このファイル内の `<servers>` 要素が、Cloud Manager が提供するデフォルトの `settings.xml` ファイルに結合されます。`adobe` と `cloud-manager` で始まるサーバー ID は予約済みと見なされるため、カスタムサーバーでは使用しないでください。サーバー ID がこれらのプレフィックスのいずれかに一致しない場合、デフォルトの ID `central` は Cloud Manager でミラーリングされません。

このファイルを配置すると、サーバー ID は `<repository>` および/または `<pluginRepository>` 要素を `pom.xml` ファイル。 一般に、これらの `<repository>` や `<pluginRepository>` 要素は、[Cloud Manager 固有のプロファイル](#activating-maven-profiles-in-cloud-manager)に含まれますが、厳密に必要とは限りません。

例えば、リポジトリが `https://repository.myco.com/maven2`Cloud Manager が使用するユーザー名は、 `cloudmanager` パスワードは `secretword`.

まず、パスワードをパイプライン上の秘密として設定します。

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword
```

次に、`.cloudmanager/maven/settings.xml` ファイルからこれを参照します。

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
    <servers>
        <server>
            <id>myco-repository</id>
            <username>cloudmanager</username>
            <password>${env.CUSTOM_MYCO_REPOSITORY_PASSWORD}</password>
        </server>
    </servers>
</settings>
```

最後に、`pom.xml` ファイル内のサーバー ID を参照します。

```xml
<profiles>
    <profile>
        <id>cmBuild</id>
        <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
        </activation>
        <build>
            <repositories>
                <repository>
                    <id>myco-repository</id>
                    <name>MyCo Releases</name>
                    <url>https://repository.myco.com/maven2</url>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                </repository>
            </repositories>
            <pluginRepositories>
                <pluginRepository>
                    <id>myco-repository</id>
                    <name>MyCo Releases</name>
                    <url>https://repository.myco.com/maven2</url>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                </pluginRepository>
            </pluginRepositories>
        </build>
    </profile>
</profiles>
```

### ソースのデプロイ {#deploying-sources}

バイナリと共に Java ソースを Maven リポジトリーにデプロイすることをお勧めします。

の設定 `maven-source-plugin` プロジェクト内：

```xml
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-source-plugin</artifactId>
            <executions>
                <execution>
                    <id>attach-sources</id>
                    <goals>
                        <goal>jar-no-fork</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
```

### プロジェクトソースのデプロイ {#deploying-project-sources}

バイナリと共にプロジェクトソース全体を Maven リポジトリにデプロイすることをお勧めします。 これにより、正確なアーティファクトを再構築できます。

の設定 `maven-assembly-plugin` プロジェクト内：

```xml
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-assembly-plugin</artifactId>
            <executions>
                <execution>
                    <id>project-assembly</id>
                    <phase>package</phase>
                    <goals>
                        <goal>single</goal>
                    </goals>
                    <configuration>
                        <descriptorRefs>
                            <descriptorRef>project</descriptorRef>
                        </descriptorRefs>
                    </configuration>
                </execution>
            </executions>
        </plugin>
```

## コンテンツパッケージのスキップ {#skipping-content-packages}

Cloud Manager では、ビルドは、任意の数のコンテンツパッケージを作成できます。
様々な理由により、コンテンツパッケージを作成してもデプロイしないことが望ましい場合があります。例えば、テストのみに使用するコンテンツパッケージを作成する場合や、ビルドプロセスの別のステップで（つまり、別のパッケージのサブパッケージとして）再パッケージ化される場合に便利です。

これらのシナリオに対応するために、Cloud Manager は、ビルドコンテンツパッケージのプロパティで、`cloudManagerTarget` という名前のプロパティを探します。このプロパティが `none`に設定しない場合、パッケージはスキップされ、デプロイされません。 このプロパティを設定する仕組みは、ビルドがコンテンツパッケージを作成する方法によって異なります。例えば、 `filevault-maven-plugin` 次のようにプラグインを設定します。

```xml
        <plugin>
            <groupId>org.apache.jackrabbit</groupId>
            <artifactId>filevault-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```

を使用 `content-package-maven-plugin` 次のようになります。

```xml
        <plugin>
            <groupId>com.day.jcr.vault</groupId>
            <artifactId>content-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```

## ビルドアーティファクトの再利用 {#build-artifact-reuse}

多くの場合、同じコードが複数の AEM 環境にデプロイされます。Cloud Manager は、複数のフルスタックパイプライン実行で同じ Git コミットが使用されていることを検出した場合、コードベースの再ビルドを可能な限り避けます。

実行が開始されると、ブランチパイプラインの現在の HEAD コミットが抽出されます。コミットハッシュは、UI に表示され、API を使用して確認できます。ビルドステップが正常に完了すると、結果として生成されたアーティファクトはそのコミットハッシュに基づいて保存され、後続のパイプライン実行で再利用できます。

同じプログラム内にあるパッケージは、パイプラインをまたいで再利用されます。再利用可能なパッケージを探す際に、AEM はブランチを無視し、ブランチをまたいでアーティファクトを再利用します。

再利用が行われると、ビルドステップとコード品質ステップが元の実行の結果に事実上置き換えられます。ビルドステップのログファイルには、アーティファクトと、最初にアーティファクトのビルドに使用された実行情報が一覧表示されます。

そのようなログ出力の例を次に示します。

```shell
The following build artifacts were reused from the prior execution 4 of pipeline 1 which used commit f6ac5e6943ba8bce8804086241ba28bd94909aef:
build/aem-guides-wknd.all-2021.1216.1101633.0000884042.zip (content-package)
build/aem-guides-wknd.dispatcher.cloud-2021.1216.1101633.0000884042.zip (dispatcher-configuration)
```

コード品質ステップのログにも、類似の情報が含まれます。

### 例 {#example-reuse}

#### 例 1 {#example-1}

プログラムに 2 つの開発パイプラインがあるとします。

* ブランチ `foo` のパイプライン 1
* ブランチ `bar` のパイプライン 2

両方のブランチが同じコミット ID 上にあります。

1. 最初にパイプライン 1 を実行すると、パッケージは通常どおりビルドされます。
1. 次に、パイプライン 2 を実行すると、パイプライン 1 で作成したパッケージが再利用されます。

#### 例 2 {#example-2}

プログラムには次の 2 つのブランチがあるとします。

* ブランチ `foo`
* ブランチ `bar`

両方のブランチのコミット ID が同じです。

1. 開発パイプラインは、`foo` のビルドと実行をおこないます。
1. その後、実稼動パイプラインが `bar` をビルドおよび実行します。

この場合、同じコミットハッシュが特定されたので、`foo` のアーティファクトは実稼動パイプラインで再利用されます。

### オプトアウト {#opting-out}

必要に応じて、パイプライン変数 `CM_DISABLE_BUILD_REUSE` を `true` に設定して、特定のパイプラインに対して再利用動作を無効にできます。この変数を設定した場合でも、コミットハッシュは抽出され、結果として生成されたアーティファクトは後で使用するために保存されますが、以前に保存されたアーティファクトは再利用されません。この動作を理解するために、次のシナリオについて考えてみます。

1. 新しいパイプラインが作成されます。
1. そのパイプラインが実行され（実行番号 1）、現在の HEAD コミットが `becdddb` となっています。実行が完了すると、結果として生成されたアーティファクトが保存されます。
1. この `CM_DISABLE_BUILD_REUSE` 変数が設定されます。
1. コードを変更せずにパイプラインが再実行されます。`becdddb` に関連付けられたアーティファクトが保存されていますが、`CM_DISABLE_BUILD_REUSE` 変数が設定されているので再利用されません。
1. コードが変更され、パイプラインが実行されます。HEAD コミットは `f6ac5e6` になります。実行が完了すると、結果として生成されたアーティファクトが保存されます。
1. `CM_DISABLE_BUILD_REUSE` 変数が削除されます。
1. コードを変更せずに、パイプラインが再実行されます。`f6ac5e6` に関連付けられたアーティファクトが保存されているため、それらのアーティファクトは再利用されます。

### 注意事項 {#caveats}

* ビルドアーティファクトは、コミットハッシュが同じかどうかに関係なく、異なるプログラムをまたいで再利用されることはありません。
* ブランチやパイプラインが異なる場合でも、ビルドアーティファクトは同じプログラム内で再利用されます。
* [Maven バージョン処理](/help/managing-code/maven-project-version.md) では、実稼動パイプラインでのみ、プロジェクトのバージョンを置き換えます。したがって、開発デプロイ実行と実稼動パイプライン実行の両方で同じコミットが使用され、開発デプロイパイプラインが先に実行される場合、バージョンは変更されずにステージング環境と実稼動環境にデプロイされます。ただし、この場合もタグは作成されます。
* 保存されたアーティファクトが正常に取得されなかった場合、ビルドステップは、アーティファクトが保存されていない場合と同じように実行されます。
* 以前に作成したビルドアーティファクトを Cloud Manager で再利用する場合、`CM_DISABLE_BUILD_REUSE` 以外のパイプライン変数は考慮されません。

## ベストプラクティスに基づくコードの開発 {#develop-your-code-based-on-best-practices}

アドビのエンジニアリングおよびコンサルティングチームは、[AEM 開発者向けの包括的なベストプラクティス](https://experienceleague.adobe.com/docs/experience-manager-65/developing/bestpractices/best-practices.html)を策定しました。
