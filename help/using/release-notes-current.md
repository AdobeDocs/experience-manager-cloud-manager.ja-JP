---
title: リリースノート（2020.10.0）
seo-title: AEM Cloud Manager リリースノート（2020.10.0）
description: このページでは、Cloud Manager リリース 2020.10.0 について説明します。
seo-description: このページでは、AEM Cloud Manager リリース 2020.10.0 について説明します。
translation-type: tm+mt
source-git-commit: aad2da58e5934999884553619dd97d42cc725d88
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 54%

---

# リリースノート（2020.10.0） {#release-notes-for}

以下の節では [!UICONTROL Cloud Manager] リリース 2020.10.0 の一般リリースノートの概要を説明します。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2020.10.0 のリリース日は 2020 年 01 月 10 日です。

## バグ修正 {#bug-fixes}

* パフォーマンステストに使用されるクローラーで、特定のリソースタイプが有効なWebリンクとして誤って考慮されていました。

* 場合によっては、パフォーマンステストの完了手順が正しく処理されず、長時間の手順が実行されることがありました。

* 実稼働環境でのデプロイメント用にディスパッチャーキャッシュの無効化が設定されている場合、無効化が2回実行されることがありました。