---
title: リリースノート（2020.8.0）
seo-title: AEM Cloud Manager リリースノート（2020.8.0）
description: このページでは、Cloud Manager リリース 2020.8.0 について説明します。
seo-description: このページでは、AEM Cloud Manager リリース 2020.8.0 について説明します。
translation-type: tm+mt
source-git-commit: c2f5caf50f2e20c07807369aee7914c17fded4de
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 87%

---

# リリースノート（2020.8.0） {#release-notes-for}

以下の節では [!UICONTROL Cloud Manager] リリース 2020.8.0 の一般リリースノートの概要を説明します。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2020.8.0 のリリース日は 2020 年 8 月 06 日です。

## 新機能 {#whats-new}

認証バウンドのプライベート Maven リポジトリがサポートされるようになりました。

## バグ修正 {#bug-fixes}

* 不要で望ましくない一部の SonarQube プラグインが、コード品質スキャンの一部として実行されていました。

* パイプラインの実行ページで、ブランチ名の形式が正しくありませんでした。

* 単一のパブリッシュ、単一の Dispatcher とコールドスタンバイの作成者を含むトポロジにデプロイすると、Dispatcher が誤ってロードバランサーから削除されていました。

* 一部のケースで、パイプラインの実行完了が正常に記録されなかったため、パイプラインが新たに実行されないことがありました。

* 内部通信の問題が原因で、パイプラインの実行が&#x200B;*停止*&#x200B;することがあります。

* プログラムカードのツールチップの一貫性が適切に保てていませんでした。

* There was a color mismatch on the **Overview** page.

* サイトパフォーマンステストで、認証のオプション使用がサポートされるようになりました。

* 作成者インスタンスのディスパッチャーキャッシュは、Cloud Managerを使用してディスパッチャー設定がデプロイされると、自動的にフラッシュされます。

