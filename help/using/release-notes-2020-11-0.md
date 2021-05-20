---
title: リリースノート（2020.11.0）
seo-title: AEM Cloud Manager リリースノート（2020.11.0）
description: このページでは、Cloud Manager リリース 2020.11.0 について説明します。
seo-description: このページでは、AEM Cloud Manager リリース 2020.11.0 について説明します。
feature: リリース情報
exl-id: c283c55d-156f-4540-9353-e6337d185842
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 100%

---

# リリースノート（2020.11.0）{#release-notes-for}

以下の節では、[!UICONTROL Cloud Manager] リリース 2020.11.0 の一般リリースノートの概要を説明します。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2020.11.0 のリリース日は 2020 年 11 月 13 日です。

## 新機能 {#whats-new}

* Cloud Manager の「**学習**」タブが更新され、UI に新しい画像が追加されました。

## バグ修正 {#bug-fixes}

* お客様に起因する特定のデプロイメントエラーが、デプロイメントログで明示的に表記されるようになりました。

* ビルドの実行に先立っておこなわれる依存関係の読み込みには、Maven プラグインのダウンロードが必要でした。

* 言語を選択するための Cloud Manager フッターからのリンクが、正しい場所を指すようになりました。

* コードスキャン時に SonarQube プロセスが起動しないことがあります。これが自動検出され、再起動が試行されるようになりました。

* パフォーマンステストで使用されるサイトクロール処理の際、最初の 3 レベルの深度トラバーサルでタイムアウトしたリクエストは、自動的に再試行されます。
