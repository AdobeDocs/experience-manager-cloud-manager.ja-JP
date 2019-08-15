---
title: リリースノート（2019.8.0）
seo-title: AEM Cloud Manager リリースノート（2019.8.0）
description: このページでは、Cloud Manager リリース 2019.8.0 について説明します。
seo-description: このページでは、AEM Cloud Manager リリース 2019.8.0 について説明します。
translation-type: tm+mt
source-git-commit: 365cd6dfe65059c0c529f774bbcda946d47b0db5

---

# リリースノート（2019.8.0） {#release-notes-for}

[!UICONTROL Cloud Manager] 2019.8.0リリースでは、選択的なコンテンツパッケージの選択、ビルドパフォーマンスの向上、様々なマイナーバグの修正がサポートされています。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2019.8.0 のリリース日は 2019 年 8 月 19 日です。

## 最新情報 {#whats-new}

* [Adobe I/O CLIを使用して、Cloud Manager APIへの新しいコマンドラインインターフェイス](https://github.com/adobe/aio-cli-plugin-cloudmanager)を追加しました。
* ビルドによって生成される特定のコンテンツパッケージは、skipableとして宣言されているため、デプロイされません。詳しくは、"AEMアプリケーションプロジェクトの作成」の ******[「コンテンツパッケージのスキップ」の節](create-an-application-project.md) を参照してください。
* ビルドコンテナ内のプリロードされた依存関係のセットが、不要なネットワークリクエストを避けるように修正されました。
* 一部の誤った設定プログラムの概要ページのメッセージが改善されました。

## バグ修正 {#bug-fixes}

* SLAレポートにアクセスする場合、デフォルトの年は2018ではなく2018でした。
* 環境名が長い場合、レポート画面の環境セレクターのサイズが正しく増加しませんでした。
* ***configAndInstallshouldOnlyContainsRegionIDodes*** コード品質ルールは、Sling Rewrierコンポーネントが使用されたときに偽陽性を生成しました。
* ***configAndInstallshouldOnlyContainsIdentityIDodes*** コード品質ルールは、稀なパス構造に対して偽陽性を生成しました。
* アセットのみの顧客は、一貫してAEM環境に移動できない可能性があります。
* 分岐 [!UICONTROL とプロジェクト] の作成ダイアログが異なるブラウザーで異なってレンダリングされます。
