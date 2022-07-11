---
title: Dispatcher の設定
description: Cloud Manager を使用して Dispatcher 設定ファイルをデプロイする方法について説明します.
exl-id: ffc2b60e-bde7-48ca-b268-dea0f8fd4e30
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 15%

---


# Dispatcher の設定 {#manage-your-dispatcher-configurations}

Cloud Manager を使用して Dispatcher 設定ファイルをデプロイする方法について説明します

## Cloud Manager での Dispatcher 設定のデプロイ {#deploying-dispatcher-configurations}

Cloud Manager では、Web サーバーと Dispatcher の設定ファイルが、通常のAEMコンテンツパッケージと共に Git リポジトリに格納されていると仮定して、それらの設定ファイルをデプロイできます。

この機能を活用するために、Maven ビルドでは、少なくとも 2 つのディレクトリを含む.zip ファイルを作成する必要があります。 `conf` および `conf.d`. この.zip ファイルは、 `maven-assembly-plugin`.

組み込みを使用して Cloud Manager で生成されたプロジェクト [プロジェクト作成ウィザード](/help/getting-started/using-the-wizard.md) 適切な Maven プロジェクト構造が自動的に作成されている。 Adobe Managed Services(AMS) を初めて使用する場合は、このパスをお勧めします。

Dispatcher インスタンスにデプロイすると、Dispatcher インスタンス上のこれらのディレクトリの内容が Git リポジトリ内の内容で上書きされます。 Web サーバーおよび Dispatcher 設定ファイルを正しく使用するには、頻繁に環境固有の情報が必要になるので、最初にカスタマーサクセスエンジニア (CSE) に依頼して、これらの環境変数を `/etc/sysconfig/httpd`.

## 既存の Managed Services のお客様向けの Dispatcher 設定 {#steps-for-configuring-dispatcher}

以下の手順に従って、最初の Dispatcher 設定を完了します。

1. 現在の実稼動設定ファイルを CSE から取得します。
1. 公開レンダラー IP など、ハードコードされた環境固有のデータを削除し、変数に置き換えます。
1. 各ターゲット Dispatcher に対して必要な変数をキーと値のペアで定義し、CSE に依頼してに追加します。 `/etc/sysconfig/httpd` 各インスタンスで
1. ステージング環境で更新された設定をテストします。
1. テストが完了したら、CSE に依頼して実稼動環境にデプロイします。
1. ファイルを Git リポジトリにコミットします。
1. Cloud Manager を使用してデプロイします。

>[!NOTE]
>
>Dispatcher と Web サーバーの設定の Git リポジトリへの移行は、Cloud Manager のオンボーディング時におこなうことができますが、後でおこなうこともできます。

### 例 {#example}

特定のファイルおよびディレクトリ構造は、プロジェクトの仕様によって異なる場合がありますが、この例では、Apache および Dispatcher 設定を含めるためのプロジェクトの構築方法に関する具体的なガイドを提供する必要があります。

1. サブディレクトリを作成し、`dispatcher` という名前を付けます。

   ここでは任意の名前を使用できますが、この手順で作成したディレクトリ名は、手順 6 で使用した名前と同じにする必要があります。

