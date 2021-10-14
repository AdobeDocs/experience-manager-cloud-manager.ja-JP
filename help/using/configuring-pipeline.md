---
title: CI／CD パイプラインの設定
seo-title: Configure your CI/CD Pipeline
description: このページでは、Cloud Manager からのパイプライン設定について説明します。
seo-description: Before you start to deploy your code, you must configure your pipeline settings from the AEM Cloud Manager.
uuid: 35fd56ac-dc9c-4aca-8ad6-36c29c4ec497
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
content-type: reference
discoiquuid: ba6c763a-b78a-439e-8c40-367203a719b3
feature: CI-CD Pipeline
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
source-git-commit: bdbee51ff0a61c2a72ff7ae3a742e2dd817c671a
workflow-type: tm+mt
source-wordcount: '1459'
ht-degree: 63%

---

# CI／CD パイプラインの設定 {#configure-your-ci-cd-pipeline}

>[!NOTE]
>AEM as a Cloud Servic で CI／CD パイプライン用に Cloud Manager を設定する方法については、[こちら](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=ja#using-cloud-manager)を参照してください。

以下のページでは、**パイプライン**&#x200B;の設定方法について説明します。パイプラインの動作の仕組みについて詳しくは、[CI／CD パイプラインの概要](ci-cd-pipeline.md)を参照してください。

## ビデオチュートリアル {#video-tutorial-one}

### Cloud Manager でのパイプラインの設定 {#config-pipeline-video}

CI／CD 実稼動パイプラインの設定は、パイプラインを開始するトリガー、実稼動環境のデプロイメントを制御するパラメーター、およびテストパラメーターのパフォーマンスを定義します。

>[!VIDEO](https://video.tv.adobe.com/v/26314/)


## フローについて {#understanding-the-flow}

[!UICONTROL Cloud Manager] UI の&#x200B;**パイプライン設定**&#x200B;タイルからパイプラインを設定することができます。

パイプラインの設定はデプロイメントマネージャーが担当します。その際は、まず **Git リポジトリー**&#x200B;からブランチを選択します。パイプライン設定は以下で構成されます。

* パイプラインを開始するトリガーの定義
* 実稼動デプロイメントを制御するパラメーターの定義
* パフォーマンステストパラメーターの設定

## パイプラインの設定 {#setting-up-the-pipeline}

>[!CAUTION]
>
>パイプラインは、Git リポジトリーが少なくとも 1 つのブランチを持ち、[プログラム設定](setting-up-program.md)が完了するまで、設定できません。

コードのデプロイを開始する前に、[!UICONTROL Cloud Manager] からパイプライン設定を指定する必要があります。

>[!NOTE]
>
>初期設定後にパイプライン設定を変更できます。

## パイプラインカードからの新しい実稼動パイプラインの追加 {#adding-production-pipeline}

[!UICONTROL Cloud Manager] UI を使用してプログラムを設定し、少なくとも 1 つの環境を設定したら、実稼動パイプラインを追加する準備が整います。

次の手順に従って、実稼動パイプラインの動作と環境を設定します。

1. **プログラムの概要** ページから **パイプライン** カードに移動します。

1. **+Add** をクリックし、「**実稼動パイプラインを追加**」を選択します。

   ![](/help/using/assets/configure-pipelines/add-prod1.png)

1. **実稼動パイプラインを** 追加ダイアログボックスが表示されます。

   1. パイプライン名を入力します。 **リポジトリ** と **Git ブランチ** を選択できます。

      ![](/help/using/assets/configure-pipelines/add-prod2.png)

   1. **デプロイメントトリガー** と **重要な失敗動作** は、**デプロイメントオプション** から設定できます。

      ![](/help/using/assets/configure-pipelines/add-prod3.png)


      パイプラインを開始するトリガーを定義できます。

      * **手動** - UI を使用して、パイプラインを手動で開始します。
      * **Git の変更時** - 設定された Git ブランチにコミットが追加されるたびに CI/CD パイプラインを開始します。このオプションを選択しても、常にパイプラインを手動で開始できます。

         >[!NOTE]
         >パイプラインのセットアップまたは編集中に、デプロイメントマネージャーは、品質ゲートのいずれかで重要なエラーが検出された場合のパイプラインの動作を定義できます。
      これは、より自動化されたプロセスを求めるお客様に役に立ちます。使用できるオプションは以下のとおりです。

      * **毎回確認する** - デフォルトの設定。重要なエラーが検出されたときに手動で介入する必要があります。
      * **ただちにキャンセルする** - 重要なエラーが検出されると、常にパイプラインはキャンセルされます。このオプションでは、基本的に、各エラーをユーザーが手動で拒否する状況をエミュレートします。
      * **ただちに承認する** - 重要なエラーが検出されても、常にパイプラインは自動的に続行されます。このオプションでは、基本的に、各エラーをユーザーが手動で承認する状況をエミュレートします。
   1. 「**デプロイメントオプション**」を選択します。

      ![](/help/using/assets/configure-pipelines/add-prod4.png)

      * **ステージデプロイメント後に承認**&#x200B;機能は、実稼動環境のデプロイメント前の承認と同様に機能しますが、ステージデプロイメントステップの直後（テストの実行前）に行われます。一方、実稼動環境のデプロイメント前の承認は、すべてのテストが完了した後に行われます。

      * **ロードバランサーのスキップ**
   1. 「ステージ」で「**Dispatcher Configurations**」を選択します。

   1. 「実稼動」で「**デプロイメントオプション**」を選択します。 ここで、実稼動デプロイメントを制御するパラメーターを定義します。次の 3 つのオプションが使用可能です。

      * **GoLive の承認を使用** - [!UICONTROL Cloud Manager] UI を使用して、ビジネスオーナー、プロジェクトマネージャー、デプロイメントマネージャーのいずれかがデプロイメントを手動で承認する必要があります。
      * **CSE Oversight を使用** - CSE が実際にデプロイメントを開始します。CSE Oversight が有効になっている場合は、パイプラインの設定または編集中に、デプロイメントマネージャーは次のオプションを選択できます。

      * **任意の CSE**：対応可能な任意の CSE に問い合わせます。
      * **担当の CSE**：顧客に割り当てられている特定の CSE（CSE が不在の場合はバックアップ）に問い合わせます。

      * **スケジュール設定** - このオプションを使用すると、ユーザーはスケジュールされた実稼動デプロイメントを有効にできます。

         >[!NOTE]
         >「**スケジュール設定**」オプションが選択されている場合は、パイプラインでステージングデプロイメント（および、「**GoLive の承認を使用**」が有効な場合はその承認）の&#x200B;**後**&#x200B;に実稼動デプロイメントをスケジュールして、スケジュールが設定されるのを待つことができます。ユーザーは、実稼動デプロイメントをすぐに実行することもできます。
         >
         >デプロイメントのスケジュールを設定する、または実稼動デプロイメントをすぐに実行する場合は、[コードのデプロイ](deploying-code.md)を参照してください。
   1. 実稼動環境用に **Dispatcher 設定** を設定します。

      デプロイメントマネージャーは、パイプラインの設定または編集中に、AEM Dispatcher キャッシュからパブリッシュインスタンス向けに&#x200B;**無効化**&#x200B;または&#x200B;**フラッシュ**&#x200B;する一連のコンテンツパスを設定できます。

      ステージングデプロイメントと実稼動デプロイメントに別々に一連のパスを設定できます。設定した場合、これらのキャッシュアクションは、コンテンツパッケージがデプロイされた直後にデプロイメントパイプラインステップの一部として実行されます。これらの設定では、標準の AEM Dispatcher 動作を使用します。無効化は、コンテンツがオーサーからパブリッシュにアクティブ化された場合と同様に、キャッシュを無効化します。フラッシュはキャッシュを削除します。

      一般に、無効化アクションを使用する方が望ましいですが、フラッシュが必要な場合もあります（特に、AEM HTML クライアントライブラリを使用する場合など）。

      >[!NOTE]
      >
      >Dispatcher のキャッシュについて詳しくは、[Dispatcher の概要](dispatcher-configurations.md)を参照してください。





1. すべてのオプションを選択したら、「**続行**」をクリックします。

1. **ステージテスト** の手順で、オプションを選択します。 ライセンスを取得している製品に応じて、*AEM Sites* および *AEM Assets* のパフォーマンステストを設定できます。詳しくは、[パフォーマンステスト](understand-your-test-results.md#performance-testing)を参照してください。

   1. 「**サイトコンテンツ配信/分散負荷重み付け**」からオプションを選択します。 詳しくは、パフォーマンステストの [AEM Sites](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#aem-sites) を参照してください。

      ![](/help/using/assets/configure-pipelines/add-prod5.png)

   1. **Assets パフォーマンステスト配布** からオプションを選択します。 詳しくは、パフォーマンステストの [AEM Assets](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#aem-assets) を参照してください。

      ![](/help/using/assets/configure-pipelines/add-prod6.png)

1. 「**保存**」をクリックして、実稼動パイプラインの追加を完了します。

### 実稼動パイプラインの編集 {#editing-prod-pipeline}

パイプライン設定は、**プログラムの概要** ページで編集できます。

設定したパイプラインを編集するには、次の手順に従います。

1. **プログラムの概要** ページから **パイプライン** カードに移動します。

1. **をクリックします…** パイプライン **カードから** を開き、**編集** をクリックします（下図を参照）。


1. **実稼動パイプラインを編集** ダイアログボックスが表示されます。

   1. 「**設定**」タブを使用すると、**パイプライン名**、**デプロイメントトリガー**、**重要な指標の失敗動作** を更新できます。

      >[!NOTE]
      >Cloud Manager でリポジトリを追加および管理する方法については、[ リポジトリの追加と管理 ](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) を参照してください。


   1. 「**ソース**」タブには、「**実稼動環境** にデプロイする前に一時停止」および「**実稼動環境のデプロイメントオプション**」の「**スケジュール済み**」オプションをオンまたはオフにするオプションがあります。


   1. 「**エクスペリエンス監査**」オプションを使用すると、新しいページを更新または追加できます。


1. パイプラインの編集が完了したら、「**更新**」をクリックします。

1. 「**パイプラインを設定**」をクリックして、パイプラインを設定します。

   ![](assets/Setup-Pipeline.png)




## 非実稼動パイプラインとコード品質専用パイプライン

ステージングおよび実稼動環境にデプロイするメインパイプラインに加えて、顧客は、**実稼動以外のパイプライン**&#x200B;と呼ばれる追加のパイプラインを設定できます。このパイプラインでは、常にビルドステップとコード品質ステップを実行します。また、オプションで Adobe Managed Services 環境にデプロイすることもできます。

## ビデオチュートリアル {#video-tutorial-two}

### Cloud Manager の非実稼動およびコード品質専用パイプライン {#non-prod-video}

CI／CD 実稼動以外のパイプラインは、コード品質パイプラインとデプロイパイプラインの 2 つのカテゴリに分類されます。コード品質は、Git ブランチのすべてのコードをパイプライン化し、Cloud Manager のコード品質スキャンに対して構築および評価されます。

>[!VIDEO](https://video.tv.adobe.com/v/26316/)

### 実稼動以外のパイプラインの追加 {#add-non-production-pipeline}

ホーム画面には、このパイプラインが新しいカードに一覧表示されます。

1. Cloud Manager のホーム画面から **パイプライン** カードにアクセスします。 「**+追加**」をクリックし、「**非実稼動パイプラインを追加**」を選択します。

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. **非実稼動パイプラインを追加ダ**  イアログボックスが表示されます。作成するパイプラインのタイプを、**コード品質パイプライン** または **デプロイメントパイプライン** のいずれかから選択します。

   さらに、**デプロイメントトリガー** から、**デプロイメントオプション** と **重要な失敗動作** を設定することもできます。 「**続行**」をクリックします。

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add2.png)


1. 新しく作成した非実稼動パイプラインが **パイプライン** カードに表示されるようになりました。

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add4.png)


   パイプラインは、次に示すように、3 つのアクションと共にホーム画面のカードに表示されます。

   * **** を追加 — 新しいパイプラインを追加できます。
   * **リポジトリー情報へアクセス** - Cloud Manager Git リポジトリーへのアクセスに必要な情報をユーザーが取得できるようにします.
   * **詳細情報** - CI／CD パイプラインのドキュメントリソースの概要に移動します。

### 実稼動以外のパイプラインの編集 {#editing-nonprod-pipeline}

**プログラムの概要** ページから、**パイプラインカード** からパイプライン設定を編集できます。

次の手順に従って、設定済みの非実稼動パイプラインを編集します。

1. **プログラムの概要** ページから **パイプライン** カードに移動します。

1. 非実稼動パイプラインを選択し、「**...」をクリックします。**. 下の図に示すように、「**編集**」をクリックします。

   ![](/help/using/assets/configure-pipelines/non-prod-pipeline-edit1.png)

1. **実稼動パイプラインを編集** ダイアログボックスが表示され、**パイプライン名**、**リポジトリ**、**Git ブランチ**、**デプロイメントトリガー** および **重要な失敗指標を更新できます動作**。

   ![](/help/using/assets/configure-pipelines/non-prod-pipeline-edit2.png)

   >[!NOTE]
   >Cloud Manager でリポジトリを追加および管理する方法については、[ リポジトリの追加と管理 ](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) を参照してください。


1. 非実稼動パイプラインの編集が完了したら、「**更新**」をクリックします。


## 次の手順 {#the-next-steps}

パイプラインを設定したら、コードをデプロイする必要があります。

詳しくは、[コードのデプロイ](deploying-code.md)を参照してください。
