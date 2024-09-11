---
title: 分岐の設定
description: Git で最初の分岐を設定する方法と、CI/CD パイプラインでアプリケーションコードをデプロイする際に分岐を使用する方法について説明します。
exl-id: ff2ae28f-902e-4fb2-aeb1-3636cb5cd9bb
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '324'
ht-degree: 100%

---


# 分岐の設定 {#configuring-branches}

Git で最初の分岐を設定する方法と、CI/CD パイプラインでアプリケーションコードをデプロイする際に分岐を使用する方法について説明します。

## Git での最初の分岐の設定 {#setting-up-your-first-branch-in-git}

Cloud Manager でオンボーディングされるプログラムごとに、最初は空の Git リポジトリが 1 つ[プロビジョニングされます](/help/requirements/environment-provisioning.md)。このリポジトリには、開発プロセスで対象とする数の分岐を格納できますが、アプリケーションコードをステージング環境および実稼動環境にデプロイする CI/CD パイプラインで使用される分岐が少なくとも 1 つ必要です。この分岐の名前として `main` を使用することをお勧めします。好都合なことに、このアプローチは、新規プロジェクトを設定する際の Git クライアントのデフォルト動作になっています。

例えば、新規プロジェクトを設定する場合、次のような一連のコマンドを実行します。

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
>必ずしも、コマンドラインクライアントを使用する必要はありません。スタンドアロンアプリケーションとして、または Eclipse や IntelliJ などの統合開発環境（IDE）の一部として使用できるグラフィカルな Git クライアントが各種あります。クライアントアプリケーションが HTTPS で Git をサポートしている限り、[!UICONTROL Cloud Manager] と互換性がある必要があります。

## 最初の分岐のプッシュ {#pushing-your-first-branch}

1 つ以上のリビジョンをコミットしたら、[!UICONTROL Cloud Manager] リポジトリをリモートとして追加した後、そのリポジトリにコミットをプッシュできます。

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
>[!UICONTROL Cloud Manager] のオンボーディング中に、アドビ CSE（カスタマーサクセスエンジニア）からユーザーに具体的な URL と資格情報が提供されます。

## 追加の分岐 {#additional-branches}

非常にシンプルなプロジェクトにはただ 1 つの `main` 分岐でも十分なことがありますが、ほとんどの場合は、より複雑な分岐戦略が必要になります。多くのお客様は、`develop` という分岐で日常的な開発アクティビティを実行するプロセスに従います。デプロイメントの際に、開発分岐は `main` 分岐に結合されます。

>[!TIP]
>
>よく使用される Git コマンドについて詳しくは、[Git チートシート](https://training.github.com/downloads/github-git-cheat-sheet)を参照してください。
