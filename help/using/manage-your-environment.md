---
title: 環境の管理
seo-title: 環境の管理
description: 'null'
seo-description: このページでは、Cloud Manager での CI／CD パイプラインの設定および実行に使用される実稼働環境および非実稼働環境の一覧を示します。
uuid: 04e67572-11db-4d5d-acf3-fd7f644a95f0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER／CLOUDMANAGER
topic-tags: using
discoiquuid: c5b39de2-3a9b-437f-98e8-e6e6249a5b3a
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# 環境の管理 {#manage-your-environments}

Cloud Manager の**概要**ページには、管理対象のすべての AEM 環境を一覧表示する**環境**タイルが含まれています。

一覧される各環境には、関連するステータスが表示されます。

![](assets/Manage_Environments1.png)

## Cloud Manager での環境へのアクセス {#accessing-environments-in-cloud-manager}

**環境**タイルには、プログラムでプロビジョニングされた実稼動環境とステージング環境が表示されます。

ステータスは、環境内のノード全体の総合的な稼働状態です。すべてのノードが実行中であれば緑、停止しているノードが 1 つでもあれば赤、準備中のノードが 1 つでもあれば青、稼働状態が使用不可のノードが 1 つでもあれば黄色になります。

![](assets/manage_environments-screen2.png)

### 環境 {#environments}

「**管理**」をクリックすると、**環境**画面が表示されます。

**環境**画面には、プログラムの**実稼動環境および*ステージ*環境ごとにカードが表示されます。環境の名前は各カードの上部に表示されます。カードには、環境内のノードの表と、CPU（Tシャツサイズで表示）、ストレージ、地域およびステータスが含まれます。

>[!NOTE]
>
>ノードの**ステータス**は、VM の稼働状態を表し、サーバー上の AEM のステータスは表しません。ステータスは**実行中**（緑の円）、**停止**（赤の円）、**準備中**（青の円）、**使用不可**（黄色の円）のいずれかです。

![](assets/Manage_Environments2.png)
