---
title: リリースノート（2018.5.0）
seo-title: AEM Cloud Manager リリースノート（2018.5.0）
description: このページでは、Cloud Manager リリース 2018.5.0 について説明します。
seo-description: このページでは、AEM Cloud Manager リリース 2018.5.0 について説明します。
uuid: 37f8b155-6984-454d-83a8-3f5fb081be97
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 6d1e7098-b56e-4172-8373-486f186f3d53
feature: リリース情報
translation-type: tm+mt
source-git-commit: c5d32d49782c899d013fcc60b9c4d2b67e9350ae
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 100%

---


# リリースノート（2018.5.0） {#release-notes-for}

以下の節では [!UICONTROL Cloud Manager] リリース 2018.5.0 の一般リリースノートの概要を説明します。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2018.5.0 のリリース日は 2018 年 7 月 12 日です。

## 最新情報 {#what-s-new}

* **CI／CD パイプライン通知** - パイプラインイベントの [!UICONTROL Experience Cloud] 通知が表示されるようになります。詳しくは、[通知](notifications.md)を参照してください。

* **スケジュールされた実稼動デプロイメント** - ユーザーが実稼動デプロイメントの日時をスケジュールできるようになりました。詳しくは、[コードのデプロイ](deploying-code.md)を参照してください。

* **ステータス**&#x200B;ページのタイトルが&#x200B;**アクティビティ**&#x200B;に変更されました。

* パイプラインの実行中に発生した問題について、より具体的な情報がホームページに表示されるようになりました。
* パフォーマンステストインフラストラクチャが改善されました。

## バグ修正 {#bug-fixes}

* 一部の状況では、間違った SonarQube プロファイルが使用された結果、不正確なコード品質指標が得られていました。
* SonarQube チェック CQBP-75 で特定の OSGi 注釈が無視されていました。
* CI／CD パイプラインがキャンセルされた場合、状態の表示に矛盾がありました。

## 既知の問題 {#known-issues}

* プログラムリスト画面で **AEM** および&#x200B;**監視**&#x200B;へのリンクを使用すると、現在のブラウザータブが置き換えられ、新しいタブが開きます。

