---
title: 新規プロジェクトウィザードの使用
description: このページでは、ウィザードを使用して AEM アプリケーションプロジェクトを作成する方法を説明します
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
source-git-commit: cb791a4f148ba394687b5e824b75fe1386d83c18
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 9%

---


# 新規プロジェクトウィザードの使用 {#using-the-wizard}

新しい顧客として Cloud Manager にオンボーディングされると、空の Git リポジトリが提供されます。 Cloud Manger では、最初に、 [AEM Project Archetype](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype) を出発点として使用します。

ウィザードを使用してAEMプロジェクトを作成するには、次の手順に従います。

1. [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) で Cloud Manager にログインし、適切な組織を選択します。

1. まだの場合は、 [プログラムを作成します。](program-setup.md) プログラムが作成されると、Cloud Manager はリポジトリがまだ設定されていないことを認識し、特別なコールトゥアクションカードが **概要** 画面

   ![プロジェクト CTA を作成](/help/assets/image2018-10-3_14-29-44.png)

1. クリック **作成** をクリックして、ウィザードを起動し、重要な値を指定します。

   * **タイトル**  — これはプロジェクトのタイトルで、デフォルトではプログラム名に設定されます。
   * **新しいブランチ名**  — これは Git リポジトリーの最初のブランチで、デフォルトでは `main`.

   ![プロジェクト値](/help/assets/screen_shot_2018-10-08at55825am.png)

1. ダイアログには、下の方のハンドルをクリックして開くことができるドロワーがあります。 展開されたフォームでは、ダイアログにAEMプロジェクトのアーキタイプのすべての設定パラメーターが表示されます。 これらのパラメーターには、 **タイトル** 指定済みで、変更は必要ありません。 これらは、お客様の情報のためにここで説明されます。

   ![詳細なアーキタイプパラメーター](/help/assets/screen_shot_2018-10-08at60032am.png)

1. クリック **作成** ：アーキタイプを使用してスタータープロジェクトを作成し、名前付き git ブランチにコミットします。

これで、ベースプロジェクトが作成されました。 これで、パイプラインを設定できます。

## 既存のお客様または移行中のお客様 {#existing-migrating}

現在 Adobe Managed Services(AMS) を使用しているユーザー、またはに移行するオンプレミスのAEMユーザーの場合、git または他のバージョン管理システムに既にプロジェクトコードが存在している可能性があります。

このような場合、プロジェクトを Cloud Manager の Git リポジトリに読み込みます。
