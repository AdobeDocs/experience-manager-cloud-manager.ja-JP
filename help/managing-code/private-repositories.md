---
title: Cloud Managerでのプライベートリポジトリの追加
description: 独自のプライベート GitHub リポジトリを操作するために Cloud Manager を設定する方法について説明します。
feature: Release Information
exl-id: e0d103c9-c147-4040-bf53-835e93d78a0b
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 40%

---


# Cloud Managerでのプライベートリポジトリの追加 {#private-repositories}

独自の プライベート GitHub リポジトリを操作するために Cloud Manager を設定する方法について説明します。

## 概要 {#overview}

Cloud Managerをプライベート GitHub リポジトリと連携するように設定すると、GitHub 内で直接コードを検証できるので、Adobeリポジトリと頻繁に同期する必要がなくなります。

>[!NOTE]
>
>この機能は、パブリック GitHub 専用です。自己ホスト型 GitHub のサポートは利用できません。

## 設定 {#configuration}

設定は、次の 2 つの主な手順で構成されます。

1. [リポジトリを追加](#add-repo)
1. [プライベートリポジトリの所有権の検証](#validate-ownership)

### リポジトリを追加 {#add-repo}

1. Cloud Managerの **プログラムの概要** ページで、「**リポジトリ**」タブをクリックして **リポジトリ** ページに切り替え、「**リポジトリを追加**」をクリックします。

1. **リポジトリを追加** ダイアログボックスで、リポジトリタイプとして **プライベートリポジトリ** を選択します。

1. リポジトリの詳細を指定します

   * **リポジトリ名** - 表現名
   * **リポジトリ URL** - リポジトリの URL。`.git` で終了する必要があります。
   * **説明**（オプション）- 必要に応じてリポジトリの詳細な説明

   ![独自のリポジトリの追加](/help/assets/repositories/add-own-github.png)

1. 「**保存**」をクリックします。

>[!TIP]
>
>Cloud Manager でのリポジトリ管理について詳しくは、[Cloud Manager リポジトリ](/help/managing-code/managing-repositories.md)を参照してください。

### プライベートリポジトリの所有権の検証 {#validate-ownership}

Cloud Manager は GitHub リポジトリを認識しましたが、引き続きアクセスする必要があります。アクセス権を付与するには、Adobe GitHub アプリをインストールし、指定したリポジトリを所有していることを確認する必要があります。

1. 独自のリポジトリを追加すると、「**プライベートリポジトリ所有権の検証**」ダイアログボックスが表示されます。

   ![プライベートリポジトリの所有権の検証](/help/assets/repositories/private-repo-validate.png)

1. Cloud Managerは GitHub アプリを使用して、リポジトリと安全にやり取りします。

   GitHub 組織の所有者は、`https://github.com/apps/cloud-manager-for-aem` にあるアプリをインストールし、リポジトリへのアクセス権を付与する必要があります。 詳しくは、GitHub のドキュメントを参照してください。

1. セキュリティを強化するには、リポジトリのデフォルトブランチに秘密鍵ファイルを作成します。 **生成** をクリックします。

1. **確認** をクリックして、シークレットファイルの生成を確認します。

   ![秘密鍵の生成の確認](/help/assets/repositories/confirm-generation.png)

1. **プライベートリポジトリ所有権検証** ダイアログボックスに戻ると、Cloud Managerは、「**秘密鍵ファイルコンテンツ** フィールドにコンテンツを生成しました。 そのフィールドからコンテンツをコピーします。

   シークレットファイルの内容は 1 回だけ表示されます。 このウィンドウを閉じる前にコンテンツをコピーしない場合は、秘密鍵を再生成する必要があります。

   ![秘密鍵ファイルコンテンツのコピー](/help/assets/repositories/new-secret.png)

1. GitHub リポジトリのデフォルトブランチに `.well-known/adobe/cloud-manager-challenge` という名前の新しいファイルを作成し、秘密鍵ファイルコンテンツをそのファイルにペーストして保存します。

1. アプリケーションをインストールし、秘密鍵ファイルがリポジトリに存在したら、**プライベートリポジトリ所有権の検証** ダイアログの **検証** をクリックできます。

アプリはインストールでき、任意の順序で秘密鍵ファイルを生成できます。 ただし、検証するには、両方の手順を完了する必要があります。

検証が行われるまで、リポジトリは赤いアイコンと共にリストされます。これは、リポジトリがまだ検証されておらず、まだ使用できないことを示します。

![未検証のリポジトリ](/help/assets/repositories/unvalidated-repo.png)

**タイプ**&#x200B;列では、アドビ提供のリポジトリ（**Adobe**）と独自の GitHub リポジトリ（**GitHub**）を簡単に識別できます。

後でリポジトリに戻って検証を完了するには、**リポジトリ** ページに移動します。 追加した GitHub リポジトリの横にある省略記号ボタンをクリックし、ドロップダウンメニューから **所有権の検証** を選択します。

## Cloud Managerでのプライベートリポジトリの使用 {#using}

Cloud Managerで GitHub リポジトリーを検証すると、統合が完了し、Cloud Managerでリポジトリーを使用できるようになります。

1. プルリクエストを作成すると、GitHub チェックが自動的に開始されます。

   ![GitHub チェック](/help/assets/repositories/github-checks.png)

1. プルリクエストごとに、[ フルスタックコード品質パイプライン ](/help/using/managing-pipelines.md) が自動的に作成されます。 このパイプラインは、プルリクエストの更新のたびに開始されます。

1. GitHub チェックは、コード品質チェックが完了するまで、実行中状態のままになります。 コード品質の結果は、GitHub チェックに反映されます。

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

* Cloud Managerの GitHub チェックを使用してプルリクエストの検証を一時停止することはできません。 GitHub リポジトリがCloud Managerで検証されている場合、Cloud Managerはそのリポジトリに対して作成されたプルリクエストの検証を試みます。
* Adobe GitHub アプリが GitHb 組織から削除されると、すべてのリポジトリのプルリクエスト検証機能が削除されます。
* 実稼動フルスタックパイプラインでプライベートリポジトリを使用する場合、Git タグは作成およびプッシュされません。
* プライベートリポジトリとコミット時のビルドトリガーを使用するパイプラインは、選択したブランチに新しいコミットがプッシュされた場合に自動的に開始されません。
* [アーティファクト再利用機能](/help/getting-started/project-setup.md#build-artifact-reuse)は、プライベートリポジトリには適用されません。
