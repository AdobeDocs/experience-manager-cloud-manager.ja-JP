---
title: リリースノート（2019.7.0）
seo-title: AEM Cloud Manager リリースノート（2019.7.0）
description: このページでは、Cloud Manager リリース 2019.7.0 について説明します。
seo-description: このページでは、AEM Cloud Manager リリース 2019.7.0 について説明します。
translation-type: tm+mt
source-git-commit: 7cfa0cf66efd5891263bfcc83a5149daec5c8b67

---

# リリースノート（2019.7.0） {#release-notes-for}

[!UICONTROL Cloud Manager] 2019.7.0リリースには、新しいコード品質ルールと新しい製品アップデートウィザードが追加されています。詳しくは、以下の節を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2019.7.0 のリリース日は 2019 年 7 月 18 日です。

## 最新情報 {#whats-new}

本番用デプロイメントの開始時にExperience Cloud通知が送信されるようになりました。

## バグ修正 {#bug-fixes}

* 場合によっては、Cloud Managerは、PythonおよびPHPファイルに対して静的コード分析を実行します。
* FileVault InstallHooksを含むパッケージが、コード品質手順で一貫して実行されませんでした。
* 一部の組み合わせでは、コード品質の問題が一貫して並べ替えられませんでした。
* パイプライン実行ページでいくつかの視覚的問題が発生していました。
* パフォーマンステストステップは、基になるクラウドインフラストラクチャからリソース制約によってランダムに失敗することがあります。
* ネットワークの問題によって、特定の顧客ビルドが失敗することがあります。