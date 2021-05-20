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
>AEM as aCloud Service版のCloud Managerの最新のリリースノートについては、[最新のリリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access)を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2021.5.0 のリリース日は 2021 年 5 月 06 日です。次回のリリースは2021年6月3日に予定されています。

## 新機能 {#whats-new}

* PackageOverlaps品質ルールで、同じパッケージが複数回（同じデプロイ済みパッケージセット内の複数の埋め込み場所など）デプロイされた場合を検出するようになりました。

* パブリックAPIのリポジトリエンドポイントにGitのURLが含まれるようになりました。

* プログラムを編集ワークフローでは、ユーザーは10進数以外のKPI値のみ設定できます。

* コードをAdobeGitにプッシュ中に発生する断続的なエラーが解決されました。

* プログラムの編集エクスペリエンスが更新されました。

## バグ修正 {#bug-fixes}

* パイプライン変数APIは、「削除済み」変数を削除する代わりに、ステータス「削除済み」のみをマークします。

* コードスメルタイプの品質の問題の一部が、信頼性評価に誤って影響していました。

* UTCの午前0時から午前1時の間にパイプラインの実行が開始された場合、Cloud Managerで生成されるアーティファクトのバージョンが前日に作成されたバージョンより大きくなることは保証されていませんでした。

* 一部のAdobe Managed Services(AMS)のお客様は、Cloud Manager APIを使用して、Adobe I/O開発者コンソールで新しいプロジェクトを作成できませんでした。
