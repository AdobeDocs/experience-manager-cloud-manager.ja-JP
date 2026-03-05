---
title: Cloud Manager 2026.3.0 のリリースノート
description: Adobe Managed ServicesのCloud Manager 2026.3.0 のリリースについて説明します。
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 9ce8a2ca2117992421052b76b0f5c7c9c5a6195b
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 19%

---

# Adobe Managed ServicesのCloud Manager 2026.3.0 のリリースノート {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Adobe Managed Servicesでの [!UICONTROL Cloud Manager] 2026.3.0 のリリースについて説明します。

[Adobe Experience Manager as a Cloud Service の最新のリリースノート](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/release-notes/home)も参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] 2026.3.0 のリリース日は 2026 年 3 月 5 日（木）です。
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

次回のリリース予定は 2026 年 4 月 2 日木曜日（PT）です。

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## 新機能 {#what-is-new}

* **AEM Experience Hubでの UI 拡張機能のサポート**
[AEM Experience Hub](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/experience-hub/experience-hub) で UI 拡張機能がサポートされるようになり、開発者はAdobe App Builderを使用して作成されたカスタム機能やウィジェットを使用してインターフェイスを拡張できるようになりました。

  詳しくは、[AEM Experience Hub](https://developer.adobe.com/uix/docs/services/aem-experience-hub/) を参照してください。

* **設定パイプラインで管理シークレットがサポートされるようになりました**

  ユーザーは、Cloud Manager設定パイプラインで直接シークレットを追加および管理できるようになりました。 これらのシークレットは、パイプライン設定仕様の値を安全に上書きし、柔軟な環境固有のデプロイメントをサポートします。

  ![&#x200B; 選択したパイプラインのドロップダウンメニューの「変数を表示/編集」オプション &#x200B;](/help/release-notes/assets/view-edit-variables-option.png)
  *選択したパイプラインのドロップダウンメニューの「変数を表示/編集」オプション*

  ![&#x200B; 変数設定ダイアログボックス &#x200B;](/help/release-notes/assets/view-edit-variables-variablesconfig-dialogbox.png)*変数設定ダイアログボックス*

* **安定性、パフォーマンス、信頼性の向上**

  このリリースには、Cloud Managerの安定性、パフォーマンス、信頼性を向上させる最適化およびメンテナンスの更新が含まれています。


## Beta プログラム {#beta-program}

Cloud ManagerのBeta プログラムに参加すると、一般リリース前に今後リリースされる機能を独占的に利用できます。

現在、次の機能が利用できます。

<!--
### Experience Hub Extensibility and Customization {#exp-hub-extensibility}

[Experience Hub](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/experience-hub/experience-hub) serves as your entry point to AEM, customized for your organization's needs. Tell Adobe about your existing AEM UI extensions so they can help you enable them in Experience Hub with minimal effort.

![Diagram of Experience Hub extensibility and customization workflow](/help/release-notes/assets/experience-hub-extensibility-customization.png)

Embed custom experiences in Experience Hub to extend and personalize your organization's dashboard. In addition to Adobe's built-in widgets, add your own using the [UI Extensibility](https://developer.adobe.com/uix/docs/) framework. Build JavaScript-based UI apps and surface them to your users to meet business-specific requirements and workflows. 

Interested in the beta? Email [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) with your Adobe OrgID and a short description of the customization you intend to create.
-->

### モジュールのキャッシュによるビルドの高速化 {#quick-build-cm-pipelines}

新しいビルドモデルでは、（リポジトリ全体ではなく）変更されたモジュールのみを、モジュールレベルのキャッシュを使用してコンパイルし、ビルド時間を短縮します。 これは、コード品質、フルスタック、ステージ専用のパイプラインに適用されます。

![&#x200B; フルビルドとスマートビルドの 2 つのビルド戦略オプションが表示されている実稼動以外のパイプラインを編集ダイアログボックス &#x200B;](/help/release-notes/assets/non-production-pipeline-edit.png)
*フルビルドとスマートビルドの 2 つのビルド戦略オプションが表示されている実稼動以外のパイプラインを編集ダイアログボックス。*

**パイプラインを追加/編集** ダイアログボックスの「**Sourceコード**」タブにある新しい **ビルド方法** セクションで、次のいずれかのビルドオプションを選択できます。

* **フルビルド** – 実行ごとにリポジトリ内のすべてのモジュールをビルドします。
* **スマートビルド** – 前回のコミット以降に変更されたモジュールのみをビルドし、全体的なビルド時間を短縮します。

使用するパイプラインを制御できます **スマートビルド**。 ベータ版では、このオプションは **コード品質** パイプラインと **開発デプロイメント** パイプラインにのみ表示されます。

ご興味がある場合 Adobe OrgID とプログラム ID を記載して [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com) にメールでお問い合わせください。

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline variables](/help/getting-started/build-environment.md#pipeline-variables). -->

## バグ修正 {#bug-fixes}

AMS リリースの 2026 年 3 月のCloud Managerには、重要なバグ修正はありません。

<!--
Known Issues {#known-issues}

* A -->
