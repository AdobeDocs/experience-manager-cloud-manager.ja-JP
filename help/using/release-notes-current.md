---
title: リリースノート（2022.3.0）
description: Cloud Manager リリース 2022.3.0 のリリースノートです。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 6e98f9d2fcd69799bad86d1e247212b26273bd0b
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 29%

---


# Cloud Manager リリース 2022.3.0 のリリースノート {#release-notes}

このページでは、 [!UICONTROL Cloud Manager] リリース 2022.3.0。

>[!NOTE]
>
>AEM as a Cloud Service の Cloud Manager の最新リリースノートについては、[AEM as a Cloud Service の Cloud Manager の最新リリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja)を参照してください。

## リリース日 {#release-date}

のリリース日 [!UICONTROL Cloud Manager] リリース 2022.3.0 は 2022 年 3 月 10 日です。 次回のリリースは 2022 年 4 月 7 日に予定されています。

## 新機能 {#what-is-new}

* [この `reliability_rating` 重要指標](understand-your-test-results.md) は無効になっています。
* ユーザーが **パイプライン** Cloud Manager のページを参照してください。

## バグ修正 {#bug-fixes}

* [この **ロードバランサーの変更をスキップ** オプション](configuring-production-pipelines.md#adding-production-pipeline) が適切に無効になるようになりました。
* [この **ロードバランサーの変更をスキップ** オプション](configuring-production-pipelines.md#adding-production-pipeline) が、デプロイメントパイプラインの編集ワークフローに表示されるようになりました。
* 手動で作成した Git リポジトリのサブセットで、間違った名前値が使用されていたので、影響を受けました [アーティファクトの再利用機能を構築します。](setting-up-project.md#build-artifact-reuse) これらのリポジトリの名前は変更され、Cloud Manager API/UI で修正された名前がユーザーに表示されます。
* [コード品質パイプラインを追加または編集する場合、](configuring-non-production-pipelines.md) 指標の失敗を処理するオプションは表示されなくなりました。
* 予期しないパイプライン変数設定が、ビルドステップでエラーを引き起こさなくなりました。
