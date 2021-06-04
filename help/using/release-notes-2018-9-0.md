---
title: リリースノート（2018.9.0）
seo-title: AEM Cloud Manager リリースノート（2018.9.0）
description: このページでは、Cloud Manager リリース 2018.9.0 について説明します。
seo-description: このページでは、AEM Cloud Manager リリース 2018.9.0 について説明します。
uuid: 3af5808f-828f-4846-bee4-1e62194b48ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 85a1dcf3-2eef-4ba8-b4d1-09e4a88c7bd0
feature: リリース情報
exl-id: bf611743-ded2-4503-97c8-12b12454c7b7
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 100%

---

# リリースノート（2018.9.0） {#release-notes-for}

[!UICONTROL Cloud Manager] 2018.9.0 リリースでは、[!UICONTROL Cloud Manager] の CI／CD パイプラインを他のシステムと統合するための Adobe I/O ベースの API（Adobe I/O Events など）をサポートするようになりました。また、React の UI レイヤーの書き直しにも着手しました。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2018.9.0 のリリース日は 2018 年 11 月 1 日（PT）です。

## 新機能 {#whats-new}

* **CI／CD パイプライン** - Cloud [!UICONTROL Manager] の CI／CD パイプラインを他のシステムと統合するための新しい API およびイベントシステムが導入されました。詳しくは、[!UICONTROL Cloud Manager] API ドキュメント（https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html）を参照してください。

* **UI** - 応答性が向上した新しい UI レイヤーが導入されました。

## バグ修正 {#bug-fixes}

* [!UICONTROL Cloud Manager] 2018.8.0 では、アクティビティページの期間が分および時間単位で一覧表示されていましたが、その情報はテーブルヘッダーに反映されていませんでした。
* まれに、新規アプリケーションプロジェクトウィザードを起動できないことがありました。
* 新規アプリケーションプロジェクトウィザードダイアログのボタンのラベルがわかりにくくなっていました。
* 状況によっては、アクティビティページで「詳細」ボタンをクリックすると、概要ページにリダイレクトされることがありました。
* 予期しない状況でまれに、概要ページにカードが表示されないことがありました。
* アセットアイコンが、すべての顧客のプログラムリストページに表示されていました。
* バックエンドエラーが発生した場合、パイプラインの実行が検証ステップに残っているように見えることがありました&#x200B;*。*
* ある状況で、プログラム説明の長さが誤って計算されていました。

## 既知の問題 {#known-issues}

* アプリケーションプロジェクトウィザードを使用して作成したブランチにダッシュを含めることができません。
* Adobe [!UICONTROL Experience Cloud] の通知サイドバーでは、通知の読み込みに一貫性がない場合があります。ただし、通知は Adobe [!UICONTROL Experience Cloud] には表示され、設定に応じて電子メールでも送信されます。
