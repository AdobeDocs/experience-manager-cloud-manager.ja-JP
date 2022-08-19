---
title: 新規プロジェクトウィザードの使用
description: このページでは、ウィザードを使用して AEM アプリケーションプロジェクトを作成する方法を説明します
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
source-git-commit: cb791a4f148ba394687b5e824b75fe1386d83c18
workflow-type: ht
source-wordcount: '330'
ht-degree: 100%

---


# 新規プロジェクトウィザードの使用 {#using-the-wizard}

新しい顧客として Cloud Manager にオンボーディングされると、空の Git リポジトリが提供されます。 最初に、Cloud Manger は、出発点として [AEM プロジェクトアーキタイプ](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype)に基づいて最小限の AEM プロジェクトを作成するためのウィザードを提供します。

ウィザードを使用して AEM プロジェクトを作成するには、次の手順に従います。

1. [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) で Cloud Manager にログインし、適切な組織を選択します。

1. まだ作成していない場合は、[プログラムを作成します。](program-setup.md) プログラムを作成すると、Cloud Manager はリポジトリがまだ設定されていないことを認識し、特別なコールトゥアクションカードが&#x200B;**概要**&#x200B;画面に表示されます。

   ![プロジェクト CTA を作成](/help/assets/image2018-10-3_14-29-44.png)

1. 「**作成**」をクリックしてウィザードを開始し、重要な値を入力します。

   * **タイトル** - これはプロジェクトのタイトルで、デフォルトではプログラム名に設定されます。
   * **新しいブランチ名** - これは Git リポジトリの最初のブランチで、デフォルトでは `main` になります。

   ![プロジェクト値](/help/assets/screen_shot_2018-10-08at55825am.png)

1. ダイアログにはドロワーがあり、下部にあるハンドルをクリックすると開くことができます。展開された形式では、ダイアログに AEM プロジェクトアーキタイプのすべての設定パラメーターが表示されます。これらのパラメーターには、既に指定した&#x200B;**タイトル**&#x200B;に基づいて生成されるデフォルト値が入っており、変更する必要はありません。ここでは、情報目的でこれらの値について説明します。

   ![詳細なアーキタイプパラメーター](/help/assets/screen_shot_2018-10-08at60032am.png)

1. 「**作成**」をクリックして、アーキタイプを使用してスタータープロジェクトを作成し、名前付き Git ブランチにコミットします。

これで、ベースプロジェクトが作成されました。これで、パイプラインを設定できます。

## 既存のお客様または移行中のお客様 {#existing-migrating}

現在 Adobe Managed Services (AMS) を使用しているお客様、または移行中のオンプレミス AEM のお客様の場合、Git または他のバージョン管理システムに既にプロジェクトコードが存在している可能性があります。

このような場合、プロジェクトを Cloud Manager の Git リポジトリに読み込みます。