---
title: リリースノート（2021.11.0）
description: このページでは、Cloud Manager リリース 2021.11.0 について説明します。
feature: Release Information
source-git-commit: 099a4490e3a8578b9f3485fd1514d1e97db977ab
workflow-type: ht
source-wordcount: '372'
ht-degree: 100%

---

# リリースノート（2021.11.0） {#release-notes-for}

以下の節では、[!UICONTROL Cloud Manager] リリース 2021.11.0 の一般リリースノートの概要を説明します。

>[!NOTE]
>AEM as a Cloud Service での Cloud Manager の最新のリリースノートについては、[現在のリリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja#getting-access)を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2021.11.0 のリリース日は 2021 年 11 月 04 日（PT）です。次回のリリースは 2021 年 12 月 16 日（PT）に予定されています。

## 新機能 {#whats-new}

* パイプライン実行の詳細に Git Commit ID が表示されるようになり、ビルドされたコードの追跡が容易になりました。

* この `x-request-id` 応答ヘッダーが、[www.adobe.io](https://www.adobe.io/) の API Playground に表示されるようになりました。このヘッダーは、トラブルシューティングのためにカスタマーケアに関する問題を送信する際に役立ちます。

* ユーザーには、パイプラインがゼロのパイプラインカードから適切なガイダンスが提供されます。

* 新しいアクティビティページが使用できるようになりました。このページでは、パイプラインやコード実行などのアクティビティに関連する詳細を表示できます。時間が経つと、このページに表示されるアクティビティの範囲は拡大し、詳細も表示されるようになります。

* カーソルを合わせたときにステータスのポップオーバーが表示され、詳細の概要を簡単に確認できる新しいパイプラインページが追加されました。パイプラインの実行状況が、関連する詳細と共に表示されます。

* パイプラインの編集 API で、Dispatcher の無効化とフラッシュパスの設定がサポートされるようになりました。

* パイプラインの編集 API で、デプロイフェーズで使用する環境の変更がサポートされるようになりました。

* OakPal スキャンプロセスの最適化が、大規模パッケージに導入されました。

* 品質問題の CSV ファイルに、品質問題ごとのタイムスタンプが含まれるようになりました。

* 環境ページの「管理」ボタンは UI に表示されなくなりました。

## バグ修正 {#bug-fixes}

* 正常でないビルド設定があると、パイプラインの Maven アーティファクトキャッシュに不要なファイルが保存され、ビルドコンテナの開始と停止時に不要なネットワーク I/O が発生していました。

* デプロイフェーズが存在しない場合、パイプライン PATCH API は失敗します。

* 共通の基本パスを持つクライアントライブラリがある場合、`ClientlibProxyResourceCheck` 品質ルールで偽陽性の問題が発生していました。

* リポジトリーの最大数に達したエラーメッセージで、エラーの理由が明記されていませんでした。

* まれに、特定の応答コードの不適切な再試行処理が原因でパイプラインが失敗することがありました。
