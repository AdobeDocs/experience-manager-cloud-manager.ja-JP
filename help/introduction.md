---
title: AMS 用 Cloud Manager の概要
description: ここでは、Adobe Managed Services（AMS）用 Cloud Manager の概要と、組織がクラウドで Adobe Experience Manager を自己管理できるようにする仕組みについて説明します。
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
source-git-commit: a2cea28061304d109a3c9a48650d01255579443c
workflow-type: tm+mt
source-wordcount: '1322'
ht-degree: 100%

---


# [!UICONTROL Cloud Manager]の概要（AMS 用） {#introduction-to-cloud-manager}

ここでは、Adobe Managed Services（AMS）用 Cloud Manager の概要と、組織がクラウドで Adobe Experience Manager を自己管理できるようにする仕組みについて説明します。

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="AMS 用 Cloud Manager の概要"
>abstract="組織がクラウドで Adobe Experience Manager を自己管理できるようにします。このサービスには継続的統合および継続的配信（CI／CD）フレームワークが備わっているので、IT チームや実装パートナーはパフォーマンスやセキュリティを妥協することなくカスタマイズや更新を迅速に配信できます。"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=ja#cloud-manager" text="プログラムの作成"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=ja#cloud-manager" text="環境の作成"

## はじめに {#introduction}

Adobe Experience Manager の [!UICONTROL Cloud Manager] を使用すると、開発者は、Adobe Experience Manager のベストプラクティスに基づいて構築された、合理化されたワークフローを通じて、効果的な顧客エクスペリエンスを作成できます。Adobe Experience Manager に最適化された CI／CD パイプラインを使用すると、コードをチェックインするだけで開発ワークフローを簡単に統合し、実稼動の準備完了までフローを進めることができます。build フェーズでは、カスタムコードのアップデートはベストプラクティスに照らして徹底的にテストされ、信頼性の高いアプリケーションを顧客に提供します。Cloud Manager は、オープン API アプローチを採用し、既存のプロセスやツールを中断することなくシステムとの統合を可能にします。

>[!NOTE]
>
>このドキュメントでは、Adobe Managed Services（AMS）用 Cloud Manager の特長と機能について具体的に説明します。
>
>AEM as a Cloud Service の同等のドキュメントについては、[AEM as a Cloud Service のドキュメント](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/home.html?lang=ja)を参照してください。

Cloud Manager を使用すると、開発チームは次の機能を利用できます。

* コードの継続的インテグレーション／継続的配信（CI／CD）により、数か月／数週間かかっていた市場投入時間を数日／数時間へと短縮します。

* 実稼動にプッシュする前に、ベストプラクティスに基づいたコード検査、パフォーマンステストおよびセキュリティ検証を行い、実稼動の中断を最小限に抑えることができます。

* 既存の DevOps プロセスを補完する API 接続

* 自動スケーリング機能により、容量増加の必要性をインテリジェントに検出し、Dispatcher／パブリッシュの追加セグメントを自動的にオンラインにします。

この画像は、[!UICONTROL Cloud Manager] で使用される CI／CD プロセスフローを示します。

![CI／CD フロー](/help/assets/screen_shot_2018-05-12at73843pm.png)

## [!UICONTROL Cloud Manager] の主な機能 {#key-features-in-cloud-manager}

次に Cloud Manager の選択した主な機能について詳しく説明します。

### セルフサービスインターフェイス {#self-service-interface}

[!UICONTROL Cloud Manager] のユーザーインターフェイス（UI）を使用すると、Adobe Experience Manager アプリケーションのクラウド環境および CI／CD パイプラインに簡単にアクセスして管理できます。

アプリケーション特有の主要業績評価指標（KPI）（1 分あたりのピークページビュー数とページ読み込みに対する予想応答時間）を定義します。これが、最終的にデプロイメントが成功したかどうかを測定するための基礎となります。様々なチームメンバーの役割と権限を簡単に定義できます。セルフサービスインターフェイスによって制御が可能となりますが、必要に応じて必要なガイダンスを提供するアドビ内のエキスパートにアクセスできます。

[!UICONTROL Cloud Manager] の UI を確認して使用を開始するには、[初回ログイン](/help/getting-started/first-time-login.md)のドキュメントを参照してください。

### CI／CD パイプライン {#ci-cd-pipeline}

[!UICONTROL Cloud Manager] の主要機能の 1 つは、最適化された CI／CD パイプラインを使用して、Web サイト上の新しいコンポーネントの追加などのカスタムコードやアップデートの配信を高速化する機能です。

[!UICONTROL Cloud Manager] UI を使用して、CI／CD パイプラインを設定および開始できます。このパイプラインの一部として、徹底したコードスキャンが実行され、高品質なアプリケーションのみが実稼動環境へ渡されるようにします。

[!UICONTROL Cloud Manager] の UI からのパイプラインの設定について詳しくは、[実稼動パイプラインの設定](/help/using/production-pipelines.md)および[実稼動以外のパイプラインの設定](/help/using/non-production-pipelines.md)を参照してください。

### 柔軟なデプロイメントモード {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] には、ビジネス要件の変化に応じてエクスペリエンスを配信できるように、柔軟に設定可能なデプロイメントモードが用意されています。

自動トリガーモードでは、コードコミットなどの特定のイベントに基づいて、コードが自動的に環境にデプロイされます。また、業務時間外を含め、指定した期間、コードのデプロイメントをスケジュールすることもできます。

