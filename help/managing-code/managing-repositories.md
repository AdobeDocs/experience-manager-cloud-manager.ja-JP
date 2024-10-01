---
title: Cloud Managerでのリポジトリの管理
description: Cloud Managerで Git リポジトリを表示、追加、削除する方法について説明します。
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
source-git-commit: ee84c682b6bd2b9144b3f75d544dea33a5ad944b
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 23%

---


# Cloud Managerでのリポジトリの管理 {#cloud-manager-repos}

Cloud Managerで Git リポジトリを表示、追加、削除する方法について説明します。

## 概要 {#overview}

Cloud Managerのリポジトリは、Git を使用してプロジェクトのコードを保存および管理するために使用されます。 追加した *プログラム* ごとに、Adobeが管理するリポジトリが自動的に作成されます。

さらに、Adobeが管理するリポジトリを増やすか、独自のプライベートリポジトリを追加するかを選択できます。 プログラムにリンクされているすべてのリポジトリは、**リポジトリ** ページで表示できます。

Cloud Manager内で作成されたリポジトリは、パイプラインの追加または編集時に選択することもできます。 パイプラインの設定について詳しくは、[CI/CD パイプライン ](/help/overview/ci-cd-pipelines.md) を参照してください。

各パイプラインはプライマリリポジトリまたはブランチにリンクされています。 ただし、[Git サブモジュールのサポート ](/help/managing-code/git-submodules.md) を使用すると、ビルドプロセス中に複数のセカンダリブランチを含めることができます。

## リポジトリーページの表示 {#repositories-window}

**リポジトリ** ページには、選択したリポジトリの詳細が表示されます。 この情報には、使用中のリポジトリのタイプが含まれます。 リポジトリが **リポジトリ** とマークされている場合は、Adobeが管理するAdobeであることを示しています。 **GitHub** というラベルが付いている場合は、管理するプライベート GitHub リポジトリを指します。 さらに、このページには、リポジトリの作成日時や関連付けられたパイプラインなどの詳細が表示されます。

選択したリポジトリーに対してアクションを実行するには、リポジトリーをクリックし、![ 詳細アイコン ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) を使用してドロップダウンメニューを開きます。 Adobeが管理するリポジトリの場合は、**[ブランチを確認/プロジェクトを作成](#check-branches)** できます。

![ リポジトリのアクション ](assets/repository-actions.png)
*リポジトリーページのドロップダウンメニュー。*

ドロップダウンメニューで使用できるその他のアクションには、**[リポジトリー URL をコピー](#copy-url)**、**[表示と更新](#view-update)**、**[削除](#delete)** があります。

**リポジトリーページを表示するには：**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) で Cloud Manager にログインし、適切な組織とプログラムを選択します。

1. **プログラムの概要** ページのサイドメニューで、![ フォルダーアイコン ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg)**リポジトリ** をクリックします。

1. **リポジトリ** ページには、選択したプログラムに関連付けられているすべてのリポジトリが表示されます。

   ![ リポジトリーページ ](assets/repositories.png)
   *Cloud Managerのリポジトリーページ*


## リポジトリを追加 {#adding-repositories}

リポジトリを追加するには、ユーザーが **デプロイメントマネージャー** または **ビジネスオーナー** の役割を持っている必要があります。

**リポジトリ** ページの右上隅付近にある「**リポジトリを追加**」をクリックします

![ リポジトリを追加ダイアログボックス。](assets/repository-add.png)
*「リポジトリを追加」ダイアログボックス*

Cloud Managerでは、Adobeが管理するリポジトリ （**Adobeリポジトリ**）と自己管理するリポジトリ （**プライベートリポジトリ**）の 2 種類のリポジトリがサポートされています。 設定の必須フィールドは、追加するリポジトリーのタイプによって異なります。 詳しくは、以下のトピックを参照してください。

* [Cloud Manager での Adobe リポジトリの追加](/help/managing-code/adobe-repositories.md)
* [Cloud Manager でのプライベートリポジトリの追加](/help/managing-code/private-repositories.md)

特定の企業または IMS 組織のすべてのプログラムで使用できるリポジトリは 300 個までです。

## リポジトリ情報へのアクセス {#repo-info}

**リポジトリ**&#x200B;ウィンドウでリポジトリを表示する際に、ツールバーの「**リポジトリ情報へアクセス**」ボタンをクリックすると、アドビが管理するリポジトリにプログラムでアクセスする方法の詳細を表示できます。

![リポジトリ情報](assets/repository-access-repo-info2.png)

**リポジトリ情報**&#x200B;ウィンドウが開き、詳細が表示されます。リポジトリ情報へのアクセスについて詳しくは、[リポジトリ情報へのアクセス](/help/managing-code/accessing-repositories.md)を参照してください。

## ブランチを確認/ プロジェクトを作成 {#check-branches}

**AEM Cloud Manager** では、**ブランチを確認/プロジェクトを作成** アクションは、リポジトリの現在のステータスに応じて、2 つの目的を果たします。

* リポジトリーを新しく作成する場合、このアクションは、[AEM プロジェクトアーキタイプ ](https://experienceleague.adobe.com/ja/docs/experience-manager-core-components/using/developing/archetype/overview) を使用してサンプルプロジェクトを生成します。
* サンプルプロジェクトが既にリポジトリに作成されている場合、このアクションはリポジトリとそのブランチのステータスを確認し、サンプルプロジェクトが既に存在するかどうかに関するフィードバックを提供します。

  ![ブランチを確認アクション](assets/check-branches.png)

## リポジトリ URL をコピー {#copy-url}

**リポジトリ URL をコピー** アクションは、**リポジトリ** ページで選択したリポジトリの URL をクリップボードにコピーして、他の場所で使用します。

## リポジトリの表示と更新 {#view-update}

**表示と更新** アクションを実行すると、**リポジトリを更新** ダイアログボックスが開き、リポジトリの **名前** と **リポジトリ URL のプレビュー** を表示できます。 さらに、リポジトリの **説明** を更新できます。

![リポジトリ情報の表示と更新](assets/repository-view-update.png)

## リポジトリの削除 {#delete}

**削除**&#x200B;アクションでは、プロジェクトからリポジトリを削除します。リポジトリがパイプラインに関連付けられている場合は、削除できません。

![ リポジトリの削除 ](assets/delete.png)

Cloud Manager でリポジトリを削除すると、そのリポジトリは削除済みとしてマークされ、ユーザーはアクセスできなくなります。ただし、復元の目的でシステム内で維持されます。

同じ名前のリポジトリを削除した後に新しいリポジトリを作成しようとすると、次のエラーメッセージが表示されます。

`An error has occurred while trying to create repository. Contact your CSE or Adobe Support.`

このエラーメッセージが表示された場合は、Adobeサポートにお問い合わせください。 削除したリポジトリの名前を変更したり、新しいリポジトリに対する別の名前を選択したりする際に役立ちます。
