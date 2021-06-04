---
title: リリースノート（2021.5.0）
description: このページでは、Cloud Manager リリース 2021.5.0 について説明します。
feature: リリース情報
source-git-commit: 3f17f252d89a1753c9cb121461b048f619d28415
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 97%

---

# リリースノート（2021.5.0） {#release-notes-for}

以下の節では、[!UICONTROL Cloud Manager] リリース 2021.5.0 の一般リリースノートの概要を説明します。

>[!NOTE]
>AEM as a Cloud Service での Cloud Manager の最新のリリースノートについては、[現在のリリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja#getting-access)を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2021.5.0 のリリース日は 2021 年 5 月 6 日（PT）です。
次回のリリースは2021年6月11日に予定されています。

## 新機能 {#whats-new}

* PackageOverlaps 品質ルールは、デプロイされたパッケージセットに同じパッケージが複数回（複数の埋め込み場所に）デプロイされた場合に検出するようになりました。

* Public API のリポジトリーエンドポイントに、Git URL が含まれるようになりました。

* プログラムの編集ワークフローでは、ユーザーは非 10 進型の KPI 値の設定のみが許可されます。

* コードを Adobe Git にプッシュ中に発生していた断続的なエラーが解決されました。

* プログラムの編集エクスペリエンスが新しくなりました。

## バグ修正 {#bug-fixes}

* パイプライン変数 API は、「削除済み」変数を削除するのではなく、ステータスを「削除済み」にするだけです。

* コードの臭いのタイプの品質問題が、誤って信頼性の評価に影響していました。

* パイプラインの実行が午前 0 時から午前 1 時（UTC）の間に開始された場合、Cloud Manager で生成されるアーティファクトのバージョンが、前日に作成されたバージョンより大きいことが保証されませんでした。

* Adobe Managed Services（AMS）の一部のユーザーが、Cloud Manager API を使用して、Adobe I/O デベロッパーコンソールで新しいプロジェクトを作成することができませんでした。
