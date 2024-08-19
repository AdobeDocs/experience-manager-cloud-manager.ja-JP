---
title: ブランチの設定
description: Git で最初のブランチを設定する方法と、CI/CD パイプラインでアプリケーションコードをデプロイするためにブランチを使用する方法について説明します。
exl-id: ff2ae28f-902e-4fb2-aeb1-3636cb5cd9bb
source-git-commit: 11a6a53d8cbfb689810a9a8e7d82293a49863084
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 14%

---


# ブランチの設定 {#configuring-branches}

Git で最初のブランチを設定する方法と、CI/CD パイプラインでアプリケーションコードをデプロイするためにブランチを使用する方法について説明します。

## Git での最初のブランチの設定 {#setting-up-your-first-branch-in-git}

Cloud Manager でオンボーディングされるプログラムごとに、最初は空の Git リポジトリが 1 つ[プロビジョニングされます](/help/requirements/environment-provisioning.md)。このリポジトリーには、開発プロセスで必要な数のブランチを格納できますが、アプリケーションコードをステージングおよび実稼動環境にデプロイするために CI/CD パイプラインで使用されるブランチが少なくとも 1 つ必要です。 このブランチの名前として `main` を使用することをお勧めします。好都合なことに、この方法は、新規プロジェクトを設定する際の Git クライアントのデフォルトの動作になっています。

例えば、新しいプロジェクトを設定する場合は、次のような一連のコマンドを実行します。

```shell
$ git init
Initialized empty Git repository in /Users/myname/workspace/new-project/.git/
... steps which add Maven build files and source code ...
$ git add pom.xml core/pom.xml core/src ui.apps/pom.xml ui.apps/src
$ git commit -m "initial commit"
 19 files changed, 777 insertions(+)
 create mode 100644 core/pom.xml
 create mode 100644 pom.xml
 create mode 100644 ui.apps/pom.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/config.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/definition/.content.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/filter.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/nodetypes.cnd
 create mode 100644 ui.apps/src/main/content/META-INF/vault/properties.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/apps/my-aem-project/install/.vltignore
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/policies/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/policies/_rep_policy.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/template-types/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/template-types/_rep_policy.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/templates/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/templates/_rep_policy.xml
```

>[!NOTE]
>
>コマンドラインクライアントを使用する必要はありません。 スタンドアロンアプリケーションとして、または Eclipse や IntelliJ などの統合開発環境（IDE）の一部として使用できるグラフィカルな Git クライアントが各種あります。 クライアントアプリケーションが HTTPS で Git をサポートしている限り、[!UICONTROL Cloud Manager] と互換性がある必要があります。

## 最初のブランチのプッシュ {#pushing-your-first-branch}

1 つ以上のリビジョンをコミットした場合は、[!UICONTROL Cloud Manager] リポジトリをリモートとして追加した後、そのリポジトリにコミットをプッシュできます。

```shell
$ git remote add adobe <url>
$ git push adobe master
Counting objects: 36, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (27/27), done.
Writing objects: 100% (36/36), 7.31 KiB | 1.83 MiB/s, done.
Total 36 (delta 6), reused 0 (delta 0)
To <url>
 * [new branch]      main -> main
```

>[!NOTE]
>
>[!UICONTROL Cloud Manager] のオンボーディング中に、AdobeCSE （カスタマーサクセスエンジニア）から具体的な URL と資格情報が提供されます。

## 追加のブランチ {#additional-branches}

非常に単純なプロジェクトでは 1 つの `main` ブランチで十分な場合もありますが、ほとんどの場合、より複雑なブランチ戦略が必要になります。 多くのお客様は、「`develop`」というブランチで日々の開発活動を実行するプロセスに従います。 開発ブランチは、デプロイメントの時期になると `main` ブランチに結合されます。

>[!TIP]
>
>よく使用される Git コマンドについては、[Git チートシート ](https://training.github.com/downloads/github-git-cheat-sheet) を参照してください。
