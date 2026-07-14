---
title: 新規プロジェクトウィザードの使用
description: このページでは、ウィザードを使用して AEM アプリケーションプロジェクトを作成する方法を説明します。
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
TQID: https://experienceleague.adobe.com/zoiHL1lNC2XN-T9g0dh3pQyL4Yw3uYgFpHs8d6hkj3M
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: fa6be369b979682cebf68852603725d8754605ab
workflow-type: tm+mt
source-wordcount: 317
ht-degree: 54%

---

# 新規プロジェクトウィザードの使用 {#using-the-wizard}

新しいお客様としてCloud Managerにオンボーディングすると、空のGit リポジトリが提供されます。 Cloud Managerでは、[AEM プロジェクトアーキタイプ ](https://github.com/adobe/aem-project-archetype)に基づいて最小限のAEM プロジェクトを作成するウィザードを利用できます。

**新しいプロジェクト ウィザードを使用するには：**

1. [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) で Cloud Manager にログインし、適切な組織を選択します。

1. まだ作成していない場合は、[プログラムを作成](program-setup.md)します。 プログラムが作成されると、Cloud Managerはリポジトリが設定されていないことを検出します。 その後、**概要**&#x200B;画面に特別なプロンプトカードが表示されます。

   ![プロジェクト CTA を作成](/help/assets/image2018-10-3_14-29-44.png)

1. 「**作成**」をクリックしてウィザードを開始し、重要な値を入力します。

   * **タイトル** - プロジェクトのタイトル。 デフォルトでは、プログラムの名前に設定されます。
   * **新しいブランチ名** - Git リポジトリの最初のブランチ。 デフォルトでは `main` です。

   ![プロジェクト値](/help/assets/screen_shot_2018-10-08at55825am.png)

1. ダイアログボックスには、下部のアイコンをクリックして表示できるセクションがあります。 展開された形式では、ダイアログボックスに AEM プロジェクトアーキタイプのすべての設定パラメーターが表示されます。 これらのパラメーターには、既に指定した&#x200B;**タイトル**&#x200B;に基づいて生成されるデフォルト値が入っており、変更する必要はありません。 ここでは、情報目的でこれらの値について説明します。

   ![詳細なアーキタイプパラメーター](/help/assets/screen_shot_2018-10-08at60032am.png)

1. 「**作成**」をクリックして、アーキタイプを使用してスタータープロジェクトを作成し、名前付き Git ブランチにコミットします。

これで、ベースプロジェクトが作成されました。 これで、パイプラインを設定できます。

## 既存のお客様または移行中のお客様 {#existing-migrating}

現在のAdobe Managed Services（AMS）のお客様または移行中のオンプレミス AEMのお客様の場合は、Gitまたはその他のバージョン管理システムに既にプロジェクトコードがあります。

このような場合は、プロジェクトを Cloud Manager の Git リポジトリに読み込むことができます。
