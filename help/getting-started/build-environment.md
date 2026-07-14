---
title: ビルド環境
description: Cloud Manager ユーザーがコードを作成およびテストするための専用のビルド環境について説明します。
exl-id: b3543320-66d4-4358-8aba-e9bdde00d976
TQID: https://experienceleague.adobe.com/AdGVWjyF0DXEX7jH5S39JQ506oVnNYGtYqAWNHcQeP8
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a01bfd36-4ab8-4bf8-9dc0-5b45b890552e
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
subfeature_v2:
  - id: d9eb3b3e-9447-4ed4-bf4a-96c7b245cb27
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 1692390e24f8fa7d719bd8293a99586ec4ec36d4
workflow-type: tm+mt
source-wordcount: 1205
ht-degree: 50%

---

# ビルド環境 {#build-environment}

Cloud Managerがコードのビルドとテストに使用する専用のビルド環境について説明します。

## 環境の詳細 {#details}

Cloud Manager のビルド環境には、次の属性があります。

* ビルド環境は Linux ベースで、Ubuntu 22.04 から派生しています。
* Apache Maven 3.9.4 がインストールされています。
   * アドビでは、ユーザーに [HTTP ではなく HTTPS を使用するように Maven リポジトリを更新](#https-maven)することをお勧めします。
* インストールされる Java バージョンは Oracle JDK 8u401 と Oracle JDK 11.0.22 です。
   * `/usr/lib/jvm/jdk1.8.0_401`
   * `/usr/lib/jvm/jdk-11.0.22`
* デフォルトでは、`JAVA_HOME` 環境変数は `/usr/lib/jvm/jdk1.8.0_401` に設定されています。これには、Oracle JDK 8u401 が含まれています。 詳しくは、[代替Maven実行JDK バージョン &#x200B;](#alternate-maven) セクションを参照してください。
* 追加の必要なシステムパッケージがインストールされます。
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* その他のパッケージは、[追加システムパッケージのインストール &#x200B;](#installing-additional-system-packages)の節で説明されているように、ビルド時にインストールされます。
* あらゆる構築は、新しい環境で行われます。 ビルドコンテナは、実行間のデータを保持しません。
* Mavenは、次の3つのコマンドで実行されます。
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven は、`settings.xml` ファイルを使用してシステムレベルで設定されます。このファイルには、`adobe-public` というプロファイルを使用したアドビの公開アーティファクトリポジトリが自動的に含まれています 詳しくは、[アドビの公開 Maven リポジトリ](https://repo1.maven.org/)を参照してください。
* Node.js 18 は、[フロントエンドパイプライン](/help/overview/ci-cd-pipelines.md)で使用できます。

>[!IMPORTANT]
>Maven ツールチェーンのサポートは、Cloud Manager 2025.06.0で削除されました。 JDKの選択は、`.cloudmanager/java-version`を通じてのみサポートされるようになりました。 詳しくは、[特定のJava バージョンの使用](#using-java-version)を参照してください。

>[!NOTE]
>
>Cloud Managerは`jacoco-maven-plugin`の特定のバージョンを定義していませんが、使用するバージョンは少なくとも`0.7.5.201505241946`である必要があります。

>[!TIP]
>
>Cloud Manager APIの使用方法について詳しくは、次の関連情報を参照してください。
>
>* [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager)
>* [API 統合の作成](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration)
>* [API の権限](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions)

## HTTPS Maven リポジトリ {#https-maven}

Cloud Manager [2023.10.0](/help/release-notes/2023/2023-10-0.md)は、ビルド環境のローリングアップデート（2023.12.0 リリースで完了）を開始しました。これには、Maven 3.8.8へのアップデートが含まれています。 Maven 3.8.1で導入された変更は、潜在的な脆弱性に対処するためのセキュリティ強化でした。 具体的には、[Maven リリースノート](https://maven.apache.org/docs/3.8.1/release-notes.html#cve-2021-26291)で説明するように、Maven では安全でないすべての `http://*` ミラーをデフォルトで無効にするようになりました。

一部のユーザーは、安全でないHTTP接続を使用するMaven リポジトリからアーティファクトをダウンロードする際に、ビルド手順で問題が発生します。

アップデートされたバージョンでスムーズなエクスペリエンスを実現するために、アドビでは、ユーザーが Mavenリポジトリを更新して HTTP ではなく HTTPS を使用することをお勧めします。 この調整は、業界の安全な通信プロトコルへの移行をサポートし、安全で信頼性の高いビルドプロセスを維持します。

## 特定の Java バージョンの使用 {#using-java-version}

デフォルトでは、Cloud Manager ビルドプロセスでビルドされたプロジェクトは、Oracle 8 JDK を使用します。 代替JDKを使用したいお客様は、Maven実行プロセス全体で代替JDK バージョンを選択できます。

>[!IMPORTANT]
>
>Maven ツールチェーンは、Cloud Manager 2025.06.0ではサポートされなくなりました。 maven-toolchains-plugin設定を含むパイプラインが`Cannot find matching toolchain definitions.`で失敗することに注意してください。`.cloudmanager/java-version` ファイルを使用して、代わりにJDK 11、17、または21を選択してください。
>
>**移行ガイダンス：**
>
>1. ソースコントロールにコミットされている`org.apache.maven.plugins:maven-toolchains-plugin` エントリと`toolchains.xml`をすべて削除して、ツールチェーンを削除します。
>1. [代替Maven実行JDK バージョン &#x200B;](#alternate-maven)の説明に従って、`.cloudmanager/java-version` （21、17または11）のJDKを選択します。
>1. Adobeでは、Cloud Manager ビルドキャッシュをクリアするか、新しいパイプライン実行をトリガーすることをお勧めします。
>

<!--
DEPRECATED 
### Maven Toolchains {#maven-toolchains}

The [Maven Toolchains plug-in](https://maven.apache.org/plugins/maven-toolchains-plugin/) lets projects select a specific JDK (or toolchain) to use in the context of toolchains-aware Maven plug-ins. This process is done in the project's `pom.xml` file by specifying a vendor and version value. A sample section in the `pom.xml` file is the following:

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

This process causes all toolchains-aware Maven plug-ins to use the Oracle JDK, version 11.

When using this method, Maven itself still runs using the default JDK (Oracle 8) and the `JAVA_HOME` environment variable is not changed. Therefore, checking or enforcing the Java version through plug-ins like the [Apache Maven Enforcer Plug-in](https://maven.apache.org/enforcer/maven-enforcer-plugin/) does not work and such plug-ins must not be used.

The currently available vendor/version combinations are:

|Vendor|Version|
|---|---|
| Oracle |1.8|
| Oracle |1.11|
| Oracle |11|
| Sun |1.8|
| Sun |1.11|
| Sun |11|

>[!NOTE]
>
>Starting April 2022, Oracle JDK is going to be the default JDK for the development and operation of AEM applications. Cloud Manager's build process automatically switches to using Oracle JDK, even if an alternative option is explicitly selected in the Maven toolchain. See the [April release notes](/help/release-notes/2022/2022-4-0.md) for more details.
-->

### Maven 実行の代替 JDK バージョン {#alternate-maven}

Mavenの実行全体のJDKとして、Oracle 8またはOracle 11を選択できます。 この方法では、すべてのプラグインに使用されるJDKが変更されます。 その結果、[Apache Maven Enforcer Plug-in](https://maven.apache.org/enforcer/maven-enforcer-plugin/)を使用したJava バージョンの確認と適用がサポートされます。

このプロセスを実行するには、パイプラインで使用されるGit リポジトリブランチに`.cloudmanager/java-version`という名前のファイルを作成します。 このファイルの内容は `11` か `8` のどちらかにすることができます。 その他の値は無視されます。 `11`が指定されている場合、システムはOracle 11を使用し、`JAVA_HOME`環境変数を`/usr/lib/jvm/jdk-11.0.22`に設定します。 `8`が指定されている場合、システムはOracle 8を使用し、`JAVA_HOME`環境変数を`/usr/lib/jvm/jdk1.8.0_401`に設定します。

## 環境変数 {#environment-variables}

### 標準環境変数 {#standard-environ-variables}

場合によっては、プログラムやパイプラインに関する情報に基づいてビルドプロセスを変更する必要があります。

例えば、JavaScriptの縮小にgulpなどのツールを使用する場合、開発環境とステージング環境および実稼動環境で異なる縮小レベルを使用します。

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

[Dispatcher](https://experienceleague.adobe.com/ja/docs/experience-manager-dispatcher/using/dispatcher) で使用できるのは、通常の環境変数のみです。 秘密鍵は使用できません。

ただし、環境変数は `IfDefine` ディレクティブでは使用できません。

>[!TIP]
>
>デプロイする前に、[Dispatcher をローカルで](https://experienceleague.adobe.com/ja/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools)使用して、環境変数の使用を検証します。

#### OSGi 設定 {#osgi}

[OSGi 設定](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/implementing/deploying/configuring/configuring-osgi)では、通常の環境変数とシークレットの両方を使用できます。

### パイプライン変数 {#pipeline-variables}

場合によっては、ビルドプロセスは特定の設定変数に依存します。 これらの変数は、Git リポジトリに配置するには不適切です。または、同じブランチを使用するパイプライン実行を変更する必要があります。

Cloud Manager では、これらの変数を Cloud Manager API または Cloud Manager CLI を介してパイプラインごとに設定できます。 変数は、プレーンテキストとして保存されるか、保存時に暗号化されます。 どちらの場合も、変数はビルド環境内で環境変数として使用可能になり、変数は `pom.xml` ファイル内または他のビルドスクリプト内から参照できます。

CLI を使用して変数を設定するには、次のようなコマンドを実行します。

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

現在の変数は、次のようなコマンドを使用して一覧表示できます。

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

変数は、一定の制限に従う必要があります。

* 変数名には、英数字とアンダースコア （`_`）のみを使用できます。
   * 慣例により、名前はすべて大文字です。
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

正常に機能するには、追加のシステムパッケージをインストールする必要があるビルドもあります。 例えば、ビルドはPythonまたはRuby スクリプトを呼び出し、適切な言語インタープリターをインストールする必要があります。 このシナリオは、[`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/)を呼び出してAPTを呼び出すことによって処理できます。 この実行は、Cloud Manager固有のMaven プロファイルでラップされます。 例えば、Python のインストールでは、次の操作を実行できます。

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

この方法は、言語固有のパッケージをインストールするためにも使用できます。 つまり、RubyGemsには`gem`を、Python パッケージには`pip`を使用します。

>[!NOTE]
>
>この方法でシステムパッケージをインストールしても、Adobe Experience Manager の実行に使用されているランタイム環境にはインストールされません。 AEM環境にシステムパッケージをインストールする必要がある場合は、Adobe担当者にお問い合わせください。
