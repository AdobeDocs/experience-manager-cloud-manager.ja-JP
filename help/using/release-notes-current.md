---
title: リリースノート（2019.6.0）
seo-title: AEM Cloud Manager リリースノート（2019.6.0）
description: このページでは、Cloud Manager リリース 2019.6.0 について説明します。
seo-description: このページでは、AEM Cloud Manager リリース 2019.6.0 について説明します。
translation-type: tm+mt
source-git-commit: 75563d3f4b2a27d943c052993c97d830338ead9c

---

# リリースノート（2019.6.0） {#release-notes-for}

[!UICONTROL Cloud Manager] 2019.6.0 リリースには、重要な機能変更は含まれていません。詳細は、以下の節を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン2019.6.0のリリース日です。

## 最新情報 {#whats-new}

* AEMアップデートを正常に実行できるようにするための新しい製品アップデートウィザード。（製品アップデートウィザードページへのリンク）
* コンテンツ構造を調べるコード品質ルール。（カスタムコード品質ルールページへのリンク）
* gitプッシュの最大サイズが1GBに増加しました。

## バグ修正 {#bug-fixes}

* 場合によっては、以前のエラーが原因でパイプラインを開始できないことがありました。

## 既知の問題 {#known-issues}

* コード品質のCSVダウンロードは、重大度に従って並べ替えられるとは限りません。
* OSGi設定がconfigフォルダーの下のネストフォルダーに配置されている場合、False陽性はconfigAndInstallshouldOnlyContainsIdentityodesルールによってレポートされることがあります。
