---
title: AMS 用 Cloud Manager の概要
description: ここでは、Adobe Managed Services（AMS）用 Cloud Manager の概要と、組織がクラウドで Adobe Experience Manager を自己管理できるようにする仕組みについて説明します。
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
TQID: https://experienceleague.adobe.com/VR-H6ubMFgVrkfzDvY4JWYlUtM-Dkztdewr5LiSZK1w
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
  - id: ff09c71c-26a9-449a-85f8-2aeb8ce96100
subfeature_v2:
  - id: a4d14782-c381-4db2-89e3-8cf3f31b103c
  - id: c14b2f98-ee16-4c49-b87b-919c91b01d9d
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: ee4f497a8bb5fb2d37fd8283721ebc9891f9053a
workflow-type: tm+mt
source-wordcount: 1266
ht-degree: 69%

---

# [!UICONTROL Cloud Manager]の概要（AMS 用） {#introduction-to-cloud-manager}

AMS向けCloud Manager（Adobe Managed Services）について、および組織がクラウドでAdobe Experience Managerを自己管理できるようにする方法については、こちらをご覧ください。

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="AMS 用 Cloud Manager の概要"
>abstract="CI/CD フレームワークを使用して、Adobe Experience Managerをクラウドで自己管理できます。 このフレームワークにより、パフォーマンスやセキュリティを犠牲にすることなく、カスタマイズや更新を迅速化できます。"
>additional-url="https://experienceleague.adobe.com/ja/docs/experience-manager-learn/cloud-service/cloud-manager/programs#cloud-manager" text="プログラムの作成"
>additional-url="https://experienceleague.adobe.com/ja/docs/experience-manager-learn/cloud-service/cloud-manager/environments#cloud-manager" text="環境の作成"

## はじめに {#introduction}

Adobe Experience Manager の [!UICONTROL Cloud Manager] を使用すると、開発者は、Adobe Experience Manager のベストプラクティスに基づいて構築された、合理化されたワークフローを通じて、効果的な顧客エクスペリエンスを作成できます。 ADOBE EXPERIENCE MANAGER向けに最適化されたCI/CD パイプラインを使用すると、コードを確認して開発ワークフローを統合し、本番環境での使用に移行できます。 build フェーズでは、カスタムコードのアップデートはベストプラクティスに照らして徹底的にテストされ、信頼性の高いアプリケーションを顧客に提供します。 Cloud Manager は、オープン API アプローチを採用し、既存のプロセスやツールを中断することなくシステムとの統合を可能にします。

>[!NOTE]
>
>このドキュメントでは、Adobe Managed Services（AMS）用 Cloud Manager の特長と機能について具体的に説明します。
>
>AEM as a Cloud Service の同等のドキュメントについて詳しくは、[AEM as a Cloud Service のドキュメント](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/implementing/home)を参照してください。

Cloud Manager を使用すると、開発チームは次の機能を利用できます。

* コードの継続的インテグレーション/継続的デリバリー（CI/CD）により、開発サイクルを数か月/数週間から数日/数時間に短縮。
* 実稼動にプッシュする前に、ベストプラクティスに基づいたコード検査、パフォーマンステストおよびセキュリティ検証を行い、実稼動の中断を最小限に抑えることができます。
* 既存の DevOps プロセスを補完する API 接続
* 自動スケーリングにより、容量を増やす必要がなくなり、Dispatcher/パブリッシングセグメントの追加を自動的にプロビジョニングできます。

![CI/CD フロー](/help/assets/screen_shot_2018-05-12at73843pm.png) [!UICONTROL Cloud Manager] で使用される CI/CD プロセスフロー。

## [!UICONTROL Cloud Manager] の主な機能 {#key-features-in-cloud-manager}

次のセクションでは、Cloud Managerの主な機能について説明します。

### セルフサービスインターフェイス {#self-service-interface}

[!UICONTROL Cloud Manager] の UI を確認して使用を開始する方法について詳しくは、[初回ログイン](/help/getting-started/first-time-login.md)を参照してください。

[!UICONTROL Cloud Manager]のユーザーインターフェイス （UI）を使用すると、Adobe Experience Manager アプリケーションのクラウド環境とCI/CD パイプラインに簡単にアクセスして管理できます。

1 分あたりのピークページビュー数とページ読み込みに対する予想応答時間など、アプリケーション特有の主要業績評価指標（KPI）を定義します。 これらの KPI は、デプロイメントの成功を測定する基盤として機能します。 様々なチームメンバーの役割と権限を簡単に定義できます。 セルフサービスインターフェイスによって、完全に制御できます。 また、ベストプラクティスリソースへのリンクや、必要に応じてアドビのエキスパートからガイダンスを受けるアクセスも提供します。

### CI/CD パイプライン {#ci-cd-pipeline}

[!UICONTROL Cloud Manager]の主な機能の1つは、最適化されたCI/CD パイプラインを使用して、カスタムコードの配信や、web サイトでの新しいコンポーネントの追加などの更新を高速化できることです。

[!UICONTROL Cloud Manager] UIを使用して、CI/CD パイプラインを設定および開始できます。 このパイプラインの一部として、徹底したコードスキャンが実行され、高品質なアプリケーションのみが本番環境へ渡されるようにします。

[!UICONTROL Cloud Manager]のUIからパイプラインを設定する方法について詳しくは、[実稼動パイプラインの設定](/help/using/production-pipelines.md)および[実稼動以外のパイプラインの設定](/help/using/non-production-pipelines.md)を参照してください。

### 柔軟なデプロイメントモード {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] には、ビジネス要件の変化に応じてエクスペリエンスを配信できるように、柔軟に設定可能なデプロイメントモードが用意されています。

