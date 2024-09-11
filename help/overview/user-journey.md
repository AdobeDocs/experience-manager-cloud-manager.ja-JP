---
title: ユーザージャーニー
description: 様々なオンボーディングシナリオと、Cloud Manager を使い始める方法について説明します。
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '532'
ht-degree: 100%

---


# ユーザージャーニー {#user-journey}

AEM（Adobe Experience Manager）ユーザーは、次のシナリオのいずれかに該当する可能性があります。

* AEM を初めて使用する。
* 現在 AEM 6.x を使用している。
* [!UICONTROL Cloud Manager] を使用するには、AEM 6.5 にアップグレードする必要があります。

このドキュメントでは、これらの 3 つのシナリオを説明し、[!UICONTROL Cloud Manager] を使い始める際のジャーニーについて説明します。

>[!NOTE]
>
>[!UICONTROL Cloud Manager] は、AEM 6.4 以上を使用している Adobe Managed Services （AMS）のユーザーのみが利用できます。

## オンボーディング {#onboarding}

AMS を初めて使用する場合と、既存の AMS ユーザーでは、オンボーディングプロセスは異なります。

### Adobe Managed Services を初めて使用する {#new-to-ams}

新規のお客様は、Adobe Managed Services のオンボーディングプロセスの一環として [!UICONTROL Cloud Manager] にオンボーディングされます。

オンボーディングプロセスの一環として、次の内容のウェルカムメールが届きます。

* [!UICONTROL Cloud Manager] にアクセスする URL。
* [!UICONTROL Experience Cloud] へのログイン手順。
* Admin Console を使用してユーザーと権利を管理し、ユーザーが必要に応じて [!UICONTROL Cloud Manager] にアクセスする手順。

### Adobe Managed Services の現在のお客様 {#existing-customer}

既存の AMS のお客様は、まず既存の実稼動環境および実稼動以外の環境を AEM 6.4 以上にアップグレードする必要があります。

アップグレード中に、Cloud Manager にオンボーディングされ、[!UICONTROL Cloud Manager] にアクセスする URL が提供されます。さらに、[!UICONTROL Cloud Manager] にアクセスする必要があるユーザーについては、Admin Console を使用して、ユーザーとそれぞれの権限を管理する必要があります。

また、AEM 環境に新しいコードの変更をデプロイするのに、[!UICONTROL Cloud Manager] の使用を開始する際には、既存の AEM プロジェクトを、推奨されるベストプラクティスに従う必要があります。

AEM 6.5 へのアップグレードの利点について詳しくは、[AEM 6.5 へのアップグレード](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/implementing/deploying/upgrading/upgrade)を参照してください。

## [!UICONTROL Cloud Manager] へのアクセス {#accessing-cloud-manager}

Adobe Identity Management の資格情報を使用して、[!UICONTROL Experience Cloud] ランディングページにログインします。そこから、ソリューション切り替えボタンで「AEM」を選択して、[!UICONTROL Cloud Manager] と AEM 環境にアクセスします。

[!UICONTROL Cloud Manager] に初めてログインした後、[!UICONTROL Cloud Manager] UI から直接 AEM 環境にアクセスできるようになります。この時点で、[!UICONTROL Cloud Manager] のすべての機能を確認する準備が整い、ステージング環境および実稼動環境に最初のコード分岐をデプロイする準備が整いました。

[!UICONTROL Cloud Manager] の使用を開始する方法について詳しくは、[初回ログイン](/help/getting-started/first-time-login.md)を参照してください。

AEM について詳しくは、[デプロイとメンテナンス](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/implementing/deploying/deploying/deploy)を参照してください。

## [!UICONTROL Cloud Manager] の使用を開始する方法 {#getting-started-with-cloud-manager}

[!UICONTROL Cloud Manager] にログインした後は、次の方法で AEM プロジェクトを開始できます。

1. コードリポジトリ環境を設定します。
1. チームと役割を設定します。具体的には、Admin Console を使用してユーザーを [!UICONTROL Cloud Manager] プロファイルに追加することで、役割のメンバーシップが割り当てられます。
1. Git リポジトリでソースコード分岐を設定します。
1. 負荷とパフォーマンスの KPI（主要業績評価指標）に関する目標を定義します。
1. すべての品質チェックが完了したら、コードをステージング環境および実稼動環境に正常にデプロイするテストシナリオを定義します。

## エンドツーエンドのジャーニー {#end-to-end-journey}

この図は、[!UICONTROL Cloud Manager] CI/CD パイプラインを使用してコード変更をステージング環境および実稼動環境にデプロイする場合の、高レベルでのカスタマージャーニーの概要を示します。

![エンドツーエンドのジャーニー](/help/assets/screen_shot_2018-05-15at124004pm.png)