1. このサブディレクトリには、Maven Assembly プラグインを使用して Dispatcher .zip ファイルを構築する Maven モジュールが含まれます。 これを開始するには、 `dispatcher` ディレクトリ、 `pom.xml` ファイルにこのコンテンツを含め、 `parent` 参照 `artifactId`、および `name` 必要に応じて。

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <project xmlns="http://maven.apache.org/POM/4.0.0"
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
       <modelVersion>4.0.0</modelVersion>
       <parent>
           <!-- reference to your parent pom -->
       </parent>
   
       <artifactId>dispatcher</artifactId> <!-- feel free to change this -->
       <packaging>pom</packaging>
       <name>dispatcher</name> <!-- feel free to change this -->
   
       <build>
           <plugins>
               <plugin>
                   <groupId>org.apache.maven.plugins</groupId>
                   <artifactId>maven-assembly-plugin</artifactId>
                   <version>3.1.0</version>
                   <executions>
                       <execution>
                           <phase>package</phase>
                           <goals><goal>single</goal></goals>
                           <configuration>
                               <descriptors>
                                   <descriptor>assembly.xml</descriptor>
                               </descriptors>
                               <appendAssemblyId>false</appendAssemblyId>
                           </configuration>
                       </execution>
                   </executions>
               </plugin>
           </plugins>
       </build>
   </project>
   ```

   * 手順 1 と同様に、ここにある artifactId と名前は、必要に応じて他の値にすることができます。 `dispatcher` は、ここでは例として使用しています。

1. Maven Assembly プラグインには、 `descriptor` .zip ファイルの作成方法を定義します。 この記述子を作成するには、 `dispatcher` サブディレクトリ名 `assembly.xml` を次の内容で置き換えます。 このファイル名は、上記の `pom.xml` ファイルの 26 行目で参照されることに注意してください。

   ```xml
   <assembly xmlns="http://maven.apache.org/ASSEMBLY/2.0.0"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://maven.apache.org/ASSEMBLY/2.0.0 http://maven.apache.org/xsd/assembly-2.0.0.xsd">
     <id>distribution</id>
     <formats>
       <format>zip</format>
     </formats>
     <includeBaseDirectory>false</includeBaseDirectory>
     <fileSets>
       <fileSet>
         <directory>${basedir}/src</directory>
         <includes>
           <include>**/*</include>
         </includes>
         <outputDirectory></outputDirectory>
       </fileSet>
     </fileSets>
   </assembly>
   ```

1. サブディレクトリを作成し、 `src` （上記の 11 行目のアセンブリ記述子で参照されたもの）dispatcher サブディレクトリ内で、実際の Apache および Dispatcher 設定を保存します。 この `src` ディレクトリ内に、`conf`、`conf.d`、`conf.dispatcher.d` および `conf.modules.d` という名前のディレクトリを作成します。

1. 次の項目に `conf`, `conf.d`, `conf.dispatcher.d`、および `conf.modules.d` ディレクトリに設定ファイルを格納します。 例えば、デフォルト設定は、これらのファイルとシンボリックリンクで構成されています。

   ```
   dispatcher
   ├── assembly.xml
   ├── pom.xml
   └── src
       ├── conf
       │  ├── httpd.conf
       │  └── magic
       ├── conf.d
       │  ├── README
       │  ├── autoindex.conf
       │  ├── available_vhosts
       │  │  ├── aem_author.vhost
       │  │  ├── aem_flush.vhost
       │  │  ├── aem_health.vhost
       │  │  ├── aem_lc.vhost
       │  │  └── aem_publish.vhost
       │  ├── dispatcher_vhost.conf
       │  ├── enabled_vhosts
       │  │  ├── aem_author.vhost -> ../available_vhosts/aem_author.vhost
       │  │  ├── aem_flush.vhost -> ../available_vhosts/aem_flush.vhost
       │  │  └── aem_publish.vhost -> ../available_vhosts/aem_publish.vhost
       │  ├── rewrites
       │  │  ├── base_rewrite.rules
       │  │  └── xforwarded_forcessl_rewrite.rules
       │  ├── userdir.conf
       │  ├── variables
       │  │  └── ams_default.vars
       │  ├── welcome.conf
       │  └── whitelists
       │      └── 000_base_whitelist.rules
       ├── conf.dispatcher.d
       │  ├── available_farms
       │  │  ├── 000_ams_author_farm.any
       │  │  ├── 001_ams_lc_farm.any
       │  │  └── 999_ams_publish_farm.any
       │  ├── cache
       │  │  ├── ams_author_cache.any
       │  │  ├── ams_author_invalidate_allowed.any
       │  │  ├── ams_publish_cache.any
       │  │  └── ams_publish_invalidate_allowed.any
       │  ├── clientheaders
       │  │  ├── ams_author_clientheaders.any
       │  │  ├── ams_common_clientheaders.any
       │  │  ├── ams_lc_clientheaders.any
       │  │  └── ams_publish_clientheaders.any
       │  ├── dispatcher.any
       │  ├── enabled_farms
       │  │  ├── 000_ams_author_farm.any -> ../available_farms/000_ams_author_farm.any
       │  │  └── 999_ams_publish_farm.any -> ../available_farms/999_ams_publish_farm.any
       │  ├── filters
       │  │  ├── ams_author_filters.any
       │  │  ├── ams_lc_filters.any
       │  │  └── ams_publish_filters.any
       │  ├── renders
       │  │  ├── ams_author_renders.any
       │  │  ├── ams_lc_renders.any
       │  │  └── ams_publish_renders.any
       │  └── vhosts
       │      ├── ams_author_vhosts.any
       │      ├── ams_lc_vhosts.any
       │      └── ams_publish_vhosts.any
       └── conf.modules.d
           ├── 00-base.conf
           ├── 00-dav.conf
           ├── 00-lua.conf
           ├── 00-mpm.conf
           ├── 00-proxy.conf
           ├── 00-systemd.conf
           ├── 01-cgi.conf
           └── 02-dispatcher.conf
   ```

1. 最後に、 `pom.xml` ファイルをプロジェクトのルートに追加し、 `<module>` 要素を使用して dispatcher モジュールを組み込みます。

   例えば、既存のモジュールリストが以下の場合、

   ```xml
       <modules>
           <module>core</module>
           <module>ui.apps</module>
           <module>ui.content</module>
       </modules>
   ```

   以下のように変更する必要があります。

   ```xml
       <modules>
           <module>core</module>
           <module>ui.apps</module>
           <module>ui.content</module>
           <module>dispatcher</module>
       </modules>
   ```

   * 手順 1 で述べたように、 `<module>` 要素は、作成されたディレクトリ名と一致する必要があります。

1. テストするには、を実行します。 `mvn clean package` 」と入力します。 出力には、次のような行が表示されます。

   ```
   [INFO] --- maven-assembly-plugin:3.1.0:single (default) @ dispatcher ---
   [INFO] Reading assembly descriptor: assembly.xml
   [INFO] Building zip: /Users/me/mycompany/dispatcher/target/dispatcher-1.0-SNAPSHOT.zip
   ```

   このファイルを解凍して、コンテンツを表示することもできます。

   ```shell
   $ unzip -l dispatcher/target/dispatcher-1.0-SNAPSHOT.zip
   Archive:  dispatcher/target/dispatcher-1.0-SNAPSHOT.zip
     Length      Date    Time    Name
   ---------  ---------- -----   ----
           0  09-12-2018 12:53   conf.modules.d/
           0  10-19-2018 10:38   conf.dispatcher.d/
           0  09-12-2018 12:53   conf.dispatcher.d/available_farms/
           0  09-12-2018 12:53   conf.dispatcher.d/filters/
           0  09-12-2018 12:53   conf.dispatcher.d/renders/
           0  09-12-2018 12:53   conf.dispatcher.d/cache/
           0  09-12-2018 12:53   conf.dispatcher.d/clientheaders/
           0  09-12-2018 12:53   conf.dispatcher.d/enabled_farms/
           0  09-12-2018 12:53   conf.dispatcher.d/vhosts/
           0  09-12-2018 12:53   conf.d/
           0  09-12-2018 12:53   conf.d/rewrites/
           0  09-12-2018 12:53   conf.d/whitelists/
           0  09-12-2018 12:53   conf.d/variables/
           0  11-01-2018 13:53   conf.d/enabled_vhosts/
           0  09-12-2018 12:53   conf.d/available_vhosts/
           0  09-12-2018 12:53   conf/
          88  09-12-2018 12:53   conf.modules.d/00-systemd.conf
        4913  09-12-2018 12:53   conf.dispatcher.d/available_farms/999_ams_publish_farm.any
         152  09-12-2018 12:53   conf.dispatcher.d/renders/ams_lc_renders.any
         490  09-12-2018 12:53   conf.dispatcher.d/clientheaders/ams_common_clientheaders.any
        1727  09-12-2018 12:53   conf.d/rewrites/base_rewrite.rules
          36  09-12-2018 12:53   conf.d/enabled_vhosts/aem_author.vhost
       11753  09-12-2018 12:53   conf/httpd.conf
         957  09-12-2018 12:53   conf.modules.d/00-proxy.conf
         944  09-12-2018 12:53   conf.dispatcher.d/available_farms/001_ams_lc_farm.any
         220  09-12-2018 12:53   conf.dispatcher.d/cache/ams_author_invalidate_allowed.any
          43  09-12-2018 12:53   conf.dispatcher.d/enabled_farms/999_ams_publish_farm.any
         516  09-12-2018 12:53   conf.d/welcome.conf
          37  09-12-2018 12:53   conf.d/enabled_vhosts/aem_publish.vhost
       13077  09-12-2018 12:53   conf/magic
          96  09-12-2018 12:53   conf.modules.d/02-dispatcher.conf
        2601  09-12-2018 12:53   conf.dispatcher.d/available_farms/000_ams_author_farm.any
         837  09-12-2018 12:53   conf.dispatcher.d/cache/ams_author_cache.any
          42  09-12-2018 12:53   conf.dispatcher.d/enabled_farms/000_ams_author_farm.any
        2926  09-12-2018 12:53   conf.d/autoindex.conf
        2555  09-12-2018 12:53   conf.d/available_vhosts/aem_lc.vhost
          41  09-12-2018 12:53   conf.modules.d/00-lua.conf
        2234  09-12-2018 12:53   conf.dispatcher.d/filters/ams_publish_filters.any
         220  09-12-2018 12:53   conf.dispatcher.d/cache/ams_publish_invalidate_allowed.any
         402  09-12-2018 12:53   conf.dispatcher.d/dispatcher.any
         573  09-12-2018 12:53   conf.d/whitelists/000_base_whitelist.rules
         871  09-12-2018 12:53   conf.d/available_vhosts/aem_flush.vhost
         139  09-12-2018 12:53   conf.modules.d/00-dav.conf
         742  09-12-2018 12:53   conf.dispatcher.d/filters/ams_author_filters.any
         557  09-12-2018 12:53   conf.dispatcher.d/cache/ams_publish_cache.any
         105  09-12-2018 12:53   conf.dispatcher.d/vhosts/ams_lc_vhosts.any
         101  09-12-2018 12:53   conf.dispatcher.d/vhosts/ams_publish_vhosts.any
        3582  09-12-2018 12:53   conf.d/dispatcher_vhost.conf
        2529  09-12-2018 12:53   conf.d/available_vhosts/aem_publish.vhost
         742  09-12-2018 12:53   conf.modules.d/00-mpm.conf
          88  09-12-2018 12:53   conf.dispatcher.d/filters/ams_lc_filters.any
         177  09-12-2018 12:53   conf.dispatcher.d/clientheaders/ams_lc_clientheaders.any
         366  09-12-2018 12:53   conf.d/README
        2723  09-12-2018 12:53   conf.d/available_vhosts/aem_author.vhost
        3739  09-12-2018 12:53   conf.modules.d/00-base.conf
         138  09-12-2018 12:53   conf.dispatcher.d/renders/ams_author_renders.any
          44  09-12-2018 12:53   conf.dispatcher.d/clientheaders/ams_publish_clientheaders.any
         112  09-12-2018 12:53   conf.dispatcher.d/vhosts/ams_author_vhosts.any
         580  09-12-2018 12:53   conf.d/variables/ams_default.vars
          35  09-12-2018 12:53   conf.d/enabled_vhosts/aem_flush.vhost
        1252  09-12-2018 12:53   conf.d/userdir.conf
         451  09-12-2018 12:53   conf.modules.d/01-cgi.conf
         321  09-12-2018 12:53   conf.dispatcher.d/renders/ams_publish_renders.any
         170  09-12-2018 12:53   conf.dispatcher.d/clientheaders/ams_author_clientheaders.any
         220  09-12-2018 12:53   conf.d/rewrites/xforwarded_forcessl_rewrite.rules
        1753  09-12-2018 12:53   conf.d/available_vhosts/aem_health.vhost
   ---------                     -------
       69017                     66 files
   ```
