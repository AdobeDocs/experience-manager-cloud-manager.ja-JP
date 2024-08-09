---
title: 2024.7.0 のリリースノート
description: Cloud Manager 2024.7.0 のリリースノートについて説明します。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 7%

---


# Cloud Manager 2024.7.0 のリリースノート {#release-notes}

このページは、[!UICONTROL Cloud Manager] 2024.7.0 のリリースノートです。

>[!NOTE]
>
>AEM as a Cloud ServiceのCloud Managerの最新のリリースノートについては、[AEM as a Cloud ServiceのCloud Managerの最新のリリースノート ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current) を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] 2024.7.0 のリリース日は 2024 年 7 月 18 日です。 次回のリリースは 2024年8月13日（PT）に予定されています。

## 新機能 {#what-is-new}

* コミット時にパイプラインを開始するための [ 実稼動パイプライン ](/help/using/production-pipelines.md#adding-production-pipeline) および [ 実稼動以外のパイプライン ](/help/using/non-production-pipelines.md#adding-non-production-pipeline)トリガー&#x200B;**Git の変更時** が [ プライベートリポジトリ ](/help/managing-code/private-repositories.md) で使用できるようになりました。
* 実稼動前のパイプラインは手動でのみトリガーでき、**Git の変更時** として設定することはできません。
* 実稼動専用パイプラインの場合、昇格可能な実行のリストには、実稼動環境にデプロイされたアーティファクトのバージョンよりも大きいアーティファクトのバージョンを持つ実行が含まれます。
* [AEM プロジェクトアーキタイプ ](https://experienceleague.adobe.com/ja/docs/experience-manager-core-components/using/developing/archetype/overview) が [ バージョン 49](https://github.com/adobe/aem-project-archetype/tree/aem-project-archetype-49) に更新されました。

## 早期導入プログラム {#early-adoption}

Cloud Managerの早期導入プログラムに参加して、今後の機能をテストする機会を得ます

### ステージング専用パイプラインと実稼動用パイプライン {#staging-production-only-pipelines}

[ ステージング専用および実稼動専用パイプライン ](/help/using/stage-prod-only.md) のサポートが導入され、フルスタックの実稼動デプロイメントパイプラインを、より小さな専用のデプロイメントに分割できるようになりました。

この新機能をテストし、フィードバックを共有することに関心がある場合は、Adobe IDに関連付けられたメールアドレスから `Grp-cloudmanager_splitpipelines@adobe.com` にメールを送信します。
