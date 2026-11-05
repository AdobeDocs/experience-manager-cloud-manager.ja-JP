---
title: Cloud Manager 2026.11.0のリリースノート
description: Adobe Managed ServicesのCloud Manager 2026.11.0のリリースについて説明します。
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
TQID: 'https://experienceleague.adobe.com/4zfTpSYuFwrJZ-oeL1SObT14v2Rd--Z1hKn5JllHAro'
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
    internal-label: Experience Manager Cloud Manager
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: ed762d86-a04b-452b-a08f-86359bb8ff27
    internal-label: Configuration and operations
subfeature_v2:
  - id: c21ccc2b-e0c8-4853-bf41-f12259ed93f8
    internal-label: Release information
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
source-git-commit: 772379fc5c641fcde07165a2beb2d49e964b481d
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 9%
---

# Adobe Managed ServicesのCloud Manager 2026.11.0のリリースノート {#release-notes}

<!-- add "hold: true" to metadata above to be able to commit/merge to Main WITHOUT Publishig -->

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Adobe Managed Servicesの[!UICONTROL Cloud Manager] 2026.11.0のリリースについて説明します。

[Adobe Experience Manager as a Cloud Service の最新のリリースノート](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/release-notes/home)も参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] 2026.11.0のリリース日は2026年11月5日木曜日です。
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

次回のリリース予定は2026年12月3日木曜日です。

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## 新機能 {#new-features}

AMS版Cloud Managerの2026年11月リリースには、大きな新機能はありません。


## Beta プログラム {#beta-program}

一般リリースの前に、今後の機能に限定でアクセスするには、Cloud Managerのベータプログラムに参加してください。

>[!IMPORTANT]
>
>Beta リリースには問題が含まれており、いかなる保証も提供されません。 Adobeは、ベータ版リリースを（Adobe サポートサービスを通じて、またはその他の方法で）維持、修正、更新、変更、またはその他の方法でサポートする義務を負いません。 お客様は、ベータリリースを自分のリスクで使用します。 ベータ版リリースの正しい機能やパフォーマンス、または付随するドキュメントや資料に依存しないでください。 ベータ版の機能およびAPIは、予告なく変更される場合があります。 ベータ版リリースの使用は、完全にお客様の責任で行います。

現在、次のベータプログラムの商談を利用できます。

### AEM Managed Servicesのweb階層パイプライン {#web-tier-pipelines}

Cloud Managerでは、AMS プログラム用の専用のWeb階層パイプラインがサポートされるようになりました。これにより、フルスタックのデプロイとは独立して、Dispatcherおよびweb階層設定をデプロイできます。 これにより、web層の変更の迅速な反復と、不要なパイプライン全体の実行の削減が可能になります。 Web階層パイプラインが設定されている場合、フルスタックパイプラインは、デプロイメントの競合を防ぐために、その環境のweb階層デプロイメントを自動的にスキップします。 Web階層パイプラインを削除すると、デフォルトのデプロイメント動作が自動的に復元されます。

Betaに参加するには、Adobe カスタマーサクセスエンジニアにお問い合わせください。


## バグ修正 {#bug-fixes}

* 導入後のセキュリティテストが断続的に失敗する。 Adobe Managed Services プログラムでは、デプロイメント後のセキュリティテストのSSL設定チェックが多くのプログラムで断続的に失敗し、再試行に合格して、不要なパイプラインエラーが発生します。 チェックが更新され、間違って失敗しなくなります。 （CMGR-79870）

<!--
Known Issues {#known-issues}
-->
