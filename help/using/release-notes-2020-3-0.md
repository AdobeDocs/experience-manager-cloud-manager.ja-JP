---
title: リリースノート（2020.3.0）
seo-title: AEM Cloud Manager リリースノート（2020.3.0）
description: このページでは、Cloud Manager リリース 2020.3.0 について説明します。
seo-description: このページでは、AEM Cloud Manager リリース 2020.3.0 について説明します。
translation-type: tm+mt
source-git-commit: e7da473a22bec1d3d9b3d39bf654af0c596fe86d

---

# リリースノート（2020.3.0） {#release-notes-for}

以下の節では [!UICONTROL Cloud Manager] リリース 2020.3.0 の一般リリースノートの概要を説明します。

## リリース日 {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2020.3.0 is March 05, 2020.

## 最新情報 {#whats-new}

* ビルドステップのログを、ビルドステップの実行中に使用できるようになりました。
* パイプライン実行の詳細ページの一部のメッセージを編集し、わかりやすくしました。

## バグ修正 {#bug-fixes}

* デプロイメントが失敗した場合、特定のデプロイメント設定でデプロイ手順を記録できなくなることがありました。
* Managed Services プログラムのデプロイメント手順内で特定のエラーが発生すると、以降の実行が開始に失敗する可能性がありました。
* ビルド手順で使用されるエフィメラル SonarQube インスタンスが、設定されたタイムアウト内での開始に失敗する場合がありました。
* 特定のプロジェクトでは、*ResourceResolver オブジェクトを常に閉じる必要があり*、Null Pointer 例外が発生していましたが、パイプラインの実行には影響しませんでした。