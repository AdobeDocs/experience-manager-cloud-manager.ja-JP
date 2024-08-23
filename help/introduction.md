---
title: AMS 用 Cloud Manager の概要
description: ここでは、Adobe Managed Services（AMS）用 Cloud Manager の概要と、組織がクラウドで Adobe Experience Manager を自己管理できるようにする仕組みについて説明します。
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
source-git-commit: 4c4a2688cab8e5c81efa4b7b5e26f3c7b5dc30d6
workflow-type: tm+mt
source-wordcount: '1256'
ht-degree: 56%

---


# [!UICONTROL Cloud Manager]の概要（AMS 用） {#introduction-to-cloud-manager}

ここでは、AMS 用Cloud Manager（クラウドManaged Services）の概要と、AdobeでAdobe Experience Managerを自己管理する方法を説明します。

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="AMS 用 Cloud Manager の概要"
>abstract="組織がクラウドで Adobe Experience Manager を自己管理できるようにします。このサービスには継続的インテグレーションと継続的デリバリー（CI／CD）フレームワークが備わっているので、IT チームや実装パートナーはパフォーマンスやセキュリティを妥協することなくカスタマイズや更新を迅速に配信できます。"
>additional-url="https://experienceleague.adobe.com/ja/docs/experience-manager-learn/cloud-service/cloud-manager/programs#cloud-manager" text="プログラムの作成"
>additional-url="https://experienceleague.adobe.com/ja/docs/experience-manager-learn/cloud-service/cloud-manager/environments#cloud-manager" text="環境の作成"

## はじめに {#introduction}

Adobe Experience Manager の [!UICONTROL Cloud Manager] を使用すると、開発者は、Adobe Experience Manager のベストプラクティスに基づいて構築された、合理化されたワークフローを通じて、効果的な顧客エクスペリエンスを作成できます。Adobe Experience Managerに最適化された CI/CD パイプラインを使用すると、コードをチェックインするだけで開発ワークフローを簡単に統合し、実稼動の準備完了までフローを進めることができます。 build フェーズでは、カスタムコードのアップデートはベストプラクティスに照らして徹底的にテストされ、信頼性の高いアプリケーションを顧客に提供します。Cloud Manager は、オープン API アプローチを採用し、既存のプロセスやツールを中断することなくシステムとの統合を可能にします。

>[!NOTE]
>
>このドキュメントでは、Adobe Managed Services（AMS）用 Cloud Manager の特長と機能について具体的に説明します。
>
>AEM as a Cloud Service の同等のドキュメントについて詳しくは、[AEM as a Cloud Service のドキュメント](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/implementing/home)を参照してください。

Cloud Manager を使用すると、開発チームは次の機能を利用できます。

* コードの継続的統合/継続的配信（CI/CD）により、数か月/数週間かかっていた市場投入時間を数日/数時間へと短縮します。

* 実稼動にプッシュする前に、ベストプラクティスに基づいたコード検査、パフォーマンステストおよびセキュリティ検証を行い、実稼動の中断を最小限に抑えることができます。

* 既存の DevOps プロセスを補完する API 接続。

* 自動スケーリング機能により、容量増加の必要性がインテリジェントに検出され、追加のDispatcher/公開セグメントが自動的にオンラインになります。

![CI/CD フロー ](/help/assets/screen_shot_2018-05-12at73843pm.png)[!UICONTROL Cloud Manager] で使用される CI/CD プロセスフロー。

## [!UICONTROL Cloud Manager] の主な機能 {#key-features-in-cloud-manager}

次に Cloud Manager の選択した主な機能について詳しく説明します。

### セルフサービスインターフェイス {#self-service-interface}

[!UICONTROL Cloud Manager] のユーザーインターフェイス （UI）を使用すると、Adobe Experience Manager アプリケーションのクラウド環境および CI/CD パイプラインに簡単にアクセスして管理できます。

1 分あたりのピークページビュー数や予想されるページ読み込み応答時間など、アプリケーション固有の主要業績評価指標（KPI）を定義します。 これらの KPI は、デプロイメントの成功を測定するための基盤として機能します。 様々なチームメンバーの役割と権限を簡単に定義できます。セルフサービスインターフェイスを使用すると、完全に制御できます。 また、必要に応じて、ベストプラクティスのリソースへのリンクやガイダンスのためのAdobeエキスパートへのアクセスも提供します。

[!UICONTROL Cloud Manager] の UI を確認して使用を開始するには、[初回ログイン](/help/getting-started/first-time-login.md)を参照してください。

### CI/CD パイプライン {#ci-cd-pipeline}

[!UICONTROL Cloud Manager] の主要機能の 1 つは、最適化された CI／CD パイプラインを使用して、Web サイト上の新しいコンポーネントの追加などのカスタムコードやアップデートの配信を高速化する機能です。

[!UICONTROL Cloud Manager] UI を使用して、CI／CD パイプラインを設定および開始できます。このパイプラインの一部として、徹底したコードスキャンが実行され、高品質なアプリケーションのみが実稼動環境へ渡されるようにします。

