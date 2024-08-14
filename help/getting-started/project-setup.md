---
title: プロジェクトの設定
description: Cloud Manager でプロジェクトを管理およびデプロイできるようにプロジェクトを設定する方法について説明します。
exl-id: ed994daf-0195-485a-a8b1-87796bc013fa
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '1395'
ht-degree: 55%

---


# プロジェクトの設定 {#setting-up-your-project}

Cloud Manager でプロジェクトを管理およびデプロイできるようにプロジェクトを設定する方法について説明します。

## 既存プロジェクトの編集 {#modifying-project-setup-details}

既存のAEM プロジェクトは、Cloud Managerで正常にビルドおよびデプロイできるように、いくつかの基本ルールに従う必要があります。

* プロジェクトは Apache Maven を使用してビルドする必要があります。
* Git リポジトリのルートに `pom.xml` ファイルが必要です。
   * この `pom.xml` ファイルでは、必要な数のサブモジュール（その中にさらに他のサブモジュールを含む場合があります）を参照できます。
   * 追加の Maven アーティファクトリポジトリへの参照を `pom.xml` ファイルに追加できます。
   * 設定時には、[パスワードで保護されたアーティファクトリポジトリー](#password-protected-maven-repositories)へのアクセスがサポートされます。ただし、ネットワークで保護されたアーティファクトリポジトリーへのアクセスはサポートされていません。
* デプロイ可能なコンテンツパッケージは、`target` という名前のディレクトリに含まれているコンテンツパッケージ .zip ファイルをスキャンすることで検出されます。
   * 任意の数のサブモジュールでコンテンツパッケージを作成することができます。
* デプロイ可能な Dispatcher アーティファクトは、`conf` および `conf.d` という名前の `target` のサブディレクトリに含まれている `zip` ファイルをスキャンすることで検出されます。
* 複数のコンテンツパッケージがある場合、パッケージデプロイメントの順序は保証されません。
* 特定の順序が必要な場合は、コンテンツパッケージの依存関係を使用して順序を定義できます。
* パッケージはデプロイメントから[スキップ](#skipping-content-packages)できます。

## Cloud Managerでの Maven プロファイルのアクティブ化 {#activating-maven-profiles-in-cloud-manager}

ごく一部のケースでは、開発用ワークステーションで実行する場合とは異なり、Cloud Manager 内で実行する場合にはビルドプロセスを少し変える必要が出ることもあります。この場合は、[Maven プロファイル](https://maven.apache.org/guides/introduction/introduction-to-profiles.html)を使用して、Cloud Manager を含む環境ごとのビルドの違いを定義できます。

Cloud Manager ビルド環境内での Maven プロファイルのアクティベーションは、[ 環境変数 ](/help/getting-started/build-environment.md#environment-variables) があるかどうかを調べて行う必要 `CM_BUILD` あります。 逆に、Cloud Manager ビルド環境以外でのみ使用するためのプロファイルは、この変数がないかどうかを調べることでアクティブ化する必要があります。

例えば、Cloud Manager内でビルドが実行されたときにのみ簡単なメッセージを出力する場合は、次のようにします。

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

Cloud Manager以外でビルドが実行されたときにのみ簡単なメッセージを出力する場合は、次のようにします。

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

パスワードで保護された Maven リポジトリーのアーティファクトは、慎重に使用する必要があります。これは、この方法でデプロイされたコードは、Cloud Managerの品質ゲートによって適用される品質チェックの対象として完全には除外されないためです。 また、Adobeでは、バイナリと共に Java ソースとプロジェクトのソースコード全体もデプロイすることをお勧めします。

>[!TIP]
>
>パスワードで保護された Maven リポジトリのアーティファクトは、使用されることはまれです。AEM に関連付けられていないコードに対してのみ使用してください。

パスワードで保護された Maven リポジトリーをCloud Managerから使用するには、パスワード（および任意でユーザー名）をシークレット [ パイプライン変数 ](/help/getting-started/build-environment.md#pipeline-variables) として指定し、Git リポジトリーの `.cloudmanager/maven/settings.xml` という名前のファイル内でそのシークレットを参照します。 このファイルは、[Maven 設定ファイル](https://maven.apache.org/settings.html)スキーマに従います。

Cloud Managerのビルドプロセスが開始すると、このファイル内の `<servers>` 要素が、Cloud Managerから提供されるデフォルトの `settings.xml` ファイルに結合されます。 カスタムサーバーでは、`adobe` および `cloud-manager` で始まるサーバー ID を使用しないでください。 このような ID は予約済みと見なされます。 Cloud Managerは、指定されたプレフィックスの 1 つまたはデフォルトの ID`central` に一致するサーバ ID のみをミラーリングします。

このファイルを配置すると、サーバー ID は `pom.xml` ファイル内の `<repository>` 要素や `<pluginRepository>` 要素内から参照されます。一般に、これらの `<repository>` 要素や `<pluginRepository>` 要素は、[Cloud Manager 固有のプロファイル](#activating-maven-profiles-in-cloud-manager)に含まれていますが、厳密には必要ありません。

例えば、リポジトリーが `https://repository.myco.com/maven2` にあり、Cloud Managerが使用するユーザー名が `cloudmanager` で、パスワードが `secretword` だとします。

まず、パスワードをパイプライン上の秘密として設定します。

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword
```

次に、`.cloudmanager/maven/settings.xml` ファイルから次の内容を参照します。

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

### ソースをデプロイ {#deploying-sources}

バイナリと共に Java ソースを Maven リポジトリにデプロイすることをお勧めします。

プロジェクトで `maven-source-plugin` を設定します。

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

バイナリと共にプロジェクトソース全体を Maven リポジトリにデプロイすることをお勧めします。 これにより、正確なアーティファクトを再ビルドできます。

プロジェクトで `maven-assembly-plugin` を設定します。

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

## コンテンツパッケージをスキップ {#skipping-content-packages}

Cloud Manager では、ビルドは、任意の数のコンテンツパッケージを作成できます。
様々な理由により、コンテンツパッケージを生成してもデプロイしないことが望ましい場合があります。例えば、この方法は、テストのみを目的としてコンテンツパッケージをビルドする場合や、ビルドプロセスの別の手順でコンテンツパッケージが再パッケージ化される場合に役立ちます。 つまり、別のパッケージのサブパッケージとして使用されます。

これらのシナリオに対応するため、Cloud Manager はビルドコンテンツパッケージのプロパティで、`cloudManagerTarget` という名前のプロパティを探します。このプロパティが `none` に設定されている場合、パッケージはスキップされ、デプロイされません。 このプロパティを設定する仕組みは、ビルドがコンテンツパッケージを作成する方法によって異なります。 例えば、`filevault-maven-plugin` を使用する場合は、次のようにプラグインを設定します。

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

`content-package-maven-plugin` の場合は、次のようになります。

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

多くの場合、同じコードが複数の AEM 環境にデプロイされます。Cloud Managerは、複数のフルスタックパイプライン実行で同じ Git コミットが使用されていることを検出した場合、コードベースの再ビルドを可能な限り避けます。

実行が開始されると、ブランチパイプラインの現在の HEAD コミットが抽出されます。コミットハッシュは、UI に表示され、API 経由で表示されます。 ビルドステップが正常に完了すると、結果として生成されたアーティファクトはそのコミットハッシュに基づいて保存され、後続のパイプライン実行で再利用できます。

同じプログラム内にあるパッケージは、パイプラインをまたいで再利用されます。再利用可能なパッケージを探す際に、AEM はブランチを無視し、ブランチをまたいでアーティファクトを再利用します。

再利用が行われると、ビルドステップとコード品質ステップが元の実行の結果に事実上置き換えられます。ビルドステップのログファイルには、アーティファクトと、最初にアーティファクトのビルドに使用された実行情報が一覧表示されます。

そのようなログ出力の例を次に示します。

```shell
The following build artifacts were reused from the prior execution 4 of pipeline 1 which used commit f6ac5e6943ba8bce8804086241ba28bd94909aef:
build/aem-guides-wknd.all-2021.1216.1101633.0000884042.zip (content-package)
build/aem-guides-wknd.dispatcher.cloud-2021.1216.1101633.0000884042.zip (dispatcher-configuration)
```

コード品質ステップのログにも、同様の情報が含まれます。

### 例 {#example-reuse}

#### 例 1 {#example-1}

プログラムに 2 つの開発パイプラインがあるとします。

* ブランチ `foo` のパイプライン 1
* ブランチ `bar` のパイプライン 2

両方のブランチが同じコミット ID 上にあります。

1. 最初にパイプライン 1 を実行すると、パッケージは通常どおりビルドされます。
1. その後、パイプライン 2 を実行すると、パイプライン 1 で作成されたパッケージが再利用されます。

#### 例 2 {#example-2}

プログラムにはブランチ `foo` とブランチ `bar` という 2 つのブランチがあるとします。

両方のブランチのコミット ID が同じです。

1. 開発パイプラインは、`foo` のビルドと実行を行います。
1. その後、実稼動パイプラインが `bar` のビルドと実行を行います。

この場合、同じコミットハッシュが特定されたので、`foo` のアーティファクトは実稼動パイプラインで再利用されます。

### オプトアウト {#opting-out}

必要に応じて、パイプライン変数 `CM_DISABLE_BUILD_REUSE` を `true` に設定して、特定のパイプラインに対して再利用動作を無効にできます。この変数を設定した場合でも、コミットハッシュは抽出されます。 結果として生成されたアーティファクトは後で使用するために保存されますが、以前に保存されたアーティファクトは再利用されません。 この動作を理解するために、次のシナリオについて考えてみます。

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
* [Maven バージョン処理](/help/managing-code/maven-project-version.md) では、実稼動パイプラインでのみ、プロジェクトのバージョンを置き換えます。開発パイプラインと実稼動パイプラインの両方に同じコミットが使用され、開発パイプラインが最初に実行される場合、バージョンは変更されずにステージング環境と実稼動環境にデプロイされます。 ただし、この場合もタグは作成されます。
* 保存されたアーティファクトが正常に取得されなかった場合、ビルドステップは、アーティファクトが保存されていないかのように実行されます。
* 以前に作成したビルドアーティファクトを Cloud Manager で再利用する場合、`CM_DISABLE_BUILD_REUSE` 以外のパイプライン変数は考慮されません。

## ベストプラクティスに基づくコードの開発 {#develop-your-code-based-on-best-practices}

アドビのエンジニアリングチームとコンサルティングチームは、[AEM 開発者向けの包括的なベストプラクティス](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/developing/bestpractices/best-practices)を策定しました。
