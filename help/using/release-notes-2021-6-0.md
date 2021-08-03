---
title: リリースノート（2021.6.0）
description: このページでは、Cloud Manager リリース 2021.6.0 について説明します。
feature: リリース情報
source-git-commit: ee701dd2d0c3921455a0960cbb6ca9a3ec4793e7
workflow-type: ht
source-wordcount: '314'
ht-degree: 100%

---

# リリースノート（2021.6.0） {#release-notes-for}

以下の節では、[!UICONTROL Cloud Manager] リリース 2021.6.0 の一般リリースノートの概要を説明します。

>[!NOTE]
>AEM as a Cloud Service での Cloud Manager の最新のリリースノートについては、[現在のリリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja#getting-access)を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2021.6.0 のリリース日は 2021 年 6 月 10 日（PT）です。次回のリリースは 2021 年 6 月 15 日（PT）に予定されています。

## 新機能 {#whats-new}

* （該当する場合）Assets と Sites のテストが並行して実行されるようになり、パイプラインの合計実行時間が短縮されます。この機能は、今後数週間にわたり、お客様に対して有効になる予定です。

* ビルド手順中にダウンロードされた Maven の依存関係は、パイプライン実行から次回の実行までの間にキャッシュされるようになりました。この機能は、今後数週間にわたり、お客様に対して有効になる予定です。

* プロジェクトの作成時に使用されるデフォルトのブランチ名と、Git 管理ワークフロー経由のデフォルトのプッシュコマンドで使用されるデフォルトのブランチ名が `main` に変更されました。

* UI でのプログラムの編集エクスペリエンスが更新されました。詳しくは、[プログラムの編集](/help/using/setting-up-program.md#editing-program)を参照してください。

* 品質ルール `ImmutableMutableMixCheck` が更新され、`/oak:index` ノードが不変として分類されるようになりました。

* 品質ルール `CQBP-84` と `CQBP-84--dependencies` は、1 つのルールに統合されました。この統合の一環として、AEM ランタイムにデプロイされるサードパーティの依存関係の問題を、依存関係のスキャンでより正確に特定できます。

* 状況によっては、「スキップされたテスト」指標の計算に失敗すると、パイプライン実行が失敗することがあります。

## バグ修正 {#bug-fixes}

* ルート要素名の後に改行を含む JCR ノード定義が正しく解析されなかった問題を修正しました。

* リストリポジトリー API は、削除されたリポジトリーをフィルタリングしません。

* スケジュール手順に無効な値が指定された場合、誤ったエラーメッセージが表示されていました。

* パイプライン実行が実稼動ステップへのデプロイに到達し、ユーザーが実行を停止すると、UI のデプロイステータスメッセージに、実際に何が起きているかが正しく反映されないことがありました。
