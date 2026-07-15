---
title: プログラム設定
description: オンボーディング後、ビジネスオーナーはプログラムの初期設定を行う必要があります。
exl-id: 795c7112-d564-4fbf-96a1-152a6c286bf2
TQID: https://experienceleague.adobe.com/AqaA4GSOptV11h2y4V1Mt15KmEhEYBaiM-RvBFjtfWY
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: fa6be369b979682cebf68852603725d8754605ab
workflow-type: tm+mt
source-wordcount: 549
ht-degree: 65%

---

# プログラム設定 {#program-setup}

オンボーディング後、ビジネスリードは、説明を追加し、重要業績評価指標（KPI）を定義することで、プログラムを設定します。 次に、これらの KPI をパフォーマンステストに使用します。

## [!UICONTROL Cloud Manager] を使用したプログラム設定 {#program-setup-cloud-manager}

1. [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) で Cloud Manager にログインし、適切な組織を選択します。

1. 「**プログラムを設定**」をクリックして設定プロセスを開始します。

   ![プログラムを設定](/help/assets/set-up-program/setup1.png)

1. **プログラムを設定**&#x200B;ダイアログボックスでは、次の 3 つのタブにプログラム情報を入力できます。

   * **一般**
   * **KPI**
   * **プロビジョニング**

1. 「**一般**」タブで、プログラムの説明を追加し、オプションで「**写真を変更**」をクリックしてサムネールをアップロードします。

   ![「一般」タブ](/help/assets/Setup_Program-General.png)

1. 「**KPI**」タブで、KPI を定義します。 この例では、**AEM Sites** と **AEM Assets** に別個の KPI を定義します。 ライセンス取得済みの製品の KPI を指定します。

   Cloud Manager での KPI の測定方法について詳しくは、[KPI](#kpis) の節を参照してください。

   ![KPI の定義](/help/assets/Setup_Program-KPIs.png)

1. **プロビジョニング** タブで、プログラムで自動拡張が有効になっている場合は、環境のオンデマンド拡張オプションを定義できます。

   自動拡張は実稼動環境にのみ適用され、一部のお客様のプログラムでは使用できません。

   ![「プロビジョニング」オプション](/help/assets/Setup_Program-Provisioning.png)

1. 「**保存**」をクリックします。

プログラムが作成されます。 プログラムを使用する準備が整うまでに、リソースをプロビジョニングするのに数分かかります。

## プログラムの編集 {#editing-program}

設定後にプログラムを編集できます。

**プログラムを編集するには：**

1. [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) で Cloud Manager にログインし、適切な組織を選択します。

1. Cloud Manager のホーム画面でソリューションに移動します。

1. 「**プログラムを編集**」をクリックして、**概要**&#x200B;ページからプログラムを更新または変更します。

   ![プログラムオプションを編集](/help/assets/set-up-program/edit-program1.png)

1. **プログラムを編集**&#x200B;ダイアログが表示され、プログラムを更新できます。 使用可能なフィールドについて詳しくは、[Cloud Manager を使用したプログラムの設定](#program-setup-cloud-manager)の節を参照してください。

   ![プログラムを編集ダイアログ](/help/assets/set-up-program/edit-program-general.png)

1. 「**更新**」をクリックして変更を保存します。

変更は Cloud Manager に直ちに保存されますが、次にパイプラインが実行されるまで環境に反映されません。

まだパイプラインを作成していない場合は、[実稼動パイプラインの設定](/help/using/production-pipelines.md)および[実稼動以外のパイプラインの設定](/help/using/non-production-pipelines.md)を参照してください。

## プログラム間の切り替え {#swithing-programs}

プログラムを操作する際に、Cloud Manager の概要ページに戻ることなく、別のプログラムにすばやく切り替えることができます。

別のプログラムへの切り替え、現在のプログラムの編集、新しいプログラムの追加を行うには、アクションバーを使用します。

![プログラムスイッチャー](/help/assets/set-up-program/setup2.png)

## KPI {#kpis}

Sites KPI は、ステージング環境で実行されるテストで測定されます。 通常、これらのKPIは、ステージング環境の機能に合わせて調整されます。

例えば、本番環境で1分間あたり平均1000 ページビューを期待し、本番環境に4台のDispatcher/パブリッシングサーバーを持つユーザーは、このシナリオを1分間あたり250 ページビューに減らします。 このシナリオでは、ステージング環境が1つのDispatcherとパブリッシュのサーバーペアのみで構成されることを前提としています。

Assets のパフォーマンステストでは、30 分間にわたってアセットを繰り返しアップロードします。 各アセットの処理時間と、様々なシステムレベルの指標が、テスト全体にわたって測定されます。

AkamaiやCloudFrontなどのコンテンツ配信ネットワーク（CDN）が本番環境用に設定されている。 [!UICONTROL Cloud Manager]はステージング環境に対して直接テストを行うため、CDNを通過すると予想されるトラフィックのみがKPIに反映されます。 つまり、キャッシュミスです。 通常、このトラフィックは総本番トラフィックの比較的小さなサブセットです。

## ビデオの概要 {#video}

>[!VIDEO](https://video.tv.adobe.com/v/34266?captions=jpn)
