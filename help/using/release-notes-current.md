---
title: リリースノート（2021.6.0）
description: このページでは、Cloud Manager リリース 2021.6.0 について説明します。
feature: リリース情報
source-git-commit: 5111a918b8063ab576ef587dc3c8d66ad976fc1a
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 27%

---

# リリースノート（2021.6.0） {#release-notes-for}

以下の節では、[!UICONTROL Cloud Manager] リリース 2021.6.0 の一般リリースノートの概要を説明します。

>[!NOTE]
>AEM as a Cloud Service での Cloud Manager の最新のリリースノートについては、[現在のリリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja#getting-access)を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2021.6.0 のリリース日は 2021 年 6 月 10 日（PT）です。次回のリリースは2021年7月16日に予定されています。

## 新機能 {#whats-new}

* アセットとSitesのテストが（該当する場合）並行して実行されるようになり、パイプラインの合計実行時間が短縮されます。 この機能は、今後数週間のお客様に対して有効になる予定です。

* ビルド手順中にダウンロードされたMavenの依存関係は、パイプライン実行の間でキャッシュされるようになりました。 この機能は、今後数週間のお客様に対して有効になる予定です。

* プロジェクトの作成時と、Gitワークフローを管理するデフォルトのプッシュコマンドで使用されるデフォルトのブランチ名が`main`に変更されました。

* UIでのプログラムの編集エクスペリエンスが更新されました。

* 品質ルール`ImmutableMutableMixCheck`が更新され、`/oak:index`ノードが不変として分類されるようになりました。

* 品質ルール`CQBP-84`と`CQBP-84--dependencies`は、1つのルールに統合されました。

* 状況によっては、「スキップされたテスト」指標の計算に失敗すると、パイプライン実行が失敗することがあります。

## バグ修正 {#bug-fixes}

* ルート要素名の後に改行を含むJCRノード定義が正しく解析されなかった問題を修正しました。

* リストリポジトリAPIは、削除されたリポジトリをフィルタリングしません。

* スケジュール手順に無効な値が指定された場合、誤ったエラーメッセージが表示されていました。

* パイプラインの実行が実稼動ステップへのデプロイに達し、ユーザーが実行を停止した場合、UIのデプロイステータスメッセージに実際に何が起きているかが正しく反映されないことがありました。
