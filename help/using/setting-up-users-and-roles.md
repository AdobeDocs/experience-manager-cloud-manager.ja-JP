---
title: ユーザーとロールの追加
seo-title: ユーザーとロールの追加
description: 'null'
seo-description: Admin Console でユーザーを Cloud Manager 製品プロファイルに追加することで、特定のロールメンバーシップを割り当てることができます。この節では、この機能について詳しく見ていきます。
uuid: fa204c28-83df-48bb-8360-e158f080dee7
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER／CLOUDMANAGER
topic-tags: requirements
discoiquuid: 1b421993-22c3-4de0-ba64-c1080d07ad5e
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# ユーザーとロールの追加{#add-users-and-roles}

[!UICONTROL Cloud Manager] の多くの機能には、使用するための特定の権限が必要です。例えば、プログラムの主要業績評価指標（KPI）を設定できるのは、特定のユーザーだけです。これらの権限は、論理的にグループ化されてロールになります。

[!UICONTROL Cloud Manager] では、現在、特定の機能を使用できるかどうかを制御する次の 4 つのユーザーロールを定義しています。

* ビジネスオーナー
* プログラムマネージャー
* デプロイメントマネージャー
* デベロッパー

>[!CAUTION]
>
>[!UICONTROL Cloud Manager] を使用するには、Adobe ID と Adobe Managed Services 製品コンテキストが必要です。

## ロールの定義 {#role-definitions}

>[!NOTE]
>
>Admin Console の「開発者」ペルソナは、[!UICONTROL Cloud Manager] の「デベロッパー」ロールとは無関係です。

ロールの概要を次の表に示します。

| [!UICONTROL Cloud Manager] のロール | 説明 |
|--- |--- |
| ビジネスオーナー | KPI の定義、実稼働デプロイメントの承認、重大な 3 層エラーのオーバーライドを担当します。 |
| プログラムマネージャー | [!UICONTROL Cloud Manager] を使用して、チームの設定、ステータスのレビュー、KPI の確認をおこないます。重大な 3 層エラーを承認することができます。 |
| デプロイメントマネージャー | デプロイメント作業を管理します。[!UICONTROL Cloud Manager] を使用して、ステージング環境または実稼働環境へのデプロイメントを実行します。CI／CD パイプラインを編集できます。重大な 3 層エラーを承認することができます。Git リポジトリにアクセスできます。Git リポジトリへのアクセス権を要求するには、CSE／AMS 担当者にお問い合わせください。 |
| デベロッパー | カスタムアプリケーションコードを開発およびテストします。主に [!UICONTROL Cloud Manager] を使用してステータスを確認します。コードをコミットするには、Git リポジトリにアクセスできる必要があります。このロールのユーザーを追加する際に CSE／AMS 担当者に連絡して、Git リポジトリへのアクセス権を付与してください。 |
| カスタマーサクセスエンジニア | AMS のお客様のカスタマーサクセスを全般的にサポートします。CSE 管理が必要なデプロイメントを実行するために、[!UICONTROL Cloud Manager] を操作します。 |
| コンテンツ作成者 | 通常は、[!UICONTROL Cloud Manager] を操作しません。（[!UICONTROL Experience Cloud] からナビゲートした）[!UICONTROL Cloud Manager] プログラムスイッチャーを使用して、AEM にアクセスできます。 |

>[!NOTE]
>
>[!UICONTROL Cloud Manager] Git リポジトリへのアクセスは、担当の CSE によって管理されます。ユーザーの追加や削除については、CSE に連絡してください。
>
>新しく追加したユーザーが Git リポジトリへのアクセス権を必要とする場合は、CSE／AMS 担当者に連絡してアクセス権を付与してもらう必要があります。これらのロールでは、Git リポジトリに自動的にアクセスできるようになるわけではありません。Git リポジトリにアクセスできるユーザーは最大 3 人までです。

## Admin Console を使用したプロファイルの作成 {#using-admin-console-to-create-a-profile}

[!UICONTROL Cloud Manager] のロールは Adobe Admin Console で管理されます。特定のロールメンバーシップは、Admin Console でユーザーを [!UICONTROL Cloud Manager] 製品プロファイルに追加することで提供されます。

Adobe Admin Console でユーザーを [!UICONTROL Cloud Manager] **製品プロファイル**に追加することで、特定のロールメンバーシップを割り当てることができます。Admin Console では、組織全体にわたるアドビ製品の使用権限を一元的に管理できます。Adobe Admin Consoleについて詳しくは、管理コンソールの [マニュアル](https://helpx.adobe.com/enterprise/using/admin-console.html)を参照してください。

>[!NOTE]
>
>Admin Console にアクセスしてチーム（ユーザーとロール）を設定するには、ブラウザーを開き、[https://adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise) にアクセスします。

ロールに基づく適切な権限を [!UICONTROL Cloud Manager] ユーザーに付与するには、顧客の**組織**の管理者が [!UICONTROL AEM Managed Services] 製品コンテキストの下で新しい製品プロファイルを作成する必要があります。

ロールに基づく適切な権限を [!UICONTROL Cloud Manager] ユーザーに与えるには、4 つの [!UICONTROL Cloud Manager] ロールに対応する 4 つの新しい製品プロファイルを管理者が [!UICONTROL AEM Managed Services] 製品コンテキストの下に作成する必要があります。

* ビジネスオーナー
* デプロイメントマネージャー
* デベロッパー
* プログラムマネージャー

以下の図に示すように、これらの製品プロファイルに対して、 [管理コンソール](https://adminconsole.adobe.com/) を [!UICONTROL 使用してユーザー/グループ]を作成または追加できます。

1. Admin Console にログインし、「**新規プロファイル**」をクリックして新しいプロファイルを追加します。

   ![](assets/admin_console_roles-1.png)

1. [!UICONTROL Cloud Manager] の新しいロールを設定するためのフィールドに入力します。

   「**プロファイル名**」と「**表示名**」を入力して、新しいプロファイルを作成します。また、プロファイルの「**権限グループ**」を選択することもできます。

   「**完了**」をクリックして、プロファイル作成手順を完了します。

   >[!NOTE]
   >
   >これらの製品プロファイルを作成する際、**表示名**は、[!UICONTROL Cloud Manager] で定義されている値（以下の表を参照）である必要があります。**プロファイル名**は任意ですが、混乱を避けるために、以下の*推奨プロファイル名*列の値を使用することをお勧めします。それには、製品プロファイルの作成時に「**プロファイル名と同じ**」チェックボックスをオフにし、対応する値を「**表示名**」として指定します。

   | **ロール** | **表示名（必須）** | **推奨プロファイル名** |
   |---|---|---|
   | ビジネスオーナー | CM_BUSINESS_OWNER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - ビジネスオーナーロール |
   | デプロイメントマネージャー | CM_DEPLOYMENT_MANAGER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - デプロイメントマネージャーロール |
   | デベロッパー | CM_DEVELOPER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - デベロッパーロール |
   | プログラムマネージャー | CM_PROGRAM_MANAGER_ROLE_PROFILE | [!UICONTROL Cloud Manager] - プログラムマネージャーロール |

   ![](assets/screen_shot_2018-05-04at171819.png)

1. 製品プロファイルを作成したら、それらの製品プロファイルにユーザー（またはグループ）を追加できます。

   ![](assets/image2018-4-9_15-19-26.png)

   ![](assets/image2018-4-9_15-16-47.png)

