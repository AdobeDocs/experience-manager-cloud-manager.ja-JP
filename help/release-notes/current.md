---
title: Cloud Manager 2026.7.0のリリースノート
description: Adobe Managed ServicesのCloud Manager 2026.7.0のリリースについて説明します。
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
TQID: https://experienceleague.adobe.com/4zfTpSYuFwrJZ-oeL1SObT14v2Rd--Z1hKn5JllHAro
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: acd33650c938d49bac5c319f8c938202fe543bbd
workflow-type: tm+mt
source-wordcount: 391
ht-degree: 14%

---


# Adobe Managed ServicesのCloud Manager 2026.7.0のリリースノート {#release-notes}

<!-- add "hold: true" to metadata above to be able to commit/merge to Main WITHOUT Publishig -->

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Adobe Managed Servicesの[!UICONTROL Cloud Manager] 2026.6.0のリリースについて説明します。

[Adobe Experience Manager as a Cloud Service の最新のリリースノート](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/release-notes/home)も参照してください。

## リリース日 {#release-date}

2026.7.0年[!UICONTROL Cloud Manager]のリリース日は2026年7月9日木曜日です。
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

次回のリリース予定は2026年8月6日木曜日（木）です。

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## 新機能 {#what-is-new}

<!-- There are no significant new features in the June 2026 Cloud Manager on AMS release. -->

* **モジュールのキャッシュによるビルド パフォーマンスの向上**
新しいビルドモデルでは、モジュールレベルのキャッシュを使用して、変更されたモジュールのみを（リポジトリ全体ではなく）コンパイルし、ビルドパフォーマンスを向上させます。 本番パイプラインに適用されます。 **スマートビルド**&#x200B;を使用する実稼動パイプラインを制御します。

  詳しくは、次を参照してください。

   * [実稼動パイプラインでのスマートビルドの使用について](/help/using/production-pipelines.md#about-smart-build)および[実稼動以外のパイプラインでのスマートビルドの使用について](/help/using/non-production-pipelines.md#about-smart-build)
   * [実稼動パイプラインを追加](/help/using/production-pipelines.md##adding-production-pipeline)および[実稼動以外のパイプラインを追加](/help/using/non-production-pipelines.md#add-non-production-pipeline)。

## Beta プログラム {#beta-program}

Cloud Manager の Beta プログラムに参加すると、一般リリース前の新機能に特別アクセスできます。

>[!IMPORTANT]
>
>Beta リリースには欠陥が含まれており、いかなる保証もなしに「現状のまま」提供されます。 Adobeは、ベータ版のリリースを（Adobe サポートサービスまたはその他の方法により）維持、修正、更新、変更、またはその他の方法でサポートする義務を負いません。 お客様は、独自のリスクでベータリリースを使用し、ベータリリースの正しい機能やパフォーマンス、または付随するドキュメントや資料に依存しないでください。 ベータ版の機能およびAPIは、予告なく変更される場合があります。 ベータ版リリースの使用は、完全にお客様の責任で行います。

現在、次のベータプログラムの機会が利用可能です。

### AEM Managed Servicesのweb階層パイプライン {#web-tier-pipelines}

Cloud Managerでは、AMS プログラム用の専用のWeb階層パイプラインがサポートされるようになりました。これにより、フルスタックのデプロイとは独立して、Dispatcherおよびweb階層設定をデプロイできます。 これにより、web層の変更の迅速な反復と、不要なパイプライン全体の実行の削減が可能になります。 Web階層パイプラインが設定されている場合、フルスタックパイプラインは、デプロイメントの競合を防ぐために、その環境のweb階層デプロイメントを自動的にスキップします。 Web階層パイプラインを削除すると、デフォルトのデプロイメント動作が自動的に復元されます。

Betaに参加するには、Adobe カスタマーサクセスエンジニアにお問い合わせください。




## バグ修正 {#bug-fixes}

AMS版Cloud Managerの2026年7月リリースには、重大なバグ修正はありません。

<!--
Known Issues {#known-issues}

* A 
-->
