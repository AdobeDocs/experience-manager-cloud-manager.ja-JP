---
title: リリースノート（2021.12.0）
description: Cloud Manager リリース 2021.12.0 のリリースノートです。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 61f2d1e0882b752d1a1d5e62f9c028aa71941efe
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 100%

---

# Cloud Manager リリース 2021.12.0 のリリースノート {#release-notes}

次のセクションでは、[!UICONTROL Cloud Manager] リリース 2021.12.0 のリリースノートの概要を説明します。

>[!NOTE]
>
>AEM as a Cloud Service の Cloud Manager の最新のリリースノートについては、「[AEM as a Cloud Service の Cloud Manager の最新のリリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja)」を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] リリース 2021.12.0 のリリース日は 2021 年 12 月 16 日です。次回のリリースは 2022 年 1 月（PT）の予定です。

## 新機能 {#whats-new}

* UI ではすでに表示されているコミットハッシュも、API で提供されるようになりました。
* アクティビティページにパイプラインを実行中のポップオーバーが追加され、パイプラインの詳細が一目でわかるようになりました。
* アクティビティページに表示される追加の詳細を含める更新を行いました。
* Cloud Manager の「学習」タブに、API ガイドと関連リソースへのクイックアクセスが追加されました。
* Deployment Manager のロールを持つユーザーは、リポジトリページのアクションメニューから、ブランチのないリポジトリに対してプロジェクト/ブランチ作成ウィザードを開始できるようになりました。
* パイプラインの追加または編集ワークフローにいる Deployment Manager は、選択したリポジトリにブランチがない場合、ブランチまたはプロジェクトを作成する方法を通知されるようになりました。
* 実稼動パイプラインの編集ウィンドウで、実稼動用のステージ環境が複数ある場合、環境選択用のドロップダウンを使用できるようになりました。
* Cloud Manager で使用される AEM プロジェクトアーキタイプのバージョンが 32 に更新されました。

## バグ修正 {#bug-fixes}

* 完全なスタック実稼動パイプラインの名前は、ユーザーが名前フィールドに別の名前を入力した場合でも、「実稼動パイプライン」のままです。