デプロイメントトリガーとは無関係に、デプロイメントがトリガーされるたびに、CI／CD パイプライン実行の一環として品質チェックが常に実行されます。品質チェックには、お客様およびパートナーに負担をかけることなく、すぐに使えるコード検査、セキュリティテストおよびパフォーマンステストが含まれています。

コードと品質チェックのデプロイについて詳しくは、[コードのデプロイ](/help/using/code-deployment.md)のドキュメントを参照してください。

## Cloud Manager のオプション機能 {#optional-features-in-cloud-manager}

Cloud Manager には、特定の環境設定やニーズに応じた、プロジェクトに役立つ追加の高度な機能が用意されています。これらの機能にご興味があれば、カスタマーサクセスエンジニア（CSE）またはアドビ担当者に詳細をお問い合わせください。

### 自動スケーリング {#autoscaling}

実稼動環境に異常な高負荷がかかると、[!UICONTROL Cloud Manager] は、追加容量の必要性を検出し、自動スケーリング機能を使用して追加容量を自動的にオンラインにします。

このような場合、[!UICONTROL Cloud Manager] は自動スケーリングプロビジョニング処理を自動的にトリガーし、自動スケーリングイベントの通知を送信し、数分以内に追加容量をオンラインにします。追加容量は実稼動環境において、実行中の Dispatcher／パブリッシュノードと同じシステム仕様に一致する同じ地域でプロビジョニングされます。

自動スケーリング機能は、Dispatcher／パブリッシュ層にのみ適用され、Dispatcher／パブリッシュのペアの 1 個以上の追加セグメント、最大で 10 個のセグメントで、水平スケールメソッドを使用して実行されます。プロビジョニングされた追加容量は、CSE（カスタマーサクセスエンジニア）が指定した 10 営業日以内に、手動でスケーリングされます。

>[!NOTE]
>
>自動スケーリングがアプリケーションに適しているかどうかを確認したい場合は、担当の CSE またはアドビ担当者にお問い合わせください。

### ブルー／グリーンデプロイメント {#blue-green}

ブルー／グリーンデプロイメントは、ブルーとグリーンと呼ばれる 2 つの同一の実稼動環境を実行することで、ダウンタイムとリスクを低減する手法です。

常に 1 つの環境のみが実稼働し、実稼働環境がすべての実稼動トラフィックを処理します。一般に、ブルーは現在稼働中の環境、グリーンはアイドル状態です。

* ブルー／グリーンデプロイメントは、Cloud Manager CI／CD パイプラインのアドオンで、パブリッシュインスタンスと Dispatcher インスタンスの 2 つ目のセット（グリーン）が作成され、デプロイメントに使用されます。その後、グリーンのインスタンスが実稼動用ロードバランサーに接続され、古いインスタンス（ブルー）が削除されて終了します。
* このブルー／グリーン実装はインスタンスを一時的なものとして扱い、ブルー／グリーンパイプライン反復ごとに、新しいパブリッシュサーバーと Dispatcher サーバーのセットが作成されます。
* グリーンのロードバランサーが設定の一部として作成されます。このロードバランサーは変更されることはなく、グリーンまたは「テスト」URL を示す必要があります。
* ブルー／グリーンデプロイメント中に、既存のパブリッシュ層／Dispatcher 層の正確なレプリカが作成されます。

#### ブルー／グリーンデプロイメントのフロー {#flow}

ブルー／グリーンデプロイメントが有効な場合、デプロイメントフローは標準の Cloud Service デプロイメントフローとは異なります。

| 手順 | ブルー／グリーンデプロイメント | 標準デプロイメント |
|---|---|---|
| 1 | オーサーへのデプロイメント | オーサーへのデプロイメント |
| 2 | テスト用に一時停止 | - |
| 3 | グリーンのインフラストラクチャが作成されます | - |
| 4 | グリーンのパブリッシュ層／Dispatcher 層へのデプロイメント | パブリッシャーへのデプロイメント |
| 5 | テスト用に一時停止（最大 24 時間） | - |
| 6 | グリーンのインフラストラクチャが実稼動用ロードバランサーに追加されます | - |
| 7 | ブルーのインフラストラクチャが実稼働用ロードバランサーから削除されます - |
| 8 | 最終的なサインオフ用に一時停止（最大 24 時間） | - |
| 9 | ブルーのインフラストラクチャは自動的に終了します | - |
| 10 | パイプライン完了 | - |

#### ブルー／グリーンの実装 {#implementing}

実稼動デプロイメントに Cloud Manager を使用しているすべての AMS ユーザーは、ブルー／グリーンのデプロイメントを使用する資格があります。ただし、ブルー／グリーンデプロイメントを使用する場合は、環境の追加検証およびアドビ CSE による設定が必要です。

ブルー／グリーンデプロイメントにご興味がある場合は、次の要件と制限事項を考慮し、担当の CSE にお問い合わせください。

#### 要件と制限事項 {#limitations}

* ブルー／グリーンは、パブリッシュと Dispatcher のペアでのみ使用できます。
* プレビューの Dispatcher とパブリッシュのペアは、ブルー／グリーンデプロイメントには含まれていません。
* すべての Dispatcherとパブリッシュのペアは、他のすべての Dispatcherとパブリッシュのペアと同じです。
* ブルー／グリーンは、実稼動環境でのみ使用できます。
* Azure だけでなく、AWS でもブルー／グリーンが利用できます。
* Assets のみのお客様は、ブルー／グリーンを利用できません。
