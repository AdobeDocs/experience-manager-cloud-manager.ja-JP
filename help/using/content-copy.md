---
title: コンテンツのコピーによる環境の整合性の確保
description: Cloud Managerのコンテンツコピーを使用すると、可変コンテンツをオンデマンドでAdobeのManaged ServicesでホストされているAdobe Experience Manager 6.x 実稼動環境から下位のテスト用の環境にコピーできます。
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: 228006b424504306e916014bbe8543dc41ba43b5
workflow-type: tm+mt
source-wordcount: '1312'
ht-degree: 34%

---


# コンテンツのコピーによる環境の整合性の確保 {#content-copy}

Cloud Managerのコンテンツコピーを使用すると、可変コンテンツをオンデマンドでAdobeのManaged ServicesでホストされているAdobe Experience Manager 6.x 実稼動環境から下位のテスト用の環境にコピーできます。

## コンテンツコピーについて {#introduction}

現在の実際のデータは、テスト、検証、ユーザー受け入れの目的で役立ちます。コンテンツコピーを使用すると、AMS でホストされている実稼動AEM 6.x 環境からステージングまたは開発環境にコンテンツをコピーできます。 このワークフローは、様々なテストシナリオをサポートします。

コンテンツセットは、コピーするコンテンツを定義します。コンテンツセットには、コピーする可変コンテンツを含む JCR パスのリストが含まれます。コンテンツがソース環境からターゲット環境に移動します。すべてが、同じ Cloud Manager プログラム内で行われます。

コンテンツセットでは、次のパスを使用できます。

```text
/content/**
/conf/**
/etc/**
/var/workflow/models/**
/var/commerce/**
```

コンテンツをコピーする場合、ソース環境が真のソースです。

* 宛先環境でコンテンツを編集する場合、パスが一致すると、ソースのコンテンツによって上書きされます。
* パスが異なる場合、ソースのコンテンツは宛先のコンテンツと結合されます。

## 権限 {#permissions}

コンテンツのコピー機能を使用するには、ソース環境とターゲット環境で、ユーザーを **デプロイメントマネージャー** の役割に割り当てる必要があります。

## コンテンツセットの作成 {#create-content-set}

コンテンツをコピーする前に、コンテンツセットを定義する必要があります。定義すると、コンテンツセットを再使用してコンテンツをコピーできます。コンテンツセットを作成するには、次の手順に従います。

**コンテンツセットを作成するには：**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) で Cloud Manager にログインし、適切な組織とプログラムを選択します。

1. ページの左上隅にある ![ メニューアイコンを表示 ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) をクリックして、左側のメニューを開きます。

1. 左側のメニューの「**サービス**」ページで、「![ コンテンツセット **](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) のボックスアイコン** をクリックします。

1. ページの右上隅付近にある「**コンテンツセットを追加**」をクリックします。

   ![コンテンツセット](/help/assets/content-sets.png)

1. **`Add Content Set`** ダイアログボックスの「**詳細**」タブで、「**名前**」フィールドと「**説明**」フィールドにコンテンツセットの名前と説明（オプション）を入力し、「**続行**」をクリックします。

   ![コンテンツセットの詳細](/help/assets/add-content-set-details.png)

1. 「**コンテンツパス**」タブの「**パス**」テキストフィールドに、変更が可能で、コンテンツセットに含める必要のあるコンテンツへのパスを指定します。

   `/content`、`/conf`、`/etc`、`/var/workflow/models` または `/var/commerce` で始まるパスのみが包含の対象となります。

1. **![フォルダー追加アイコン ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderAdd_18_N.svg) パスを追加** をクリックして、コンテンツセットにパスを追加（または含める）します。

1. （オプション）必要に応じて、前の 2 つの手順を繰り返して追加パス（最大 50）を追加します。 それ以外の場合は、次の手順に進みます。

   ![コンテンツセットへのパスの追加](/help/assets/add-content-set-paths.png)

1. （オプション）コンテンツセットを絞り込むには、オプションで、除外する含まれるコンテンツパス内のサブパスを指定できます。

   1. 制限するコンテンツパスの組み込みの右側にある ![ フォルダー削除アイコン ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg) をクリックします。
   1. テキストフィールドに、ダイアログボックスに表示されるルートパスへの相対パスを入力します。
   1. ![ フォルダー削除アイコン ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg)**除外パス** をクリックします。
   1. 必要に応じて、手順 1 ～ 3 を繰り返します。 上記の手順で除外パスをさらに追加します。制限はありません。 それ以外の場合は、次の手順に進みます。

   ![パスの除外](/help/assets/add-content-set-paths-excluded.png)

