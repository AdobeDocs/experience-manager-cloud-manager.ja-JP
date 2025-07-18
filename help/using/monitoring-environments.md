---
title: 環境の監視
description: Cloud Manager で環境を監視する方法について説明します。
exl-id: 32886133-d6c0-4aed-8bb0-81b84f63e825
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 74%

---


# 環境の監視 {#monitoring-environments}

Cloud Manager で環境を監視する方法について説明します。

## 指標しきい値 {#thresholds}

[!UICONTROL Cloud Manager] のシステム監視は、環境内の個々のインスタンスを監視し、各インスタンスの様々な指標を追跡することで行われます。各指標には、*警告*&#x200B;しきい値と&#x200B;*重大*&#x200B;しきい値の 2 つのしきい値が定義されています。

指標が警告しきい値を超えた（ただし、重大しきい値は下回った）場合は、警告状態にあると見なされます。

指標が重大しきい値を超えている場合は、重大な状態にあると見なされます。

これらのしきい値は Adobe Managed Services で設定され、[!UICONTROL Cloud Manager] に表示されます。ほとんどの場合、しきい値は顧客間で統一されていますが、特定の顧客要件に合わせて Adobe Managed Services がしきい値を編集する場合もあります。しきい値に関する質問は、カスタマーサクセスエンジニア（CSE）にお問い合わせください。

## システム監視へのアクセス {#accessing-system-monitoring}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) で Cloud Manager にログインし、適切な組織とプログラムを選択します。

1. 監視するプログラムの ![ 詳細アイコン、省略記号 ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) をクリックします。
1. メニューの **管理** で **監視を表示** をクリックして、システム監視情報を表示する **レポート** ページを開きます。

   ![設定](/help/assets/first-timea1.png)

。

## システム監視の概要 {#system-monitoring-overview}

**レポート**&#x200B;ページの「**システム監視**」セクションには、プログラム内の監視対象環境が一覧表示されます。次の 4 つの異なるカテゴリにわたって、高レベルのヘルスの概要が報告されます。

* ホスト
* ストレージ
* ネットワーク
* アプリケーション

各カテゴリのステータスは、個々の指標を要約したものです。カテゴリ内のいずれかの指標が重大な状態にある場合、概要ページでは、カテゴリ全体が重大な状態になります。同じ要約が環境レベルとインスタンスレベルでもおこなわれます。

![システム監視の概要](/help/assets/System-Monitoring-Reports.png)

>[!NOTE]
>
>デフォルトでは、このページに移動すると、実稼動環境のインスタンスが表示されますが、他の環境も開くことができます。

## システム監視の詳細 {#system-monitoring-detail}

特定の指標の詳細を表示するには、特定のインスタンスのカテゴリ列の 1 つや、左側のナビゲーションのカテゴリタイトルをクリックします。各詳細ページには、そのカテゴリに含まれる指標の一連のグラフが表示されます。環境内のすべてのインスタンスまたは特定のインスタンスの指標を表示できます。右上隅のドロップダウンボックスを使用して、環境とインスタンスを切り替えることができます。

![環境を選択](/help/assets/System_Monitoring1.png)

左側のナビゲーションには、現在選択されている環境およびインスタンスのデータが存在する、現在選択中のカテゴリ内の使用可能な指標が表示されます。

個々のグラフには、ステータスとデータの時間的変化のグラフのほか、しきい値が表示されます。複数のインスタンスが表示される場合、各インスタンスのデータは別個の系列になります。

![指標グラフ](/help/assets/Monitoring_Graphs1.png)

凡例で個々の系列をクリックして、その系列をグラフ上で非表示にすることができます。
例えば、警告しきい値系列をクリックすると、重大しきい値のみ表示されます。

![グラフを修正](/help/assets/Monitoring_Graphs2.png)

### 指標の定義 {#metric-definitions}

#### ホスト {#host}

* **`Load Per Core`**:CPUが実行しているプロセスの数。 または、待機状態にあるキュー内プロセスの数を 1 分間（load1）、5 分間（load5）、15 分間（load15）にわたって平均したものです。
* **P`rocess Count`**：現在開いているプロセスの数。
* **`User Count`**: シェルセッションがアクティブなユーザーの数。
* **`Memory Usage`**：現在割り当てられているシステムメモリの割合（パーセント）。
* **`JVM Memory`**：割り当てられている Java ヒープのサイズ（MB 単位）。
* **`Old Generation Space`**：現在割り当てられている JVM 旧世代メモリの割合（パーセント）。

#### ネットワーク {#network}

* **`CQ Port Check`**:AEMまたはDispatcherのポートにアクセスするための応答時間（秒単位）。 オーサー、パブリッシュ、Dispatcher には、それぞれ異なる指標があります。

#### ストレージ {#storage}

* **`Disk Space`**：ホスト上の各マウントポイントに使用されているディスク領域（MB 単位）。 マウントポイントごとに異なる指標があります。少なくとも、`/` と `/mnt` の指標が表示されますが、特定のインスタンス設定によっては、追加のマウントポイント指標を使用できる場合があります。
* **`Folder Size`**
* **`AEM Segment Store`**:AEM セグメントストアに使用されているディスク領域（GB 単位）。

#### アプリケーション {#application}

* **`Replication Agent`**: テストレプリケーションイベントの時間（秒単位）。
   * レプリケーションエージェントごとに別個の指標があります。
* **`Dispatcher Flush`**：現在Dispatcher フラッシュキューにある項目数。

## SLA レポート {#sla-reporting}

契約されたサービスレベル契約（SLA）に対する AEM の実稼動環境のパフォーマンスを確認できます。

次のグラフに、2019年の月別 SLA 達成度を示します。

![SLA 2018 グラフ](/help/assets/SLA-Reports-one.png)

システムの監視グラフと同様、データポイントをロールオーバーすると、その月の特定の値が表示されます。

![データポイントのロールオーバー](/help/assets/SLA-Reports-two.png)

このグラフの「**イベント分析**」セクションには、現在選択している年の中でプログラムに発生した一連のインシデントが表示されます。インシデントごとに、時間範囲、原因および一連のコメントが記載されています。

![イベント分析](/help/assets/sla-reporting3.png)

## SLA 指標 {#sla-metrics}

* **`Author Contract`**:Adobe Managed Servicesとの契約でオーサー層に対して定義されたSLA。
* **`AMS Author SLA`**：実稼動作成者層の測定稼動時間（ベンダーまたはAdobeが原因となって発生したインシデントを組み込んでいます）。
* **`Author SLA`**：オーサー層の測定稼動時間で、メンテナンスウィンドウなどの計画的なダウンタイムは無視されます。
* **`End User Contract`**:Adobe Managed Servicesとの契約でパブリッシュ層用に定義されたSLA。
* **`AMS End User SLA`**：実稼動公開層の測定アップタイムで、ベンダーまたはAdobeが原因となって発生したインシデントを組み込んでいます。
* **`End User SLA`**：メンテナンスウィンドウなどの計画的なダウンタイムを無視した、パブリッシュ層の測定稼動時間。

## ビデオチュートリアル {#video-tutorial}

次のビデオでは、Cloud Manager レポートで作成されたグラフを、プログラム環境のビューに使用する方法の概要について説明します。

>[!VIDEO](https://video.tv.adobe.com/v/34274?captions=jpn)
