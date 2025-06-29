---
title: 役割ベースの権限
description: Cloud Manager の事前設定された役割ベースの権限によるクラウドリソースへのアクセスの管理について説明します。
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 99%

---


# 役割ベースの権限 {#role-based-permissions}

[!UICONTROL Cloud Manager] には、適切な権限を持つ事前設定済みのロールが用意されています。例えば、デベロッパーには、開発したコードを Git リポジトリーにプッシュする権限があります。ビジネスオーナーには、主要業績評価指標（KPI）を定義したりデプロイメントを承認したりできる様々な権限があります。

>[!NOTE]
>
>このドキュメントでは、Adobe Managed Services（AMS）用 Cloud Manager の役割ベースの権限について説明します。
>
>AEM as a Cloud Service の同等のドキュメントについては、AEM as a Cloud Service ドキュメントの [Cloud Manager の概要](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/onboarding/concepts/cloud-manager-introduction#role-based-permissions)ドキュメントを参照してください。

## ユーザーの役割 {#user-roles}

[!UICONTROL Cloud Manager] の役割管理は、[Admin Console](https://helpx.adobe.com/jp/enterprise/using/admin-console.html) を使用して行います。[!UICONTROL Cloud Manager] のユーザーはすべて、顧客の IMS 組織のメンバーであり、Adobe Managed Services 製品コンテキストを持っている必要があります。特定の役割のメンバーシップは、Admin Console でユーザーを [!UICONTROL Cloud Manager] 製品プロファイルに追加することで提供されます。

役割の設定方法について詳しくは、[ユーザーと役割の設定](/help/requirements/users-and-roles.md)を参照してください。

Admin Console で割り当てることができる役割の一覧を次の表に示します。

| [!UICONTROL Cloud Manager] の役割 | 説明 |
|---|---|
| ビジネスオーナー | [!UICONTROL Cloud Manager] の初期設定を実行し、KPI の定義、実稼動デプロイメントの承認および必要に応じて重大な 3 層エラーのオーバーライドを担当するプライマリユーザーです。 |
| コンテンツ作成者 | ユーザーは、通常、Cloud Manager を操作しませんが、Cloud Manager プログラムスイッチャー（Experience Cloud からナビゲート）を使用して Adobe Experience Manager（AEM）にアクセスする場合があります。 |
| カスタマーサクセスエンジニア | ユーザーは主に AMS のカスタマーサクセスをサポートし、[!UICONTROL Cloud Manager] と関与してデプロイメントを実行します。これらのデプロイメントには、アドビカスタマーサクセスエンジニア（CSE）による監視が必要です。 |
| デプロイメントマネージャー | ユーザーは、[!UICONTROL Cloud Manager] でデプロイメント操作を管理してステージングおよび実稼動デプロイメントを実行し、必要に応じて重大な 3 層エラーを承認し、Git リポジトリにアクセスできます。 |
| 開発者 | ユーザーは、カスタムアプリケーションコードの開発およびテストを担当し、主に [!UICONTROL Cloud Manager] を使用してデプロイメントステータスを確認するほか、Git リポジトリにコミットできます。 |
| プログラムマネージャー | ユーザーは [!UICONTROL Cloud Manager] を使用してチームの設定、ステータスの確認、KPI の表示を行い、必要に応じて重大な 3 層エラーの承認も行う場合があります。 |

## ユーザーの権限 {#user-permissions}

各役割には、特定の事前設定済み権限があります。使用可能な権限とそれを実行できる役割の一覧を次の表に示します。

| 権限 | 説明 | ビジネスオーナー | デプロイメントマネージャー | プログラムマネージャー | 開発者 | CSE |
| --- | --- | --- | --- | --- | --- | --- |
| `Read the Application` | プログラム KPI を読み取ります | x | x | x | x | x |
| `Write Application` | プログラムの設定または編集 | x | | | | |
| `Add Program` | 新規プログラムを追加します | x |  |  |  |  |
| `Read Environment` | 環境の詳細を参照します | x | x | x | x | x |
| `Create Execution` | パイプラインを開始します | x | x | x | | |
| `Read Execution` | 実行ステータスを参照します | x | x | x | x | x |
| `Resume Execution` | 一時停止した実行を再開する機能 | x | x | x | | x |
| `Execution Approve Deploy to Production` | 運用開始を承認します | x | x | x | | |
| `Execution Schedule Deploy to Production` | 実稼動デプロイメントをスケジュール | x | x | x | | x |
| `Execution Deploy to Production` | CSE による監督のために一時停止した際にアプリケーションを実稼動環境にデプロイします |  |  |  |  | x |
| `Execution Cancel` | 現在の実行のキャンセル |  |  | x |  |  |
| `Execution Override Quality Gate Failures` | 重大な品質ゲートエラーを承認します | x | x | x |  |  |
| `Pipeline Create` | パイプラインをセットアップ／編集します |  | x |  |  |  |
| `Pipeline Read` | パイプラインの詳細を参照します | x | x | x | x | x |
| `Pipeline Write` | パイプラインをセットアップ／編集します |  | x |  |  |  |
| P`ipeline Modify Approval` | ビジネスオーナーオプションの編集を許可します |  | x |  |  |  |
| `Pipeline Modify Managed Deployment` | CSE 監督オプションの編集を許可します |  | x |  |  |  |
| `Pipeline Delete` | パイプラインの削除を許可します |  | x |  |  |  |
| `Step Read` | ステップの品質指標の結果を参照します | x | x | x | x | x |
| `Generate Personal Access Token` | Git にアクセス |  | x |  | x |  |

<!-- CQDOC-22080 | Download log files  |  |  | x |  | x |  | -->

ユーザーの設定方法について詳しくは、[ユーザーと役割の設定](/help/requirements/users-and-roles.md)を参照してください。

>[!TIP]
>
>設定可能な権限を持つカスタム権限プロファイルも使用できます。詳しくは、[カスタム権限](/help/using/custom-permissions.md)を参照してください。
