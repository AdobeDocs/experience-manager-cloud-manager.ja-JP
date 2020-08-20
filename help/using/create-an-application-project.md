---
title: AEM アプリケーションプロジェクトの作成
seo-title: AEM アプリケーションプロジェクトの作成
description: 'null'
seo-description: Cloud Manager の使用を開始する際の AEM プロジェクトの設定について説明します。
uuid: 7b976ebf-5358-49d8-a58d-0bae026303fa
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: getting-started
discoiquuid: 76c1a8e4-d66f-4a3b-8c0c-b80c9e17700e
translation-type: ht
source-git-commit: ea9c4836caba1221cae75c600f77fd542a71d52c
workflow-type: ht
source-wordcount: '1741'
ht-degree: 100%

---


# AEM アプリケーションプロジェクトの作成 {#create-an-aem-application-project}

## ウィザードを使用した AEM アプリケーションプロジェクトの作成 {#using-wizard-to-create-an-aem-application-project}

ユーザーが Cloud Manager にオンボーディングされると、空の Git リポジトリが提供されます。現在の Adobe Managed Services（AMS）ユーザー（または AMS に移行中のオンプレミス AEM ユーザー）は、通常、プロジェクトコードを既に Git（または別のバージョン管理システム）に格納してあり、プロジェクトを Cloud Manager の Git リポジトリにインポートすることになります。ただし、新規ユーザーは既存のプロジェクトを持っていません。

新規ユーザーが作業に着手しやすくなるように、Cloud Manager では、最小限の AEM プロジェクトを出発点として作成できるようになりました。このプロセスは、[**AEM プロジェクトアーキタイプ**](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype)に基づいておこなわれます。


Cloud Manager で AEM アプリケーションプロジェクトを作成するには、次の手順に従います。

1. Cloud Manager にログインし、基本的なプログラム設定が完了すると、リポジトリが空の場合、**概要**&#x200B;画面に特別なコールトゥアクションカードが表示されます。

   ![](assets/image2018-10-3_14-29-44.png)

1. 「**作成**」をクリックして、ダイアログボックスを開きます。ここで、AEM プロジェクトアーキタイプで必要なパラメーターを指定できます。デフォルトでは、ダイアログボックスで次の 2 つの値が要求されます。

   * **タイトル** - デフォルトでは&#x200B;*プログラム名*&#x200B;に設定されています。

   * **新しいブランチ名** - デフォルトでは *master* になっています。

   ![](assets/screen_shot_2018-10-08at55825am.png)

   ダイアログボックスには、ダイアログの下部近くにあるハンドルをクリックして開くことができるドロワーがあります。これを展開すると、そのアーキタイプの設定パラメーターがすべてダイアログに表示されます。これらのパラメーターの多くは、**タイトル**&#x200B;に基づいて生成されるデフォルト値を持っています。

   ![](assets/screen_shot_2018-10-08at60032am.png)

   >[!NOTE]
   >
   >例えば、**Title** が ***We.Finance*** の場合、「ベース Maven アーティファクト ID」パラメーターは ***com.wefinance*** として生成されます。これらの値は、必要に応じて変更できます。
   >
   >
   >例えば、生成された値を ***com.wefinance*** から ***net.wefinance*** に変更できます。

1. 前の手順で「**作成**」をクリックして、アーキタイプを使用してスタータープロジェクトを作成し、名前付き Git ブランチにコミットします。これが完了したら、パイプラインを設定できます。

## プロジェクトの設定 {#setting-up-your-project}

### プロジェクト設定の詳細を変更する {#modifying-project-setup-details}

Cloud Manager で正常にビルドおよびデプロイされるために、既存の AEM プロジェクトはいくつかの基本ルールに従う必要があります。

* プロジェクトは Apache Maven を使用してビルドする必要があります。
* Git リポジトリのルートには *pom.xml* ファイルが必要です。この *pom.xml* ファイルでは、必要な数のサブモジュールを参照できます（それらのサブモジュールでさらに他のサブモジュールなどを参照している場合もあります）。

