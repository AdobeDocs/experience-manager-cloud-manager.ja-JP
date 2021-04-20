---
title: リリースノート（2020.3.0）
seo-title: AEM Cloud Manager リリースノート（2020.3.0）
description: このページでは、Cloud Manager リリース 2020.3.0 について説明します。
seo-description: このページでは、AEM Cloud Manager リリース 2020.3.0 について説明します。
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 100%

---

# リリースノート（2020.3.0） {#release-notes-for}

以下の節では [!UICONTROL Cloud Manager] リリース 2020.3.0 の一般リリースノートの概要を説明します。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2020.3.0 のリリース日は 2020 年 3 月 05 日です。

## 最新情報 {#whats-new}

* ビルドステップのログを、ビルドステップの実行中に使用できるようになりました。
* パイプライン実行の詳細ページの一部のメッセージを編集し、わかりやすくしました。

## バグ修正 {#bug-fixes}

* デプロイメントが失敗した場合、特定のデプロイメント設定でデプロイ手順を記録できなくなることがありました。
* Managed Services プログラムのデプロイメント手順内で特定のエラーが発生すると、以降の実行が開始に失敗する可能性がありました。
* ビルド手順で使用されるエフィメラル SonarQube インスタンスが、設定されたタイムアウト内での開始に失敗する場合がありました。
* 特定のプロジェクトでは、*ResourceResolver オブジェクトを常に閉じる必要があり*、Null Pointer 例外が発生していましたが、パイプラインの実行には影響しませんでした。