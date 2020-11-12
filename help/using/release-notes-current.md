---
title: リリースノート（2020.11.0）
seo-title: AEM Cloud Manager リリースノート（2020.11.0）
description: このページでは、Cloud Manager リリース 2020.11.0 について説明します。
seo-description: このページでは、AEM Cloud Manager リリース 2020.11.0 について説明します。
translation-type: tm+mt
source-git-commit: 30d782f5a095b1b07ec4f2039def9ba30a559325
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# リリースノート（2020.11.0） {#release-notes-for}

以下の節では [!UICONTROL Cloud Manager] リリース 2020.11.0 の一般リリースノートの概要を説明します。

## リリース日 {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2020.11.0 is November 12, 2020.

## 新機能 {#whats-new}

* Cloud Managerの「 **Learn** 」タブが更新され、UIの新しい画像が表示されます。

## バグ修正 {#bug-fixes}

* お客様が原因で発生した展開エラーが、展開ログで明示的に見つかるようになりました。

* ビルドの実行前に行われた依存関係の読み込みには、Mavenプラグインのダウンロードが必要です。

* Cloud Managerのフッターから言語を選択するリンクが、正しい場所に移動するようになりました。

* コードのスキャン中に、SonarQubeプロセスが開始しないことがあります。 これは自動検出され、再起動が試行されます。

* パフォーマンステストで使用されるサイトのクロール処理中に、深さトラバーサルの最初の3つのレベルでタイムアウトした要求は、自動的に再試行されます。