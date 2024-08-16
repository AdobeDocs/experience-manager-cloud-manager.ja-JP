---
title: ユーザージャーニー
description: 様々なオンボーディングシナリオとCloud Managerの基本を学びます。
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: 6a5615c0db91c62fc8858b967021b46c7b383aa0
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 24%

---


# ユーザージャーニー {#user-journey}

AEM（Adobe Experience Manager）のユーザーは、次のいずれかの状況に当てはまる可能性があります。

* AEMを初めて使用する場合。
* 現在、AEM 6.x を使用しています。
* [!UICONTROL Cloud Manager] を使用するには、AEM 6.5 にアップグレードする必要があります。

このドキュメントでは、これらの 3 つのシナリオを説明し、[!UICONTROL Cloud Manager] を使い始める際のジャーニーについて説明します。

>[!NOTE]
>
>[!UICONTROL Cloud Manager] は、AEM 6.4 以上を使用している Adobe Managed Services （AMS）のユーザーのみが利用できます。

## オンボーディング {#onboarding}

AMS を初めて使用する場合と、既存の AMS ユーザーでは、オンボーディングプロセスは異なります。

### Adobe Managed Services を初めて使用する {#new-to-ams}

新規のお客様は、AdobeManaged Servicesのオンボーディングプロセスの一環として ]0}Cloud Manager} にオンボーディングされます。[!UICONTROL 

オンボーディングプロセスの一環として、次の内容のお知らせメールが届きます。

* [!UICONTROL Cloud Manager] にアクセスする URL。
* [!UICONTROL Experience Cloud] へのログイン手順。
* Admin Console を使用してユーザーと権利を管理し、ユーザーが必要に応じて [!UICONTROL Cloud Manager] にアクセスする手順

### 現在のAdobe Managed Servicesのお客様 {#existing-customer}

既存の AMS ユーザーは、まず既存の実稼動環境および実稼動以外の環境をAEM 6.4 以降にアップグレードする必要があります。

アップグレード中、ユーザーはCloud Managerにオンボーディングされ、[!UICONTROL Cloud Manager] にアクセスするための URL が提供されます。 さらに、[!UICONTROL Cloud Manager] にアクセスする必要があるユーザーについては、Admin Consoleを使用して、ユーザーとそれぞれの権限を管理する必要があります。

また、AEM環境に新しいコードの変更をデプロイするために、[!UICONTROL Cloud Manager] の使用を開始するので、既存のAEM プロジェクトを、推奨されるベストプラクティスに従う必要があります。

AEM 6.5 へのアップグレードの利点について詳しくは、[AEM 6.5 へのアップグレード](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/upgrading/upgrade)を参照してください。

## [!UICONTROL Cloud Manager] へのアクセス {#accessing-cloud-manager}

AdobeのIdentity Management資格情報を使用して ]Experience Cloud} ランディングページにログインします。 [!UICONTROL ソリューション切り替えボタンで「AEM」を選択すると、[!UICONTROL Cloud Manager] およびAEM環境にアクセスできます。

[!UICONTROL Cloud Manager] に初めてログインした後、[!UICONTROL Cloud Manager] UI から直接AEM環境にアクセスできるようになります。 最初のコードブランチをステージ環境および実稼動環境にデプロイすると、この時点で、[!UICONTROL Cloud Manager] のすべての機能を確認する準備が整います。

[!UICONTROL Cloud Manager] を使い始めるには、[ 初回ログイン ](/help/getting-started/first-time-login.md) を参照してください。

AEMについて詳しくは、[ デプロイとメンテナンス ](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/implementing/deploying/deploying/deploy) を参照してください。

## [!UICONTROL Cloud Manager] の基本を学ぶ {#getting-started-with-cloud-manager}

[!UICONTROL Cloud Manager] にログインした後は、次の操作を実行してAEM プロジェクトを開始できます。

1. コードリポジトリー環境を設定します。
1. チームと役割を設定します。 具体的には、Admin Console を使用してユーザーを [!UICONTROL Cloud Manager] プロファイルに追加することで、役割のメンバーシップが割り当てられます。
1. Git リポジトリにソースコードブランチを設定します。
1. 目標を負荷とパフォーマンスの KPI （主要業績評価指標）の観点から定義します。
1. すべての品質チェックに合格したら、コードをステージ環境および実稼動環境に正常にデプロイするためのテストシナリオを定義します。

## エンドツーエンドのジャーニー {#end-to-end-journey}

この図は、[!UICONTROL Cloud Manager] CI/CD パイプラインを使用してコード変更をステージング環境および実稼動環境にデプロイする場合の、高レベルでのカスタマージャーニーの概要を示します。

![エンドツーエンドのジャーニー](/help/assets/screen_shot_2018-05-15at124004pm.png)
