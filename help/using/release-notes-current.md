---
title: リリースノート（2019.12.0）
seo-title: AEM Cloud Manager リリースノート（2019.12.0）
description: このページでは、Cloud Manager リリース 2019.12.0 について説明します。
seo-description: このページでは、AEM Cloud Manager リリース 2019.12.0 について説明します。
translation-type: tm+mt
source-git-commit: 1f31e654272afa60cac3376ce4dc3bc76f0d9dda

---

# リリースノート（2019.12.0） {#release-notes-for}

The following section outlines the general Release Notes for [!UICONTROL Cloud Manager] Release 2019.12.0 and adds updates to pipeline execution and enhancements to code quality scans.
詳しくは、以下の節を参照してください。

## リリース日 {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2019.12.0 is December 12, 2019.

## 最新情報 {#whats-new}

* 現在は、パイプライン実行のステップに、各ステップの完了タイムスタンプが表示されます。
* Javaコードを含まないプロジェクトのコード品質スキャンで、コードカバレッジ率100%がレポートされるようになりました。
* CQディスパッチャー設定のヘルスチェックが削除されました。


## バグ修正 {#bug-fixes}

* 一部のブラウザーで日付が正しく表示されない問題を修正しました。
* まれに、パフォーマンステストが実行中の間に、実稼働パイプラインが承認ステップに移動することがあります。
* 特定の状態で、概要ページの上部のボタンが正しく配置されない問題を修正しました。
* 特定の状況では、権限のないユーザーが、ボタン自体をクリックできない状態で、パイプラインを開始するボタンを表示していました。
* 非実稼働パイプラインのアクションボタンが、間違った場所に表示されることがあります。
* granite:Rankingノードタイプを持つパッケージで、特定の品質ルール違反をスキャンできませんでした。
* コード品質プロセスで発生した一部のエラーは、誤ってバグとしてカウントされました。
* 特定のトポロジに対して監視データを読み込めませんでした。
