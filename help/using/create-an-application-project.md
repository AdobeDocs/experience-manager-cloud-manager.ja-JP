---
title: AEM アプリケーションプロジェクトの作成
seo-title: AEM アプリケーションプロジェクトの作成
description: 'null'
seo-description: Cloud Manager の使用を開始する際の AEM プロジェクトの設定について説明します。
uuid: 7b976ebf-5358-49d8-a58d-0bae026303fa
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER／CLOUDMANAGER
topic-tags: getting-started
discoiquuid: 76c1a8e4-d66f-4a3b-8c0c-b80c9e17700e
translation-type: tm+mt
source-git-commit: 81f4e0b3b31a8be1f0620b70442b0268159e4ec0

---


# AEM アプリケーションプロジェクトの作成 {#create-an-aem-application-project}

## ウィザードを使用した AEM アプリケーションプロジェクトの作成 {#using-wizard-to-create-an-aem-application-project}

ユーザーが Cloud Manager にオンボーディングされると、空の Git リポジトリが提供されます。現在の Adobe Managed Services（AMS）ユーザー（または AMS に移行中のオンプレミス AEM ユーザー）は、通常、プロジェクトコードを既に Git（または別のバージョン管理システム）に格納してあり、プロジェクトを Cloud Manager の Git リポジトリにインポートすることになります。ただし、新規ユーザーは既存のプロジェクトを持っていません。

新規ユーザーが作業に着手しやすくなるように、Cloud Manager では、最小限の AEM プロジェクトを出発点として作成できるようになりました。This process is based on the [**AEM Project Archetype**](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-10-08T12:52:50.071-0400

2018.8.0: Added this new section

 -->

Cloud Manager で AEM アプリケーションプロジェクトを作成するには、次の手順に従います。

1. Cloud Manager にログインし、基本的なプログラム設定が完了すると、リポジトリが空の場合、**概要**&#x200B;画面に特別なコールトゥアクションカードが表示されます。

   ![](assets/image2018-10-3_14-29-44.png)

1. 「**作成**」をクリックして、**パイプライン設定**&#x200B;画面に移動します。

   ![](assets/image2018-10-3_14-30-22.png)

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

* 追加の Maven アーティファクトリポジトリへの参照を *pom.xml* ファイルに追加できます。ただし、パスワードで保護またはネットワークで保護されたアーティファクトリポジトリへのアクセスはサポートされていません。
* デプロイ可能なコンテンツパッケージは、*target* という名前のディレクトリに含まれているコンテンツパッケージ *zip* ファイルをスキャンすることで検出されます。任意の数のサブモジュールでコンテンツパッケージを作成することもできます。

* デプロイ可能な Dispatcher アーティファクトは、*conf* および *conf.d* というディレクトリを持つ *zip* ファイル（これも *target* という名前のディレクトリに含まれる）をスキャンすることで検出されます

* 複数のコンテンツパッケージがある場合、パッケージデプロイメントの順序は保証されません。特定の順序が必要な場合は、コンテンツパッケージの依存関係を使用して順序を定義できます。

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-10-08T09:20:10.106-0400

2018.8.0: added existing in the opening sentence

 -->

## ビルド環境の詳細 {#build-environment-details}

特殊なビルド環境を使用してコードを作成およびテストします。この環境には次のような特性があります。

* ビルド環境は、Ubuntu18.04から派生するLinuxベースです。
* Apache Maven 3.6.0 がインストールされています。
* インストールされている Java のバージョンは Oracle JDK 8u202 です。
* 必要な追加のシステムパッケージが、次のようにいくつかインストールされています。

   * bzip2
   * unzip
   * libpng
   * imagemagick
   * graphicsmagick

* その他のパッケージは、以下に説明 [するようにビルド時にインストール](#installing-additional-system-packages)できます。
* すべてのビルドは、Pristine 環境で実行されます。ビルドコンテナは実行から次回の実行までの間、状態を保持しません。
* Maven は常に *mvn --batch-mode clean org.jacoco:jacoco-maven-plugin:prepare-agent package* というコマンドで実行されます。
* Maven は、settings.xml ファイルを使用してシステムレベルで設定されます。このファイルには、アドビの公開&#x200B;**アーティファクト**&#x200B;リポジトリが自動的に含まれています(Refer to [Adobe Public Maven Repository](https://repo.adobe.com/) for more details).

## Cloud Manager での Maven プロファイルのアクティブ化 {#activating-maven-profiles-in-cloud-manager}

ごく一部のケースでは、開発用ワークステーションで実行する場合とは異なり、Cloud Manager 内で実行する場合にはビルドプロセスを少し変える必要が出ることもあります。この場合は、[Maven プロファイル](https://maven.apache.org/guides/introduction/introduction-to-profiles.html)を使用して、Cloud Manager を含む環境ごとのビルドの違いを定義できます。

Cloud Manager ビルド環境内での Maven プロファイルのアクティブ化は、`CM_BUILD` という名前の環境変数があるかどうかを調べることでおこなう必要があります。この変数は、常に Cloud Manager ビルド環境内で設定されます。逆に、Cloud Manager ビルド環境以外でのみ使用するためのプロファイルは、この変数がないかどうかを調べることでアクティブ化する必要があります。

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

## カスタム環境変数

場合によっては、顧客のビルドプロセスが、Git リポジトリに格納するのに適さない特定の設定変数に依存していることがあります。Cloud Manager では、カスタマーサクセスエンジニア（CSE）がこれらの変数を顧客別に設定できます。これらの変数は、安全な格納先に保存され、特定の顧客のビルドコンテナにのみ表示されます。この機能を使用する顧客は、担当の CSE に連絡して変数を設定してもらう必要があります。

設定が完了すると、これらの変数は環境変数として使用可能になります。これらの変数を Maven プロパティとして使用するには、pom.xml ファイルを参照します（変数は、前述のようにプロファイル内にあるはずです）。

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                  <property>
                        <name>env.CM_BUILD</name>
                  </property>
            </activation>
            <properties>
                  <my.custom.property>${env.MY_CUSTOM_PROPERTY}</my.custom.property>  
            </properties>
        </profile>
```

>[!NOTE]
>
>環境変数名に使用できるのは、英数字と下線（_）のみです。慣例では、名前はすべて大文字である必要があります。

## 追加のシステムパッケージのインストール {#installing-additional-system-packages}

一部のビルドでは、完全に機能するために追加のシステムパッケージをインストールする必要があります。例えば、ビルドでPythonまたはrubyスクリプトを呼び出し、結果として適切な言語インタープリターをインストールする必要があるとします。これは [、](https://www.mojohaus.org/exec-maven-plugin/) exec- maven- pluginを呼び出してAPTを呼び出すことで実行できます。この実行は通常、Cloud Manager固有のMavenプロファイルに含める必要があります。例えば、Pythonをインストールするには:

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

この方法は、言語固有のパッケージ（RubyGEMやPythonパッケージ用など `gem` ）のインストールに `pip` も使用できます。

>[!NOTE]
>
>この方法でシステムパッケージをインストールしても、 **Adobe Experience Managerの実行に使用されるランタイム環境に** はインストールされません。AEM環境にインストールされているシステムパッケージが必要な場合は、カスタマーサクセスエンジニア（CSE）にお問い合わせください。

## ベストプラクティスに基づくコードの開発 {#develop-your-code-based-on-best-practices}

Adobe Engineering and Consulting teams have developed a [comprehensive set of best practices for AEM developers](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/best-practices.html).
