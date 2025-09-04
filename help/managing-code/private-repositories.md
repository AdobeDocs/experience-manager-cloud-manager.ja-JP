---
title: Cloud Manager でのプライベートリポジトリの追加
description: 独自のプライベート GitHub リポジトリを操作する Cloud Manager を設定する方法について説明します。
feature: Release Information
exl-id: e0d103c9-c147-4040-bf53-835e93d78a0b
source-git-commit: 34c0b39d50dd4998cb75cc032d71d24798dee729
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 90%

---


# Cloud Manager でのプライベートリポジトリの追加 {#private-repositories}

独自のプライベート GitHub リポジトリを操作する Cloud Manager を設定する方法について説明します。

## 概要 {#overview}

Cloud Manager をプライベート GitHub リポジトリで設定すると、GitHub 内でコードを直接検証できるので、Adobe リポジトリと頻繁に同期する必要がなくなります。

>[!NOTE]
>
>この機能は、パブリック GitHub 専用です。自己ホスト型 GitHub のサポートは利用できません。

## 設定 {#configuration}

設定は、次の 2 つの主な手順で構成されます。

1. [リポジトリを追加](#add-repo)
1. [プライベートリポジトリの所有権の検証](#validate-ownership)



### リポジトリの追加 {#add-repo}

1. Cloud Manager の&#x200B;**プログラムの概要**&#x200B;ページで、「**リポジトリ**」タブをクリックして&#x200B;**リポジトリ**&#x200B;ページに切り替え、「**リポジトリを追加**」をクリックします。

1. **リポジトリを追加**&#x200B;ダイアログボックスで、リポジトリタイプとして「**プライベートリポジトリ**」を選択します。

1. リポジトリの詳細を指定します

   * **リポジトリ名** - 表現名
   * **リポジトリ URL** - リポジトリの URL。`.git` で終了する必要があります。
   * **説明**（オプション）- 必要に応じてリポジトリの詳細な説明

   ![独自のリポジトリの追加](/help/assets/repositories/add-own-github.png)

1. 「**保存**」をクリックします。

>[!TIP]
>
>Cloud Manager でのリポジトリ管理について詳しくは、[Cloud Manager リポジトリ](/help/managing-code/managing-repositories.md)を参照してください。



### プライベートリポジトリ所有権の検証 {#validate-ownership}

Cloud Manager は GitHub リポジトリを認識しましたが、引き続きアクセスする必要があります。アクセス権を付与するには、Adobe GitHub アプリをインストールし、指定したリポジトリを所有していることを確認する必要があります。

1. 独自のリポジトリを追加すると、**プライベートリポジトリの所有権の検証**&#x200B;ダイアログボックスが表示されます。

   ![プライベートリポジトリの所有権の検証](/help/assets/repositories/private-repo-validate.png)

1. Cloud Manager は、GitHub アプリを使用して、リポジトリと安全にやり取りします。

   GitHub 組織の所有者は、`https://github.com/apps/cloud-manager-for-aem` にあるアプリをインストールし、リポジトリへのアクセス権を付与する必要があります。詳しくは、GitHub のドキュメントを参照してください。

1. セキュリティを強化するには、リポジトリのデフォルトのブランチに秘密鍵ファイルを作成します。「**生成**」をクリックします。

1. 「**確認**」をクリックして、秘密鍵ファイルの生成を確認します。

   ![秘密鍵の生成の確認](/help/assets/repositories/confirm-generation.png)

1. **プライベートリポジトリの所有権の検証**&#x200B;ダイアログボックスに戻ると、Cloud Manager は「**秘密鍵ファイルコンテンツ**」フィールドにコンテンツを生成しています。そのフィールドからコンテンツをコピーします。

   秘密鍵ファイルのコンテンツは 1 回だけ表示されます。このウィンドウを閉じる前にコンテンツをコピーしない場合は、秘密鍵を再生成する必要があります。

   ![秘密鍵ファイルコンテンツのコピー](/help/assets/repositories/new-secret.png)

1. GitHub リポジトリのデフォルトブランチに `.well-known/adobe/cloud-manager-challenge` という名前の新しいファイルを作成し、秘密鍵ファイルコンテンツをそのファイルにペーストして保存します。

1. アプリがインストールされ、秘密鍵ファイルがリポジトリに存在すると、**プライベートリポジトリの所有権の検証**&#x200B;ダイアログで「**検証**」をクリックできます。

アプリのインストールと秘密鍵ファイルの生成は、任意の順序で行うことができます。ただし、検証する前に両方の手順を完了する必要があります。

検証されるまで、リポジトリは赤色のアイコンで表示されます。これは、リポジトリがまだ検証されておらず、まだ使用できないことを示します。

![未検証のリポジトリ](/help/assets/repositories/unvalidated-repo.png)

**タイプ**&#x200B;列では、アドビ提供のリポジトリ（**Adobe**）と独自の GitHub リポジトリ（**GitHub**）を簡単に識別できます。

後でリポジトリに戻って検証を完了するには、**リポジトリ**&#x200B;ページに移動します。追加した GitHub リポジトリの横にある ![ 詳細アイコン、省略記号 ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) をクリックし、**所有権の検証** をクリックします。


## Cloud Manager でのプライベートリポジトリの使用 {#using}

Cloud Manager で GitHub リポジトリを検証すると統合が完了し、Cloud Manager でリポジトリを使用できるようになります。

**Cloud Manager でプライベートリポジトリを使用するには：**

1. プルリクエストを作成すると、GitHub チェックが自動的に開始します。

   ![GitHub チェック](/help/assets/repositories/github-checks.png)

1. プルリクエストごとに、[フルスタックコード品質パイプライン](/help/using/managing-pipelines.md)が自動的に作成されます。このパイプラインは、プルリクエストの更新のたびに開始されます。

1. GitHub チェックは、コード品質チェックが完了するまで、実行中状態のままになります。 コード品質の結果は、GitHub チェックに生成されます。

   ![GitHub コード品質チェック](/help/assets/repositories/github-code-quality.png)

プルリクエストが閉じられるか結合されると、作成したフルスタックコード品質パイプラインが自動的に削除されます。

>[!TIP]
>
>プルリクエストチェックの実行時に GitHub 経由で提供される情報について詳しくは、[GitHub チェック注釈](github-annotations.md)ドキュメントを参照してください。

>[!TIP]
>
>プライベートリポジトリに対する各プルリクエストを検証するために自動的に作成されるパイプラインは、制御することができます。詳しくは、[プライベートリポジトリに対する GitHub チェック設定](github-check-config.md)を参照してください。



## プライベートリポジトリとパイプラインの関連付け {#pipelines}

検証済みのプライベートリポジトリは、[フルスタックパイプラインおよびフロントエンドパイプライン](/help/overview/ci-cd-pipelines.md)に関連付けることができます。



## 制限事項 {#limitations}

Cloud Manager でプライベートリポジトリを使用する場合は、特定の制限が適用されます。

* 実稼動のフルスタックパイプラインでプライベートリポジトリを使用する場合、Git タグは作成およびプッシュされません。
* Adobe GitHub アプリを GitHb 組織から削除すると、このアクションはすべてのリポジトリのプルリクエスト検証機能を削除します。
* プライベートリポジトリを使用するパイプラインと、コミット済みのビルドトリガーは、新しいコミットが選択したブランチにプッシュされても、自動的には開始されません。
* [アーティファクト再利用機能](/help/getting-started/project-setup.md#build-artifact-reuse)は、プライベートリポジトリには適用されません。
* Cloud Manager の GitHub チェックを使用して、プルリクエストの検証を一時停止することはできません。GitHub リポジトリが Cloud Manager で検証されている場合、Cloud Manager は、そのリポジトリに対して作成されたプルリクエストの検証を試みます。
* GitHub 組織が IP 制限を実施する場合は、サポートケースを開いて、許可する必要がある IP アドレスのリストを取得します。
