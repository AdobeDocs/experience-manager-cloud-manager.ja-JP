---
title: リリースノート（2020.8.0）
seo-title: AEM Cloud Manager リリースノート（2020.8.0）
description: このページでは、Cloud Manager リリース 2020.8.0 について説明します。
seo-description: このページでは、AEM Cloud Manager リリース 2020.8.0 について説明します。
translation-type: tm+mt
source-git-commit: cff6f23a674fda2f57ea481d89644de9be3f5722
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 35%

---

# リリースノート（2020.8.0） {#release-notes-for}

以下の節では [!UICONTROL Cloud Manager] リリース 2020.8.0 の一般リリースノートの概要を説明します。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2020.8.0 のリリース日は 2020 年 8 月 06 日です。

## 新機能 {#whats-new}

認証バウンドのプライベートMavenリポジトリがサポートされるようになりました。

## バグ修正 {#bug-fixes}

* 不要で望ましくない一部のSonarQubeプラグインが、コード品質スキャンの一部として実行されていました。

* パイプラインの実行ページで、ブランチ名の形式が正しくありませんでした。

* 単一の発行、単一のディスパッチャーとコールドスタンバイの作成者を含むトポロジにデプロイすると、ディスパッチャーが誤ってロードバランサーから削除されていました。

* 完了したパイプライン実行が正常に完了したと記録されなかったため、パイプラインの新しい実行が行われない場合がありました。

* 内部通信の問題が原因で、パイプライン実行が *停止することがある* 。

* プログラムカードのツールチップが、一貫して正しくなかった。

* 概要ページで色が一致していません。

