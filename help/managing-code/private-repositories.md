---
title: Cloud Manager でのプライベートリポジトリの追加
description: 独自のプライベート GitHub リポジトリを操作するために Cloud Manager を設定する方法について説明します。
feature: Release Information
exl-id: e0d103c9-c147-4040-bf53-835e93d78a0b
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 83%

---


# Cloud Manager でのプライベートリポジトリの追加 {#private-repositories}

独自の プライベート GitHub リポジトリを操作するために Cloud Manager を設定する方法について説明します。

## 概要 {#overview}

独自のプライベート GitHub リポジトリを操作すると、Cloud Manager を通じて GitHub リポジトリ内でコードを直接検証できるので、コードを Adobe リポジトリと一貫して同期する必要がなくなります。

>[!NOTE]
>
>この機能は、パブリック GitHub 専用です。自己ホスト型 GitHub のサポートは利用できません。

## 設定 {#configuration}

設定は、次の 2 つの主な手順で構成されます。

1. [リポジトリを追加](#add-repo)
1. [プライベートリポジトリの所有権の検証](#validate-ownership)

### リポジトリを追加 {#add-repo}

1. Cloud Managerの **プログラムの概要** ページで、「**リポジトリ**」タブをクリックして **リポジトリ** ページに切り替え、「**リポジトリを追加**」をクリックします。

1. **リポジトリを追加**&#x200B;ダイアログで、リポジトリタイプとして「**プライベートリポジトリ**」を選択します。

1. リポジトリの詳細を指定します

   * **リポジトリ名** - 表現名
   * **リポジトリ URL** - リポジトリの URL。`.git` で終了する必要があります。
   * **説明**（オプション）- 必要に応じてリポジトリの詳細な説明

   ![独自のリポジトリの追加](/help/assets/repositories/add-own-github.png)

1. 「**保存**」をクリックします。

>[!TIP]
>
>Cloud Managerでのリポジトリの管理について詳しくは、[Cloud Manager リポジトリ ](/help/managing-code/managing-repositories.md) のドキュメントを参照してください。

### プライベートリポジトリの所有権の検証 {#validate-ownership}

Cloud Manager は GitHub リポジトリを認識しましたが、引き続きアクセスする必要があります。アクセス権を付与するには、Adobe GitHub アプリをインストールし、指定したリポジトリを所有していることを確認する必要があります。

1. 独自のリポジトリを追加した後、**プライベートリポジトリの所有権の検証**&#x200B;ダイアログが開きます。

   ![プライベートリポジトリの所有権の検証](/help/assets/repositories/private-repo-validate.png)

1. Cloud Manager は、GitHub アプリを使用して、リポジトリと安全にやり取りします。
   * GitHub 組織の所有者は、`https://github.com/apps/cloud-manager-for-aem` にあるアプリをインストールし、リポジトリへのアクセス権を付与する必要があります。
   * これを行う方法について詳しくは、GitHub のドキュメントを参照してください。

1. セキュリティを強化するには、リポジトリのデフォルトのブランチに秘密鍵ファイルを作成する必要があります。**生成** をクリックします。

1. **確認** をクリックして、シークレットファイルの生成を確認します。

   ![秘密鍵の生成の確認](/help/assets/repositories/confirm-generation.png)

1. **プライベートリポジトリの所有権の検証**&#x200B;ウィンドウに戻ると、Cloud Manager は「**秘密鍵ファイルコンテンツ**」フィールドにプライベートファイルのコンテンツを生成しています。そのフィールドからコンテンツをコピーします。

   * 秘密鍵ファイルのコンテンツは 1 回だけ表示されます。このウィンドウを閉じる前にコンテンツをコピーしない場合は、秘密鍵を再生成する必要があります。

   ![秘密鍵ファイルコンテンツのコピー](/help/assets/repositories/new-secret.png)

1. GitHub リポジトリのデフォルトブランチに `.well-known/adobe/cloud-manager-challenge` という名前の新しいファイルを作成し、秘密鍵ファイルコンテンツをそのファイルにペーストして保存します。

1. アプリをインストールし、秘密鍵ファイルがリポジトリに存在したら、**プライベートリポジトリ所有権の検証** ダイアログの **検証** をクリックします。

アプリのインストールと秘密鍵ファイルの作成は、任意の順序で行うことができます。ただし、検証する前に両方の手順を完了する必要があります。

検証されるまで、リポジトリは赤いアイコンで表示されます。これは、リポジトリがまだ検証されておらず、まだ使用できないことを示します。

![未検証のリポジトリ](/help/assets/repositories/unvalidated-repo.png)

**タイプ**&#x200B;列では、アドビ提供のリポジトリ（**Adobe**）と独自の GitHub リポジトリ（**GitHub**）を簡単に識別できます。

後でリポジトリに戻って検証を完了する必要がある場合は、**リポジトリ** ページで、追加した GitHub リポジトリを表す行の省略記号ボタンをクリックし、ドロップダウンメニューから **所有権の検証** を選択します。

## Cloud Manager でのプライベートリポジトリの使用 {#using}

Cloud Manager で GitHub リポジトリを検証すると統合が完了し、Cloud Manager でリポジトリを使用できるようになります。

1. プルリクエストを作成すると、GitHub チェックが自動的に開始します。

   ![GitHub チェック](/help/assets/repositories/github-checks.png)

1. プルリクエストごとに、[フルスタックコード品質パイプライン](/help/using/managing-pipelines.md)が自動的に作成されます。このパイプラインは、プルリクエストの更新のたびに開始されます。

1. GitHub チェックは、コード品質チェックが完了するまで実行状態のままになります。コード品質の結果は、GitHub チェックに生成されます。

   ![GitHub コード品質チェック](/help/assets/repositories/github-code-quality.png)

プルリクエストが閉じられるか結合されると、作成したフルスタックコード品質パイプラインが自動的に削除されます。

>[!TIP]
>
>プルリクエストチェックの実行時に GitHub 経由で提供される情報について詳しくは、[GitHub チェック注釈](github-annotations.md)ドキュメントを参照してください。

>[!TIP]
>
>プライベートリポジトリに対する各プルリクエストを検証するために自動的に作成されるパイプラインを制御できます。詳しくは、[ プライベートリポジトリの GitHub チェック設定 ](github-check-config.md) を参照してください。

## プライベートリポジトリとパイプラインの関連付け {#pipelines}

検証済みのプライベートリポジトリは、[ フルスタックパイプライン ](/help/overview/ci-cd-pipelines.md) に関連付けることができます。

## 制限事項 {#limitations}

Cloud Manager でプライベートリポジトリを使用する場合は、特定の制限が適用されます。

* Cloud Manager の GitHub チェックを使用して、プルリクエストの検証を一時停止することはできません。
   * GitHub リポジトリが Cloud Manager で検証されている場合、Cloud Manager は常に、そのリポジトリに対して作成されたプルリクエストの検証を試みます。
* Adobe GitHub アプリを GitHb 組織から削除すると、すべてのリポジトリのプルリクエスト検証機能が削除されます。
* 実稼動のフルスタックパイプラインでプライベートリポジトリを使用する場合、Git タグは作成およびプッシュされません。
* プライベートリポジトリとコミット時のビルドトリガーを使用するパイプラインは、選択したブランチに新しいコミットがプッシュされた場合に自動的に開始されません。
* [アーティファクト再利用機能](/help/getting-started/project-setup.md#build-artifact-reuse)は、プライベートリポジトリには適用されません。
