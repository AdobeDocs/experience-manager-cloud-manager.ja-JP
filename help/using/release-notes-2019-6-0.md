---
title: リリースノート（2019.6.0）
seo-title: AEM Cloud Manager リリースノート（2019.6.0）
description: このページでは、Cloud Manager リリース 2019.6.0 について説明します。
seo-description: このページでは、AEM Cloud Manager リリース 2019.6.0 について説明します。
feature: リリース情報
exl-id: 5a87f191-8203-4cb9-a810-247aece41605
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 100%

---

# リリースノート（2019.6.0） {#release-notes-for}

[!UICONTROL Cloud Manager] 2019.6.0 リリースには、新しいコード品質ルールと新しい製品アップデートウィザードが追加されました。詳しくは、以下の節を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2019.6.0 のリリース日は 2019 年 6 月 20 日（PT）です。

## 新機能 {#whats-new}

* AEM アップデートを正常に実行できるように支援する新しい製品アップデートウィザード。詳しくは、[製品アップデートウィザード](overview-productupdate-wizard.md)を参照してください。
* コンテンツ構造を調べるコード品質ルール。詳しくは、[カスタムコード品質ルール](custom-code-quality-rules.md)を参照してください。
* Git プッシュの最大サイズが 1 GB に増加しました。

## バグ修正 {#bug-fixes}

* 以前のエラーが原因でパイプラインを開始できない場合がありました。

## 既知の問題 {#known-issues}

* コード品質の CSV ダウンロードが重大度に従って並べ替えられないことがあります。
* *config* フォルダーの下にネストしたフォルダーに OSGi 設定がある場合は、*ConfigAndInstallShouldOnlyContainOsgiNodes* ルールに従って偽陽性が報告されることがあります。
