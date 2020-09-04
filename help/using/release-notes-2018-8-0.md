---
title: リリースノート（2018.8.0）
seo-title: AEM Cloud Manager リリースノート（2018.8.0）
description: このページでは、Cloud Manager リリース 2018.8.0 について説明します。
seo-description: このページでは、AEM Cloud Manager リリース 2018.8.0 について説明します。
uuid: e8aaba32-89b4-4bc5-b295-09b753252612
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 9222ac3b-525e-47c1-b481-ac9d22e3d559
translation-type: tm+mt
source-git-commit: c35398110e9d8311bf58f217efdd082cf0cfd90a
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 95%

---


# リリースノート（2018.8.0） {#release-notes-for}

[!UICONTROL Cloud Manager] 2018.8.0 リリースでは、Git コミット時に CI／CD パイプラインを自動的にトリガーできるようになったほか、AEM プロジェクトアーキタイプに基づいて Git にアプリケーションプロジェクトを作成するための新しいウィザードが追加されました。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2018.8.0 のリリース日は 2018 年 10 月 4 日です。

## 新機能 {#what-s-new}

* **プログラムの設定** - AEMプロジェクトアーキタイプを使用してアプリケーションプロジェクトをgitで作成する新しいウィザード

* **CI／CD パイプライン** - CI／CD パイプラインに次の変更が追加されました。詳しくは、[CI／CD パイプラインの設定](configuring-pipeline.md)を参照してください。

   * 設定された Git ブランチにコミットが追加されるたびに CI／CD パイプラインを開始する「Git の変更時」トリガーが導入されました。
   * ホーム画面のカードが、パイプライン実行ページの特定のセクションにディープリンクされるようになりました。
   * アクティビティページに、実行ごとに使用される特定のブランチが一覧表示されるようになりました。
   * アクティビティページに、時間および分単位で期間が表示されるようになりました。
   * パイプライン実行ページに、実行用に作成されたバージョン／タグ名が表示されるようになりました。
   * Apache Maven バージョンが 3.5.3 に更新されました。

* **ナビゲーション** - [!UICONTROL Cloud Manager] に次の変更が追加されました。

   * グローバルナビゲーションのリソースリンクをクリックすると、SharePoint の Runbook に移動します。
   * ヘルプメニューが再編成されて、[!UICONTROL Cloud Manager] 固有のコンテンツがさらに含まれるようになりました。

## バグ修正 {#bug-fixes}

* パフォーマンステストダイアログの一部の詳細が Firefox に表示されませんでした。
* 内部システム間のタイムアウトによって、デプロイメントの失敗が報告されることがありました。
* パイプライン実行に成功した場合に、アクティビティページのアイコンの色が正しく表示されないことがありました。
* パフォーマンステストダイアログに同じ指標が複数回表示される場合がありました。
* CI／CD パイプラインの開始後に新しいインスタンスを追加した場合、新しく作成されたインスタンスでデプロイメントが実行されませんでした。

## 既知の問題 {#known-issues}

* アプリケーションプロジェクトウィザードを使用して作成したブランチにダッシュを含めることができません。
* [!UICONTROL Experience Cloud] の通知サイドバーでは、通知の読み込みに一貫性がない場合があります。ただし、通知は [!UICONTROL Experience Cloud] には表示され、設定に応じて電子メールでも送信されます。

