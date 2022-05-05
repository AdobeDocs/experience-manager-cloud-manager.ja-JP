---
title: リリースノート（2022.5.0）
description: Cloud Manager リリース 2022.5.0 のリリースノートです。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 84cc4352488002ad40102ea2c507af652d9012a1
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 66%

---


# Cloud Manager リリース 2022.5.0 のリリースノート {#release-notes}

このページは、[!UICONTROL Cloud Manager] リリース 2022.5.0 のリリースノートです。

>[!NOTE]
>
>AEM as a Cloud Service の Cloud Manager の最新リリースノートについては、[AEM as a Cloud Service の Cloud Manager の最新リリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja)を参照してください。

## リリース日 {#release-date}

のリリース日 [!UICONTROL Cloud Manager] リリース 2022.5.0 は 2022 年 5 月 6 日です。 次回のリリースは 2022 年 6 月 9 日（PT）に予定されています。

## 新機能 {#what-is-new}

アセットテストからのアウトバウンド HTTP リクエストは、固定 IP 範囲から送信されるようになりました。

## バグ修正 {#bug-fixes}

* 「ロードバランサーをスキップ」の変更オプションを無効にできませんでした。
* AMS 開発デプロイ編集パイプラインワークフローに「ロードバランサーの変更をスキップ」オプションが表示されませんでした。
* 手動で作成した GIT リポジトリのサブセットで、誤った名前の値が設定されていたので、ビルドアーティファクトの再利用機能が有効になりませんでした。 これらのリポジトリの名前が変更され、Cloud Manager API／UI では修正された名前がユーザーに表示されます。
* 実稼動以外のパイプラインから得られたビルドアーティファクトが、実稼動のフルスタックパイプラインで不適切に再利用されていました。
* コード品質パイプラインを追加または編集する際に、指標の失敗を処理するためのオプションが表示されなくなりました。
* 予期しない一部のパイプライン変数設定が原因で、ビルドステップでエラーが発生する可能性がありました。
