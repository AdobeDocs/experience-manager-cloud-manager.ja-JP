---
title: リリースノート（2022.5.0）
description: Cloud Manager リリース 2022.5.0 のリリースノートです。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 0ddfd152cb15731882d198d043dd8897b5073ab4
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 82%

---


# Cloud Manager リリース 2022.5.0 のリリースノート {#release-notes}

このページは、[!UICONTROL Cloud Manager] リリース 2022.5.0 のリリースノートです。

>[!NOTE]
>
>AEM as a Cloud Service の Cloud Manager の最新リリースノートについては、[AEM as a Cloud Service の Cloud Manager の最新リリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja)を参照してください。

## リリース日 {#release-date}

のリリース日 [!UICONTROL Cloud Manager] リリース 2022.5.0 は 2022 年 5 月 6 日です。 次回のリリースは 2022 年 6 月 9 日（PT）に予定されています。

## 新機能 {#what-is-new}

AEM環境ログへのアクセスは、開発者ロールを使用しておこなうことができます。

## バグの修正 {#bug-fixes}

* 手動で作成した Git リポジトリのサブセットで名前の値が間違っていたので、ビルドアーティファクトの再利用機能が有効に働きませんでした。これらのリポジトリの名前が変更され、Cloud Manager API／UI では修正された名前がユーザーに表示されます。
* 実稼動以外のパイプラインから得られたビルドアーティファクトが、実稼動のフルスタックパイプラインで不適切に再利用されていました。
* コード品質パイプラインを追加または編集する際に、指標の失敗を処理するためのオプションが表示されなくなりました。
* 予期しない一部のパイプライン変数設定が原因で、ビルドステップでエラーが発生する可能性がありました。
