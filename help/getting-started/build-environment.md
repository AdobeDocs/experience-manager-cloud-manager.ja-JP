---
title: ビルド環境
description: Cloud Manager ユーザーがコードを作成およびテストするための専用のビルド環境について説明します。
exl-id: b3543320-66d4-4358-8aba-e9bdde00d976
source-git-commit: 4c051cd1696f8a00d0278131c9521ad4dcb956a3
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 52%

---


# ビルド環境 {#build-environment}

Cloud Manager ユーザーがコードを作成およびテストするための専用のビルド環境について説明します。

## 環境の詳細 {#details}

Cloud Manager のビルド環境には、次の属性があります。

* ビルド環境は Linux ベースで、Ubuntu 18.04 から派生しています。
* Apache Maven 3.6.0 がインストールされています。
* インストールされる Java バージョンは Oracle JDK 8u202 と Oracle JDK 11.0.2 です。
* デフォルトでは、`JAVA_HOME` 環境変数は `/usr/lib/jvm/jdk1.8.0_202` に設定されています。これには、Oracle JDK 8u202 が含まれています。の節を参照してください。 [代替 Maven 実行 JDK バージョン](#alternate-maven) 」の節を参照してください。
* 必要に応じてインストールされる追加のシステムパッケージが、次のようにいくつかあります。
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* [追加のシステムパッケージのインストール](#installing-additional-system-packages)の節で説明されているように、ビルド時にその他のパッケージがインストールされる場合があります。
* すべてのビルドは、Pristine 環境で実行されます。ビルドコンテナは、実行から次の実行までの間、状態を保持しません。
* Maven は常に次の 3 つのコマンドで実行します。
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven は、 `settings.xml` 次の名前のプロファイルを使用して、パブリックAdobeアーティファクトリポジトリを自動的に含むファイル： `adobe-public`.
   * 詳しくは、 [Adobeの公開 Maven リポジトリ](https://repo1.maven.org/) を参照してください。

>[!NOTE]
>
>Cloud Manager では、`jacoco-maven-plugin` の特定のバージョンは定義されませんが、`0.7.5.201505241946` 異常のバージョンを使用する必要があります。

>[!TIP]
>
>Cloud Manager API の使用方法については、次の追加リソースを参照してください。
>* [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager)
>* [API 統合の作成](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/)
>* [API の権限](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/)


## 特定の Java バージョンの使用 {#using-java-version}

デフォルトでは、プロジェクトは、Oracle 8 JDK を使用して Cloud Manager ビルドプロセスでビルドされます。代替 JDK を使用する場合は、次の 2 つの選択肢があります。

* [Maven ツールチェーン](#maven-toolchains)
* [Maven 実行プロセス全体での代替 JDK バージョンの選択](#alternate-maven)

### Maven ツールチェーン {#maven-toolchains}

この [Maven Toolchains プラグイン](https://maven.apache.org/plugins/maven-toolchains-plugin/) を使用すると、プロジェクトで、toolchains 対応の Maven プラグインのコンテキストで使用する特定の JDK（またはツールチェーン）を選択できます。 それには、プロジェクトの `pom.xml` ファイルでベンダーとバージョン値を指定します。`pom.xml` ファイルのサンプルセクションは次のとおりです。

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

これにより、すべてのツールチェーン対応 Maven プラグインで Oracle JDK バージョン 11 が使用されるようになります。

この方法を使用する場合、Maven 自体は引き続きデフォルト JDK（Oracle 8）を使用して実行され、`JAVA_HOME` 環境変数は変更されません。したがって、[Apache Maven Enforcer Plugin](https://maven.apache.org/enforcer/maven-enforcer-plugin/) などのプラグインによる Java バージョンの確認や強制は機能しないので、そのようなプラグインは使用しないでください。

現在利用可能なベンダー／バージョンの組み合わせは次のとおりです。

| ベンダー | バージョン |
|---|---|
| oracle | 1.8 |
| oracle | 1.11 |
| oracle | 11 |
| sun | 1.8 |
| 日 | 1.11 |
| 日 | 11 |

>[!NOTE]
>
>2022年4月以降、Oracle JDK は、AEM アプリケーションの開発と運用のためのデフォルト JDK になります。Cloud Manager のビルドプロセスは、Maven ツールチェーンで代替オプションが明示的に選択されている場合でも、OracleJDK を使用してに自動的に切り替わります。 詳しくは、 [4 月のリリースノート](/help/release-notes/2022/2022-4-0.md) 詳しくは、を参照してください。

### Maven 実行の代替 JDK バージョン {#alternate-maven}

また、Maven の実行全体の JDK としてOracle8 またはOracle11 を選択することもできます。 この場合は、ツールチェーンオプションとは異なり、ツールチェーン設定も指定される場合を除き、すべてのプラグインに使用される JDK が変更されます。ツールチェーン設定が指定される場合は、そのツールチェーン設定が引き続きツールチェーン対応 Maven プラグインに適用されます。その結果、[Apache Maven Enforcer Plugin](https://maven.apache.org/enforcer/maven-enforcer-plugin/) を使用して Java バージョンを確認および強制することができます。

それには、パイプラインで使用される Git リポジトリーブランチに `.cloudmanager/java-version` というファイルを作成します。このファイルには、次のいずれかのコンテンツを含めることができます `11` または `8`. その他の値は無視されます。If `11` が指定されている場合、Oracle11 が使用され、 `JAVA_HOME` 環境変数はに設定されます。 `/usr/lib/jvm/jdk-11.0.2`. If `8` が指定されている場合、Oracle8 が使用され、 `JAVA_HOME` 環境変数はに設定されます。 `/usr/lib/jvm/jdk1.8.0_202`.

## 環境変数 {#environment-variables}

### 標準環境変数 {#standard-environ-variables}

場合によっては、プログラムやパイプラインに関する情報に基づいてビルドプロセスを変更する必要があります。

例えば、gulp などのツールを使用してビルド時の JavaScript の縮小をおこなう場合、開発環境でビルドする際には、ステージング用と実稼動用にビルドする場合とは異なる、別の縮小レベルを使用する必要が生じる場合があります。

これをサポートするために、Cloud Manager は、各実行の標準環境変数をビルドコンテナに追加します。

| 変数名 | 説明 |
|---|---|
| `CM_BUILD` | 常に `true` に設定 |
| `BRANCH` | 実行用に設定されたブランチ |
| `CM_PIPELINE_ID` | 数値パイプライン識別子 |
| `CM_PIPELINE_NAME` | パイプライン名 |
| `CM_PROGRAM_ID` | 数値プログラム識別子 |
| `CM_PROGRAM_NAME` | プログラム名 |
| `ARTIFACTS_VERSION` | ステージングまたは実稼動パイプラインの場合、Cloud Manager で生成された合成バージョン |

### パイプライン変数 {#pipeline-variables}

場合によっては、ビルドプロセスが、Git リポジトリに格納するのに適さない特定の設定変数に依存する場合や、同じブランチを使用するパイプライン実行間で異なる必要がある場合があります。

Cloud Manager では、これらの変数を Cloud Manager API または Cloud Manager CLI を介してパイプラインごとに設定できます。変数は、プレーンテキストとして保存することも、保存時に暗号化することもできます。どちらの場合も、変数はビルド環境内で環境変数として使用可能になり、変数は `pom.xml` ファイル内または他のビルドスクリプト内から参照できます。

CLI を使用して変数を設定するには、次のようなコマンドを実行します。

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

現在の変数は、次のようなコマンドを使用してリストできます。

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

変数は、一定の制限に従う必要があります。

* 変数名に使用できるのは、英数字とアンダースコア (`_`) をクリックします。
   * 慣例により、名前はすべて大文字にする必要があります。
* 変数の数はパイプラインあたり最大 200 個までです。
* 名前は 100 文字未満にする必要があります。
* 各文字列値は 2048 文字未満にする必要があります。
* 各 secretString 値は、500 文字未満にする必要があります。

Maven 内で使用する場合 `pom.xml` ファイルにマッピングする場合は、通常、次のような構文を使用して、これらの変数を Maven プロパティにマッピングすると便利です。

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

完全に機能させるために、一部のビルドでは追加のシステムパッケージをインストールする必要があります。 例えば、Python や Ruby のスクリプトを呼び出すビルドでは、適切な言語インタープリターをインストールする必要があります。 これを行うには、[`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/) を呼び出して、APT を起動します。この実行は通常、Cloud Manager 専用の Maven プロファイルにラップされます。例えば、Python をインストールするには：

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
>この方法でシステムパッケージをインストールしても、Adobe Experience Manager の実行に使用されているランタイム環境にはインストールされません。AEM 環境にシステムパッケージをインストールする必要がある場合は、アドビ担当者にお問い合わせください。
