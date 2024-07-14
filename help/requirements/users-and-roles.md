---
title: ユーザーと役割の追加
description: Admin Consoleを使用して、ユーザーと役割を追加し、プロファイルを作成する方法について説明します。
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: dd96d773ea3e6b9c45886fe41b28d3dd70cb8a61
workflow-type: tm+mt
source-wordcount: '774'
ht-degree: 96%

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

ロールに基づく適切な権限を [!UICONTROL Cloud Manager] ユーザーに与えるには、お客様の組織内の管理者が 4 つの [!UICONTROL Cloud Manager] の役割に対応する新しい製品プロファイルを [!UICONTROL AEM Managed Services] 製品コンテキストの下に作成する必要があります。

* ビジネスオーナー
* デプロイメントマネージャー
* デベロッパー
* プログラムマネージャー

Admin Console を使用して、これらの製品プロファイルにユーザーやグループを作成または追加できます。

1. Admin Console（[`https://adminconsole.adobe.com`](https://adminconsole.adobe.com)）にログインします。

1. 「**概要**」タブをクリックし、変更する製品を&#x200B;**製品とサービス**&#x200B;カードでクリックします。該当する製品がリストにない場合は、「**製品**」タブをクリックして製品を検索し、クリックします。

   ![Admin Console の「概要」タブ](/help/assets/admin-console-overview.png)

1. 「**製品**」タブで、製品プロファイルにユーザー／グループを追加する環境をクリックします。

   ![Admin Console の「製品」タブ](/help/assets/admin-console-product.png)

1. 「**製品プロファイル**」タブで、「**新規プロファイル**」をクリックして新しいプロファイルを追加します。

   ![新しいプロファイル](/help/assets/admin-console-product-profiles.png)

1. [!UICONTROL Cloud Manager] の新しい役割を設定するための情報を入力します。

   * **プロファイル名** - **プロファイル名** は何でも構いません、混乱を避けるために、**推奨プロファイル名** 列の値を使用することをお勧めします。
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

1. 左側のナビゲーションパネルで「**ユーザー**」をクリックしたあと、ユーザーをクリックして変更します。

1. 「**製品**」セクションの省略記号ボタンをクリックし、「**編集**」を選択します。

   ![ユーザーの編集](/help/assets/admin-console-edit-user.png)

1. **製品とユーザーグループの編集**&#x200B;ダイアログで、「+」ボタンをクリックし、ユーザーに割り当てるプロファイルを選択します。

   * ユーザーが役割に既に割り当てられている場合、「+」ボタンは編集ボタン（鉛筆）になりますが、同じように機能します。

   ![製品とユーザーグループの編集](/help/assets/admin-console-edit-products-and-user-groups.png)

1. 「**保存**」をクリックして、プロファイルをユーザーに保存します。

同じ手順を繰り返して、プロファイルをユーザーグループに割り当てますが、「**ユーザー**」タブの左側のナビゲーションパネルから「**ユーザーグループ**」を選択します。ユーザーグループをクリックし、「**製品プロファイル**」タブを選択し、「**製品プロファイルを割り当て**」をクリックしてプロファイルを割り当てます。

![グループへのプロファイルの割り当て](/help/assets/admin-console-edit-user-groups.png)