[!UICONTROL Cloud Manager] の UI からのパイプラインの設定について詳しくは、[ 実稼動パイプラインの設定 ](/help/using/production-pipelines.md) および [ 実稼動以外のパイプラインの設定 ](/help/using/non-production-pipelines.md) を参照してください。

### 柔軟なデプロイメントモード {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] には、ビジネス要件の変化に応じてエクスペリエンスを配信できるように、柔軟に設定可能なデプロイメントモードが用意されています。

自動トリガーモードでは、コードコミットなどの特定のイベントに基づいて、コードが自動的に環境にデプロイされます。また、業務時間外を含め、指定した期間、コードのデプロイメントをスケジュールすることもできます。

デプロイメントトリガーとは無関係に、デプロイメントがトリガーされるたびに、CI／CD パイプライン実行の一環として品質チェックが常に実行されます。品質チェックには、コード検査、セキュリティテスト、パフォーマンステストが含まれています。これらのチェックは、お客様やパートナーに負担をかけることなく、すぐに使える状態で提供されています。

コードと品質チェックのデプロイについて詳しくは、[ コードのデプロイ ](/help/using/code-deployment.md) を参照してください。

## Cloud Managerのオプション機能 {#optional-features-in-cloud-manager}

Cloud Managerには、特定の環境設定やニーズに応じた、プロジェクトに役立つ追加の高度な機能が用意されています。 これらの機能にご興味があれば、カスタマーサクセスエンジニア（CSE）またはアドビ担当者に詳細をお問い合わせください。

### 自動スケーリング {#autoscaling}

実稼動環境に異常な高負荷がかかると、[!UICONTROL Cloud Manager] は、追加容量の必要性を検出し、自動スケーリング機能を使用して追加容量を自動的にオンラインにします。

このような場合、[!UICONTROL Cloud Manager] は自動スケーリングプロビジョニング処理を自動的にトリガーし、自動スケーリングイベントの通知を送信し、数分以内に追加容量をオンラインにします。追加容量は実稼動環境と同じリージョンでプロビジョニングされ、実行中のDispatcher/パブリッシュノードと同じシステム仕様に一致します。

自動スケーリング機能は、Dispatcherとパブリッシュの層に適用され、水平スケーリングを使用して、Dispatcherとパブリッシュのペアの 1～10 のセグメントを追加します。 プロビジョニングされた追加容量は、AdobeCSE （カスタマーサクセスエンジニア）が指定した 10 営業日以内に、手動でスケーリングされます。

>[!NOTE]
>
>自動スケーリングがアプリケーションに適しているかどうかを確認したい場合は、担当の CSE またはアドビ担当者にお問い合わせください。

### ブルー/グリーンデプロイメント {#blue-green}

ブルー／グリーンデプロイメントは、ブルーとグリーンと呼ばれる 2 つの同一の実稼動環境を実行することで、ダウンタイムとリスクを低減する手法です。

常に 1 つの環境のみが実稼働し、実稼働環境がすべての実稼動トラフィックを処理します。一般に、ブルーは現在稼働中の環境、グリーンはアイドル状態です。

* ブルー／グリーンデプロイメントは、Cloud Manager CI／CD パイプラインのアドオンで、パブリッシュインスタンスと Dispatcher インスタンスの 2 つ目のセット（グリーン）が作成され、デプロイメントに使用されます。その後、グリーンのインスタンスが実稼動用ロードバランサーに接続され、古いインスタンス（ブルー）が削除されて終了します。
* このブルー/グリーン実装はインスタンスを一時的なものとして扱い、ブルー/グリーンパイプライン反復ごとに、新しいパブリッシュサーバーとDispatcher サーバーのセットが作成されます。
* グリーンのロードバランサーが設定の一部として作成されます。 このロードバランサーは変更されることはなく、グリーンまたは「テスト」 URL を示す必要があります。
* ブルー/グリーンデプロイメント中に、既存のDispatcher/公開層の正確なレプリカが作成されます。

#### ブルー/グリーンデプロイメントフロー {#flow}

ブルー／グリーンデプロイメントが有効な場合、デプロイメントフローは標準の Cloud Service デプロイメントフローとは異なります。

| ステップ | ブルー／グリーンデプロイメント | 標準デプロイメント |
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

#### ブルー/グリーンの実装 {#implementing}

実稼動デプロイメントにCloud Managerを使用しているすべての AMS ユーザーは、ブルー/グリーンデプロイメントを使用する資格があります。 ただし、ブルー/グリーンデプロイメントを使用する場合は、環境の追加の検証と、AdobeCSE による設定が必要です。

ブルー／グリーンデプロイメントにご興味がある場合は、次の要件と制限事項を考慮し、担当の CSE にお問い合わせください。

#### 要件と制限事項 {#limitations}

* ブルー/グリーンは、Dispatcherとパブリッシャーのペアでのみ使用できます。
* プレビューの Dispatcher とパブリッシュのペアは、ブルー／グリーンデプロイメントには含まれていません。
* すべてのDispatcherとパブリッシュのペアは、他のすべてのDispatcherとパブリッシャーのペアと同じです。
* ブルー／グリーンは、実稼動環境でのみ使用できます。
* ブルー／グリーンは、AWS と Azure で使用できます。
* Assetsのみのお客様は、ブルー/グリーンを利用できません。