1. （オプション）次のいずれかの操作を行います。

   1. 除外されたサブパスの右側にある ![ クロスサイズ 500 アイコン ](https://spectrum.adobe.com/static/icons/ui_18/CrossSize500.svg) をクリックして削除します。
   1. 含まれているコンテンツパスの右側にある ![ 詳細アイコン ](https://spectrum.adobe.com/static/icons/ui_18/More.svg) をクリックし、**編集** または **削除** をクリックします。

   ![パスリストの編集](/help/assets/add-content-set-excluded-paths.png)

1. 「**作成**」をクリックします。コンテンツセットを使用して、環境間でコンテンツをコピーできるようになりました。

## コンテンツセットの編集または削除 {#edit-content-set}

コンテンツセットを編集する際、除外されたサブパスを表示するには、設定されたパスの展開が必要になる場合があります。

**コンテンツセットを編集または削除するには：**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) で Cloud Manager にログインし、適切な組織とプログラムを選択します。

1. ページの左上隅にある ![ メニューアイコンを表示 ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) をクリックして、左側のメニューを開きます。

1. 左側のメニューの **サービス** で、「![ コンテンツセット **](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) のボックスアイコン** をクリックします。

1. **コンテンツセット** ページのテーブルで、含まれているコンテンツパスの右側にある ![ 詳細アイコン ](https://spectrum.adobe.com/static/icons/ui_18/More.svg) をクリックし、**編集** または **削除** をクリックします。

![コンテンツセットの編集](/help/assets/edit-content-set.png)


## コンテンツをコピー {#copy-content}

コンテンツセットを作成したら、それを使用してコンテンツをコピーできます。

次のいずれかの条件に当てはまる場合、環境を選択できない可能性があります。

* ユーザーに必要な権限がありません。
* パイプラインまたはコンテンツのコピー操作が環境で現在実行中です。

**コンテンツをコピーするには：**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) で Cloud Manager にログインし、適切な組織とプログラムを選択します。

1. ページの左上隅にある ![ メニューアイコンを表示 ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) をクリックして、左側のメニューを開きます。

1. 左側のメニューの **サービス** で、「![ コンテンツセット **](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) のボックスアイコン** をクリックします。

1. **コンテンツセット** ページのテーブルで、コピーする含まれているコンテンツパスの右側の ![ 詳細アイコン ](https://spectrum.adobe.com/static/icons/ui_18/More.svg) をクリックしてから、「**コンテンツをコピー** をクリックします。

   ![コンテンツのコピー](/help/assets/copy-content.png)

1. **コンテンツをコピー** ダイアログボックスで、コンテンツのコピーアクション用の **Source** 環境と **宛先** 環境を選択します。

   * 宛先環境の地域は、ソース環境の地域のサブセットである必要があります。
   * コンテンツのコピーアクションを実行する前に、互換性の問題が確認されます。 **宛先** 環境を選択すると、システムによってソース環境と宛先環境が自動的に検証されます。 検証に失敗すると、プロセスが停止し、失敗の理由を説明するエラーメッセージがダイアログボックスに表示されます。

     ![コンテンツのコピー](/help/assets/copying-content.png)

1. （オプション）次のいずれかの操作をおこないます。

   1. 宛先環境で除外されたパスを *保持* するには、**`Do not delete exclude paths from destination`** のチェックボックスをオンにします。 この設定では、コンテンツセットで指定された除外パスはそのまま維持されます。
   1. 宛先環境で除外されたパスを *削除* するには、「」のチェックを外 **`Do not delete exclude paths from destination`** ます。 この設定により、コンテンツセットで指定された除外パスが削除されます。
   1. ソース環境から宛先の環境にパスのバージョン履歴をコピーするには、「**バージョンをコピー**」をオンにします。 バージョン履歴がコピーされる *ない* 場合、コンテンツのコピープロセスは大幅に高速です。



1. 「**コピー**」をクリックします。コピープロセスのステータスは、選択したコンテンツセットのコンソールに反映されます。

## コンテンツのコピーステータスの監視 {#copy-activity}

コピープロセスのステータスは、**コンテンツをコピーアクティビティ**&#x200B;ページで監視できます。

**コンテンツのコピーステータスを監視するには：**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) で Cloud Manager にログインし、適切な組織とプログラムを選択します。

1. ページの左上隅にある ![ メニューアイコンを表示 ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) をクリックして、左側のメニューを開きます。

1. 左側のメニューの **サービス** で、![ 履歴アイコン ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_History_18_N.svg) **コンテンツをコピーアクティビティ** をクリックします。

   ![コンテンツをコピーアクティビティ](/help/assets/copy-content-activity.png)

   コンテンツのコピープロセスには、次のいずれかのステータスがあります。

   | ステータス | 説明 |
   | --- | --- |
   | 処理中 | コンテンツのコピー操作が進行中です。 |
   | 完了 | コンテンツのコピー操作が正常に完了しました。 |
   | 失敗 | コンテンツのコピー操作に失敗しました。 |


## コンテンツコピーの制限 {#limitations}

* 下位環境から上位環境へのコンテンツのコピーは実行できません。
* コンテンツのコピーは、同じ層内でのみ実行できます。つまり、オーサーとオーサー間またはパブリッシュとパブリッシュ間である場合は実行できます。
* プログラム間および地域間でのコンテンツのコピーはできません。
* クラウドデータストアベースのトポロジのコンテンツのコピーは、ソース環境と宛先環境が同じクラウドプロバイダーおよび同じ地域上にある場合にのみ実行できます。
* 同じ環境でコンテンツのコピー操作を同時に実行することはできません。
* CI/CD パイプラインなどの宛先またはソース環境でアクティブな操作が実行されている場合、コンテンツのコピーは実行できません。
* コンテンツのコピーは、ソース上の移動されたコンテンツや削除されたコンテンツを追跡できないので、クローンまたはミラーリングツールとして使用しないでください。
* コンテンツコピーは、開始後に一時停止したりキャンセルしたりすることはできません。
* コンテンツコピーでは、上位の環境から選択した下位の環境にアセットとDynamic Media メタデータを複製します。 コピーしたアセットは、それぞれの Dynamic Media 設定を使用するために、下位環境で [DAM プロセスアセットワークフロー](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/assets/using/assets-workflow)を使用して再処理する必要があります。
* [2 GB を超えるアセットサイズが有効になっている Dynamic Media 設定](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb)はサポートされていません。
* ターゲット環境の地域は、ソース環境の地域と同じにするか、そのサブセットにする必要があります。

## 既知の問題 {#known-issues}

{{content-copy-known-issues}}
