---
title: Cloud Manager 2026.3.0のリリースノート
description: Adobe Managed ServicesでのCloud Manager 2026.3.0のリリースについて説明します。
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: b7e651b72d1943aef69c1c69915d4752a6163931
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 16%

---

# Adobe Managed ServicesのCloud Manager 2026.3.0のリリースノート {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Adobe Managed Servicesの[!UICONTROL Cloud Manager] 2026.3.0のリリースについて説明します。

[Adobe Experience Manager as a Cloud Service の最新のリリースノート](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/release-notes/home)も参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] 2026.3.0のリリース日は2026年3月5日木曜日です。
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

次回のリリース予定は2026年4月2日木曜日です。

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## 新機能 {#what-is-new}

* **AEM Experience HubでのUI拡張機能のサポート**
[AEM Experience Hub](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/experience-hub/experience-hub)のUI拡張機能のサポートが有効になり、開発者はAdobe App Builderを使用して構築されたカスタム機能とウィジェットでインターフェイスを拡張できるようになりました。

  詳しくは、[AEM Experience Hub](https://developer.adobe.com/uix/docs/services/aem-experience-hub/)を参照してください。

* **設定パイプラインでマネージド シークレットがサポートされるようになりました**

  Cloud Manager設定パイプラインで、シークレットを直接追加および管理できるようになりました。 これらのシークレットは、パイプライン設定仕様の値を安全に上書きし、柔軟で環境固有のデプロイメントをサポートします。

  ![選択したパイプラインのドロップダウンメニューの「変数の表示/編集」オプション &#x200B;](/help/release-notes/assets/view-edit-variables-option.png)
  *選択したパイプラインのドロップダウンメニューの「変数の表示/編集」オプション。*

  ![変数設定ダイアログボックス &#x200B;](/help/release-notes/assets/view-edit-variables-variablesconfig-dialogbox.png)*変数設定ダイアログボックス。*

* **安定性、パフォーマンス、信頼性の向上**

  このリリースには、Cloud Managerの安定性、パフォーマンス、信頼性を向上させる最適化とメンテナンスのアップデートが含まれています。


## Beta プログラム {#beta-program}

Cloud ManagerのBeta プログラムに参加して、一般リリースの前に今後の機能に限定でアクセスできます。

現在、次の機能が利用できます。

<!--
### Experience Hub Extensibility and Customization {#exp-hub-extensibility}

[Experience Hub](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/experience-hub/experience-hub) serves as your entry point to AEM, customized for your organization's needs. Tell Adobe about your existing AEM UI extensions so they can help you enable them in Experience Hub with minimal effort.

![Diagram of Experience Hub extensibility and customization workflow](/help/release-notes/assets/experience-hub-extensibility-customization.png)

Embed custom experiences in Experience Hub to extend and personalize your organization's dashboard. In addition to Adobe's built-in widgets, add your own using the [UI Extensibility](https://developer.adobe.com/uix/docs/) framework. Build JavaScript-based UI apps and surface them to your users to meet business-specific requirements and workflows. 

Interested in the beta? Email [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) with your Adobe OrgID and a short description of the customization you intend to create.
-->

### モジュールのキャッシュによるビルドの高速化 {#quick-build-cm-pipelines}

新しいビルドモデルでは、（リポジトリ全体ではなく）変更されたモジュールのみを、モジュールレベルのキャッシュを使用してコンパイルし、ビルド時間を短縮します。 これは、コード品質パイプラインとフルスタックパイプラインに適用されます。

![実稼動以外のパイプラインを編集ダイアログボックスに、フルビルドとスマートビルドの2つのビルド戦略オプションが表示されている](/help/release-notes/assets/non-production-pipeline-edit.png)
*実稼動以外のパイプラインを編集ダイアログボックスに、フルビルドとスマートビルドの2つのビルド戦略オプションが表示されている*。

**パイプラインの追加/編集** ダイアログボックスの「**Source コード**」タブで、新しい&#x200B;**ビルド戦略** セクションを使用して、次のいずれかのビルドオプションを選択できます。

* **完全ビルド** – 実行ごとにリポジトリ内のすべてのモジュールをビルドします。
* **スマートビルド** – 前回のコミット以降に変更されたモジュールのみをビルドし、全体的なビルド時間を短縮します。

[実稼動以外のパイプラインの追加](/help/using/non-production-pipelines.md#add-non-production-pipeline)および[実稼動以外のパイプラインでのスマートビルドの使用について](/help/using/non-production-pipelines.md#about-smart-build)を参照してください。

**スマートビルド**&#x200B;を使用するパイプラインを制御します。 ベータ版では、このオプションは&#x200B;**コード品質**&#x200B;および&#x200B;**開発フルスタックコード展開** パイプラインにのみ表示されます。

ご興味がある場合 Adobe OrgID とプログラム ID を記載して [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com) にメールでお問い合わせください。

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline variables](/help/getting-started/build-environment.md#pipeline-variables). -->

## バグ修正 {#bug-fixes}

AMS版Cloud Managerの2026年3月リリースには、重大なバグ修正はありません。

<!--
Known Issues {#known-issues}

* A 
-->
