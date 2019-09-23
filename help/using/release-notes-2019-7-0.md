---
title: リリースノート（2019.7.0）
seo-title: AEM Cloud Manager リリースノート（2019.7.0）
description: このページでは、Cloud Manager リリース 2019.7.0 について説明します。
seo-description: このページでは、AEM Cloud Manager リリース 2019.7.0 について説明します。
translation-type: tm+mt
source-git-commit: 365cd6dfe65059c0c529f774bbcda946d47b0db5

---

# リリースノート（2019.7.0） {#release-notes-for}

[!UICONTROL Cloud Manager] 2019.7.0 リリースでは、Experience Cloud の通知機能が更新されたほか、バグ修正として機能改善がおこなわれました。詳しくは、以下の節を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2019.7.0 のリリース日は 2019 年 7 月 18 日です。

## 最新情報 {#whats-new}

実稼動デプロイメントの開始時に Experience Cloud 通知が送信されるようになりました。

## バグ修正 {#bug-fixes}

* Cloud Manager が Python および PHP ファイルに対して静的コード分析を実行する場合がありました。
* FileVault の InstallHook を含んだパッケージが、コード品質ステップで正常に実行されていませんでした。
* 一部の組み合わせでは、コード品質の問題が正常に並べ替えられていませんでした。
* パイプライン実行ページで表示上の問題がいくつか発生していました。
* ベースとなるクラウドインフラストラクチャのリソース上の制約により、パフォーマンステストステップがランダムに失敗することがありました。
* ネットワーク上の問題により、特定の顧客ビルドが失敗することがありました。