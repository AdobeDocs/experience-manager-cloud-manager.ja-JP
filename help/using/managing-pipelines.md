---
title: パイプラインの管理
description: 既存のパイプラインの管理方法（実行、編集、削除を含む）を説明します。
exl-id: e36420d2-57c5-4375-99fb-dd47c1c8bffd
source-git-commit: 91eda02d55134fba167f30830a142a80717e9083
workflow-type: tm+mt
source-wordcount: '1170'
ht-degree: 73%

---


# パイプラインの管理 {#managing-pipelines}

既存のパイプラインの管理方法（実行、編集、削除を含む）を説明します。

## パイプラインカード {#pipeline-card}

Cloud Manager の&#x200B;**プログラムの概要**&#x200B;ページにある&#x200B;**パイプライン**&#x200B;カードには、すべてのパイプラインとその現在のステータスの概要が表示されます。

![Cloud Manager のパイプラインカード](/help/assets/configure-pipelines/pipelines-card.png)

各パイプラインの横にある ![&#x200B; 詳細アイコン、省略記号 &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) をクリックすると、次の操作を実行できます。

* [パイプラインを実行](#running-pipelines)
* [パイプラインを編集](#editing-pipelines)
* [パイプラインを削除](#deleting-pipelines)
* [詳細を表示](#view-details)

パイプラインのリストの下部には、次の一般的なオプションがあります。

* **追加** - [新しい実稼動パイプラインを追加](/help/using/production-pipelines.md)するか、[新しい実稼動以外のパイプラインを追加](/help/using/non-production-pipelines.md)します。
* **すべて表示** - ユーザーを&#x200B;**パイプライン**&#x200B;画面に移動して、すべてのパイプラインをより詳細なテーブルに表示します。
* **リポジトリ情報にアクセス** - Cloud Manager の Git リポジトリへのアクセスに必要な情報を表示します。
* **詳細情報** - CI/CD パイプラインのドキュメントリソースに移動します。

## パイプラインページ {#pipelines}

**パイプライン**&#x200B;ページには、選択したプログラムのすべてのパイプラインの完全なリストが表示されます。このリストは、[パイプラインカード](#pipeline-card)で使用可能な情報よりも包括的な情報を表示するので便利です。

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) で Cloud Manager にログインし、適切な組織とプログラムを選択します。

1. **プログラムの概要**&#x200B;ページで、「**パイプライン**」タブをクリックして、**パイプライン**&#x200B;ページに切り替えます。

1. ここでは、プログラムのすべてのパイプラインのリストを確認できるほか、**パイプラインカード**&#x200B;の場合と同様に、パイプラインの実行を開始および停止することができます。

`i` アイコンをクリックすると、パイプラインの前回または現在の実行に関する詳細が表示されます。

![パイプライン実行の詳細](/help/assets/configure-pipelines/pipeline-status.png)

「**詳細を表示**」をクリックすると、[パイプライン実行の詳細](#view-details)が表示されます。

### パイプラインのお気に入りのマーク{#pipeline-favorites}

特定のパイプラインをお気に入りとしてマークして、「**パイプライン**」ページのリストの上部に表示できます。 この機能により、頻繁にアクセスするパイプラインを見つけて実行しやすくなります。

**パイプラインのお気に入りをマークするには：**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) で Cloud Manager にログインし、適切な組織とプログラムを選択します。
1. **プログラムの概要**&#x200B;ページで、![パイプラインタブ - ワークフローアイコン](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg)「**パイプライン**」タブをクリックします。
1. **パイプライン** ページで、パイプライン名とタイプの左側にある「![&#x200B; お気に入りから外したパイプラインの星形アウトラインアイコン &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_StarOutline_18_N.svg) をクリックして、お気に入りリストに追加します。
または、![&#x200B; お気に入りのパイプラインのスターアイコン &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Star_18_N.svg) をクリックして、お気に入りリストからパイプラインを削除します。


## アクティビティページ {#activity}

**アクティビティ**&#x200B;ページには、選択したプログラムのすべてのパイプライン実行の完全なリストが表示されます。

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) で Cloud Manager にログインし、適切な組織とプログラムを選択します。

1. **プログラムの概要**&#x200B;ページで、「**アクティビティ**」タブをクリックして、**アクティビティ**&#x200B;ページに切り替えます。

1. ここでは、現在および過去の実行を含む、プログラムのすべてのパイプライン実行のリストを確認できます。

`i` アイコンをクリックすると、選択したパイプライン実行に関する詳細が表示されます。

![パイプライン実行の詳細](/help/assets/configure-pipelines/pipeline-activity.png)

「**詳細を表示**」をクリックすると、[パイプライン実行の詳細](#view-details)を確認できます。

## パイプラインの実行 {#run-one-pipeline}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) で Cloud Manager にログインし、適切な組織とプログラムを選択します。
1. **プログラムの概要**&#x200B;ページから&#x200B;**パイプライン**&#x200B;カードに移動します。
1. 実行するパイプラインの横にある ![&#x200B; 詳細アイコン、省略記号 &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) をクリックし、「**実行**」をクリックします。

   ステータス列は、パイプラインの実行が開始されたタイミングを示します。

   実行の詳細を確認するには、![&#x200B; 詳細アイコン、省略記号 &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) をもう一度クリックし、**[詳細を表示](#view-details)** をクリックします。

   パイプラインのタイプによっては、![&#x200B; その他アイコン、省略記号）をもう一度クリックして **キャンセル &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) をクリックすると、実行をキャンセルできる場合があ** ます。

## 複数のパイプラインの実行 {#run-multiple-pipelines}

Cloud Managerを使用すると、複数のパイプラインを同時に実行できるので、Adobe Managed Services（AMS）のお客様のデプロイメント効率が向上します。 **選択されている実行**&#x200B;機能を使用すると、複数のパイプラインを選択し、一度に実行するようにトリガーできます。これにより、パイプラインを個別に実行する必要がある手動の作業が軽減され、ビルドとデプロイメントのワークフローが最適化されます。

**複数のパイプラインを実行するには：**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) で Cloud Manager にログインし、適切な組織とプログラムを選択します。
1. 左側のサイドメニューから、![ワークフローアイコン](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) **パイプライン**&#x200B;をクリックします。
1. **パイプライン**&#x200B;ページのテーブルで、実行するパイプラインの横にあるチェックボックスをオンにします。
必要に応じて、![フィルターアイコン、ファネル](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Filter_18_N.svg) **フィルター**&#x200B;をクリックして、パイプラインを名前、環境、デプロイされたコードタイプ、またはこれら 3 つすべての組み合わせで並べ替えます。
1. ページの右上隅付近にある「**選択されている実行（x）**」をクリックします。
1. **選択されているパイプラインを実行（x）**&#x200B;ダイアログボックスで、「**実行（x）**」をクリックします。

   「**実行**」ボタンには、実行できるパイプラインの数が反映されます。例えば、4 つのパイプラインを選択したが、1 つが既に実行されている場合があります。または、選択したパイプラインにリンクされた環境が存在しなくなりました。このような場合、システムはそれに応じて調整します。ボタンが「実行（3）」に更新され、3 つのパイプラインが続行できることが示されます。

1. パイプラインの実行が開始され、**パイプライン**&#x200B;リストにそのステータスが更新されます。

## パイプラインを編集 {#editing-pipelines}

実行中のパイプラインは編集できません。

**パイプラインを編集するには：**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) で Cloud Manager にログインし、適切な組織とプログラムを選択します。

1. **プログラムの概要** ページから **パイプライン** カードに移動します。

1. 編集するパイプラインの横にある ![&#x200B; 詳細アイコン &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) 省略記号）をクリックし、「**編集**」をクリックします。

1. **実稼動パイプラインを編集** または **実稼動以外のパイプラインを編集** ダイアログボックスでは、パイプラインの作成時に入力したのと同じ詳細を編集できます。

   パイプラインに使用できるフィールドと設定オプションについて詳しくは、[実稼動パイプラインを設定](/help/using/production-pipelines.md)および[実稼動以外のパイプラインを設定](/help/using/non-production-pipelines.md)を参照してください。

1. 完了したら、「**更新**」をクリックします。

## パイプラインを削除 {#deleting-pipelines}

実行中のパイプラインは削除できません。

**パイプラインを削除するには：**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) で Cloud Manager にログインし、適切な組織とプログラムを選択します。

1. **プログラムの概要** ページから **パイプライン** カードに移動します。

1. 実行するパイプラインの横にある ![&#x200B; 詳細アイコン、省略記号 &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) をクリックし、「**削除**」をクリックします。


## パイプラインの詳細の表示 {#view-details}

実行中または少なくとも 1 回実行されたパイプラインの詳細のみ表示できます。

**パイプラインの詳細を表示するには：**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) で Cloud Manager にログインし、適切な組織とプログラムを選択します。

1. **プログラムの概要** ページから **パイプライン** カードに移動します。

1. 実行するパイプラインの横にある ![&#x200B; 詳細アイコン、省略記号 &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) をクリックし、**詳細を表示** をクリックします。

1. 実行中のパイプラインの詳細ページに移動します。

![パイプラインの詳細](/help/assets/configure-pipelines/pipeline-running-details.png)

ここから、診断の目的で、パイプラインの様々なステップのステータスを確認し、ビルドログを取得できます。詳しくは、[コードのデプロイメント](/help/using/code-deployment.md)のドキュメントを参照してください。

パイプライン実行のすべての手順が表示され、まだ開始されていない手順はグレーアウトされます。完了した手順には、期間が表示されます。

パイプラインの手順が完了すると、概要が表示されます。

![手順の概要](/help/assets/configure-pipelines/pipeline-step.png)

「**詳細を表示**」リンクをクリックすると、「**期間**」セクションが表示されます。この節には、そのプログラムの過去のトレンドに基づくパイプラインの平均期間が含まれます。

![期間](/help/assets/configure-pipelines/duration.png)

パイプラインに **コードスキャン** ステップが含まれており、問題が発生した場合は、「**詳細をダウンロード**」をクリックして、成功しなかった [&#x200B; コード品質テスト &#x200B;](/help/using/code-quality-testing.md) のリストを表示できます。

![コード品質の問題](assets/managing-pipelines-code-quality-issues.png)

CSV ファイルには、問題のあるコードの場所を示す&#x200B;**プロジェクトファイルの場所**&#x200B;列があります。この列はプロジェクト相対パスですが、**ファイルの場所**&#x200B;列は Maven によって生成されます。

![プロジェクトコードスキャン問題の詳細](assets/managing-pipelines-code-quality-details.png)
