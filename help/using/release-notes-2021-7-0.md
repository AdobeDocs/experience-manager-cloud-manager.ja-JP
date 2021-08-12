---
title: リリースノート（2021.7.0）
description: このページでは、Cloud Manager リリース 2021.7.0 について説明します。
feature: リリース情報
source-git-commit: e490a8f1dd17e63f35ed00d4cdf95b6e7a07b150
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 100%

---

# リリースノート（2021.7.0） {#release-notes-for}

以下の節では、[!UICONTROL Cloud Manager] リリース 2021.7.0 の一般リリースノートの概要を説明します。

>[!NOTE]
>AEM as a Cloud Service での Cloud Manager の最新のリリースノートについては、[現在のリリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja#getting-access)を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2021.7.0 のリリース日は 2021 年 7 月 15 日（PT）です。次回のリリースは 2021 年 8 月 12 日（PT）に予定されています。

## 新機能 {#whats-new}

* お客様は、Cloud Manager のビルドプロセスに Azul 8 および 11 JDK を使用できるようになりました。ツールチェーン対応の Maven プラグイン&#x200B;*または* Maven プロセスの実行全体に対して、これらの JDK のいずれかを使用するように選択できます。

* 送信エグレス IP がビルドステップログファイルに記録されるようになりました。

* 「**Git を管理**」ボタンのタイトルが「**Git 情報にアクセス**」に変更され、ダイアログが視覚的に更新されました。

* Cloud Manager で使用される AEM プロジェクトアーキタイプのバージョンが 28 に更新されました。

* 予期しないトポロジ再設定の結果、詳細なテストレポートがパイプライン実行の詳細ページから使用できなくなる場合がありました。

## バグ修正 {#bug-fixes}

* 存在しない実行の実行詳細ページに手動で移動しても、エラーが表示されず、読み込みが無限に繰り返される画面が表示されるだけでした。

* 場合によっては、Sites のパフォーマンスで使用されたコンテナが失敗しても自動再試行が 2 時間にわたって有効にならず、最終的にテストが失敗することがありました。

## 既知の問題 {#known-issues}

Azul JDK の使用に切り替えるお客様は、すべての既存アプリケーションが Azul JDK でエラーなしにコンパイルされるとは限らないことに注意してください。切り替える前に、ローカルでテストすることを強くお勧めします。