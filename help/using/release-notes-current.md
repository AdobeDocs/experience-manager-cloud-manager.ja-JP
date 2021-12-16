---
title: リリースノート（2021.12.0）
description: Cloud Manager リリース2021.12.0のリリースノートです。
feature: Release Information
source-git-commit: 910def6d82c09e0220a50a3cb34a61f2c7284cb9
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 3%

---

# Cloud Manager リリース2021.12.0のリリースノート {#release-notes}

以下の節では、 [!UICONTROL Cloud Manager] リリース2021.12.0。

>[!NOTE]
>
>AEM as a Cloud Serviceの Cloud Manager の最新のリリースノートについては、 [AEM as a Cloud Serviceの最新のリリースノートの Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## リリース日 {#release-date}

のリリース日 [!UICONTROL Cloud Manager] リリース2021.12.0は 2021 年 12 月 16 日です。 次回のリリースは 2022 年 1 月に予定されています。

## 新機能 {#whats-new}

* UI に既に表示されているコミットハッシュも API で提供されるようになりました。
* アクティビティページに、パイプラインの詳細の概要を一目で確認できる、実行中のパイプラインのポップオーバーが含まれるようになりました。
* アクティビティページに表示される追加の詳細を含めるための更新が追加されました。
* Cloud Manager の「学習」タブで、API ガイドと関連リソースにすばやくアクセスできるようになりました。
* デプロイメントマネージャーの役割を持つユーザーは、リポジトリページのアクションメニューから、ブランチのないリポジトリのプロジェクト/ブランチ作成ウィザードを開始できるようになりました。
* パイプラインの追加または編集ワークフローに属するデプロイメントマネージャーが、選択したリポジトリにブランチがない場合のブランチまたはプロジェクトの作成方法に関する情報を受け取るようになりました。
* 実稼動パイプラインを編集ウィンドウで、実稼動用の複数のステージ環境がある場合は、環境選択用のドロップダウンを使用できます。

## バグ修正 {#bug-fixes}

* ユーザーが名前フィールドに別の名前を入力した場合でも、完全なスタック実稼動パイプラインの名前は「実稼動パイプライン」のままです。