* 追加の Maven アーティファクトリポジトリへの参照を *pom.xml* ファイルに追加できます。設定時には、[パスワードで保護されたアーティファクトリポジトリ](#password-protected-maven-repositories)へのアクセスがサポートされます。ただし、ネットワークで保護されたアーティファクトリポジトリへのアクセスはサポートされていません。
* デプロイ可能なコンテンツパッケージは、*target* という名前のディレクトリに含まれているコンテンツパッケージ *zip* ファイルをスキャンすることで検出されます。任意の数のサブモジュールでコンテンツパッケージを作成することもできます。

* デプロイ可能な Dispatcher アーティファクトは、*conf* および *conf.d* というディレクトリを持つ *zip* ファイル（これも *target* という名前のディレクトリに含まれる）をスキャンすることで検出されます

* 複数のコンテンツパッケージがある場合、パッケージデプロイメントの順序は保証されません。特定の順序が必要な場合は、コンテンツパッケージの依存関係を使用して順序を定義できます。パッケージはデプロイメントから[スキップ](#skipping-content-packages)できます。

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-10-08T09:20:10.106-0400

2018.8.0: added existing in the opening sentence

 -->

## ビルド環境の詳細 {#build-environment-details}

Cloud Manager では、専用のビルド環境を使用して、コードのビルドおよびテストをおこないます。この環境には次のような特性があります。

* ビルド環境は Linux ベースで、Ubuntu 18.04 から派生しています。
* Apache Maven 3.6.0 がインストールされています。
* インストールされる Java バージョンは Oracle JDK 8u202 および 11.0.2 です。
* 必要な追加のシステムパッケージが、次のようにいくつかインストールされています。

   * bzip2
   * unzip
   * libpng
   * imagemagick
   * graphicsmagick

* [後述されている通り](#installing-additional-system-packages)、これ以外にも、ビルド時にパッケージがインストールされる場合があります。
* すべてのビルドは、Pristine 環境で実行されます。ビルドコンテナは実行から次回の実行までの間、状態を保持しません。
* Maven は常に *mvn --batch-mode clean org.jacoco:jacoco-maven-plugin:prepare-agent package* というコマンドで実行されます。
* Maven は、settings.xml ファイルを使用してシステムレベルで設定されます。このファイルには、アドビの公開&#x200B;**アーティファクト**&#x200B;リポジトリが自動的に含まれています（詳しくは、[アドビの公開 Maven リポジトリ](https://repo.adobe.com/)を参照してください）。

>[!NOTE]
>Cloud Manager では、`jacoco-maven-plugin` の特定のバージョンは定義されませんが、`0.7.5.201505241946` 異常のバージョンを使用する必要があります。

### Java 11 の使用 {#using-java-11}

Cloud Manager で、Java 8 と Java 11 の両方を使用したカスタマープロジェクトの作成がサポートされるようになりました。デフォルトでは、プロジェクトは Java 8 を使用して構築されます。プロジェクトで Java 11 を使用するお客様は、[Apache Maven Toolchains プラグイン](https://maven.apache.org/plugins/maven-toolchains-plugin/)を使用して使用できます。

これをおこなうには、pom.xml ファイルに次のような `<plugin>` エントリを追加します。

```xml
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-toolchains-plugin</artifactId>
            <version>1.1</version>
            <executions>
                <execution>
                    <goals>
                        <goal>toolchain</goal>
                    </goals>
                </execution>
            </executions>
            <configuration>
                <toolchains>
                    <jdk>
                        <version>11</version>
                        <vendor>oracle</vendor>
                    </jdk>
                </toolchains>
            </configuration>
        </plugin>
```

>[!NOTE]
>サポートされている `vendor` 値は `oracle` と `sun` で、サポートされている `version` 値は `1.8`、`1.11` および `11` です。

## 環境変数 {#environment-variables}

### 標準環境変数 {#standard-environ-variables}

場合によっては、プログラムやパイプラインに関する情報に基づいてビルドプロセスを変更する必要があります。

例えば、glup などのツールを使用してビルド時の JavaScript 縮小を実行する場合、開発環境でビルドする際には、ステージ用と実稼動用でビルドする際とは異なる、別の縮小レベルを使用することが望ましい可能性があります。

これをサポートするために、Cloud Manager は、これらの標準環境変数を各実行のビルドコンテナに追加します。

| **変数名** | **定義** |
|---|---|
| CM_BUILD | 常に「true」に設定 |
| ブランチ | 実行用に設定されたブランチ |
| CM_PIPELINE_ID | 数値パイプライン識別子 |
| CM_PIPELINE_NAME | パイプライン名 |
| CM_PROGRAM_ID | 数値プログラム識別子 |
| CM_PROGRAM_NAME | プログラム名 |
| ARTIFACTS_VERSION | ステージまたは実稼動パイプラインの場合、Cloud Manager で生成された合成バージョン |

### パイプライン変数 {#pipeline-variables}

場合によっては、顧客のビルドプロセスが、特定の設定変数に依存している可能性があります。これらの変数は Git リポジトリに配置するのに適していない場合や、同じブランチを使用するパイプライン実行間で変える必要が出る場合があります。

Cloud Manager では、これらの変数を Cloud Manager API または Cloud Manager CLI を介してパイプラインごとに設定できます。変数は、プレーンテキストとして保存することも、保存時に暗号化することもできます。どちらの場合も、変数はビルド環境内で環境変数として使用可能になり、変数は `pom.xml` ファイル内または他のビルドスクリプト内から参照できます。

CLI を使用して変数を設定するには、次のようなコマンドを実行します。

`$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test`

現在の変数は次のとおりです。

`$ aio cloudmanager:list-pipeline-variables PIPELINEID`

変数名に使用できるのは、英数字と下線（_）のみです。慣例では、名前はすべて大文字である必要があります。パイプラインあたり 200 個の変数という制限があります。名前はそれぞれ 100 文字未満、値はそれぞれ 2048 文字未満にする必要があります。

通常、`Maven pom.xml` ファイル内で使用する場合は、次のような構文を使用して、これらの変数を Maven プロパティにマップすると便利です。

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
            </activation>
            <properties>
                <my.custom.property>${env.MY_CUSTOM_VARIABLE}</my.custom.property> 
            </properties>
        </profile>
```

## Cloud Manager での Maven プロファイルのアクティブ化 {#activating-maven-profiles-in-cloud-manager}

ごく一部のケースでは、開発用ワークステーションで実行する場合とは異なり、Cloud Manager 内で実行する場合にはビルドプロセスを少し変える必要が出ることもあります。この場合は、[Maven プロファイル](https://maven.apache.org/guides/introduction/introduction-to-profiles.html)を使用して、Cloud Manager を含む環境ごとのビルドの違いを定義できます。

Cloud Manager ビルド環境内での Maven プロファイルのアクティベーションは、前述の CM_BUILD という名前の環境変数があるかどうかを調べておこなう必要があります。逆に、Cloud Manager ビルド環境以外でのみ使用するためのプロファイルは、この変数がないかどうかを調べることでアクティブ化する必要があります。

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

## パスワードで保護された Maven リポジトリのサポート {#password-protected-maven-repositories}

パスワードで保護された Maven リポジトリを Cloud Manager から使用するには、パスワード（および任意でユーザー名）を秘密の[パイプライン変数](#pipeline-variables)として指定し、git リポジトリの `.cloudmanager/maven/settings.xml` という名前のファイル内でその秘密を参照します。このファイルは、[Maven Settings File](https://maven.apache.org/settings.html) スキーマに従います。Cloud Manager のビルドプロセス開始時に、このファイル内の `<servers>` 要素が、Cloud Manager が提供するデフォルトの `settings.xml` ファイルに結合されます。`adobe` と `cloud-manager` で始まるサーバー ID は予約済みと見なされるため、カスタムサーバーでは使用しないでください。サーバー ID がこれらのプレフィックスのいずれかに&#x200B;**一致しない**&#x200B;場合、デフォルトの ID `central` は Cloud Manager でミラーリングされません。このファイルを配置すると、サーバー ID は `<repository>` 内や `pom.xml` ファイル内の `<pluginRepository>` 要素から参照されます。一般に、これらの `<repository>` や `<pluginRepository>` 要素は、[Cloud Manager 固有のプロファイル](/help/using/create-an-application-project.md#activating-maven-profiles-in-cloud-manager)に含まれますが、厳密に必要とは限りません。

例えば、リポジトリが https://repository.myco.com/maven2 にあり、Cloud Manager が使用するユーザー名が `cloudmanager` で、パスワードが `secretword` だとします。

まず、パスワードをパイプライン上の秘密として設定します。

`$ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword`

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

## 追加のシステムパッケージのインストール {#installing-additional-system-packages}

すべての機能を実装するにあたり、一部のビルドでは追加のシステムパッケージをインストールする必要があります。例えば、Python や Ruby のスクリプトが呼び出されるビルドでは、当然、適切な言語インタープリターをインストールすることが必要となります。これをおこなうには、[exec-maven-plugin](https://www.mojohaus.org/exec-maven-plugin/) を呼び出して、APT を起動します。この実行は通常、Cloud Manager 専用の Maven プロファイルにラップされます。例えば、Python は次のようにインストールします：

```xml
        <profile>
            <id>install-python</id>
            <activation>
                <property>
                        <name>env.CM_BUILD</name>
                </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <groupId>org.codehaus.mojo</groupId>
                        <artifactId>exec-maven-plugin</artifactId>
                        <version>1.6.0</version>
                        <executions>
                            <execution>
                                <id>apt-get-update</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>update</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                            <execution>
                                <id>install-python</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>install</argument>
                                        <argument>-y</argument>
                                        <argument>--no-install-recommends</argument>
                                        <argument>python</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

同じ方法を、RubyGems の `gem` や Python パッケージの `pip` など、特定の言語用のパッケージのインストールにも使用できます。

>[!NOTE]
>
>この方法でシステムパッケージをインストールしても、Adobe Experience Manager の実行に使用されているランタイム環境にはインストール&#x200B;**されません**。AEM 環境にシステムパッケージをインストールする必要がある場合は、カスタマーサクセスエンジニア（CSE）にお問い合わせください。

## コンテンツパッケージのスキップ {#skipping-content-packages}

Cloud Manager では、ビルドは、任意の数のコンテンツパッケージを作成できます。様々な理由により、コンテンツパッケージを作成してもデプロイしないことが望ましい場合があります。例えば、テストのみに使用するコンテンツパッケージを作成する場合や、ビルドプロセスの別のステップで（つまり、別のパッケージのサブパッケージとして）再パッケージ化される場合に便利です。

これらのシナリオに対応するために、Cloud Manager は、ビルドコンテンツパッケージのプロパティで、***cloudManagerTarget*** という名前のプロパティを探します。このプロパティが none に設定されている場合、パッケージはスキップされ、デプロイされません。このプロパティを設定する仕組みは、ビルドがコンテンツパッケージを作成する方法によって異なります。例えば、以下のように filevault-maven-plugin でプラグインを設定する場合、

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

content-package-maven-plugin では、同じようになります。

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

## ベストプラクティスに基づくコードの開発 {#develop-your-code-based-on-best-practices}

アドビのエンジニアリングチームとコンサルティングチームは、[AEM 開発者向けの包括的なベストプラクティス](https://helpx.adobe.com/ja-JP/experience-manager/6-4/sites/developing/using/best-practices.html)を策定しました。
