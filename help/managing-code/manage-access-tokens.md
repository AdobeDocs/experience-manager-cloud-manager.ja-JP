---
title: Cloud Managerでのアクセストークンの管理
description: Adobe Managed ServicesのCloud Managerで自分のGitを取り込むために使用されるアクセストークンを表示、編集、削除する方法について説明します。
exl-id: 873aad0b-d7c6-4bc3-a70d-bbfdc1e02193
TQID: https://experienceleague.adobe.com/o-kW-Wuj-afgXomU0kErSwYsNZziQFkpvtxvU0PQj3M
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: b52942282fe5f825181123b3839ef155753c5e23
workflow-type: tm+mt
source-wordcount: 382
ht-degree: 75%

---

# 外部リポジトリのアクセストークンを管理する {#manage-access-tokens}

Cloud Managerはアクセストークンを使用して、外部 Git プラットフォームにホストされるリポジトリを管理します。 以前は、トークンの有効期限が切れた場合、操作可能な状態を維持するために、関連するリポジトリを再度オンボーディングする必要がありました。

現在、**アクセストークンの管理**&#x200B;では、トークンをより効率的に管理できます。 サポートされているGit プロバイダー（GitHub Enterprise、GitLab、Bitbucket、Azure DevOps）のトークンを管理できます。

[Cloud Manager での外部リポジトリの追加](/help/managing-code/external-repositories.md)も参照してください。

## アクセストークンを表示する {#view-access-tokens}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)でCloud Managerにログインし、適切な組織を選択します。
1. **[My Programs](/help/getting-started/navigation.md#my-programs-console)** コンソールで、Bring Your Own Git アクセストークンを管理するプログラムを選択します。
1. サイドメニューの&#x200B;**プログラム**&#x200B;で、![フォルダーアウトラインアイコン](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **リポジトリ**&#x200B;をクリックします。
1. ページの右上隅にある「**アクセストークンの管理**」をクリックします。

   「**アクセストークンの管理**」ボタンは、プログラムが Bring Your Own Git 機能を使用している場合にのみ表示されます。

   ![アクティブなトークンと非アクティブなトークンが 1 つずつ一覧表示されているアクセストークンの管理ダイアログボックス](/help/managing-code/assets/access-tokens-manage.png)

1. **アクセストークンの管理**&#x200B;ダイアログボックスで：
   * すべてのアクセストークンがリストされています。
   * 任意のトークンを&#x200B;**編集**&#x200B;できます。
   * **削除**&#x200B;できるのは、*現在使用されていないトークン*&#x200B;のみです。 トークンが使用中の場合、「![アウトラインアイコンの削除](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg)」ボタンは無効になります。

## アクセストークンの編集 {#edit-access-tokens}

1. **アクセストークンの管理**&#x200B;ダイアログボックスで、トークン名の右側にある![編集アイコン](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg)をクリックします。
1. **アクセストークンを編集**&#x200B;ダイアログボックスで、**トークン名**&#x200B;の値や&#x200B;**アクセストークン**&#x200B;の値またはその両方を更新します。

   ![アクセストークンの編集ダイアログボックス](/help/managing-code/assets/access-tokens-edit.png)

1. **アクセストークン**&#x200B;が現在使用中の場合は、更新後に関連するすべてのリポジトリが自動的に再検証されることを警告する通知が表示されます。

1. 「**更新**」をクリックして、変更を保存します。

## アクセストークンの削除 {#delete-access-token}

1. **アクセストークンの管理**&#x200B;ダイアログボックスで、トークン名の右側にある![削除アイコン](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg)をクリックします。

   現在使用中のトークンでは、このアイコンは無効になります（![アウトラインアイコンの削除](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg)）。

1. **アクセストークンを削除**&#x200B;で、**削除**&#x200B;をクリックしてトークンを完全に削除します。
