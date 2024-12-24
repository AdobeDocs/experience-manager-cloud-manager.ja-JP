---
title: 環境の一貫性を目的とするコンテンツコピー
description: Cloud Manager のコンテンツコピーを使用すると、可変コンテンツをオンデマンドで Adobe Managed Services でホストされている Adobe Experience Manager 6.x 実稼動環境から下位の環境にテスト目的でコピーできます。
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: e3a656605ac59ca1f95985426932fddf2b53b7c9
workflow-type: ht
source-wordcount: '1321'
ht-degree: 100%

---


# 環境の一貫性を目的とするコンテンツコピー {#content-copy}

Cloud Manager のコンテンツコピーを使用すると、可変コンテンツをオンデマンドで Adobe Managed Services でホストされている Adobe Experience Manager 6.x 実稼動環境から下位の環境にテスト目的でコピーできます。

## コンテンツコピーについて {#introduction}

現在の実際のデータは、テスト、検証、ユーザー受け入れの目的で役立ちます。コンテンツコピーを使用すると、AMS でホストされている AEM 6.x 実稼動環境からステージング環境または開発環境にコンテンツをコピーできます。このワークフローは、様々なテストシナリオをサポートします。

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

宛先環境でコンテンツを編集する場合、パスが一致すると、ソースのコンテンツによって上書きされます。

パスが異なる場合、ソースのコンテンツは宛先のコンテンツと結合されます。

### 権限 {#permissions}

コンテンツコピー機能を使用するには、ソース環境とターゲット環境で、ユーザーを&#x200B;**デプロイメントマネージャー**&#x200B;の役割に割り当てる必要があります。

## コンテンツセットの作成 {#create-content-set}

コンテンツをコピーする前に、コンテンツセットを定義する必要があります。定義すると、コンテンツセットを再使用してコンテンツをコピーできます。コンテンツセットを作成するには、次の手順に従います。

**コンテンツセットを作成するには：**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) で Cloud Manager にログインし、適切な組織とプログラムを選択します。

1. ページの左上隅にある ![メニューを表示アイコン](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) をクリックして、左側のサイドメニューを開きます。

1. 左側のサイドメニューの&#x200B;**サービス**&#x200B;ページで、![ボックスアイコン](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg)「**コンテンツセット**」をクリックします。

1. ページの右上隅にある「**コンテンツセットを追加**」をクリックします。

   ![コンテンツセット](/help/assets/content-sets.png)

1. **`Add Content Set`** ダイアログボックスの「**詳細**」タブにある「**名前**」フィールドと「**説明**」フィールドに、コンテンツセットの名前とオプションの説明を入力し、「**続行**」をクリックします。

   ![コンテンツセットの詳細](/help/assets/add-content-set-details.png)

1. 「**コンテンツパス**」タブの「**パス**」テキストフィールドで、変更可能でコンテンツセットに含める必要があるコンテンツへのパスを指定します。

   `/content`、`/conf`、`/etc`、`/var/workflow/models` または `/var/commerce` で始まるパスのみが含める対象となります。

1. **![フォルダーの追加アイコン](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderAdd_18_N.svg)「パスを追加**」をクリックして、コンテンツセットにパスを追加します（または含めます）。

1. （オプション）必要に応じて、前の 2 つの手順を繰り返して、追加パス（最大 50）を追加します。それ以外の場合は、次の手順に進みます。

   ![コンテンツセットへのパスの追加](/help/assets/add-content-set-paths.png)

1. （オプション）コンテンツセットを絞り込むには、オプションで、含まれるコンテンツパス内で除外するサブパスを指定できます。

   1. 制限対象にする含まれるコンテンツパスの右側にある ![フォルダーの削除アイコン](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg) をクリックします。
   1. テキストフィールドに、ダイアログボックスに表示されるルートパスへの相対パスを入力します。
   1. ![フォルダーの削除アイコン](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg)「**除外パス**」をクリックします。
   1. 必要に応じて、上記の手順 i. ～ iii. を繰り返して除外パスをさらに追加します。制限はありません。それ以外の場合は、次の手順に進みます。

   ![パスの除外](/help/assets/add-content-set-paths-excluded.png)

1. （オプション）次のいずれかの操作を行います。

   1. 除外されたサブパスの右側にある ![クロスサイズ 500 アイコン](https://spectrum.adobe.com/static/icons/ui_18/CrossSize500.svg) をクリックして削除します。
   1. 含まれるコンテンツパスの右側にある ![その他アイコン](https://spectrum.adobe.com/static/icons/ui_18/More.svg) をクリックし、「**編集**」または「**削除**」をクリックします。

   ![パスリストの編集](/help/assets/add-content-set-excluded-paths.png)

1. 「**作成**」をクリックします。コンテンツセットを使用して環境間でコンテンツをコピーできるようになりました。

## コンテンツセットの編集または削除 {#edit-content-set}

コンテンツセットを編集する際、除外されたサブパスを表示するには、設定されたパスの展開が必要になる場合があります。

**コンテンツセットを編集または削除するには：**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) で Cloud Manager にログインし、適切な組織とプログラムを選択します。

1. ページの左上隅にある ![メニューを表示アイコン](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) をクリックして、左側のサイドメニューを開きます。

1. 左側のサイドメニューの&#x200B;**サービス**&#x200B;で、![ボックスアイコン](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg)「**コンテンツセット**」をクリックします。

1. **コンテンツセット**&#x200B;ページのテーブルで、含まれるコンテンツパスの右側にある ![その他アイコン](https://spectrum.adobe.com/static/icons/ui_18/More.svg) をクリックし、「**編集**」または「**削除**」をクリックします。

![コンテンツセットの編集](/help/assets/edit-content-set.png)

## コンテンツのコピー {#copy-content}

コンテンツセットを作成した後、それを使用してコンテンツをコピーできます。

次のいずれかの条件に該当する場合、環境を選択できないことがあります。

* ユーザーに必要な権限がない。
* パイプラインまたはコンテンツのコピー操作が環境で現在実行中である。

**コンテンツをコピーするには：**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) で Cloud Manager にログインし、適切な組織とプログラムを選択します。

