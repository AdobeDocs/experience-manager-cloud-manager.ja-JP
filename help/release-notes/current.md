---
title: 2024.6.0 のリリースノート
description: Cloud Manager リリース 2024.6.0 のリリースノートです。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: a41ea35cb685d4e88e016bc887eb2465963747e1
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 48%

---


# Cloud Manager リリース 2024.6.0 のリリースノート {#release-notes}

このページは、[!UICONTROL Cloud Manager] リリース 2024.6.0 のリリースノートです。

>[!NOTE]
>
>AEM as a Cloud Service の Cloud Manager の最新リリースノートについては、[AEM as a Cloud Service の Cloud Manager の最新リリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja)を参照してください。

## リリース日 {#release-date}

のリリース日 [!UICONTROL Cloud Manager] リリース 2024.6.0 は 2024 年 6 月 6 日です。 次回のリリースは 2024 年 7 月 11 日（PT）に予定されています。

## 新機能 {#what-is-new}

* これで、 [独自の GitHub リポジトリの使用](/help/managing-code/private-repositories.md) フルスタックパイプラインとフロントエンドパイプラインの両方のソースとして。
   * さらに、で GitHub リポジトリを利用できます [git サブモジュール](/help/managing-code/git-submodules.md) プルリクエストの検証に使用される自動生成パイプラインの制御を強化し、コードスキャン段階で重要な指標の動作を定義できるようになりました。
   * [また、次の選択肢があります](/help/managing-code/github-check-config.md) github のレポート履歴を保持するには、パイプラインに名前を付け、必要に応じてパイプライン変数を設定します。
* 新しい OakPal ルールがに追加されました [Cloud Manager のコード品質スキャン。](/help/using/custom-code-quality-rules.md#oakpal-ui-content-package)
   * 2024 年 6 月の時点で追加されたすべての新しいルールは、改行のない変更です。
   * これらの新しいルールは、Cloud Manager の 2024 年 8 月のリリース以降にパイプラインでエラーが発生する可能性があるので、できるだけ早くこれらの問題に対処することをお勧めします。

## 早期導入プログラム {#early-adoption}

早期導入プログラムに参加して、今後の機能をテストする機会を得ることができます

### ステージング専用パイプラインと実稼動専用パイプライン {#staging-production-only-pipelines}

[ステージング専用パイプラインと実稼動専用パイプライン](/help/using/stage-prod-only.md)のサポートが導入され、フルスタックの実稼動デプロイメントパイプラインをより小さな特殊なデプロイメントに分割できるようになりました。

この新機能をテストしてフィードバックを共有することに興味がある場合は、Adobe ID に関連付けられたメールアドレスから `Grp-cloudmanager_splitpipelines@adobe.com` にメールを送信してください。
