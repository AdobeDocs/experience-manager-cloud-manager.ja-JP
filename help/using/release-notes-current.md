---
title: リリースノート（2021.5.0）
description: このページでは、Cloud Manager リリース 2021.5.0 について説明します。
feature: リリース情報
source-git-commit: 83fcc49c7e3e3742930a7179b27f899bff3c4ae1
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 18%

---

# リリースノート（2021.5.0） {#release-notes-for}

以下の節では、[!UICONTROL Cloud Manager] リリース 2021.5.0 の一般リリースノートの概要を説明します。

>[!NOTE]
>AEMのCloud Managerの最新のリリースノートをCloud Serviceとして表示するには、[現在のリリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access)を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2021.5.0 のリリース日は 2021 年 5 月 06 日です。次回のリリースは2021年6月3日に予定されています。

## 新機能 {#whats-new}

* PackageOverlaps品質ルールは、同じパッケージが複数回（同じ展開済みパッケージセット内の複数の埋め込み場所など）展開された場合を検出するようになりました。

* Public APIのリポジトリエンドポイントにGit URLが含まれるようになりました。

* プログラムの編集ワークフローでは、ユーザーは10進数以外のKPI値の設定のみが許可されます。

* コードをAdobeGitにプッシュ中に発生した断続的なエラーが解決されました。

* プログラムの編集エクスペリエンスが更新されました。

## バグ修正 {#bug-fixes}

* パイプライン変数APIは、「削除済み」変数を削除する代わりに、ステータスが「削除済み」の変数のみをマークします。

* コードのにおいタイプの品質の問題が、信頼性の評価に誤って影響していました。

* パイプラインの実行が午前0時から午前1時のUTCの間に開始された場合、Cloud Managerで生成されるアーティファクトのバージョンが、前日に作成されたバージョンより大きいことは保証されませんでした。

* 一部のAdobe Managed Services(AMS)のお客様は、Cloud Manager APIを使用して、Adobe I/Oデベロッパーコンソールで新しいプロジェクトを作成できませんでした。
