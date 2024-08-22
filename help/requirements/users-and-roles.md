---
title: ユーザーと役割の追加
description: Admin Consoleを使用して、ユーザーと役割を追加し、プロファイルを作成する方法を説明します。
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '758'
ht-degree: 65%

---


# ユーザーと役割の追加 {#add-users-and-roles}

[!UICONTROL Cloud Manager] の多くの機能には、使用するための特定の権限が必要です。例えば、プログラムの主要業績評価指標（KPI）を設定できるのは、特定のユーザーだけです。これらの権限は、論理的にグループ化されて役割になります。

[!UICONTROL Cloud Manager] は現在、特定の機能を使用できるかどうかを制御する次の 4 つのユーザーロールを定義しています。

* ビジネスオーナー
* プログラムマネージャー
* デプロイメントマネージャー
* デベロッパー

>[!NOTE]
>
>[!UICONTROL Cloud Manager] を使用するには、Adobe ID と Adobe Managed Services 製品コンテキストが必要です。

## 役割の定義 {#role-definitions}

次の表に、Cloud Managerのロールの概要を示します。

| [!UICONTROL Cloud Manager] の役割 | 説明 |
| --- | --- |
| ビジネスオーナー | KPI の定義、実稼動デプロイメントの承認および必要に応じて重大な 3 層エラーの上書きを担当します。 |
| プログラムマネージャー | [!UICONTROL Cloud Manager] を使用して、チームの設定、ステータスの確認、KPI の表示を行い、必要に応じて重大な 3 層エラーの承認も行うことができます。 |
| デプロイメントマネージャー | デプロイメント操作を管理し、[!UICONTROL Cloud Manager] を使用してステージングおよび実稼動デプロイメントを実行、CI/CD パイプラインを編集、必要に応じて重大な 3 層エラーを承認します。 また、Git リポジトリーにもアクセスできます。 |
| デベロッパー | カスタムアプリケーションコードの開発およびテストを行い、主に ]0}Cloud Manager} を使用してデプロイメントステータスを表示し、コードコミットの Git リポジトリにアクセスできます。[!UICONTROL  |
| カスタマーサクセスエンジニア | CSE は、通常、AMS のお客様のカスタマーサクセスをサポートします。 CSE 管理が必要なデプロイメントを実行する目的で ]0}Cloud Manager} を操作します。[!UICONTROL  |
| コンテンツ作成者 | 通常、[!UICONTROL Cloud Managerを操作しませんが ][!UICONTROL Cloud Manager] プログラムスイッチャーを使用してAEMにアクセスすることができます。 |

>[!NOTE]
>
>Admin Console の開発者ペルソナは、[!UICONTROL Cloud Manager] のデベロッパーの役割とは無関係です。

## Admin Consoleを使用したプロファイルの作成 {#using-admin-console-to-create-a-profile}

[!UICONTROL Cloud Manager] の役割は、Admin Console から管理されます。特定の役割のメンバーシップは、Admin Console でユーザーを [!UICONTROL Cloud Manager] 製品プロファイルに追加することで提供されます。

Admin Console では、組織全体にわたるアドビ製品の使用権限を一元的に管理できます。Adobe Admin Consoleについて詳しくは、[Admin Console](https://helpx.adobe.com/jp/enterprise/using/admin-console.html) を参照してください。

管理者は、[!UICONTROL AEM Managed Services] 製品コンテキストの下で新しい製品プロファイルを作成し、[!UICONTROL Cloud Manager] ユーザー（4 つの [!UICONTROL Cloud Manager] の役割に対応）に対する役割ベースの権限を割り当てる必要があります。

* ビジネスオーナー
* デプロイメントマネージャー
* デベロッパー
* プログラムマネージャー

Admin Consoleを使用して、これらの製品プロファイルにユーザーやグループを作成または追加できます。

1. Admin Console（[`https://adminconsole.adobe.com`](https://adminconsole.adobe.com)）にログインします。

1. **概要** タブをクリックし、編集する製品を **製品とサービス** カードでクリックします。 該当する製品がリストにない場合は、「**製品**」タブをクリックして製品を検索し、クリックします。

   ![Admin Console の「概要」タブ](/help/assets/admin-console-overview.png)

1. 「**製品**」タブで、製品プロファイルにユーザー／グループを追加する環境をクリックします。

   ![Admin Console の「製品」タブ](/help/assets/admin-console-product.png)

1. 「**製品プロファイル**」タブで、「**新規プロファイル**」をクリックして新しいプロファイルを追加します。

   ![新しいプロファイル](/help/assets/admin-console-product-profiles.png)

1. [!UICONTROL Cloud Manager] の新しい役割を設定するための情報を入力します。

   * **プロファイル名** - **プロファイル名**&#x200B;は任意の名前を指定できますが、混乱を避けるために、**推奨プロファイル名**&#x200B;列の値を使用することをお勧めします。
   * **表示名** - 「**表示名**」は、[!UICONTROL Cloud Manager] で定義されている技術値（以下の表を参照）にする必要があります。
   * **権限グループ** - プロファイルの権限グループを選択できます（常に使用可能とは限りません）。

   ![新規プロファイルの作成](/help/assets/screen_shot_2018-05-04at171819.png)

   | 役割 | 表示名（必須） | 推奨プロファイル名 |
   |---|---|---|
   | ビジネスオーナー | `CM_BUSINESS_OWNER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - ビジネスオーナーの役割 |
   | デプロイメントマネージャー | `CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - デプロイメントマネージャーの役割 |
   | デベロッパー | `CM_DEVELOPER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - デベロッパーの役割 |
   | プログラムマネージャー | `CM_PROGRAM_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - プログラムマネージャーの役割 |


1. 「**完了**」をクリックして、新しいプロファイルを保存します。

## ユーザーまたはユーザーグループへのプロファイルの割り当て {#assign-profiles}

製品プロファイルを作成したら、それにユーザーまたはユーザーグループを割り当てることができます。

1. Admin Console（[`https://adminconsole.adobe.com`](https://adminconsole.adobe.com)）にログインします。

1. Admin Console で、「**ユーザー**」タブを選択します。

   ![「ユーザー」タブ](/help/assets/admin-console-users.png)

1. 左側のナビゲーションパネルで「**ユーザー**」をクリックして、ユーザーをクリックして変更します。

1. 「**製品**」セクションの省略記号ボタンをクリックし、「**編集**」を選択します。

   ![ユーザーの編集](/help/assets/admin-console-edit-user.png)

1. **製品とユーザーグループの編集**&#x200B;ダイアログボックスで、「+」ボタンをクリックし、ユーザーに割り当てるプロファイルを選択します。

   * ユーザーが役割に既に割り当てられている場合、「+」ボタンは編集ボタン（鉛筆）になりますが、同じように機能します。

   ![製品とユーザーグループの編集](/help/assets/admin-console-edit-products-and-user-groups.png)

1. 「**保存**」をクリックして、プロファイルをユーザーに保存します。

同じ手順を繰り返して、プロファイルをユーザーグループに割り当てますが、「**ユーザー**」タブの左側のナビゲーションパネルから「**ユーザーグループ**」を選択します。ユーザーグループをクリックし、「**割り当てられた製品プロファイル**」タブを選択し、「**製品プロファイルを割り当て**」をクリックしてプロファイルを割り当てます。

![グループへのプロファイルの割り当て](/help/assets/admin-console-edit-user-groups.png)
