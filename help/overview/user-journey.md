---
title: ユーザージャーニー
description: このドキュメントでは、様々なオンボーディングシナリオを説明し、Cloud Manager の使用を開始する手順について説明します。
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 94%

---


# ユーザージャーニー {#user-journey}

Adobe Experience Manager のユーザーは、次に当てはまる可能性があります。

* AEM を初めて使用する。
* 現在 AEM 6.x を使用している。
* [!UICONTROL Cloud Manager] を使用するには、AEM 6.5 リリースにアップグレードする必要があります。

このドキュメントでは、これらのシナリオを説明し、[!UICONTROL Cloud Manager] を使い始める際のジャーニーについて説明します。

>[!NOTE]
>
>[!UICONTROL Cloud Manager] は、AEM 6.4 以上を使用している Adobe Managed Services （AMS）のユーザーのみが利用できます。

## オンボーディング {#onboarding}

AMS を初めて使用する場合と、既存の AMS ユーザーでは、オンボーディングプロセスは異なります。

### Adobe Managed Services を初めて使用する {#new-to-ams}

新規のお客様は、Adobe Managed Services のオンボーディングプロセスの一環として [!UICONTROL Cloud Manager] にオンボーディングされます。

オンボーディングプロセスの一環として、次の内容のウェルカムメールが届きます。

* [!UICONTROL Cloud Manager] にアクセスする URL
* [!UICONTROL Experience Cloud] へのログイン手順
* Admin Console を使用してユーザーと権利を管理し、ユーザーが必要に応じて [!UICONTROL Cloud Manager] にアクセスする手順

### Adobe Managed Services の既存のユーザー {#existing-customer}

既存の AMS ユーザーは、まず既存の実稼動環境および実稼動以外の環境を AEM 6.4 以上にアップグレードする必要があります。

アップグレードを実行すると、Cloud Manager にオンボーディングされ、[!UICONTROL Cloud Manager] にアクセスするための URL が提供されます。さらに、[!UICONTROL Cloud Manager] にアクセスする必要があるユーザーについては、Admin Console を使用して、ユーザーとそれぞれの権限を管理する必要があります。

また、AEM 環境に新しいコードの変更をデプロイするために、[!UICONTROL Cloud Manager] の使用を開始する際には、既存の AEM プロジェクトを、推奨されるベストプラクティスに従う必要があります。

AEM 6.5 へのアップグレードの利点について詳しくは、[AEM 6.5 へのアップグレード ](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/upgrade.html?lang=ja) を参照してください。

## [!UICONTROL Cloud Manager] へのアクセス {#accessing-cloud-manager}

Adobe Identity Management 資格情報を使用して [!UICONTROL Experience Cloud] ランディングページにログインし、ソリューション切り替えインターフェイスから AEM を選択するだけで、[!UICONTROL Cloud Manager] および AEM 環境にアクセスできます。

[!UICONTROL Cloud Manager] に初めてログインした後、[!UICONTROL Cloud Manager] UI から直接 AEM 環境にアクセスできるようになります。最初のコードブランチをステージ環境および実稼動環境にデプロイすると、この時点で、[!UICONTROL Cloud Manager] のすべての機能を確認する準備が整います。

[!UICONTROL Cloud Manager] を使い始めるには、[初回ログイン](/help/getting-started/first-time-login.md)のドキュメントを参照してください。

AEMについて詳しくは、「デプロイとメンテナンス [ のドキュメントを参照し ](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html?lang=ja) ください。

## [!UICONTROL Cloud Manager] の概要 {#getting-started-with-cloud-manager}

[!UICONTROL Cloud Manager] にログインした後は、次の方法で AEM プロジェクトを開始できます。

1. コードリポジトリ環境を設定します。
1. チームと役割を設定します。
   * 具体的には、Admin Console を使用してユーザーを [!UICONTROL Cloud Manager] プロファイルに追加することで、役割のメンバーシップが割り当てられます。
1. Git リポジトリでソースコードブランチを設定します。
1. 負荷とパフォーマンスの KPI に関する目標を定義します。
1. すべての品質チェックが正常に完了したら、コードをステージ環境および実稼動環境に正常にデプロイするためのテストシナリオを定義します。

## エンドツーエンドのジャーニー {#end-to-end-journey}

この図は、[!UICONTROL Cloud Manager] CI／CD パイプラインを使用してコード変更をステージング環境および実稼動環境にデプロイする場合の、高レベルでのカスタマージャーニーの概要を示します。

![エンドツーエンドのジャーニー](/help/assets/screen_shot_2018-05-15at124004pm.png)
