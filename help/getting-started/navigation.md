---
title: Cloud Manager UI の操作
description: Cloud Manager UI の整理方法と、プログラムと環境を管理する操作方法について説明します。
exl-id: 9c1545ce-1c6d-417f-a6f4-fe53caef3433
source-git-commit: cc41d4716aa3c3683010b6dd392b5355b129d1ef
workflow-type: tm+mt
source-wordcount: '1530'
ht-degree: 52%

---


# Cloud Manager UI の操作 {#navigation}

Cloud Manager UI の整理方法と、プログラムと環境を管理する操作方法について説明します。

Cloud Manager UI は、主に次の 2 つのグラフィカルインターフェイスで構成されます。

* [マイプログラムコンソール](#my-programs-console)：すべてのプログラムを表示および管理できます。
* [プログラムの概要ウィンドウ](#program-overview)：個々のプログラムの詳細を確認して管理できます。

## マイプログラムコンソール {#my-programs-console}

[experience.adobe.com](https://experience.adobe.com/experiencemanager) でCloud Managerにログインし、適切な組織を選択すると、**マイプログラム** コンソールに移動します。

![マイプログラムコンソール](/help/getting-started/assets/cloud-manager-my-programs-console.png)

**マイプログラム** コンソールには、選択した組織でアクセス権を持つすべてのプログラムの概要が表示されます。 複数のパーツで構成されます。

|   | 領域 | 説明 |
| --- | --- | --- |
| 1 | [&#x200B; ツールバー &#x200B;](#toolbars-my-programs-toolbars) | 組織の選択、アラート、アカウント設定に使用します。 |
| 2 | 左側のパネルタブ | プログラムの現在の表示を切り替えるための様々なタブ。以下に例を示します。<br><ul><li>**Experience Manager** 様々なAEM ソリューションのホームページを開きます</li><li>**すべてのプログラム**：使用可能なすべてのプログラムが表示されます。</li><li>**ライセンス** ライセンスダッシュボードを開きます。 ライセンスダッシュボードは、*AEM as a Cloud Service プログラム* （AEMaaCS）にのみ適用され、AEM 6.5 やAEM 6.5 LTS などのAdobe Managed Services プログラムには適用されません。 プログラムのサービスの種類（AEMaaCS または AMS）を確認するには、この記事の [&#x200B; プログラムカード &#x200B;](#program-cards) の節を参照してください。 タブはデフォルトで閉じられ、![Cloud Manager ヘッダーの左側にある &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) メニューアイコン、ハンバーガーを表示 [&#x200B; ドロップダウンメニューを使用して表示でき &#x200B;](#cloud-manager-header) す。</li></ol> |
| 3 | [&#x200B; マイプログラム &#x200B;](#my-programs-section) | 選択可能なすべての使用可能なプログラムを一覧表示します。<br> プログラムについて詳しくは、[&#x200B; プログラムとプログラムタイプ &#x200B;](/help/getting-started/program-setup.md) を参照してください。 |
| 4 | [&#x200B; コールトゥアクションと統計 &#x200B;](#cta-statistics) | 最近のアクティビティの概要が表示されます。 |
| 5 | [&#x200B; クイックリンク &#x200B;](#quick-links) | 関連リソースへのクイックアクセス。 |


### ツールバー {#my-programs-toolbars}

2 つのツールバーが重なり合っています。

#### Cloud Manager ヘッダー {#cloud-manager-header}

1 つ目は Cloud Manager ヘッダーです。このヘッダーは、Cloud Manager を操作する際に保持されます。Cloud Manager プログラム全体に適用される設定と情報にアクセスできるアンカーです。

![Experience Cloud ヘッダー](/help/getting-started/assets/cloud-manager-header-toolbar.png)

| 領域 | 説明 |
| --- | --- |
| ![&#x200B; メニューアイコン、ハンバーガーを表示 &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) | 個々のプログラムの特定の部分のタブにアクセスできるドロップダウンメニュー。<br> プログラムのサービスの種類（AMS または AEMaaCS）を確認するには、このドキュメントの [&#x200B; プログラムカードの節 &#x200B;](#program-cards) を参照してください。 |
| ![Adobe赤と白のアイコン &#x200B;](/help/getting-started/assets/AdobeLogoWhiteOnRed.svg)Cloud Manager | Cloud Managerのどこにいても、Cloud Managerの **マイプログラム** コンソールをクリックして開きます。 |
| *`Name of selected organization`* | 組織セレクターには、現在ログインしている組織（この例では、*Foundation Internal*）が表示されます。 Adobe IDが複数の組織に関連付けられている場合、クリックすると別の組織に切り替わります。 |
| ![&#x200B; フィードバックアイコン &#x200B;](/help/getting-started/assets/AppComment.svg) Feedback | クリックして、Cloud Managerに関するフィードバックをAdobeに送信します。 |
| ![AI アシスタント アイコン &#x200B;](/help/getting-started/assets/AIChat.svg) | AI アシスタントは、AEM関連のクエリに対する回答の検索を合理化するように設計された対話型インターフェイスを提供します。 [AI アシスタント &#x200B;](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/ai-assistant/ai-assistant-in-aem) を参照してください |
| ![ヘルプアイコン](https://spectrum.adobe.com/static/icons/workflow_18/Smock_HelpOutline_18_N.svg) | クリックすると、学習リソースやサポートリソースにすばやくアクセスできます。 |
| ![&#x200B; 白いベルのアイコン &#x200B;](/help/getting-started/assets/Bell.svg) | クリックすると、現在割り当てられている未完了 [&#x200B; 通知 &#x200B;](/help/using/notifications.md) の数が表示されます |
| ![&#x200B; アプリアイコン &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Apps_18_N.svg) | クリックすると、AEMのホームページとAEM ソリューションをすばやく切り替えることができます |
| *`Dynamic Account icon`* | ユーザーの画像をクリックして **アカウント設定** および **プログラム設定** にアクセスするか、サインアウトします。<br> ユーザー画像を追加しないことを選択した場合、アイコンがランダムに割り当てられます（上のツールバー画像を参照）。 |

<!--
1. The ![Show menu icon, hamburger](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) icon on the left side of the header is  
   * The License Dashboard only applies to AEM as a Cloud Service programs, not AMS programs.
   * To determine the type of service your program has (AMS or AEMaaCS), see the [Program Cards section](#program-cards) of this document.
1. The **Adobe Cloud Manager** button takes you back to the **My Programs** console of Cloud Manager no matter where you are in Cloud Manager.
1. Click **Feedback** to provide feedback to Adobe about Cloud Manager.
1. The organization selector displays the organization that you are currently signed into (in this example, Foundation Internal). Click to switch to another organization if your Adobe ID is associated with multiple.
1. Clicking the solutions switcher lets you quickly jump to other Experience Cloud solutions.
1. The Help icon provides quick access to learning and support resources.
1. The notifications icon is badged with the number of currently assigned incomplete [notifications](/help/using/notifications.md)
1. Select the icon representing your user to access your user settings. If you do not select a user picture, an icon is randomly assigned. -->

#### プログラムツールバー {#program-toolbar}

プログラムツールバーには、Cloud Manager プログラムとコンテキストに適したアクションを切り替えるリンクが表示されます。

![Cloud Manager プログラムツールバー &#x200B;](/help/getting-started/assets/cloud-manager-programs-toolbar.png)

|   | 領域 | 説明 |
| --- | --- | --- |
| 1 | マイプログラム | ドロップダウンリストをクリックして開きます。このドロップダウンリストでは、プログラムを追加するか、他の既存のプログラムを選択するか、Experience Managerのホームページに戻ることができます。 |
| 2 | ![&#x200B; 情報アイコン &#x200B;](/help/getting-started/assets/Info.svg) はじめに | クリックして [&#x200B; オンボーディングドキュメントジャーニー &#x200B;](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/onboarding/journey/overview) にアクセスし、Cloud Managerを使い始めます。<br> オンボーディングジャーニーは、Adobe Experience Manager as a Cloud ServiceのCloud Manager（AEMaaCS）向けに設計されており、Adobe Managed ServicesのCloud Manager（AMS）向けではありません。 ただし、多くの概念は同じです。 |
| 3 | *`Dynamic action button`* | アクションボタンは、クリックできるコンテキストに適したアクションを提供します。例えば、**プログラムを追加** （上記の例を参照）や、ドメインを追加します。 |

### コールトゥアクションと統計 {#cta-statistics}

「コールトゥアクションと統計」セクションでは、組織の集計データが提供されます。例えば、プログラムを正常に設定した場合、過去 90 日間のアクティビティの統計には、次の内容が表示されることがあります。

* [デプロイ](/help/using/code-deployment.md)数
* 特定された[コード品質の問題](/help/using/code-quality-testing.md)の数
* ビルド数

組織の設定を開始したばかりの場合は、次の手順やドキュメントのリソースに関するヒントが表示される場合があります。

### マイプログラム {#my-programs-section}

マイプログラムコンソールのメインコンテンツは、プログラムを個々のカードとしてリストする「**マイプログラム**」セクションです。カードをクリックすると、**プログラムの概要**&#x200B;ページにアクセスしてプログラムの詳細を確認できます。

権限によっては、特定のプログラムを選択できない場合があります。

次の並べ替えオプションを使用すると、必要なプログラムをすばやく見つけることができます。

![並べ替えオプション](/help/getting-started/assets/cloud-manager-my-programs-sorting.png)

* 並べ替え：
   * 作成日
   * プログラム名
   * ステータス
* ![&#x200B; 並べ替え順の下のアイコン &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SortOrderDown_18_N.svg) / ![&#x200B; 並べ替え順の上のアイコン &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SortOrderUp_18_N.svg) プログラムをそれぞれ下または上に並べ替えます。
* ![&#x200B; クラシックグリッド表示アイコン &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ClassicGridView_18_N.svg) / ![&#x200B; テキスト箇条書きアイコンまたはリスト &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TextBulleted_18_N.svg) プログラムをそれぞれグリッド形式またはリスト形式で表示します。

#### プログラムカード {#program-cards}

すべてのプログラムはカードまたはテーブルの行で表され、プログラムの概要と、アクションを実行するためのクイックリンクを提供します。

![プログラムカード](/help/getting-started/assets/cloud-manager-program-card.png)

* プログラム画像（設定されている場合）
* プログラム名（上記の例では、*WKND Magazine*）
* サービスタイプ：
   * AMS プログラムの **Experience Manager**
   * [AEM as a Cloud Service プログラム](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/implementing/home)の **Experience Manager クラウド**
* ステータス（上記の例では *準備完了*）
* 設定済みのソリューション
* 作成日

![&#x200B; 情報アイコン &#x200B;](/help/getting-started/assets/Info.svg) をクリックすると、プログラムに関する追加情報（リスト表示で役立ちます）にすばやくアクセスできます。

![Cloud Manager AMS の情報ポップアップ &#x200B;](/help/getting-started/assets/cloud-manager-information-view.png)

![&#x200B; 詳細アイコン、省略記号 &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) をクリックすると、プログラムに対して実行できる追加のアクションにアクセスできます。

![プログラムの省略記号ボタン](/help/getting-started/assets/cloud-manager-program-ellipsis.png)

* Experience Manager ホーム
* プログラムの特定の[環境](/help/using/managing-environments.md)に移動
* [プログラムの概要](#program-overview)を開く
* [プログラムを編集](/help/getting-started/program-setup.md)
* モニタリングを表示

### クイックリンク {#quick-links}

「クイックリンク」セクションでは、役立つ関連リソースにアクセスできます。

## プログラムの概要ウィンドウ {#program-overview}

[**マイプログラム**&#x200B;コンソール](#my-programs-console)でプログラムを選択すると、**プログラムの概要**&#x200B;ページに移動できます。

![プログラムの概要](/help/getting-started/assets/cloud-manager-program-overview.png)

**プログラムの概要** Cloud Manager プログラムのすべての詳細にアクセスできます。 **マイプログラム** と同様に、いくつかの部分で構成されています。

1. [ツールバー](#program-overview-toolbar)：**マイプログラム**&#x200B;コンソールにすばやく戻ったり、プログラム内を移動したりできます。
1. [&#x200B; タブ領域 &#x200B;](#program-tabs) プログラムの様々な側面を切り替えます。
1. [コールトゥアクション](#cta)：プログラムの最後のアクションに基づきます。
1. プログラムの関連付けられた [&#x200B; 環境 &#x200B;](#environments)。
1. プログラムの関連付けられた [&#x200B; パイプライン &#x200B;](#pipelines)。

### ツールバー {#program-overview-toolbar}

プログラムの概要のツールバーは、[マイプログラムコンソール](#my-programs-toolbars)のツールバーと類似しています。ここでは違いのみを説明します。

#### Cloud Manager ヘッダー {#cloud-manager-header-2}

Cloud Managerのヘッダーには、自動的に開く ![&#x200B; メニューアイコン、ハンバーガーを表示 &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) ドロップダウンメニューがあり、プログラムの概要のナビゲート可能なタブを表示します。

![&#x200B; メニューアイコン、ハンバーガーを表示 &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) をクリックして、タブを非表示にします。

#### プログラムツールバー {#program-toolbar-2}

プログラムツールバーを使用すると、他のプログラムにすばやく切り替えることができますが、プログラムの追加や編集など、コンテキストに適したアクションにもアクセスできます。

![プログラムツールバー](assets/cloud-manager-program-toolbar.png)

さらに、![&#x200B; メニューアイコン、ハンバーガーを表示 &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) を使用してタブを非表示にした場合でも、現在表示しているタブをツールバーに表示できます。

### プログラムタブ {#program-tabs}

各プログラムには、多数のオプションとデータが関連付けられています。これらのデータはタブに集められ、プログラムの操作が簡単になります。タブを使用すると、次のパーツにアクセスできます。

* 概要 - 現在のドキュメントに記載されているプログラムの概要
* [アクティビティ](/help/using/managing-pipelines.md#activity) - プログラムのパイプライン実行の履歴
* [パイプライン](/help/using/managing-pipelines.md#pipelines) - プログラムに対して設定されたすべてのパイプライン
* [リポジトリ](/help/managing-code/managing-repositories.md) - プログラムに対して設定されたすべてのリポジトリ
* [レポート](/help/using/monitoring-environments.md#system-monitoring-overview) - SLA データなどの指標
* [環境](/help/using/managing-environments.md) - プログラムに対して設定されたすべての環境
* [コンテンツセット](/help/using/content-copy.md) - コピー目的に対して作成されたコンテンツのセット
* [コンテンツをコピーアクティビティ](/help/using/content-copy.md) - コンテンツをコピーするアクティビティ
* 学習パス - Cloud Manager に関するその他の学習リソース

デフォルトでは、プログラムを開くと、「**概要**」タブが表示されます。現在のタブがハイライト表示されます。別のタブを選択すると、その詳細が表示されます。

タブを非表示にするには、![Cloud Manager ヘッダーにある &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) メニューアイコン、ハンバーガーを表示 [&#x200B; を使用 &#x200B;](#cloud-manager-header-2) ます。

### コールトゥアクション {#cta}

「コールトゥアクション」セクションでは、プログラムのステータスに応じて役立つ情報を提供します。新しいプログラムの場合は、次の手順が提供されるほか、[プログラム作成時に設定](/help/getting-started/program-setup.md)された公開日のリマインダーが表示される場合があります。

ライブプログラムの場合、最後のデプロイメントのステータスと、詳細および新しいデプロイメントを開始するためのリンクが表示されます。

![コールトゥアクション](assets/info-banner.png)

### 環境カード {#environments}

**環境**&#x200B;カードには、環境の概要とクイックアクションへのリンクが表示されます。

**環境**&#x200B;カードには 3 つの環境のみ表示されます。「**すべて表示**」ボタンをクリックすると、プログラムのすべての環境が表示されます。

環境の管理方法について詳しくは、[環境の管理](/help/using/managing-environments.md)を参照してください。

### パイプラインカード {#pipelines}

**パイプライン**&#x200B;カードには、パイプラインの概要とクイックアクションへのリンクが表示されます。

**パイプライン**&#x200B;カードには 3 つのパイプラインのみ表示されます。「**すべて表示**」をクリックすると、プログラムのすべてのパイプラインが表示されます。

パイプラインの管理方法について詳しくは、[パイプラインの管理](/help/using/managing-pipelines.md)を参照してください。

### 役立つリソース {#useful-resources}

「**役立つリソース**」セクションには、Cloud Manager のその他の学習リソースへのリンクが含まれます。