自動トリガーモードでは、コードコミットなどの特定のイベントに基づいて、コードが自動的に環境にデプロイされます。 また、業務時間外を含め、指定した期間、コードのデプロイメントをスケジュールすることもできます。

デプロイメントトリガーとは無関係に、デプロイメントがトリガーされるたびに、CI／CD パイプライン実行の一環として品質チェックが常に実行されます。 品質チェックには、コード検査、セキュリティテスト、パフォーマンステストが含まれ、これらはすべて標準機能として提供され、お客様やパートナーの労力は必要ありません。

コードと品質チェックのデプロイについて詳しくは、[コードのデプロイ](/help/using/code-deployment.md)を参照してください。

## Cloud Manager のオプション機能 {#optional-features-in-cloud-manager}

Cloud Managerには、特定の環境の設定とニーズに応じて、プロジェクトにメリットをもたらす高度な追加機能が用意されています。 さらに詳しくは、カスタマーサクセスエンジニア（CSE）またはAdobeの担当者にお問い合わせください。

### 自動スケーリング {#autoscaling}

本番環境が異常に高い負荷にさらされている場合、[!UICONTROL Cloud Manager]は、追加の容量の必要性を検出し、その自動スケーリング機能を使用して追加の容量を自動的にプロビジョニングします。

このような場合、[!UICONTROL Cloud Manager]は自動スケーリングプロビジョニングプロセスを自動トリガーし、自動スケーリングイベントの通知を送信し、数分以内に追加容量をプロビジョニングします。 追加のキャパシティは、実稼動環境と同じリージョンでプロビジョニングされ、実行中のDispatcher/パブリッシングノードのシステム仕様と一致します。

自動スケーリング機能は、Dispatcher／パブリッシュ層にのみ適用され、水平スケーリングを使用して、Dispatcher／パブリッシュのペアの 1～10 個のセグメントを追加します。 プロビジョニングされた追加容量は、アドビ CSE（カスタマーサクセスエンジニア）が指定した 10 営業日以内に、手動でスケーリングされます。

>[!NOTE]
>
>自動スケーリングがアプリケーションに適しているかどうかを確認したい場合は、担当の CSE またはアドビ担当者にお問い合わせください。

### ブルー／グリーンデプロイメント {#blue-green}

ブルー／グリーンデプロイメントは、ブルーとグリーンと呼ばれる 2 つの同一の本番環境を実行することで、ダウンタイムとリスクを低減する手法です。

常に 1 つの環境のみが実稼働し、実稼働環境がすべての実稼動トラフィックを処理します。 一般に、ブルーは現在稼働中の環境、グリーンはアイドル状態です。

* ブルー／グリーンデプロイメントは、Cloud Manager CI／CD パイプラインのアドオンで、パブリッシュインスタンスと Dispatcher インスタンスの 2 つ目のセット（グリーン）が作成され、デプロイメントに使用されます。 その後、グリーンのインスタンスが実稼動用ロードバランサーに接続され、古いインスタンス（ブルー）が削除されて終了します。
* このブルー／グリーン実装はインスタンスを一時的なものとして扱い、ブルー／グリーンパイプライン反復ごとに、新しいパブリッシュサーバーと Dispatcher サーバーのセットが作成されます。
* グリーンのロードバランサーが設定の一部として作成されます。 このロードバランサーは変更されず、グリーン URLまたは「テスト」 URLのターゲットです。
* ブルー／グリーンデプロイメント中に、既存のパブリッシュ層／Dispatcher 層の正確なレプリカが作成されます。

#### ブルー／グリーンデプロイメントのフロー {#flow}

ブルー／グリーンデプロイメントが有効な場合、デプロイメントフローは標準の Cloud Service デプロイメントフローとは異なります。

| ステップ | ブルー／グリーンデプロイメント | 標準デプロイメント |
| --- | --- | --- |
| 1 | オーサーへのデプロイメント | オーサーへのデプロイメント |
| 2 | テスト用に一時停止 | - |
| 3 | グリーンのインフラストラクチャが作成されます | - |
| 4 | グリーン公開/Dispatcher層へのデプロイメント | パブリッシャーへのデプロイメント |
| 5 | テスト用に一時停止（最大 24 時間） | - |
| 6 | グリーンのインフラストラクチャが実稼動用ロードバランサーに追加されます | - |
| 7 | 本番ロードバランサーから青いインフラストラクチャが削除される | - |
| 8 | 最終的なサインオフ用に一時停止（最大 24 時間） | - |
| 9 | ブルーのインフラストラクチャは自動的に終了します | - |
| 10 | パイプライン完了 | - |

#### ブルー／グリーンの実装 {#implementing}

実稼動デプロイメントに Cloud Manager を使用しているすべての AMS ユーザーは、ブルー／グリーンのデプロイメントを使用する資格があります。 ただし、ブルー／グリーンデプロイメントを使用する場合は、環境の追加検証およびアドビ CSE による設定が必要です。

ブルー／グリーンデプロイメントにご興味がある場合は、次の要件と制限事項を考慮し、担当の CSE にお問い合わせください。

#### 要件と制限事項 {#limitations}

* ブルー／グリーンは、Dispatcher とパブリッシュのペアでのみ使用できます。
* プレビューの Dispatcher とパブリッシュのペアは、ブルー／グリーンデプロイメントには含まれていません。
* Dispatcher とパブリッシュのすべてのペアは、Dispatcher とパブリッシュの他のすべてのペアと同じです。
* ブルー／グリーンは、本番環境でのみ使用できます。
* ブルー／グリーンは、AWS と Azure で使用できます。
* Assets のみのお客様は、ブルー／グリーンを利用できません。
