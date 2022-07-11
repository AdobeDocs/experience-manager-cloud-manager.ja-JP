---
title: ユーザーと役割の追加
description: ユーザーと役割を追加し、Admin Consoleを作成する方法について説明します。
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: b0dbb602253939464ff034941ffbad84b7df77df
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 28%

---


# ユーザーと役割の追加 {#add-users-and-roles}

の多くの機能 [!UICONTROL Cloud Manager] 使用するには特定の権限が必要です。 例えば、特定のユーザーのみがプログラムの主要業績評価指標 (KPI) を設定できます。 これらの権限は、論理的にグループ化されて役割になります。

[!UICONTROL Cloud Manager] では、現在、特定の機能を使用できるかどうかを制御する次の 4 つのユーザー役割を定義しています。

* ビジネスオーナー
* プログラムマネージャー
* デプロイメントマネージャー
* デベロッパー

>[!NOTE]
>
>[!UICONTROL Cloud Manager] を使用するには、Adobe ID と Adobe Managed Services 製品コンテキストが必要です。

## 役割の定義 {#role-definitions}

この表は、ロールの概要を示しています。

| [!UICONTROL Cloud Manager] の役割 | 説明 |
|--- |--- |
| ビジネスオーナー | このユーザーは、KPI の定義、実稼動デプロイメントの承認、および必要に応じて重要な 3 層エラーの上書きを担当します。 |
| プログラムマネージャー | このユーザーは [!UICONTROL Cloud Manager] チームの設定を実行し、ステータスを確認し、KPI を表示し、必要に応じて重大な 3 層エラーを承認できます。 |
| デプロイメントマネージャー | このユーザーは、デプロイメント操作を管理し、 [!UICONTROL Cloud Manager] ステージング環境または実稼動環境のデプロイメントを実行するには、CI/CD パイプラインを編集し、必要に応じて重要な 3 層エラーを承認し、git リポジトリにアクセスできます。 |
| デベロッパー | このユーザーは、主にを使用して、カスタムアプリケーションコードを開発およびテストします [!UICONTROL Cloud Manager] ：デプロイメントステータスを表示し、コードコミットの git リポジトリにアクセスできるようにします。 |
| カスタマーサクセスエンジニア | このユーザーは、通常、AMS の顧客の顧客成功をサポートし、 [!UICONTROL Cloud Manager] CSE 管理が必要なデプロイメントを実行するために。 |
| コンテンツ作成者 | 通常、このユーザーは [!UICONTROL Cloud Manager] しかし、 [!UICONTROL Cloud Manager] プログラムスイッチャーを使用してAEMにアクセスします。 |

>[!NOTE]
>
>Admin Consoleの「開発者」ペルソナは、 [!UICONTROL Cloud Manager].

## Admin Console を使用したプロファイルの作成 {#using-admin-console-to-create-a-profile}

[!UICONTROL Cloud Manager] の役割は、「 」Admin Consoleから管理されます。 特定のロールメンバーシップは、ユーザーを [!UICONTROL Cloud Manager] 製品プロファイル。

Admin Consoleは、組織全体にわたるAdobeの使用権限を一元的に管理する場所です。 Adobe Admin Consoleについて詳しくは、 [Admin Console。](https://helpx.adobe.com/jp/enterprise/using/admin-console.html)

>[!NOTE]
>
>Admin Console にアクセスしてチーム（ユーザーとロール）を設定するには、 [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com).

に適切なロールベースの権限を付与するため [!UICONTROL Cloud Manager] ユーザー、顧客の組織の管理者は、 [!UICONTROL AEM Managed Services] 4 つのそれぞれに対応する製品コンテキスト [!UICONTROL Cloud Manager] 役割：

* ビジネスオーナー
* デプロイメントマネージャー
* デベロッパー
* プログラムマネージャー

Admin Consoleを使用して、これらの製品プロファイルにユーザーやグループを作成または追加できます。

1. Admin Consoleにログインし、 **新しいプロファイル** をクリックして、新しいプロファイルを追加します。

   ![新しいプロファイル](/help/assets/admin_console_roles-1.png)

1. 新しい役割を設定する情報を入力 [!UICONTROL Cloud Manager].

   * **プロファイル名**
   * **表示名**
   * **権限グループ**

1. 「**完了**」をクリックして、プロファイル作成手順を完了します。

製品プロファイルを作成する場合、 **表示名** は、で定義された技術的な値である必要があります [!UICONTROL Cloud Manager] （次の表を参照）。 この **プロファイル名** は何でもかまいませんが、混乱を避けるために、 **推奨プロファイル名** 列。 それには、製品プロファイルの作成時に「**プロファイル名と同じ**」チェックボックスをオフにし、対応する値を「**表示名**」として指定します。

| **役割** | **表示名（必須）** | **推奨プロファイル名** |
|---|---|---|
| ビジネスオーナー | `CM_BUSINESS_OWNER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - ビジネスオーナーの役割 |
| デプロイメントマネージャー | `CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - デプロイメントマネージャーの役割 |
| デベロッパー | `CM_DEVELOPER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - デベロッパーの役割 |
| プログラムマネージャー | `CM_PROGRAM_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] - プログラムマネージャーの役割 |

![新しいプロファイルの作成](/help/assets/screen_shot_2018-05-04at171819.png)

製品プロファイルを作成したら、これらの製品プロファイルにユーザー（またはグループ）を追加できます。

![ユーザーの編集](/help/assets/image2018-4-9_15-19-26.png)

![ユーザーグループ](/help/assets/image2018-4-9_15-16-47.png)
