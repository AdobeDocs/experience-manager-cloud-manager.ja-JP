---
title: リリースノート（2019.6.0）
seo-title: AEM Cloud Manager リリースノート（2019.6.0）
description: このページでは、Cloud Manager リリース 2019.6.0 について説明します。
seo-description: このページでは、AEM Cloud Manager リリース 2019.6.0 について説明します。
translation-type: tm+mt
source-git-commit: 7cfa0cf66efd5891263bfcc83a5149daec5c8b67

---

# リリースノート（2019.6.0） {#release-notes-for}

[!UICONTROL Cloud Manager] 2019.6.0リリースには、新しいコード品質ルールと新しい製品アップデートウィザードが追加されています。詳しくは、以下の節を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン2019.6.0のリリース日は、2019年6月21日です。

## 最新情報 {#whats-new}

* AEMアップデートを正常に実行できるようにするための新しい製品アップデートウィザード。Refer to [Product Update Wizard](overview-productupdate-wizard.md) to learn more.
* コンテンツ構造を調べるコード品質ルール。Refer to [Custom Code Quality Rules](custom-code-quality-rules.md) for more information.
* gitプッシュの最大サイズが1GBに増加しました。

## バグ修正 {#bug-fixes}

* 場合によっては、以前のエラーが原因でパイプラインを開始できないことがありました。

## 既知の問題 {#known-issues}

* コード品質のCSVダウンロードは、重大度に従って並べ替えられるとは限りません。
* False positives may be reported by the *ConfigAndInstallShouldOnlyContainOsgiNodes* rule if OSGi configurations are placed in a nested folder under a *config* folder.