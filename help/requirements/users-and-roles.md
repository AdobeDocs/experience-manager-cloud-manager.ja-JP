---
title: ユーザーと役割の追加
description: Admin Consoleを使用して、ユーザーと役割を追加し、プロファイルを作成する方法について説明します。
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: b0dbb602253939464ff034941ffbad84b7df77df
workflow-type: ht
source-wordcount: '581'
ht-degree: 100%

---


# ユーザーと役割の追加 {#add-users-and-roles}

[!UICONTROL Cloud Manager] の多くの機能には、使用するための特定の権限が必要です。例えば、プログラムの主要業績評価指標（KPI）を設定できるのは、特定のユーザーだけです。これらの権限は、論理的にグループ化されて役割になります。

[!UICONTROL Cloud Manager] では、現在、特定の機能を使用できるかどうかを制御する次の 4 つのユーザー役割を定義しています。

* ビジネスオーナー
* プログラムマネージャー
* デプロイメントマネージャー
* デベロッパー

>[!NOTE]
>
>[!UICONTROL Cloud Manager] を使用するには、Adobe ID と Adobe Managed Services 製品コンテキストが必要です。

## 役割の定義 {#role-definitions}

この表は、役割の概要を示しています。

| [!UICONTROL Cloud Manager] の役割 | 説明 |
|--- |--- |
| ビジネスオーナー | このユーザーは、KPI の定義、実稼動デプロイメントの承認および必要に応じて重要な 3 層エラーの上書きを担当します。 |
| プログラムマネージャー | このユーザーは [!UICONTROL Cloud Manager] を使用して、チームの設定を実行、ステータスを確認、KPI を表示し、必要に応じて重大な 3 層エラーを承認できます。 |
| デプロイメントマネージャー | このユーザーは、デプロイメント操作を管理、[!UICONTROL Cloud Manager] を使用してステージング環境または実稼動環境のデプロイメントを実行、CI／CD パイプラインを編集、必要に応じて重要な 3 層エラーを承認、Git リポジトリにアクセスできます。 |
| デベロッパー | このユーザーは、カスタムアプリケーションコードの開発およびテストを担当し、主に [!UICONTROL Cloud Manager] を使用してデプロイメントステータスを表示し、コードコミットの Git リポジトリにアクセスできます。 |
| カスタマーサクセスエンジニア | このユーザーは、通常、AMS 顧客のカスタマーサクセスをサポートし、CSE 管理が必要なデプロイメントを実行する目的で [!UICONTROL Cloud Manager] を使用します。 |
| コンテンツ作成者 | このユーザーは、通常、[!UICONTROL Cloud Manager] を使用しませんが、[!UICONTROL Cloud Manager] プログラムスイッチャーを使用して AEM にアクセスすることができます。 |

>[!NOTE]
>
>Admin Console の開発者ペルソナは、[!UICONTROL Cloud Manager] のデベロッパーの役割とは無関係です。

## Admin Console を使用したプロファイルの作成 {#using-admin-console-to-create-a-profile}

[!UICONTROL Cloud Manager] の役割は、Admin Console から管理されます。特定の役割のメンバーシップは、Admin Console でユーザーを [!UICONTROL Cloud Manager] 製品プロファイルに追加することで提供されます。

Admin Console では、組織全体にわたるアドビ製品の使用権限を一元的に管理できます。Adobe Admin Console について詳しくは、[Admin Console](https://helpx.adobe.com/jp/enterprise/using/admin-console.html) のドキュメントを参照してください。

>[!NOTE]
>
>Admin Console にアクセスしてチーム（ユーザーと役割）を設定するには、[`https://adminconsole.adobe.com`](https://adminconsole.adobe.com) を参照してください。

ロールに基づく適切な権限を [!UICONTROL Cloud Manager] ユーザーに与えるには、お客様の組織内の管理者が 4 つの [!UICONTROL Cloud Manager] の役割に対応する新しい製品プロファイルを [!UICONTROL AEM Managed Services] 製品コンテキストの下に作成する必要があります。

* ビジネスオーナー
* デプロイメントマネージャー
* デベロッパー
* プログラムマネージャー

Admin Console を使用して、これらの製品プロファイルにユーザーやグループを作成または追加できます。

1. Admin Console にログインし、「**新規プロファイル**」をクリックして新しいプロファイルを追加します。

   ![新しいプロファイル](/help/assets/admin_console_roles-1.png)

1. [!UICONTROL Cloud Manager] の新しい役割を設定するための情報を入力します。

   * **プロファイル名**
   * **表示名**
   * **権限グループ**

1. 「**完了**」をクリックして、プロファイル作成手順を完了します。

これらの製品プロファイルを作成する際、**表示名**&#x200B;は、[!UICONTROL Cloud Manager] で定義されている技術値（以下の表を参照）である必要があります。**プロファイル名**&#x200B;は任意の名前にすることができますが、混乱を避けるために、**推奨されるプロファイル名**&#x200B;列の値を使用することをお勧めします。それには、製品プロファイルの作成時に「**プロファイル名と同じ**」チェックボックスをオフにし、対応する値を「**表示名**」として指定します。

| **役割** | **表示名（必須）** | **推奨プロファイル名** |
|---|---|---|
| ビジネスオーナー | `CM_BUSINESS_OWNER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - ビジネスオーナーの役割 |
| デプロイメントマネージャー | `CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - デプロイメントマネージャーの役割 |
| デベロッパー | `CM_DEVELOPER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - デベロッパーの役割 |
| プログラムマネージャー | `CM_PROGRAM_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - プログラムマネージャーの役割 |

![新規プロファイルの作成](/help/assets/screen_shot_2018-05-04at171819.png)

製品プロファイルを作成したら、それらの製品プロファイルにユーザー（またはグループ）を追加できます。

![ユーザーの編集](/help/assets/image2018-4-9_15-19-26.png)

![ユーザーグループ](/help/assets/image2018-4-9_15-16-47.png)
