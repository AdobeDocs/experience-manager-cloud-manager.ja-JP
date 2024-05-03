---
title: 役割ベースの権限
description: Cloud Manager の事前設定された役割ベースの権限によるクラウドリソースへのアクセスの管理について説明します。
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
source-git-commit: 1c0c3a751ba2023fc2c2dd5d0d54f914373ad95b
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 97%

---


# 役割に基づく権限 {#role-based-permissions}

[!UICONTROL Cloud Manager] には、適切な権限を持つ事前設定済みの役割が用意されています。例えば、デベロッパーには、コードを開発して Git リポジトリにプッシュする権限があります。ビジネスオーナーには、主要業績評価指標（KPI）を定義したりデプロイメントを承認したりできる様々な権限があります。

>[!NOTE]
>
>このドキュメントでは、Adobe Managed Services（AMS）用 Cloud Manager の役割ベースの権限について説明します。
>
>AEM as a Cloud Service の同等のドキュメントについては、AEM as a Cloud Service ドキュメントの [Cloud Manager の概要](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/concepts/cloud-manager-introduction.html?lang=ja#role-based-permissions)ドキュメントを参照してください。

## ユーザーの役割 {#user-roles}

[!UICONTROL Cloud Manager] の役割管理は、[Admin Console](https://helpx.adobe.com/jp/enterprise/using/admin-console.html) を使用して行います。[!UICONTROL Cloud Manager] のユーザーはすべて、顧客の IMS 組織のメンバーであり、Adobe Managed Services 製品コンテキストを持っている必要があります。特定の役割のメンバーシップは、Admin Console でユーザーを [!UICONTROL Cloud Manager] 製品プロファイルに追加することで提供されます。

役割のセットアップ方法について詳しくは、[ユーザーと役割のセットアップ](/help/requirements/users-and-roles.md)を参照してください。

Admin Console で割り当てることができる役割の一覧を次の表に示します。

| [!UICONTROL Cloud Manager] の役割 | 説明 |
|---|---|
| ビジネスオーナー | これは、[!UICONTROL Cloud Manager] の初期セットアップを行うプライマリユーザーで、KPI の定義、実稼動デプロイメントの承認および必要に応じて重大な 3 層エラーのオーバーライドを担当します。 |
| プログラムマネージャー | このユーザーは [!UICONTROL Cloud Manager] を使用してチームのセットアップ、ステータスの確認、KPI の表示を行い、必要に応じて重大な 3 層エラーの承認も行う場合があります。 |
| デプロイメントマネージャー | このユーザーは、[!UICONTROL Cloud Manager] でデプロイメント操作を管理してステージングおよび実稼動デプロイメントを実行し、必要に応じて重大な 3 層エラーを承認し、Git リポジトリにアクセスできます。 |
| デベロッパー | このユーザーは、カスタムアプリケーションコードの開発およびテストを担当し、主に [!UICONTROL Cloud Manager] を使用してデプロイメントステータスを確認するほか、Git リポジトリにコミットすることができます。 |
| カスタマーサクセスエンジニア | このユーザーは、通常、AMS 顧客のカスタマーサクセスをサポートし、カスタマーサクセスエンジニア（CSE）による監督が必要なデプロイメントを実行する目的で [!UICONTROL Cloud Manager] を操作します。 |
| コンテンツ作成者 | このユーザーは、通常、[!UICONTROL Cloud Manager] を操作しませんが、[!UICONTROL Cloud Manager] プログラムスイッチャー（[!UICONTROL Experience Cloud] からナビゲート）を使用して Adobe Experience Manager（AEM）にアクセスする場合があります。 |

## ユーザーの権限 {#user-permissions}

各役割には、特定の事前設定済み権限が関連付けられています。使用可能な権限とそれを実行できる役割の一覧を次の表に示します。


| 権限 | 説明 | ビジネスオーナー | デプロイメントマネージャー | プログラムマネージャー | デベロッパー | CSE |
|--- |--- |--- |--- |--- |--- |--- |
| アプリケーションの読み取り | プログラム KPI を読み取ります | x | x | x | x | x |
| アプリケーションへの書き込み | プログラムをセットアップまたは編集します | x |  |  |  |  |
| プログラムの追加 | 新規プログラムを追加します | x |  |  |  |  |
| 環境の読み取り | 環境の詳細を参照します | x | x | x | x | x |
| 実行の作成 | パイプラインを開始します | x | x | x |  |  |
| 実行の読み取り | 実行ステータスを参照します | x | x | x | x | x |
| 実行の再開 | 一時停止した実行を再開できます | x | x | x |  | x |
| 実行における実稼動環境へのデプロイメントの承認 | 運用開始を承認します | x | x | x |  |  |
| 実行における実稼動環境へのデプロイメントのスケジュール設定 | 実稼働デプロイメントのスケジュールを設定します | x | x | x |  | x |
| 実行における実稼動環境へのデプロイメント | CSE による監督のために一時停止した際にアプリケーションを実稼動環境にデプロイします |  |  |  |  | x |
| 実行のキャンセル | 現在の実行のキャンセル |  |  | x |  |  |
| 実行における品質ゲートエラーのオーバーライド | 重大な品質ゲートエラーを承認します | x | x | x |  |  |
| パイプラインの作成 | パイプラインをセットアップ／編集します |  | x |  |  |  |
| パイプラインの読み取り | パイプラインの詳細を参照します | x | x | x | x | x |
| パイプラインへの書き込み | パイプラインをセットアップ／編集します |  | x |  |  |  |
| パイプラインにおける承認変更 | ビジネスオーナーオプションの編集を許可します |  | x |  |  |  |
| パイプラインにおける管理対象デプロイメントの変更 | CSE 監督オプションの編集を許可します |  | × |  |  |  |
| パイプラインの削除 | パイプラインの削除を許可します |  | x |  |  |  |
| ステップの読み取り | ステップの品質指標の結果を参照します | x | x | x | x | x |
| 個人用アクセストークンの生成 | Git へのアクセス |  | x |  | x |  |

ユーザーのセットアップ方法について詳しくは、[ユーザーと役割のセットアップ](/help/requirements/users-and-roles.md)のドキュメントを参照してください。

>[!TIP]
>
>設定可能な権限を持つカスタム権限プロファイルも使用できます。 ドキュメントを参照してください [カスタム権限](/help/using/custom-permissions.md) を参照してください。
