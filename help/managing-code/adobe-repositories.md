---
title: Cloud Manager での Adobe リポジトリの追加
description: Cloud Manager でアドビが管理するリポジトリを追加する方法について説明します。
exl-id: 24c6ca97-ea70-41b8-b4c7-b8b0f406a57d
TQID: https://experienceleague.adobe.com/LBI6V07enOlxe8yh-XwlkL-mdMWR0MJyKi1gUQtjtK4
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 036302d4861b59e783ac731da12078be59cdc5c4
workflow-type: tm+mt
source-wordcount: 225
ht-degree: 69%

---

# Cloud Manager での Adobe リポジトリの追加 {#adobe-repositories}

Cloud Manager でアドビが管理するリポジトリを追加する方法について説明します。

**リポジトリ** ページでは、選択したプログラムにAdobeで管理されているリポジトリを追加できます。

**Cloud Manager に Adobe リポジトリを追加するには：**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) で Cloud Manager にログインし、アドビが管理するリポジトリを追加する適切な組織とプログラムを選択します。

1. **プログラムの概要** ページのサイドメニューで、![&#x200B; フォルダーアイコン &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **リポジトリ** タブをクリックします。

1. **リポジトリ**&#x200B;ページの右上付近にある「**リポジトリを追加**」をクリックします。

   ![「リポジトリを追加」ボタン](/help/managing-code/assets/repositories-tab.png)

1. **リポジトリを追加**&#x200B;ダイアログボックスで、リポジトリタイプとして「**Adobe リポジトリ**」が選択されていることを確認します。

1. それぞれのテキストフィールドに、次を入力します。

   * **リポジトリ名** – 新しいリポジトリのわかりやすい名前。
   * **リポジトリ URL プレビュー** - リポジトリインフラストラクチャが既にAdobeによって設定、統合、管理されているため、URL パスを入力したり、既存のパスを編集したりする必要はありません。
   * **説明（オプション）** - リポジトリの詳細な説明。

   ![リポジトリを追加ダイアログボックス](/help/managing-code/assets/repository-add-adobe.png)

1. **保存**&#x200B;をクリックします。
新しいリポジトリは、**リポジトリ** ページのテーブルに表示されます。

これで、[CI/CD パイプライン](/help/overview/ci-cd-pipelines.md)を関連付けることや、[**リポジトリ**&#x200B;ページ](/help/managing-code/managing-repositories.md)内で管理することができます。

>[!TIP]
>
>また、自分で管理する GitHub リポジトリを[プライベートリポジトリ](/help/managing-code/private-repositories.md)として追加することもできます。
