---
title: ユーザージャーニー
description: このドキュメントでは、様々なオンボーディングシナリオを説明し、Cloud Manager を使い始めるためのジャーニーについて説明します。
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: b0dbb602253939464ff034941ffbad84b7df77df
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 12%

---


# ユーザージャーニー {#user-journey}

Adobe Experience Managerのユーザーは、次の操作を実行できます。

* AEMを初めて使用する場合。
* 現在AEM 6.x を使用している。
* を使用するには、AEM 6.5 リリースにアップグレードする必要があります [!UICONTROL Cloud Manager].

このドキュメントでは、これらのシナリオを説明し、使い始めるためのジャーニーについて説明します。 [!UICONTROL Cloud Manager].

>[!NOTE]
>
>[!UICONTROL Cloud Manager] は、AEM 6.4 以降を使用している Adobe Managed Services(AMS) のお客様のみが利用できます。

## オンボーディング {#onboarding}

オンボーディングプロセスは、AMS を初めて使用する場合と、既存の AMS ユーザーの場合とで異なります。

### Adobe Managed Services の新機能 {#new-to-ams}

新しいお客様は、 [!UICONTROL Cloud Manager] Adobe Managed Services のオンボーディングプロセスの一環として。

オンボーディングプロセスの一環として、次の内容のお知らせメールが届きます。

* アクセスする URL [!UICONTROL Cloud Manager]
* ログイン先 [!UICONTROL Experience Cloud]
* Admin Consoleを使用してユーザーとアクセス権を管理し、ユーザーが [!UICONTROL Cloud Manager] （必要に応じて）

### Adobe Managed Services の既存のお客様 {#existing-customer}

既存の AMS のお客様は、まず、既存の実稼動環境および非実稼動環境をAEM 6.4 以降にアップグレードする必要があります。

アップグレードを実行すると、Cloud Manager にオンボーディングされ、アクセスするための URL が提供されます [!UICONTROL Cloud Manager]. さらに、 [!UICONTROL Cloud Manager]を管理するには、まずAdmin Consoleとそれぞれの権限を管理する必要があります。

また、AEM 環境に新しいコードの変更をデプロイするために、[!UICONTROL Cloud Manager] の使用を開始する際には、既存の AEM プロジェクトを、推奨されるベストプラクティスに従う必要があります。

AEM 6.5 へのアップグレードの利点について詳しくは、このドキュメントを参照してください。 [AEM 6.5 にアップグレードします。](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/upgrade.html)

## [!UICONTROL Cloud Manager] へのアクセス {#accessing-cloud-manager}

次の場所にアクセスできます： [!UICONTROL Cloud Manager] とAEM環境にログインします。 [!UICONTROL Experience Cloud] ランディングページを開き、AdobeIdentity Management資格情報を使用して、ソリューション切り替えインターフェイスからAEMを選択します。

[!UICONTROL Cloud Manager] に初めてログインした後、[!UICONTROL Cloud Manager] UI から直接 AEM 環境にアクセスできます。この時点で、のすべての可能性を確認する準備が整いました。 [!UICONTROL Cloud Manager] 最初のコードブランチを準備して、ステージ環境と実稼動環境にデプロイします。

を使い始めるには、以下を実行します。 [!UICONTROL Cloud Manager]を参照してください。詳しくは、ドキュメントを参照してください。 [初回ログイン](/help/getting-started/first-time-login.md).

AEMについて詳しくは、 [デプロイとメンテナンス。](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html?lang=ja)

## [!UICONTROL Cloud Manager] の概要 {#getting-started-with-cloud-manager}

ログイン後 [!UICONTROL Cloud Manager] 次の方法でAEMプロジェクトを開始できます。

1. コードリポジトリ環境を設定します。
1. チームと役割の設定
   * ロールのメンバーシップは、ユーザーを [!UICONTROL Cloud Manager] プロファイルを作成します。Admin Console
1. Git リポジトリでソースコードブランチを設定します。
1. 負荷とパフォーマンスの KPI に関する目標の定義
1. すべての品質チェックが正常に完了したら、コードをステージおよび実稼動環境に正常にデプロイするためのテストシナリオを定義します。

## エンドツーエンドのジャーニー {#end-to-end-journey}

次の図は、 [!UICONTROL Cloud Manager] コードの変更をステージング環境および実稼動環境にデプロイするための CI/CD パイプライン。

![エンドツーエンドのジャーニー](/help/assets/screen_shot_2018-05-15at124004pm.png)
