---
title: プログラム設定
description: オンボーディング後、ビジネスオーナーはプログラムの初期設定を行う必要があります。
exl-id: 795c7112-d564-4fbf-96a1-152a6c286bf2
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 92%

---


# プログラム設定 {#program-setup}

オンボーディング後、ビジネスオーナーは、プログラムの説明の設定や、パフォーマンステストに使用する主要業績評価指標（KPI）の定義など、プログラムの初期設定を完了します。

## [!UICONTROL Cloud Manager] を使用したプログラム設定 {#program-setup-cloud-manager}

プログラムを設定し、KPI を定義するには、次の手順に従います。

1. [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) で Cloud Manager にログインし、適切な組織を選択します。

1. 「**プログラムを設定**」をクリックして設定プロセスを開始します。

   ![プログラムを設定](/help/assets/set-up-program/setup1.png)

1. **プログラムを設定**&#x200B;ダイアログでは、次の 3 つのタブにプログラム情報を入力できます。

   * **一般**
   * **KPI**
   * **プロビジョニング**

1. 「**一般**」タブで、プログラムの説明を追加し、オプションで「**写真を変更**」をクリックしてサムネールをアップロードします。

   ![「一般」タブ](/help/assets/Setup_Program-General.png)

1. 「**KPI**」タブで、KPI を定義します。この例では、**AEM Sites** と **AEM Assets** に別個の KPI を定義します。ライセンス取得済みの製品の KPI を指定できます。

   * Cloud Manager での KPI の測定方法について詳しくは、[KPI](#kpis) の節を参照してください。

   ![KPI の定義](/help/assets/Setup_Program-KPIs.png)

1. 「**プロビジョニング**」タブでは、プログラムで自動スケーリングが有効になっている場合の、環境に応じたオンデマンドスケーリングオプションを定義できます。

   * 自動スケーリングは実稼動環境のみに適用でき、すべての顧客プログラムには使用できない可能性があります。

   ![「プロビジョニング」オプション](/help/assets/Setup_Program-Provisioning.png)

1. 「**保存**」をクリックして、設定ウィザードを完了します。

プログラムが作成されます。プログラムが使用できる状態になるまで、リソースのプロビジョニングに数分かかる場合があります。

## プログラムの編集 {#editing-program}

設定後にプログラムを編集できます。プログラムを編集するには、次の手順に従います。

1. [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) で Cloud Manager にログインし、適切な組織を選択します。

1. Cloud Manager のホーム画面でソリューションに移動します。

1. 「**プログラムを編集**」をクリックして、**概要**&#x200B;ページからプログラムを更新または変更します。

   ![プログラムオプションを編集](/help/assets/set-up-program/edit-program1.png)

1. **プログラムを編集**&#x200B;ダイアログが表示され、プログラムを更新できます。使用可能なフィールドについて詳しくは、[Cloud Manager を使用したプログラムの設定](#program-setup-cloud-manager)の節を参照してください。

   ![プログラムを編集ダイアログ](/help/assets/set-up-program/edit-program-general.png)

1. 「**更新**」をクリックして変更を保存します。

変更は Cloud Manager に直ちに保存されますが、次のパイプラインが実行されるまで環境に反映されません。

まだパイプラインを作成していない場合は、ドキュメント [ 実稼動パイプラインの設定 ](/help/using/production-pipelines.md) および [ 実稼動以外のパイプラインの設定 ](/help/using/non-production-pipelines.md) を参照してください。

## プログラム間の切り替え {#swithing-programs}

プログラムを操作する際に、Cloud Manager の概要ページに戻ることなく、別のプログラムにすばやく切り替えることができます。

別のプログラムへの切り替え、現在のプログラムの編集、新しいプログラムの追加を行うには、アクションバーを使用します。

![プログラムスイッチャー](/help/assets/set-up-program/setup2.png)

## KPI {#kpis}

Sites KPI は、ステージング環境で実行されるテストで測定されます。一般に、これらの KPI はステージング環境の機能に合わせて縮小されます。

例えば、実稼動環境で 1 分あたり平均 1,000 ページビューを期待し、実稼動環境に 4 つの Dispatcher/パブリッシュサーバーがある場合、これを 1 分あたり 250 ページビューに拡大縮小する必要があります。これは、ステージング環境が 1 つの Dispatcher とパブリッシュサーバーのペアのみで構成されていると想定しています。

Assetsのパフォーマンステストでは、30 分間のテスト期間中にアセットを繰り返しアップロードし、各アセットの処理時間および様々なシステムレベルの指標を測定します。

実稼動環境の前に、Akamai や CloudFront などのコンテンツ配信ネットワーク（CDN）がある場合があります。[!UICONTROL Cloud Manager] はステージング環境に対して直接テストするので、KPI は、CDN を経由すると予想されるトラフィック（つまり、キャッシュミス）のみを反映している必要があります。通常、これは実稼動トラフィック全体の比較的小さいサブセットになります。

## ビデオの概要 {#video}

>[!VIDEO](https://video.tv.adobe.com/v/26313/)
