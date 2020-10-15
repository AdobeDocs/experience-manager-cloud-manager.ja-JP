---
title: Cloud Manager の概要
seo-title: Cloud Manager の概要
description: 'このページは、Cloud Manager の学習の基礎となります。 '
seo-description: 'このページは、Adobe AEM Cloud Manager の学習の基礎となります。メリットと主な機能を説明します。 '
uuid: 62d68e79-c2ba-4d8b-ba7d-33709014d5b6
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: ebcc91a5-be9e-4684-8146-d88f4013d4d1
translation-type: tm+mt
source-git-commit: 2005b7e7689d3bc0656f92ecdbe368519f0d52a9
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 97%

---


# [!UICONTROL Cloud Manager の概要]{#introduction-to-cloud-manager}

## 概要 {#introduction}

Adobe Managed Services の 1 つである [!UICONTROL Cloud Manager] を使用すると、組織は自らクラウド上で Experience Manager を管理できるようになります。このサービスには継続的統合および継続的配信（CI／CD）フレームワークが備わっているので、IT チームや実装パートナーはパフォーマンスやセキュリティを妥協することなくカスタマイズや更新を迅速に配信できます。

[!UICONTROL Cloud Manager] のセルフサービスのカスタマーポータルを使用すると、**組織**&#x200B;は以下のことを実行および活用できます。

* コードの&#x200B;**継続的統合／継続的配信**&#x200B;により、数か月／数週間かかっていた市場投入時間を数日／数時間へと短縮します。
* 実稼動の中断を最小限に抑えるために、実稼動にプッシュする前のベストプラクティスに基づいた&#x200B;**コード調査、パフォーマンステストおよびセキュリティの検証**。
* 最大限の柔軟性とコントロールを実現するための、業務時間以外の&#x200B;**自動、スケジュールまたは手動デプロイメント**。
* **自動スケーリング**&#x200B;機能により、容量増加の必要性がインテリジェントに検出され、追加の Dispatcher／パブリッシュセグメントが自動的にオンラインになります。

以下の画像に、[!UICONTROL Cloud Manager] で使用される CI／CD プロセスフローを示します。

![](assets/screen_shot_2018-05-12at73843pm.png)

## [!UICONTROL Cloud Manager] の主な機能{#key-features-in-cloud-manager}

組織は、[!UICONTROL Cloud Manager] を使用して以下の機能を利用できます。

### セルフサービスインターフェイス {#self-service-interface}

[!UICONTROL Cloud Manager] のユーザーインターフェイス（UI）を使用すると、お客様は Experience Manager アプリケーションのクラウド環境および CI／CD パイプラインに簡単にアクセスして管理できます。

お客様は、アプリケーション特有の主要業績評価指標（KPI）（1 分あたりのピークページビュー数とページ読み込みに対する予想応答時間）を定義します。これが、最終的にデプロイメントが成功したかどうかを測定するための基礎となります。様々なチームメンバーの役割と権限を簡単に定義できます。新しいセルフサービスインターフェイスでは制御は自分でできますが、必要に応じて必要なアドバイスを提供できるアドビ内の専門家にアクセスできます。

[!UICONTROL Cloud Manager] の UI を確認して使用を開始するには、[初回ログイン](https://helpx.adobe.com/experience-manager/cloud-manager/using/first-time-login.html)を参照してください。

### CI／CD パイプライン {#ci-cd-pipeline}

[!UICONTROL Cloud Manager] の主要機能の 1 つは、最適化された CI／CD パイプラインを使用して、Web サイト上の新しいコンポーネントの追加などのカスタムコードやアップデートの配信を高速化する機能です。

[!UICONTROL Cloud Manager] UI を使用して、CI／CD パイプラインを設定および開始できます。このパイプラインの間、徹底したコードスキャンが実行され、高品質なアプリケーションのみが実稼動環境に渡されます。

[!UICONTROL Cloud Manager] の UI からパイプラインを設定する方法について詳しくは、[CI／CD パイプラインの設定](https://helpx.adobe.com/experience-manager/cloud-manager/using/configuring-pipeline.html)を参照してください。

### 柔軟なデプロイメントモード {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] には、ビジネス要件の変化に応じてエクスペリエンスを配信できるように、柔軟に設定可能なデプロイメントモードが用意されています。

自動トリガーモードでは、コードコミットなどの特定のイベントに基づいて、コードが自動的に環境にデプロイされます。また、業務時間外を含め、指定した期間、コードのデプロイメントをスケジュールすることもできます。

デプロイメントトリガーとは無関係に、デプロイメントがトリガーされるたびに、CI／CD パイプライン実行の一環として品質チェックが常に実行されます。品質チェックには、お客様およびお客様のパートナーが手を加えなくてもすぐに使えるコード調査、セキュリティテスト、パフォーマンステストが含まれています。

コードと品質チェックのデプロイについて詳しくは、[コードのデプロイ](deploying-code.md)を参照してください。

### 自動スケーリング {#autoscaling}

[!UICONTROL Cloud Manager] では、実稼動環境の負荷が異常に高くなりがちな場合に追加容量の必要性を検出し、自動スケーリング機能によって、自動的に追加容量を利用できるようにします。

自動スケーリングイベント中、[!UICONTROL Cloud Manager] は自動スケーリングプロビジョニング処理を自動的にトリガーし、自動スケーリングイベントを送信し、数分以内に追加容量を利用できるようにします。追加容量は実稼動環境の、実行中の Dispatcher／パブリッシュノードと同じシステム仕様に一致する同じリージョンでプロビジョニングされます。

自動スケーリング機能は、Dispatcher／パブリッシュ層にのみ適用され、Dispatcher とパブリッシュのペアの 1 個以上の追加セグメント、最大で 10 個のセグメントで、常に水平スケール手法を使用して実行されます。プロビジョニングされた追加容量は、CSE（カスタマーサクセスエンジニア）が指定した 10 営業日以内に、手動でスケーリングされます。

>[!NOTE]
>Autoscalingがアプリケーションに適しているかどうかを調べる必要があるお客様は、CSEまたはAdobeの担当者にお問い合わせください。
