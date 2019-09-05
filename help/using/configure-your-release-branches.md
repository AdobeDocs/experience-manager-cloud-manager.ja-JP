---
title: リリースブランチの設定
seo-title: リリースブランチの設定
description: Git での AEM Cloud Manager 用リリースブランチの設定
seo-description: このページでは、Git でリリースブランチを設定する方法について説明します。
uuid: d12a8b85-b7fd-4b55-a05a-a0f874ce598c
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER／CLOUDMANAGER
topic-tags: getting-started
discoiquuid: 53807ea6-9464-429d-9322-85c9f405dff6
translation-type: ht
source-git-commit: 9c0df236c1e800802d62dea09996bb8e1e7033f7

---


# リリースブランチの設定 {#configure-your-release-branches}

## Git での最初のブランチの設定 {#setting-up-your-first-branch-in-git}

Cloud Manager でオンボーディングされるプログラムごとに、最初は空の **Git リポジトリ**&#x200B;が 1 つプロビジョニングされます。このリポジトリには、開発プロセスで対象とする数のブランチを格納できますが、アプリケーションコードをステージングおよび実稼動環境にデプロイするために CI／CD パイプラインで使用されるブランチが少なくとも 1 つ必要です。このブランチの名前として`master`を使用することをお勧めします。好都合なことに、これは、新規プロジェクトを設定する際の Git クライアントのデフォルト動作になっています。

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

## 最初のブランチのプッシュ {#pushing-your-first-branch}

少なくとも 1 つのリビジョンをコミットしたら、[!UICONTROL Cloud Manager] リポジトリを&#x200B;**リモート**&#x200B;リポジトリとして追加した後、そこにコミットを次のようにプッシュできます。

```shell
$ git remote add adobe <url>
$ git push adobe master
Counting objects: 36, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (27/27), done.
Writing objects: 100% (36/36), 7.31 KiB | 1.83 MiB/s, done.
Total 36 (delta 6), reused 0 (delta 0)
To <url>
 * [new branch]      master -> master
```

>[!NOTE]
>
>[!UICONTROL Cloud Manager] のオンボーディング中に、カスタマーサクセスエンジニアからユーザーに具体的な URL と資格情報が提供されます。

## 追加のブランチ {#additional-branches}

非常にシンプルなプロジェクトにはただ 1 つの`master`ブランチでも十分なことがありますが、ほとんどの場合は、より複雑なブランチ戦略が必要になります。多くの顧客が従っているプロセスでは、`develop`というブランチで日々の開発アクティビティが実行され、デプロイメント時に開発ブランチが`master`ブランチに結合されます。

>[!NOTE]
>
>よく使用される Git コマンドについては、[Git チートシート](https://github.github.com/training-kit/downloads/github-git-cheat-sheet)を参照してください。
