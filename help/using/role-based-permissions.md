---
title: 役割に基づく権限
description: ロールベースの権限について詳しくは、このページに従ってください。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
translation-type: tm+mt
source-git-commit: a038a3d6e35ff28190441e9d11d9c539641a85af

---


# 役割に基づく権限 {#role-based-permissions}

[!UICONTROL Cloud Manager] には、適切な権限を持つ事前設定済みのロールが含まれています。 例えば、デベロッパーには、開発したコードを **Git リポジトリ**&#x200B;にプッシュする権限があります。また、ビジネスオーナーには、主要業績評価指標（KPI）を定義しデプロイメントを承認できる様々な権限があります。

## ユーザーのロール {#user-roles}

の役割管理 [!UICONTROL Cloud Manager] は、 [Adobe Admin Consoleで行います](https://helpx.adobe.com/enterprise/using/admin-console.html)。 [!UICONTROL Cloud Manager] のユーザーは、顧客の IMS 組織のメンバーであり、Adobe Managed Services 製品コンテキストを持っている必要があります。特定のロールメンバーシップは、Admin Console でユーザーを [!UICONTROL Cloud Manager] 製品プロファイルに追加することで提供されます。

ロールの設定方法について詳しくは、[ユーザーとロールの設定](setting-up-users-and-roles.md)を参照してください。

Admin Console で割り当てることができるロールの一覧を次の表に示します。

| **[!UICONTROL Cloud Manager]ロール&#x200B;** | **説明** |
|---|---|
| ビジネスオーナー | Primary user who completes the initial [!UICONTROL Cloud Manager] setup. KPI の定義、実稼動デプロイメントの承認、重大な 3 層エラーのオーバーライドを担当します。 |
| プログラムマネージャー | [!UICONTROL Cloud Manager] を使用して、チームの設定、ステータスのレビュー、KPI の確認をおこないます。重大な 3 層エラーを承認することができます。 |
| デプロイメントマネージャー | デプロイメント作業を管理します。Uses [!UICONTROL Cloud Manager] to execute stage and production deployments. 重大な 3 層エラーを承認することができます。Git リポジトリにアクセスできます。 |
| デベロッパー | カスタムアプリケーションコードを開発およびテストします。Primarily uses [!UICONTROL Cloud Manager] to view status. Git リポジトリにコミットする権限があります。 |
| カスタマーサクセスエンジニア | AMS のお客様のカスタマーサクセスを全般的にサポートします。カスタマーサクセスエンジニア（CSE）管理が必要なデプロイメントを実行するために、[!UICONTROL Cloud Manager] を操作します。 |
| コンテンツ作成者 | Generally does not interact with [!UICONTROL Cloud Manager]. This user may use the [!UICONTROL Cloud Manager] Program Switcher (having navigated from [!UICONTROL Experience Cloud]) to access Adobe Experience Manager (AEM). |

## ユーザーの権限 {#user-permissions}

各ロールには、特定の権限、事前設定済みのタスクまたは権限が関連付けられています。使用可能な機能とその機能を実行できるロールの一覧を次の表に示します。

ユーザーの設定方法について詳しくは、[ユーザーとロールの設定](setting-up-users-and-roles.md)を参照してください。

| 権限 | 説明 | ビジネスオーナー | デプロイメントマネージャー | プログラムマネージャー | デベロッパー | CSE |
|--- |--- |--- |--- |--- |--- |--- |
| アプリケーションの読み取り | プログラムKPIを読み取ります。 | x | x | x | x | x |
| アプリケーションへの書き込み | プログラムの設定または編集。 | x |  |  |  |  |
| 環境の読み取り | 環境の詳細を参照します。 | x | x | x | x | x |
| 実行の作成 | パイプラインを開始します。 | x | x | x |  |  |
| 実行の読み取り | 実行ステータスを参照します。 | x | x | x | x | x |
| 実行の再開 | 一時停止した実行を再開できます。 | x | x | x |  | x |
| 実行における実稼動環境へのデプロイメントの承認 | GoLive 承認を提供します。 | x | x | x |  |  |
| 実行における実稼動環境へのデプロイメントのスケジュール設定 | 実稼動環境へのデプロイメントのスケジュールを設定します。 | x | x | x |  | x |
| 実行における実稼動環境へのデプロイメント | CSE 管理のために一時停止したときにアプリケーションを実稼動環境にデプロイします。 |  |  |  |  | x |
| 実行のキャンセル | 現在の実行をキャンセルします。 | x | x | x |  |  |
| 実行における品質ゲートエラーのオーバーライド | 重大な品質ゲートエラーを承認します。 | x | x | x |  |  |
| パイプラインの作成 | パイプラインを設定または編集します。 |  | x |  |  |  |
| パイプラインの読み取り | パイプラインの詳細を参照します。 | x | x | x | x | x |
| パイプラインへの書き込み | パイプラインを設定または編集します。 |  | x |  |  |  |
| パイプラインにおける承認変更 | 「ビジネスオーナー」オプションの編集を許可します。 |  | x |  |  |  |
| パイプラインにおける管理対象デプロイメントの変更 | 「CSE 管理」オプションの編集を許可します。 |  | x |  |  |  |
| ステップの読み取り | ステップの品質指標の結果を参照します。 | x | x | x | x | x |
