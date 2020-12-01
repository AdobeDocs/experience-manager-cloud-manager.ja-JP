---
title: リリースノート（2019.2.0）
seo-title: AEM Cloud Manager リリースノート（2019.2.0）
description: このページでは、Cloud Manager リリース 2019.2.0 について説明します。
seo-description: このページでは、AEM Cloud Manager リリース 2019.2.0 について説明します。
translation-type: tm+mt
source-git-commit: 98395c4413b1b6bfbb3a565388ffa32dc3880dff
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 96%

---


# リリースノート（2019.2.0） {#release-notes-for}

[!UICONTROL Cloud Manager] 2019.2.0 リリースには、新しいシステム監視機能が追加されています。これにより、Adobe Managed Services 環境の状態をシステムレベルで表示できます。


## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2019.2.0 のリリース日は 2019 年 2 月 21 日です。

## 最新情報 {#whats-new}

* 新しいシステム監視機能が導入されました。詳しくは、[環境の監視](monitor-your-environments.md)を参照してください。
* ウィザードで生成されたプロジェクトのディスパッチャーモジュールに README ファイルが含まれるようになりました。
* コードスキャンの問題の順序が改善され、問題の優先順位と一致するようになりました。
* デプロイメントの失敗時でも、ステージングインスタンスがロードバランサーに常に復元されるようになりました。
* Admin Console で新しい「API デベロッパー」ロールが利用可能になりました。これを使用すると、Adobe I/O コンソールで統合を作成する権限を特定のユーザーに付与できます。詳しくは、[開発者の管理](https://www.adobe.com/go/aac_api_prod_learn)を参照してください。
* Maven アーキタイプのバージョンがバージョン 16 に更新されました。
* Maven のバージョンがバージョン 3.6.0 に更新されました。

## バグ修正 {#bug-fixes}

* 状況によっては、ターゲット環境が Azure にホストされていると、パイプラインが実行されないことがありました。
* 環境の順序が一貫していませんでした。
* 検出されたページパスにカンマ文字が含まれている場合、パフォーマンステストが失敗することがありました。
* Web UI からパイプラインの実行が開始された場合、ブラウザーの戻るボタンが正しく機能しませんでした。
* 概要ページの「詳細情報」リンクをクリックしても、新しいタブが開きませんでした。
* プログラムサムネールをアップロードしても、すぐには表示されないことがありました。
* 場合によっては、プロジェクト固有の設定のためにコードスキャンが失敗することがありました。
* 非実稼動パイプラインカードの「詳細情報」リンクが間違った場所を指していました。
* 品質ゲートが上書きされると、ステータスの表示に矛盾が生じていました。
* 顧客がコールドスタンバイトポロジを使用すると、間違ったセキュリティテスト結果が送られていました。
* ウィザードを使用して新規プロジェクトを作成する場合、ダッシュ文字を含んだブランチを作成できませんでした。

## 既知の問題 {#known-issues}

* 監視データが更新されると、非表示の系列が非表示ではなくなります。
* 次期リリースまでは、既存の SLA レポートを表示するには手動で移動する必要があります。

   この URL を作成するには、`https://<Experience Cloud URL>/content/mac/<Experience Cloud Tenant>/managedservices/sla.html` というパターンに従います。例えば、お使いの Experience Cloud の URL が `https://weretailprod.experiencecloud.adobe.com` の場合、SLA レポートの URL は `https://weretailprod.experiencecloud.adobe.com/content/mac/weretailprod/managedservices/sla/html` になります。

   次期リリースでは [!UICONTROL Cloud Manager] 内で SLA レポートを使用できるようになるので、この問題は解決される見込みです。
