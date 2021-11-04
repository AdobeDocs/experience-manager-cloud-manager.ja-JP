---
title: リリースノート（2021.11.0）
description: このページでは、Cloud Manager リリース 2021.11.0 について説明します。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: e6e5a17c16c42e0b0ed5aedd2f9a6360fd81d8cd
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 19%

---

# リリースノート（2021.10.0） {#release-notes-for}

以下の節では、[!UICONTROL Cloud Manager] リリース 2021.11.0 の一般リリースノートの概要を説明します。

>[!NOTE]
>AEM as a Cloud Service での Cloud Manager の最新のリリースノートについては、[現在のリリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja#getting-access)を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2021.11.0 のリリース日は 2021 年 11 月 04 日（PT）です。次回のリリースは 2021 年 12 月 09 日に予定されています。

## 新機能 {#whats-new}

* Git コミット ID がパイプライン実行の詳細に表示され、作成されたコードの追跡が容易になります。

* この `x-request-id` 応答ヘッダーが、API Playground の [www.adobe.io](https://www.adobe.io/). このヘッダーは、トラブルシューティングのためにカスタマーケアの問題を送信する際に役立ちます。

* ユーザーとして、パイプラインがゼロのパイプラインカードから適切なガイダンスが提供されるのを確認します。

* 新しいアクティビティページが使用できるようになりました。このページでは、パイプラインやコード実行などのアクティビティに関連する詳細を表示できます。 時間が経つと、このページに示すアクティビティの範囲は、提供された詳細と共に拡大します。

* 詳細の概要を簡単に表示できる新しいパイプラインページと、オンホバー時のステータスポップオーバーが追加されました。 パイプラインの実行に関連する詳細と共に表示できます。

* パイプラインの編集 API で、Dispatcher の無効化とフラッシュパスの設定がサポートされるようになりました。

* パイプラインの編集 API で、デプロイフェーズで使用する環境の変更がサポートされるようになりました。

* OakPal スキャンプロセスの最適化が、大きなパッケージに導入されました。

* 品質の問題の CSV ファイルに、各品質の問題のタイムスタンプが含まれるようになりました。

* 環境ページの「管理」ボタンは、UI に表示されなくなります。

## バグ修正 {#bug-fixes}

* 正常でないビルド設定があると、パイプラインの Maven アーティファクトキャッシュに不要なファイルが保存され、ビルドコンテナの開始と停止時に不要なネットワーク I/O が発生していました。

* デプロイフェーズが存在しない場合、パイプラインPATCHAPI は失敗します。

* この `ClientlibProxyResourceCheck` 共通のベースパスを持つクライアントライブラリがある場合、品質ルールで偽陽性の問題が発生していました。

* 最大数に達したリポジトリの場合のエラーメッセージで、エラーの理由が指定されていませんでした。

* まれに、特定の応答コードの不適切な再試行処理が原因でパイプラインが失敗することがありました。
