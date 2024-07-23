---
title: 2024.7.0 のリリースノート
description: Cloud Manager リリース 2024.7.0 のリリースノートです。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 87c603a89b99f6984828280cba2041da8c72e839
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 95%

---


# Cloud Manager リリース 2024.7.0 のリリースノート {#release-notes}

このページは、[!UICONTROL Cloud Manager] リリース 2024.7.0 のリリースノートです。

>[!NOTE]
>
>AEM as a Cloud Service の Cloud Manager の最新リリースノートについては、[AEM as a Cloud Service の Cloud Manager の最新リリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja)を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] リリース 2024.7.0 のリリース日は 2024年7月18日（PT）です。次回のリリースは 2024年8月8日（PT）に予定されています。

## 新機能 {#what-is-new}

* コミット時に[実稼動パイプライン](/help/using/production-pipelines.md#adding-production-pipeline)と[実稼動以外のパイプライン](/help/using/non-production-pipelines.md#adding-non-production-pipeline)がパイプラインを開始するための **Git の変更時**&#x200B;をトリガーし、[プライベートリポジトリ](/help/managing-code/private-repositories.md)で使用できるようになりました。
* 実稼動前のパイプラインは手動でのみトリガーでき、**Git の変更時**&#x200B;として設定することはできません。
* 実稼動専用パイプラインの場合、昇格可能な実行のリストには、実稼動環境にデプロイされたアーティファクトのバージョンよりも新しいアーティファクトバージョンが含まれます。
* [AEM プロジェクトアーキタイプ ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=ja) が [ バージョン 49.](https://github.com/adobe/aem-project-archetype/tree/aem-project-archetype-49) に更新されました。


## 早期導入プログラム {#early-adoption}

早期導入プログラムに参加して、今後の機能をテストする機会を得ることができます

### ステージング専用パイプラインと実稼動専用パイプライン {#staging-production-only-pipelines}

[ステージング専用パイプラインと実稼動専用パイプライン](/help/using/stage-prod-only.md)のサポートが導入され、フルスタックの実稼動デプロイメントパイプラインをより小さな特殊なデプロイメントに分割できるようになりました。

この新機能をテストしてフィードバックを共有することに興味がある場合は、Adobe ID に関連付けられたメールアドレスから `Grp-cloudmanager_splitpipelines@adobe.com` にメールを送信してください。
