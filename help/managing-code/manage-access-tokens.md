---
title: Cloud Managerでのアクセストークンの管理
description: Adobe Managed Services上のCloud Managerで独自の Git を取り込むために使用されるアクセストークンを表示、編集、削除する方法を説明します。
badge: label="早期導入者" type="Positive" url="/help/release-notes/current.md#access-tokens"
source-git-commit: aa0eff7eb1f6b0cde9b99b7cbbfb3410e0db94a6
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 11%

---


# 外部リポジトリのアクセストークンの管理 {#manage-access-tokens}

Cloud Managerはアクセストークンを使用して、外部 Git プラットフォームにホストされるリポジトリを管理します。 以前は、トークンの有効期限が切れた場合、操作可能な状態を維持するために、関連するリポジトリを再転送する必要がありました。

**アクセストークンの管理** 機能を使用すると、トークンをより効率的に管理できます。 サポートされている外部 Git プロバイダー（GitHub Enterprise、GitLab、Bitbucket、Azure DevOps など）に接続されているトークンを表示、名前変更、削除できます。

[Cloud Managerへの外部リポジトリの追加 ](/help/managing-code/external-repositories.md) も参照してください。

>[!NOTE]
>
>この記事で説明する機能は、早期導入プログラムを通じてのみ使用できます。詳細および早期導入ユーザーとしてサインアップするには、[ アクセストークンの管理 ](/help/release-notes/current.md#access-tokens) を参照してください。

## アクセストークンの表示 {#view-access-tokens}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) で Cloud Manager にログインし、適切な組織を選択します。
1. **[マイプログラム](/help/getting-started/navigation.md#my-programs-console)** コンソールで、独自の Git アクセストークンを管理するプログラムを選択します。
1. サイドメニューの&#x200B;**プログラム**&#x200B;で、![フォルダーアウトラインアイコン](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **リポジトリ**&#x200B;をクリックします。
1. ページの右上隅付近にある「**アクセストークンを管理**」をクリックします。

   「**アクセストークンを管理**」ボタンは、プログラムが「独自の Git を作成」機能を使用している場合にのみ表示されます。

   ![ アクティブなトークンと非アクティブなトークンが 1 つずつ一覧表示されている「アクセストークンの管理」ダイアログボックス ](/help/managing-code/assets/access-tokens-manage.png)

1. **アクセストークンの管理** ダイアログボックスで、
   * すべてのアクセストークンが表示されます。
   * 任意のトークンを **編集** できます。
   * **現在使用中ではない** トークンのみ *削除* できます。 トークンが使用中の場合、「![ アウトラインの削除アイコン ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg) ボタンは無効になります。

## アクセストークンの編集 {#edit-access-tokens}

1. **アクセストークンの管理** ダイアログボックスで、トークン名の右側にある ![ 編集アイコン ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) をクリックします。
1. **アクセストークンを編集** ダイアログボックスの **トークン名** テキストフィールドで、トークン名を更新します。

   アクセストークン秘密鍵自体は変更できません。

   ![ アクセストークンを編集ダイアログボックス ](/help/managing-code/assets/access-tokens-edit.png)

1. トークンが使用中の場合は、関連するすべてのリポジトリーが自動的に再検証されることを警告する通知が表示されます。

1. 「**更新**」をクリックして、変更を保存します。

## アクセストークンの削除 {#delete-access-token}

1. **アクセストークンの管理** ダイアログボックスで、トークン名の右側にある ![ 削除アイコン ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg) をクリックします。

   現在使用中のトークンでは、このアイコンは無効になります（![ アウトラインの削除アイコン ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg)）。

1. **アクセストークンを削除** ダイアログボックスで、「**削除**」をクリックして、トークンを永続的に削除します。