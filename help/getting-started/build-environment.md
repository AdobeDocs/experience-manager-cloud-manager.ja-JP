---
title: ビルド環境
description: Cloud Manager ユーザーがコードを作成およびテストするための専用のビルド環境について説明します。
exl-id: b3543320-66d4-4358-8aba-e9bdde00d976
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '1262'
ht-degree: 97%

---


# ビルド環境 {#build-environment}

Cloud Manager ユーザーがコードを作成およびテストするための専用のビルド環境について説明します。

## 環境の詳細 {#details}

Cloud Manager のビルド環境には、次の属性があります。

* ビルド環境は Linux ベースで、Ubuntu 22.04 から派生しています。
* Apache Maven 3.9.4 がインストールされています。
   * アドビでは、ユーザーに [HTTP ではなく HTTPS を使用するように Maven リポジトリを更新](#https-maven)することをお勧めします。
* インストールされる Java バージョンは Oracle JDK 8u401 と Oracle JDK 11.0.22 です。
   * `/usr/lib/jvm/jdk1.8.0_401`
   * `/usr/lib/jvm/jdk-11.0.22`
* デフォルトでは、`JAVA_HOME` 環境変数は `/usr/lib/jvm/jdk1.8.0_401` に設定されています。これには、Oracle JDK 8u401 が含まれています。詳しくは、[Maven 実行の代替 JDK バージョン](#alternate-maven)の節を参照してください。
* 必要に応じてインストールされる追加のシステムパッケージが、次のようにいくつかあります。
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* [追加のシステムパッケージのインストール](#installing-additional-system-packages)の節で説明されているように、ビルド時にその他のパッケージがインストールされる場合があります。
* どのビルドも、初期状態の環境で実行されます。ビルドコンテナは実行間で状態を保持しません。
* Maven は、次の 3 つのコマンドで実行されます。
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven は、`settings.xml` ファイルを使用してシステムレベルで設定されます。このファイルには、`adobe-public` というプロファイルを使用したアドビの公開アーティファクトリポジトリが自動的に含まれています詳しくは、[アドビの公開 Maven リポジトリ](https://repo1.maven.org/)を参照してください。
* Node.js 18 は、[フロントエンドパイプライン](/help/overview/ci-cd-pipelines.md)で使用できます。

>[!NOTE]
>
>Cloud Manager では、`jacoco-maven-plugin` の特定のバージョンは定義されませんが、使用するバージョンは `0.7.5.201505241946` 以上である必要があります。

>[!TIP]
>
>Cloud Manager API の使用方法については、次の追加リソースを参照してください。
>
>* [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager)
>* [API 統合の作成](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/)
>* [API の権限](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/)

## HTTPS Maven リポジトリ {#https-maven}

Cloud Manager [リリース 2023.10.0](/help/release-notes/2023/2023-10-0.md) では、Maven 3.8.8 へのアップデートを含む、ビルド環境へのローリングアップデートが開始されました（リリース 2023.12.0 で完了）。Maven 3.8.1 で導入された重要な変更は、潜在的な脆弱性を軽減することを目的としたセキュリティ強化でした。具体的には、[Maven リリースノート](https://maven.apache.org/docs/3.8.1/release-notes.html#cve-2021-26291)で説明するように、Maven では安全でないすべての `http://*` ミラーをデフォルトで無効にするようになりました。

このセキュリティ強化の結果、一部のユーザーには、ビルド手順で、特に安全でない HTTP 接続を使用する Maven リポジトリからアーティファクトをダウンロードする際に問題が発生する場合があります。

アップデートされたバージョンでスムーズなエクスペリエンスを実現するために、アドビでは、ユーザーが Mavenリポジトリを更新して HTTP ではなく HTTPS を使用することをお勧めします。この調整は、業界でセキュアな通信プロトコルへの移行が進むのに合わせて行われ、安全で信頼性の高いビルドプロセスを維持するのに役立ちます。

## 特定の Java バージョンの使用 {#using-java-version}

デフォルトでは、Cloud Manager ビルドプロセスでビルドされたプロジェクトは、Oracle 8 JDK を使用します。代替 JDK を使用する場合は、次の 2 つの選択肢があります。

* [Maven ツールチェーン](#maven-toolchains)
* [Maven 実行プロセス全体で使用する代替 JDK バージョンを選択する](#alternate-maven)

### Maven ツールチェーン {#maven-toolchains}

[Maven ツールチェーンプラグイン](https://maven.apache.org/plugins/maven-toolchains-plugin/)では、ツールチェーン対応の Maven プラグインのコンテキストで使用する特定の JDK（またはツールチェーン）をプロジェクトで選択できます。このプロセスは、プロジェクトの `pom.xml` ファイルでベンダーとバージョンの値を指定することで実行されます。`pom.xml` ファイルのサンプルセクションは次のとおりです。

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

このプロセスにより、すべてのツールチェーン対応 Maven プラグインで Oracle JDK バージョン 11 が使用されるようになります。

この方法を使用する場合、Maven 自体は引き続きデフォルト JDK（Oracle 8）を使用して実行され、`JAVA_HOME` 環境変数は変更されません。したがって、[Apache Maven Enforcer Plug-in](https://maven.apache.org/enforcer/maven-enforcer-plugin/) などのプラグインによる Java バージョンの確認や強制は機能しないので、そのようなプラグインは使用しないでください。

現在利用可能なベンダー／バージョンの組み合わせは次のとおりです。

| ベンダー | バージョン |
|---|---|
| Oracle | 1.8 |
| Oracle | 1.11 |
| Oracle | 11 |
| Sun | 1.8 |
| Sun | 1.11 |
| Sun | 11 |

>[!NOTE]
>
>2022年4月以降、Oracle JDK は、AEM アプリケーションの開発と運用のためのデフォルト JDK になります。Cloud Manager のビルドプロセスは、Maven ツールチェーンで代替オプションを明示的に選択した場合でも、Oracle JDK の使用に自動的に切り替わります。詳しくは、[4月のリリースノート](/help/release-notes/2022/2022-4-0.md)を参照してください。

### Maven 実行の代替 JDK バージョン {#alternate-maven}

また、Maven 実行全体の JDK として Oracle 8 または Oracle 11 を選択することもできます。この場合は、ツールチェーンオプションとは異なり、ツールチェーン設定も指定される場合を除き、すべてのプラグインに使用される JDK が変更されます。ツールチェーン設定が指定される場合は、そのツールチェーン設定が引き続きツールチェーン対応 Maven プラグインに適用されます。その結果、[Apache Maven Enforcer Plug-in](https://maven.apache.org/enforcer/maven-enforcer-plugin/) を使用して Java バージョンを確認および強制することができます。

このプロセスを実行するには、パイプラインで使用される Git リポジトリ分岐に `.cloudmanager/java-version` というファイルを作成します。このファイルの内容は `11` か `8` のどちらかにすることができます。その他の値は無視されます。`11` が指定されている場合は、Oracle 11 が使用され、`JAVA_HOME` 環境変数が `/usr/lib/jvm/jdk-11.0.22` に設定されます。 `8` が指定されている場合は、Oracle 8 が使用され、`JAVA_HOME` 環境変数が `/usr/lib/jvm/jdk1.8.0_401` に設定されます。

## 環境変数 {#environment-variables}

### 標準環境変数 {#standard-environ-variables}

場合によっては、プログラムやパイプラインに関する情報に基づいてビルドプロセスを変更する必要があります。

例えば、JavaScript の縮小に gulp などのツールを使用する場合、開発環境とステージング環境および実稼動環境で異なる縮小レベルを使用することをお勧めします。

これをサポートするために、Cloud Manager では、実行ごとに標準環境変数をビルドコンテナに追加します。

| 変数名 | 説明 |
|---|---|
| `CM_BUILD` | 常に `true` に設定 |
| `BRANCH` | 実行用に設定されたブランチ |
| `CM_PIPELINE_ID` | 数値パイプライン識別子 |
| `CM_PIPELINE_NAME` | パイプライン名 |
| `CM_PROGRAM_ID` | 数値プログラム識別子 |
| `CM_PROGRAM_NAME` | プログラム名 |
| `ARTIFACTS_VERSION` | ステージングパイプラインまたは実稼動パイプラインの場合、Cloud Manager で生成された合成バージョン |

### 標準環境変数の可用性 {#availability}

標準環境変数は、様々な場所で使用できます。

#### オーサー、プレビュー、パブリッシュの各環境 {#author-preview-publish}

オーサー、プレビュー、パブリッシュの各環境では、通常の環境変数とシークレットの両方を使用できます。

#### Dispatcher {#dispatcher}

[Dispatcher](https://experienceleague.adobe.com/ja/docs/experience-manager-dispatcher/using/dispatcher) で使用できるのは、通常の環境変数のみです。秘密鍵は使用できません。

ただし、環境変数は `IfDefine` ディレクティブでは使用できません。

>[!TIP]
>
>デプロイする前に、[Dispatcher をローカルで](https://experienceleague.adobe.com/ja/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools)使用して、環境変数の使用を検証します。

#### OSGi 設定 {#osgi}

[OSGi 設定](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/implementing/deploying/configuring/configuring-osgi)では、通常の環境変数とシークレットの両方を使用できます。

### パイプライン変数 {#pipeline-variables}

場合によっては、ビルドプロセスが、特定の設定変数に依存している可能性があります。これらの変数が Git リポジトリに配置するのに適していない場合や、同じ分岐を使用するパイプライン実行間で変更する必要があります。

Cloud Manager では、これらの変数を Cloud Manager API または Cloud Manager CLI を介してパイプラインごとに設定できます。変数は、プレーンテキストとして保存することも、保存時に暗号化することもできます。どちらの場合も、変数はビルド環境内で環境変数として使用可能になり、変数は `pom.xml` ファイル内または他のビルドスクリプト内から参照できます。

CLI を使用して変数を設定するには、次のようなコマンドを実行します。

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

現在の変数は、次のようなコマンドを使用して一覧表示できます。

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

変数は、一定の制限に従う必要があります。

* 変数名には、英数字とアンダースコア（`_`）のみを含めることができます。
   * 慣例により、名前はすべて大文字にする必要があります。
* 変数の数はパイプラインあたり最大 200 個までです。
* 各名前は 100 文字未満にする必要があります。
* 各文字列値は 2048 文字未満にする必要があります。
* 各 `secretString` 値は 500 文字未満にする必要があります。

Maven `pom.xml` ファイル内で使用する場合は、通常、次のような構文を使用して、これらの変数を Maven プロパティにマッピングすると便利です。

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

## 追加のシステムパッケージのインストール {#installing-additional-system-packages}

完全に機能させるために、一部のビルドでは追加のシステムパッケージをインストールする必要があります。例えば、Python や Ruby のスクリプトを呼び出す可能性のあるビルドでは、適切な言語インタープリターをインストールしておく必要があります。このシナリオは、[`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/) を呼び出して、APT を起動することで実行できます。この実行は通常、Cloud Manager 固有の Maven プロファイルにラップされます。例えば、Python のインストールでは、次の操作を実行できます。

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

また、この方法を使用して、言語固有のパッケージをインストールすることもできます。つまり、RubyGems には `gem`、Python パッケージには `pip` を使用します。

>[!NOTE]
>
>この方法でシステムパッケージをインストールしても、Adobe Experience Manager の実行に使用されているランタイム環境にはインストールされません。AEM 環境にシステムパッケージをインストールする必要がある場合は、アドビ担当者にお問い合わせください。
