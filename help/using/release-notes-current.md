---
title: リリースノート（2020.3.0）
seo-title: AEM Cloud Manager リリースノート（2020.3.0）
description: このページでは、Cloud Manager リリース 2020.3.0 について説明します。
seo-description: このページでは、AEM Cloud Manager リリース 2020.3.0 について説明します。
translation-type: tm+mt
source-git-commit: 44671d89edad0ccb6ded998b62beb5fa012678e9

---

# リリースノート（2020.3.0） {#release-notes-for}

以下の節では [!UICONTROL Cloud Manager] リリース 2020.3.0 の一般リリースノートの概要を説明します。

## リリース日 {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2020.3.0 is March 05, 2020.

## 最新情報 {#whats-new}

* これで、ビルドステップのログは、ビルドステップの実行中に使用できます。
* パイプライン実行の詳細ページの一部のメッセージが、明確にするために編集されました。

## バグ修正 {#bug-fixes}

* 展開が失敗した場合、展開手順のログが使用できない原因となる展開設定があります。
* マネージドサービスプログラムの展開手順内で特定のエラーが発生すると、以降の実行の開始に失敗する可能性があります。
* ビルド手順で使用されるEphemeral SonarQubeインスタンスが、設定されたタイムアウト内で開始に失敗する場合がありました。
* 特定のプロジェクトでは、 *ResourceResolverオブジェクトを常に閉じる必要があり* 、Null Pointer例外が発生します。ただし、これはパイプラインの実行には影響しませんでした。


