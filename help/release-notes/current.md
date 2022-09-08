---
title: リリースノート（2022.9.0）
description: Cloud Manager リリース 2022.9.0 のリリースノートです。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: e74d386d0b2d50a7e276bb7ead7594ef448742ae
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 35%

---


# Cloud Manager リリース 2022.9.0 のリリースノート {#release-notes}

このページは、[!UICONTROL Cloud Manager] リリース 2022.9.0 のリリースノートです。

>[!NOTE]
>
>AEM as a Cloud Service の Cloud Manager の最新リリースノートについては、[AEM as a Cloud Service の Cloud Manager の最新リリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja)を参照してください。

## リリース日 {#release-date}

のリリース日 [!UICONTROL Cloud Manager] リリース 2022.9.0 は 2022 年 9 月 8 日です。 次回のリリースは 2022 年 10 月 7 日に予定されています。

## 新機能 {#what-is-new}

* Cloud Manager での水平方向の複数地域の自動スケーリングのサポート。
* AEM環境への移動方法とプログラムアクセスの制限に関するガイドを持つ Cloud Manager ユーザーの役割のみを持つユーザー向けにカスタマイズされた新しいようこそページカード。
* Cloud Manager の役割を持たないお客様は、プログラムの詳細にアクセスできません。 ただし、CM ランディングページから作成エンドポイントに移動することはできます。
* 回復性の向上を構築することで、再試行の失敗に起因するパイプライン障害を排除します。

## バグ修正 {#bug-fixes}

* Maven がプライベートリポジトリへの接続に関する問題に直面した場合の、顧客のAEMアプリビルドに関するお客様のフィードバックを改善しました。
* ヘルスチェックシステムが有効なヘルススコアを取得できない場合、自動スケールイベントがトリガーされないことが稀にあります。
