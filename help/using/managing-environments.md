---
title: 環境の管理
description: Cloud Manager を使用して環境を管理する方法について説明します。
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
source-git-commit: 116a930eea08b2bb9d288ec153519699754e0374
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 100%

---


# 環境の管理 {#managing-environments}

Cloud Manager を使用して環境を管理する方法について説明します。

## 概要ページ {#overview-page}

Cloud Manager の&#x200B;**概要**&#x200B;ページには、管理対象のすべての AEM 環境を一覧表示する&#x200B;**環境**&#x200B;タイルが含まれています。

一覧される各環境には、関連するステータスが表示されます。

![概要ページ](/help/assets/Manage-Environ-Overview.png)

## 環境タイル {#environments-tile}

**環境**&#x200B;タイルには、プログラムでプロビジョニングされた実稼動環境とステージング環境がステータスと共に表示されます。

ステータスは、環境内のノード全体で、次の優先順位でロールアップされた電源状態です。

* 緑 - すべてのノードが実行中です
* 赤 - 1 つ以上のノードが停止しています。
* 青 - 1 つ以上のノードが準備中です。
* 黄 - 1 つ以上のノードの電源が切れています。

![環境タイル](/help/assets/Environments-card-new.png)

## 環境の管理 {#managing-environments-with-cloud-manager}

**環境**&#x200B;タイルで、任意の環境の行をタップまたはクリックして&#x200B;**環境**&#x200B;画面を表示します。

**環境**&#x200B;画面には、プログラムの実稼動環境およびステージ環境が表示されます。 環境の名前は各カードの上部に表示されます。 カードには、環境内のノードの表と、CPU（T シャツサイズで表示）、ストレージ、地域およびステータスが含まれます。

>[!NOTE]
>
>ノードの&#x200B;**ステータス**&#x200B;は、VM の稼動状態を表し、サーバー上の AEM のステータスは表しません。 ステータスは次のとおりです。

* 緑 - 実行中
* 赤 - 停止
* 青 - 準備中
* 黄 - 使用不可

![「環境」タブ](/help/assets/Environments-tab.png)

>[!NOTE]
>
>名前などの環境の詳細は、プロビジョニング後は変更できません。

>[!NOTE]
>
>環境ログが必要な場合は、カスタマーサクセスエンジニア経由でリクエストできます。

## ビデオチュートリアル {#video-tutorial}

次のビデオでは、AEM オーサリング、パブリッシング、および Dispatcher インスタンスで構成される Cloud Manager 環境の概要について説明します。

>[!VIDEO](https://video.tv.adobe.com/v/26318/)
