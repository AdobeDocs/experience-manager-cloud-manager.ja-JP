---
title: リリースノート（2022.3.0）
description: Cloud Manager リリース 2022.3.0 のリリースノートです。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 79b2729814af483844d095ed8d6db6cead2ceaf7
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 25%

---


# Cloud Manager リリース 2022.3.0 のリリースノート {#release-notes}

このページでは、 [!UICONTROL Cloud Manager] リリース 2022.3.0。

>[!NOTE]
>
>AEM as a Cloud Service の Cloud Manager の最新リリースノートについては、[AEM as a Cloud Service の Cloud Manager の最新リリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja)を参照してください。

## リリース日 {#release-date}

のリリース日 [!UICONTROL Cloud Manager] リリース 2022.3.0 は 2022 年 3 月 10 日です。 次回のリリースは 2022 年 4 月 7 日に予定されています。

## 新機能 {#what-is-new}

* (Cloud Serviceのみ )AEM環境ログへのアクセスは、開発者の役割を使用しておこなうことができます。
* (AMS):アセットテストからの外部 HTTP リクエストは、固定 IP 範囲から取得されるようになりました。


## バグ修正 {#bug-fixes}

* （AMS のみ） **ロードバランサーの変更をスキップ** オプションを無効にできませんでした。
* (AMS) **ロードバランサーの変更をスキップ** オプションが AMS 開発デプロイに表示されませんでした **パイプラインワークフローを編集**.
* 手動で作成した Git リポジトリのサブセットで、誤った名前の値が返され、ビルドアーティファクトの再利用機能が有効になりませんでした。 これらのリポジトリの名前は変更され、Cloud Manager API/UI で修正された名前がユーザーに表示されます。
* 実稼動以外のパイプラインからのビルドアーティファクトが、実稼動のフルスタックパイプラインで不適切に再利用されました。
* コード品質パイプラインを追加または編集する際に、指標の失敗を処理するためのオプションが表示されなくなりました。
* 予期しない一部のパイプライン変数設定がビルドステップで原因となる場合がありました。
