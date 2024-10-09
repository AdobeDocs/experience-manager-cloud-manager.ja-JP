---
title: Cloud Manager での Adobe リポジトリの追加
description: Cloud Manager でアドビが管理するリポジトリを追加する方法について説明します。
exl-id: 24c6ca97-ea70-41b8-b4c7-b8b0f406a57d
source-git-commit: 675568426df0df5890dd8c72bfb53c24a4c5d666
workflow-type: ht
source-wordcount: '230'
ht-degree: 100%

---

# Cloud Manager での Adobe リポジトリの追加 {#adobe-repositories}

Cloud Manager でアドビが管理するリポジトリを追加する方法について説明します。

**リポジトリ**&#x200B;ページを使用すると、アドビが管理するリポジトリを選択したプログラムに簡単に追加できます。

**Cloud Manager に Adobe リポジトリを追加するには：**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) で Cloud Manager にログインし、アドビが管理するリポジトリを追加する適切な組織とプログラムを選択します。

1. **プログラムの概要**&#x200B;ページのサイドメニューで、![フォルダーアイコン](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg)「**リポジトリ**」タブをクリックします。

1. **リポジトリ**&#x200B;ページの右上付近にある「**リポジトリを追加**」をクリックします。

   ![「リポジトリを追加」ボタン](/help/managing-code/assets/repositories-tab.png)

1. **リポジトリを追加**&#x200B;ダイアログボックスで、リポジトリタイプとして「**Adobe リポジトリ**」が選択されていることを確認します。

1. それぞれのテキストフィールドに、次を入力します。

   * **リポジトリ名** - 新しいリポジトリの表現名。
   * **リポジトリ URL のプレビュー** - リポジトリインフラストラクチャは既に配置され、アドビによって完全に統合および管理されているので、URL パスを入力したり、既存のパスを編集したりする必要はありません。
   * **説明（オプション）** - リポジトリの詳細な説明。

   ![リポジトリを追加ダイアログボックス](/help/managing-code/assets/repository-add-adobe.png)

1. 「**保存**」をクリックします。
新しいリポジトリが**リポジトリ**&#x200B;ページのテーブルに表示されます。

これで、[CI/CD パイプライン](/help/overview/ci-cd-pipelines.md)を関連付けることや、[**リポジトリ**&#x200B;ページ](/help/managing-code/managing-repositories.md)内で管理することができます。

>[!TIP]
>
>また、自分で管理する GitHub リポジトリを[プライベートリポジトリ](/help/managing-code/private-repositories.md)として追加することもできます。
