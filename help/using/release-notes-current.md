---
title: リリースノート（2021.10.0）
description: このページでは、Cloud Manager リリース 2021.10.0 について説明します。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: b28f8f1bedb92428d332716510cbf0fd714fada6
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 20%

---

# リリースノート（2021.10.0） {#release-notes-for}

以下の節では、[!UICONTROL Cloud Manager] リリース 2021.10.0 の一般リリースノートの概要を説明します。

>[!NOTE]
>AEM as a Cloud Service での Cloud Manager の最新のリリースノートについては、[現在のリリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja#getting-access)を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2021.10.0 のリリース日は 2021 年 14 月 10 日（PT）です。次回のリリースは 2021 年 11 月 4 日に予定されています。

## 新機能 {#whats-new}

* 実稼動パイプラインを「緊急」モードで実行できるようになりました。このモードでは、緊急デプロイメントのセキュリティとパフォーマンステストの手順を回避できます。

* Cloud Serviceとの一貫性を保つために、既存のデプロイメントパイプラインが参照され、UI で「フルスタック」パイプラインとしてラベル付けされるようになりました。

* パイプラインカードが更新され、実稼動パイプラインと非実稼動パイプラインの両方を表示する単一の統合面が表示され、各パイプラインに関連付けられたアクションメニューから直接「実行/一時停止/再開」を選択できます。

* デプロイメントマネージャーの役割を持つユーザーが、UI を使用して、セルフサービス方式で実稼動パイプラインを削除できるようになりました。

* パイプラインエクスペリエンスの追加と編集が更新され、使い慣れた最新のモデルを使用できるようになりました。

* Cloud Manager のユーザーは、ランディングページの右上にある **フィードバック** ボタンを使用して、UI から直接フィードバックを送信できるようになりました。

* 年別の SLA グラフを Cloud Manager ユーザーインターフェイスからダウンロードできるようになりました。

* コード品質と非実稼動パイプラインの実行で、ビルド手順中により効率的な浅いクローン作成プロセスを使用できるようになり、特に大きな Git リポジトリを持つお客様のビルド時間が短縮されます。

* Cloud Manager API ドキュメントに、ログインしたユーザーがブラウザーで API を試すことができる、インタラクティブなプレイグラウンドが含まれるようになりました。 詳しくは、[Cloud Manager API のプレイグラウンド ](https://www.adobe.io/experience-cloud/cloud-manager/reference/playground/) を参照してください。

* 「移動先」の選択オプションが無効になっている場合は、プログラムカードのツールチップがわかりやすくなります。 「実稼動環境は存在しません」と表示されるようになります。


## バグ修正 {#bug-fixes}

* 内部システムから読み取ったデータが正しく入力されなかった場合、CSE から提供された関連のないデータが Cloud Manager に正しく反映されない可能性があります。

* 特定のお客様の状況で、ビルド手順中にダウンロードされた無効なアーティファクト（ビルドエラーの原因となっていたはず）が無視されていました。
