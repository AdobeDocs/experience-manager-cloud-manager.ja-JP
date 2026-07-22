---
title: 環境の監視
description: Cloud Manager で環境を監視する方法について説明します。
exl-id: 32886133-d6c0-4aed-8bb0-81b84f63e825
TQID: https://experienceleague.adobe.com/1WlZ7i3267CTPVQrvLi9FlzJuTjzSzpghePEMlSygjY
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: 59ab2b4824e516576d0905376b80c37edc49e53d
workflow-type: tm+mt
source-wordcount: 843
ht-degree: 57%

---

# 環境の監視 {#monitoring-environments}

Cloud Manager で環境を監視する方法について説明します。

## 指標しきい値 {#thresholds}

[!UICONTROL Cloud Manager] のシステム監視は、環境内の個々のインスタンスを監視し、各インスタンスの様々な指標を追跡することで行われます。 各指標には、*警告*&#x200B;しきい値と&#x200B;*重大*&#x200B;しきい値の 2 つのしきい値が定義されています。

指標が警告しきい値を超えた（ただし、重大しきい値は下回った）場合は、警告状態にあると見なされます。

指標が重大しきい値を超えている場合は、重大な状態にあると見なされます。

これらのしきい値は Adobe Managed Services で設定され、[!UICONTROL Cloud Manager] に表示されます。 通常、しきい値は顧客間で一貫していますが、Adobe Managed Servicesでは、お客様固有の要件に合わせてしきい値を編集する場合があります。 しきい値に関する質問は、カスタマーサクセスエンジニア（CSE）にお問い合わせください。

## システム監視へのアクセス {#accessing-system-monitoring}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) で Cloud Manager にログインし、適切な組織とプログラムを選択します。

1. 監視するプログラムの![詳細アイコン、省略記号](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)をクリックします。
1. メニューの&#x200B;**管理**&#x200B;で、**監視を表示**&#x200B;をクリックして、システム監視情報を表示する&#x200B;**レポート** ページを開きます。

   ![設定](/help/assets/first-timea1.png)

。

## システム監視の概要 {#system-monitoring-overview}

**レポート**&#x200B;ページの「**システム監視**」セクションには、プログラム内の監視対象環境が一覧表示されます。 次の 4 つの異なるカテゴリにわたって、高レベルのヘルスの概要が報告されます。

* ホスト
* ストレージ
* ネットワーク
* アプリケーション

各カテゴリのステータスは、個々の指標を要約したものです。 カテゴリ内のいずれかの指標がクリティカル状態に達した場合、カテゴリ全体が概要ページでクリティカルになります。 同じ要約は、環境レベルまたはインスタンスレベルで表示できます。

![システム監視の概要](/help/assets/System-Monitoring-Reports.png)

>[!NOTE]
>
>デフォルトでは、このページに移動すると、本番環境のインスタンスが表示されますが、他の環境も開くことができます。

## システム監視の詳細 {#system-monitoring-detail}

特定の指標の詳細を表示するには、特定のインスタンスのカテゴリ列の 1 つや、左側のナビゲーションのカテゴリタイトルをクリックします。 各詳細ページには、そのカテゴリに含まれる指標の一連のグラフが表示されます。 環境内のすべてのインスタンスまたは特定のインスタンスの指標を表示できます。 右上隅のドロップダウンボックスを使用して、環境とインスタンスを切り替えることができます。

![環境を選択](/help/assets/System_Monitoring1.png)

左側のナビゲーションには、現在選択されている環境およびインスタンスのデータが存在する、現在選択中のカテゴリ内の使用可能な指標が表示されます。

個々のグラフには、ステータスとデータの時間的変化のグラフのほか、しきい値が表示されます。 複数のインスタンスが表示される場合、各インスタンスのデータは別々の系列で表示されます。

![指標グラフ](/help/assets/Monitoring_Graphs1.png)

個々の系列は、凡例の系列をクリックすることで、グラフ上の表示から削除できます。
例えば、警告しきい値シリーズをクリックすると、クリティカルしきい値のみが表示されます。

![グラフを修正](/help/assets/Monitoring_Graphs2.png)

### 指標の定義 {#metric-definitions}

#### ホスト {#host}

* **`Load Per Core`**: CPUで実行中のプロセスの数。 または、待機状態にあるキュー内プロセスの数を 1 分間（load1）、5 分間（load5）、15 分間（load15）にわたって平均したものです。
* **`Process Count`**：現在開いているプロセスの数。
* **`User Count`**: アクティブなシェルセッションを持つユーザーの数。
* **`Memory Usage`**：現在割り当てられているシステム メモリの割合。
* **`JVM Memory`**：割り当てられたJava ヒープのサイズ （MB単位）。
* **`Old Generation Space`**：現在割り当てられているJVMの古い生成メモリの割合。

#### ネットワーク {#network}

* **`CQ Port Check`**: AEMまたはDispatcher ポートにアクセスするための応答時間（秒単位）。 オーサー、パブリッシュ、Dispatcher には、それぞれ異なる指標があります。

#### ストレージ {#storage}

* **`Disk Space`**: ホスト上の各マウントポイントに使用されているディスク領域（メガバイト単位）。 マウントポイントごとに異なる指標があります。 最低でも、`/`と`/mnt`の指標がありますが、特定のインスタンス設定に応じて、追加のマウントポイント指標を利用できます。
* **`Folder Size`**
* **`AEM Segment Store`**: AEM セグメントストアで使用されているディスク領域（ギガバイト単位）。

#### アプリケーション {#application}

* **`Replication Agent`**: テスト レプリケーション イベントの時間（秒単位）
  * レプリケーションエージェントごとに別個の指標があります。
* **`Dispatcher Flush`**：現在Dispatcher フラッシュキューにある項目の数

## SLA レポート {#sla-reporting}

契約されたサービスレベル契約（SLA）に対する AEM の実稼動環境のパフォーマンスを確認できます。

次のグラフに、2019年の月別 SLA 達成度を示します。

![SLA 2018 グラフ](/help/assets/SLA-Reports-one.png)

システムモニタリンググラフと同様に、データポイントにカーソルを合わせると、その月の特定の値が表示されます。

![データポイントのロールオーバー](/help/assets/SLA-Reports-two.png)

このグラフの「**イベント分析**」セクションには、現在選択している年の中でプログラムに発生した一連のインシデントが表示されます。 インシデントごとに、時間範囲、原因および一連のコメントが記載されています。

![イベント分析](/help/assets/sla-reporting3.png)

## SLA 指標 {#sla-metrics}

* **`Author Contract`**：作成者層のAdobe Managed Servicesとの契約で定義されたSLA。
* **`AMS Author SLA`**：実稼動作成者層の測定済み稼働時間。仕入先またはAdobeによって発生したインシデントを考慮します。
* **`Author SLA`**: メンテナンスウィンドウなどのスケジュールされたダウンタイムを無視する、オーサー層の測定されたアップタイム。
* **`End User Contract`**：パブリッシュ層のAdobe Managed Servicesとの契約で定義されたSLA。
* **`AMS End User SLA`**：実稼動公開層の測定済み稼働時間。ベンダーまたはAdobeによって発生したインシデントを考慮します。
* **`End User SLA`**: メンテナンスウィンドウなどのスケジュールされたダウンタイムを無視する、公開層の測定されたアップタイム。

## ビデオチュートリアル {#video-tutorial}

このビデオでは、Cloud Manager レポートで作成されたチャートを使用して、プログラム環境をモニターする方法の概要を説明します。

>[!VIDEO](https://video.tv.adobe.com/v/26315/)
