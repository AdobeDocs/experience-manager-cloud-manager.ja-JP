---
title: リリースノート（2019.8.0）
seo-title: AEM Cloud Manager リリースノート（2019.8.0）
description: このページでは、Cloud Manager リリース 2019.8.0 について説明します。
seo-description: このページでは、AEM Cloud Manager リリース 2019.8.0 について説明します。
translation-type: tm+mt
source-git-commit: 548d18f251cf8c4c827d2208fec04cde235ce731

---

# リリースノート（2019.8.0） {#release-notes-for}

[!UICONTROL Cloud Manager] 2019.8.0 リリースでは、選択的にビルドされたコンテンツパッケージのサポートが追加され、ビルドのパフォーマンスが向上し、様々なマイナーなバグが修正されています。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2019.8.0 のリリース日は 2019 年 8 月 19 日です。

## 最新情報 {#whats-new}

* [Adobe I/O CLI](https://github.com/adobe/aio-cli-plugin-cloudmanager) による、Cloud Manager API に対する新しいコマンドラインインターフェイス。
* ビルドによって作成された特定のコンテンツパッケージがスキップ可能として宣言され、デプロイされなくなることがあります。詳しくは、[AEM アプリケーションプロジェクトの作成](create-an-application-project.md)の&#x200B;***コンテンツパッケージのスキップ***&#x200B;の節を参照してください。
* ビルドコンテナのプリロードされた依存関係のセットは、一部の不要なネットワーク要求を避けるように修正されています。
* 間違って設定された特定のプログラムの概要ページのメッセージが改善されました。

## バグ修正 {#bug-fixes}

* SLA レポートにアクセスする場合、デフォルトの年が 2019 ではなく、2018 になっていました。
* 長い環境名の場合、レポート画面の環境セレクターのサイズが適切に増加していませんでした。
* Sling Rewriter コンポーネントが使用されると、***ConfigAndInstallShouldOnlyContainOsgiNodes*** コード品質ルールが偽陽性を生成していました。
* 特定の一般的でないパス構造で、***ConfigAndInstallShouldOnlyContainOsgiNodes*** コード品質ルールが偽陽性を生成していました。
* アセットのみのお客様の場合、AEM 環境に一貫性のあるナビゲートができないことがありました。
* [!UICONTROL ブランチおよびプロジェクトを作成]ダイアログが異なるブラウザーで異なってレンダリングされていました。