1. ページの左上隅にある ![メニューを表示アイコン](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) をクリックして、左側のサイドメニューを開きます。

1. 左側のサイドメニューの&#x200B;**サービス**&#x200B;で、![ボックスアイコン](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg)「**コンテンツセット**」をクリックします。

1. **コンテンツセット**&#x200B;ページのテーブルで、コピー対象の含まれるコンテンツパスの右側にある ![その他アイコン](https://spectrum.adobe.com/static/icons/ui_18/More.svg) をクリックし、「**コンテンツをコピー**」をクリックします。

   ![コンテンツのコピー](/help/assets/copy-content.png)

1. **コンテンツをコピー**&#x200B;ダイアログボックスで、コンテンツコピーアクションの&#x200B;**ソース**&#x200B;環境と&#x200B;**宛先**&#x200B;環境を選択します。

   * 宛先環境の地域は、ソース環境の地域のサブセットにする必要があります。
   * コンテンツコピーアクションを実行する前に、互換性の問題が確認されます。**宛先**&#x200B;環境を選択すると、システムによってソース環境と宛先環境が自動的に検証されます。検証に失敗すると、プロセスが停止し、失敗の理由を説明するエラーメッセージがダイアログボックスに表示されます。

     ![コンテンツのコピー](/help/assets/copying-content.png)

1. （オプション）次のいずれかの操作を行います。

   1. 宛先環境で除外されたパスを&#x200B;*保持*&#x200B;するには、「**`Do not delete exclude paths from destination`**」をオンにします。この設定では、コンテンツセットで指定した除外パスはそのまま維持されます。
   1. 宛先環境で除外されたパスを&#x200B;*削除*&#x200B;するには、「**`Do not delete exclude paths from destination`**」をオフにします。この設定では、コンテンツセットで指定した除外パスが削除されます。
   1. ソース環境から宛先環境にパスのバージョン履歴をコピーするには、「**バージョンをコピー**」をオンにします。バージョン履歴をコピー&#x200B;*しない*&#x200B;場合、コンテンツのコピープロセスは大幅に高速になります。

1. 「**コピー**」をクリックします。コピープロセスのステータスは、選択したコンテンツセットのコンソールに反映されます。

## コンテンツコピーのステータスの確認 {#copy-activity}

コピープロセスのステータスは、**コンテンツをコピーアクティビティ**&#x200B;ページで監視できます。

**コンテンツコピーのステータスを確認するには：**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) で Cloud Manager にログインし、適切な組織とプログラムを選択します。

1. ページの左上隅にある ![メニューを表示アイコン](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) をクリックして、左側のサイドメニューを開きます。

1. 左側のサイドメニューの&#x200B;**サービス**&#x200B;で、![履歴アイコン](https://spectrum.adobe.com/static/icons/workflow_18/Smock_History_18_N.svg)「**コンテンツをコピーアクティビティ**」をクリックします。

   ![コンテンツをコピーアクティビティ](/help/assets/copy-content-activity.png)

   コンテンツコピープロセスは以下のいずれかになります。

   | ステータス | 説明 |
   | --- | --- |
   | 処理中 | コンテンツコピープロセスが進行中です。 |
   | 完了 | コンテンツコピープロセスが正常に完了しました。 |
   | 失敗 | コンテンツコピープロセスに失敗しました。 |

## コンテンツコピーの制限事項 {#limitations}

* 下位環境から上位環境へのコンテンツのコピーは実行できません。
* コンテンツのコピーは、同じ層内でのみ実行できます。つまり、オーサーとオーサー間またはパブリッシュとパブリッシュ間である場合は実行できます。
* プログラム間および地域間でのコンテンツのコピーはできません。
* クラウドデータストアベースのトポロジのコンテンツのコピーは、ソース環境と宛先環境が同じクラウドプロバイダーおよび同じ地域上にある場合にのみ実行できます。
* 同じ環境でコンテンツのコピー操作を同時に実行することはできません。
* CI/CD パイプラインなどの宛先またはソース環境でアクティブな操作が実行されている場合、コンテンツのコピーは実行できません。
* コンテンツコピーは、ソース上の移動されたコンテンツや削除されたコンテンツをトラックできないので、クローンまたはミラーリングツールとして使用しないでください。
* コンテンツコピーは、開始後の一時停止またはキャンセルはできません。
* コンテンツコピーは、アセットと Dynamic Media メタデータを上位環境から選択した下位環境に複製します。それぞれの Dynamic Media 設定を使用するには、コピーしたアセットは、下位環境で [DAM プロセスアセットワークフロー](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/assets/using/assets-workflow)を使用して再処理する必要があります。
* [2 GB を超えるアセットサイズが有効になっている Dynamic Media 設定](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb)はサポートされていません。
* ターゲット環境の地域は、ソース環境の地域と同じにするか、そのサブセットにする必要があります。

## コンテンツコピーの既知の問題 {#known-issues}

{{content-copy-known-issues}}
