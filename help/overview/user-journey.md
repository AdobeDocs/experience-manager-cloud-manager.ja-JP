---
title: ユーザーオンボーディング
description: 様々なオンボーディングシナリオと、Cloud Manager を使い始める方法について説明します。
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
TQID: https://experienceleague.adobe.com/EnNaMZzu5bLUD3Jjsp6ovqFvoFM30ju4FOQJfmySLEk
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 2cd89edca1c1dfac7f1b7b68eccdf1416efb4724
workflow-type: tm+mt
source-wordcount: 567
ht-degree: 62%

---

# ユーザーオンボーディング {#user-journey}

AEM（Adobe Experience Manager）のユーザーは、次のいずれかのシナリオに当てはまります。

* AEM を初めて使用する。
* 現在 AEM 6.x を使用している。
* [!UICONTROL Cloud Manager] を使用するには、AEM 6.5 にアップグレードする必要があります。

このドキュメントでは、これらの3つのシナリオについて説明し、[!UICONTROL Cloud Manager]を使い始めるためのプロセスについて説明します。

>[!NOTE]
>
>[!UICONTROL Cloud Manager] は、AEM 6.4 以上を使用している Adobe Managed Services （AMS）のユーザーのみが利用できます。

## オンボーディング {#onboarding}

AMS を初めて使用する場合と、既存の AMS ユーザーでは、オンボーディングプロセスは異なります。

### Adobe Managed Services を初めて使用する {#new-to-ams}

新規のお客様は、Adobe Managed Servicesのオンボーディングプロセスの一環として[!UICONTROL Cloud Manager]にオンボーディングされます。

オンボーディングプロセスの一環として、次の内容のウェルカムメールが届きます。

* [!UICONTROL Cloud Manager] にアクセスする URL。
* [!UICONTROL Experience Cloud] へのログイン手順。
* Admin Consoleを使用して、ユーザーとそれぞれの権限を管理し、必要に応じてCloud Managerにアクセスできるようにするための手順を説明します。

### Adobe Managed Services の現在のお客様 {#existing-customer}

既存の AMS のお客様は、まず既存の本番環境および本番以外の環境を AEM 6.4 以上にアップグレードする必要があります。

アップグレード中に、Cloud Manager にオンボーディングされ、[!UICONTROL Cloud Manager] にアクセスする URL が提供されます。 さらに、[!UICONTROL Cloud Manager] にアクセスする必要があるユーザーについては、Admin Console を使用して、ユーザーとそれぞれの権限を管理する必要があります。

[!UICONTROL AEM]を使用して新しいコード変更をAEM環境にデプロイし始めるので、既存のCloud Manager プロジェクトも推奨事項に準拠する必要があります。

AEM 6.5 へのアップグレードの利点について詳しくは、[AEM 6.5 へのアップグレード](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/implementing/deploying/upgrading/upgrade)を参照してください。

## [!UICONTROL Cloud Manager] へのアクセス {#accessing-cloud-manager}

Adobe Identity Management の資格情報を使用して、[!UICONTROL Experience Cloud] ランディングページにログインします。 ソリューションスイッチャーから「AEM」を選択し、[!UICONTROL Cloud Manager]およびAEM環境にアクセスします。

[!UICONTROL Cloud Manager] に初めてログインした後、[!UICONTROL Cloud Manager] UI から直接 AEM 環境にアクセスできるようになります。 この時点で、[!UICONTROL Cloud Manager]のすべての機能を使用し、最初のコードブランチをステージング環境と実稼動環境にデプロイする準備を整えます。

[!UICONTROL Cloud Manager] の使用を開始する方法について詳しくは、[初回ログイン](/help/getting-started/first-time-login.md)を参照してください。

AEM について詳しくは、[デプロイとメンテナンス](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/implementing/deploying/deploying/deploy)を参照してください。

## [!UICONTROL Cloud Manager] の使用を開始する方法 {#getting-started-with-cloud-manager}

[!UICONTROL Cloud Manager] にログインした後は、次の方法で AEM プロジェクトを開始できます。

1. コードリポジトリ環境を設定します。
1. チームと役割を設定します。 具体的には、Admin Console を使用してユーザーを [!UICONTROL Cloud Manager] プロファイルに追加することで、役割のメンバーシップが割り当てられます。
1. Git リポジトリでソースコード分岐を設定します。
1. 負荷とパフォーマンスのKPI （主要業績評価指標）を定義します。
1. すべての品質チェックが完了したら、コードをステージング環境および本番環境に正常にデプロイするテストシナリオを定義します。

## プロセスの概要 {#end-to-end-journey}

次の図は、[!UICONTROL Cloud Manager] CI/CD パイプラインを使用してコード変更をステージング環境と実稼動環境にデプロイする際のプロセスをまとめたものです。

![Cloud Managerへのオンボーディングに関するカスタマージャーニー。環境のプロビジョニングまたはアップグレード、ユーザーおよびロールの管理、プロジェクトの実装、CI/CD パイプラインを通じた新規顧客および既存顧客のパスを表示します。](/help/assets/screen_shot_2018-05-15at124004pm.png)
