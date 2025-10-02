---
title: Cloud Manager 2025.10.0 のリリースノート
description: Adobe Managed Services の Cloud Manager 2025.10.0 のリリースについて説明します。
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 25eebd297fe2cdd82d4905fac9ae38e1ce46153f
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 59%

---

# Adobe Managed Services の Cloud Manager 2025.10.0 のリリースノート {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Adobe Managed Services の [!UICONTROL Cloud Manager] 2025.10.0 のリリースについて説明します。

[Adobe Experience Manager as a Cloud Service の最新のリリースノート](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/release-notes/home)も参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] 2025.10.0 のリリース日は 2025年10月2日（PT）です。

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

次回のリリース予定は 2025年11月6日木曜日（PT）です。

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## 新機能 {#what-is-new}







## Beta プログラム {#beta-program}

Cloud ManagerのBeta プログラムに参加すると、一般リリース前に今後リリースされる機能を独占的に利用できます。

現在、以下の機能が利用可能です。

### Experience Hubの拡張性とカスタマイズ {#exp-hub-extensibility}

[Experience Hub](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/experience-hub/experience-hub) は、組織のニーズに合わせてカスタマイズされた、AEMへのエントリポイントとして機能します。 Adobeに既存のAEM UI 拡張機能を通知し、最小限の労力でExperience Hubで有効にできるようにします。

![Experience Hubの拡張性とカスタマイズワークフローの図 &#x200B;](/help/release-notes/assets/experience-hub-extensibility-customization.png)

カスタムエクスペリエンスをExperience Hubに埋め込むと、組織のダッシュボードを拡張し、パーソナライズすることができます。 Adobeの組み込みウィジェットに加えて、[UI 拡張機能 &#x200B;](https://developer.adobe.com/uix/docs/) フレームワークを使用して独自のウィジェットを追加します。 JavaScript ベースの UI アプリを作成し、ビジネス固有の要件とワークフローを満たすようにユーザーに表示します。

ベータ版に興味がありますか？ Adobeの OrgID と作成するカスタマイズの簡単な説明を [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) にメールで送信します。

### モジュールのキャッシュによるビルドの高速化 {#quick-build-cm-pipelines}

新しいビルドモデルでは、（リポジトリ全体ではなく）変更されたモジュールのみを、モジュールレベルのキャッシュを使用してコンパイルし、ビルド時間を短縮します。 コード品質、フルスタック、ステージ専用のパイプラインに適用されます。

ベータ版に興味がありますか？ Adobeの OrgID とプログラム ID を記載したメール [0&rbrace;beta_quickbuild_cmpipelines@adobe.com&rbrace; を送信します。](mailto:beta_quickbuild_cmpipelines@adobe.com)

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline variables](/help/getting-started/build-environment.md#pipeline-variables). -->


### Bring Your Own Git (BYOG) {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

Azure DevOps Git リポジトリを Cloud Manager にオンボードできるようになりました。これは、最新の Azure DevOps リポジトリとレガシー VSTS（Visual Studio Team Services）リポジトリの両方に対応しています。

* Edge Delivery Services のユーザーは、オンボードされたリポジトリを使用して、サイトコードを同期およびデプロイできます。
* AEM as a Cloud Service および Adobe Managed Services（AMS）のユーザーは、リポジトリをフルスタックパイプラインとフロントエンドパイプラインの両方にリンクできます。

追加のパイプラインタイプと、コード品質パイプラインを通じたプルリクエスト検証のサポートは、近日リリース予定です。

[Cloud Manager でのプライベートリポジトリの追加](/help/managing-code/external-repositories.md)を参照してください。

![リポジトリを追加ダイアログボックス](/help/release-notes/assets/azure-repo.png)

この新機能をテストしてフィードバックを共有することに興味がある場合は、Adobe ID に関連付けられたメールアドレスから [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) にメールを送信します。 使用する Git プラットフォームと、プライベート／パブリックまたはエンタープライズリポジトリ構造のいずれを使用するかを必ず含めてください。

#### アクセストークンを管理{#manage-access-tokens}

Cloud Managerで「**アクセストークンの管理**」を使用して、外部 BYOG リポジトリ (GitHub Enterprise、GitLab、Bitbucket、Azure DevOps など) に関連付けられたアクセストークンを表示、名前変更、削除します。

[アクセストークンを管理](/help/managing-code/manage-access-tokens.md)をご覧ください。

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. -->

## バグ修正 {#bug-fixes}

10 月のCloud Manager リリースには重要なバグ修正はありません。

<!--
Known Issues {#known-issues}

* A -->
