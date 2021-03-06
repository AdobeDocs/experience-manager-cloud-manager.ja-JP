---
title: AMS 用 Cloud Manager の概要
description: ここから始めて、Adobe Managed Services(AMS) の Cloud Manager について理解し、組織がクラウド内のAdobe Experience Managerを自己管理できるようにする方法を学びます。
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
source-git-commit: b0dbb602253939464ff034941ffbad84b7df77df
workflow-type: tm+mt
source-wordcount: '878'
ht-degree: 23%

---


# の概要 [!UICONTROL Cloud Manager] （AMS 用） {#introduction-to-cloud-manager}

ここから始めて、Adobe管理サービス (AMS) の Cloud Manager について理解し、組織がクラウド内のAdobe Experience Managerを自己管理できるようにする方法を学びます。

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="AMS 用 Cloud Manager の概要"
>abstract="組織がクラウド内のAdobe Experience Managerを自己管理できるようにします。 このサービスには継続的統合および継続的配信（CI／CD）フレームワークが備わっているので、IT チームや実装パートナーはパフォーマンスやセキュリティを妥協することなくカスタマイズや更新を迅速に配信できます。"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=ja#cloud-manager" text="プログラムの作成"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=ja#cloud-manager" text="環境の作成"

## はじめに {#introduction}

Adobe Experience Manager の [!UICONTROL Cloud Manager] を使用すると、開発者は、Adobe Experience Manager のベストプラクティスに基づいて構築された、合理化されたワークフローを通じて、効果的な顧客エクスペリエンスを作成できます。Adobe Experience Manager向けに最適化された CI/CD パイプラインを使用すると、コードをチェックインするだけで開発ワークフローを簡単に結合でき、その後は実稼動に向けてすべての作業を進めることができます。 ビルドフェーズでは、カスタムコードの更新がベストプラクティスに照らして徹底的にテストされ、信頼できるアプリケーションを顧客に提供します。 Cloud Manager はオープンな API アプローチを使用し、既存のプロセスやツールを中断することなく、お客様のシステムとの統合を可能にします。

>[!NOTE]
>
>このドキュメントでは、Adobe Managed Services(AMS) 用 Cloud Manager の機能について特に説明します。
>
>AEM as a Cloud Serviceの同等のドキュメントについては、 [AEMas a Cloud Serviceドキュメント。](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/home.html?lang=ja)

Cloud Manager を使用すると、開発チームは次の機能を利用できます。

* コードの継続的統合/継続的配信 (CI/CD) により、数か月/数週間から数日/数時間に短縮

* 実稼動の中断を最小限に抑えるために、実稼動にプッシュする前のベストプラクティスに基づくコード検査、パフォーマンステスト、セキュリティ検証

* 既存の DevOps プロセスを補完する API 接続

* 容量増加の必要性をインテリジェントに検出し、追加の Dispatcher/パブリッシュセグメントを自動的にオンラインにする自動スケーリング

この図は、 [!UICONTROL Cloud Manager]:

![CI/CD フロー](/help/assets/screen_shot_2018-05-12at73843pm.png)

## [!UICONTROL Cloud Manager] の主な機能 {#key-features-in-cloud-manager}

以下は、Cloud Manager の選択した主な機能について詳しく説明します。

### セルフサービスインターフェイス {#self-service-interface}

のユーザーインターフェイス (UI) [!UICONTROL Cloud Manager] を使用すると、Adobe Experience Managerアプリケーションのクラウド環境や CI/CD パイプラインに簡単にアクセスして管理できます。

アプリケーション固有の主要業績評価指標 (KPI)（1 分あたりのピークページビュー数、ページ読み込みの予想応答時間など）を定義して、デプロイメント成功を測定する際の基礎となります。 様々なチームメンバーの役割と権限を簡単に定義できます。セルフサービスインターフェイスは、お客様の手に制御を与えますが、必要に応じて必要なガイダンスを提供できるAdobe内の専門家へのアクセスとベストプラクティスリソースへのリンクも提供します。

を参照して使用を開始するには、以下を実行します。 [!UICONTROL Cloud Manager]の UI（ドキュメントを参照） [初回ログイン。](/help/getting-started/first-time-login.md)

### CI／CD パイプライン {#ci-cd-pipeline}

[!UICONTROL Cloud Manager] の主要機能の 1 つは、最適化された CI／CD パイプラインを使用して、Web サイト上の新しいコンポーネントの追加などのカスタムコードやアップデートの配信を高速化する機能です。

を通じて [!UICONTROL Cloud Manager] UI を使用して、CI/CD パイプラインを設定および開始できます。 このパイプラインの一環として、徹底したコードスキャンが実行され、高品質なアプリケーションのみが実稼動環境に渡されます。

[!UICONTROL Cloud Manager] の UI からのパイプラインの設定について詳しくは、[実稼動パイプラインの設定](/help/using/production-pipelines.md)および[実稼動以外のパイプラインの設定](/help/using/non-production-pipelines.md)を参照してください。

### 柔軟なデプロイメントモード {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] は、ビジネスニーズの変化に応じてエクスペリエンスを配信できるように、柔軟に設定可能なデプロイメントモードを提供します。

自動トリガーモードでは、コードコミットなどの特定のイベントに基づいて、コードが自動的に環境にデプロイされます。 また、業務時間外を含め、指定した期間、コードのデプロイメントをスケジュールすることもできます。

デプロイメントトリガーとは無関係に、デプロイメントがトリガーされるたびに、CI/CD パイプライン実行の一環として品質チェックが常に実行されます。 品質チェックには、コード検査、セキュリティテスト、パフォーマンステストが含まれます。これらはすべて、お客様やパートナーが手を加えることなく、すぐに使用できる状態で提供されます。

コードと品質チェックのデプロイについて詳しくは、 [コードのデプロイ。](/help/using/code-deployment.md)

### 自動スケーリング {#autoscaling}

実稼動環境の負荷が異常に高くなる可能性がある場合に、 [!UICONTROL Cloud Manager] 追加容量の必要性を検出し、自動スケーリング機能を使用して追加容量を自動的にオンラインにします。

このような場合、 [!UICONTROL Cloud Manager] 自動スケーリングプロビジョニングプロセスを自動的にトリガーし、自動スケーリングイベントの通知を送信し、数分以内に追加容量をオンラインにします。 追加容量は実稼動環境の、実行中の Dispatcher/パブリッシュノードと同じシステム仕様に一致する同じリージョンでプロビジョニングされます。

自動スケーリング機能は、Dispatcher/パブリッシュ層にのみ適用され、水平スケーリング方法を使用して実行されます。Dispatcher/パブリッシュペアの 1 つ以上の追加セグメントが、最大 10 個まであります。 プロビジョニングされた追加容量は、CSE（カスタマーサクセスエンジニア）が指定した 10 営業日以内に、手動でスケーリングされます。

>[!NOTE]
>
>自動スケーリングがアプリケーションに適しているかどうかを確認したいお客様は、CSE またはAdobe担当者にお問い合わせください。
