---
title: Cloud Manager 2025.6.0 のリリースノート
description: Adobe Managed Services の Cloud Manager 2025.5.0 のリリースについて説明します。
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '556'
ht-degree: 71%

---

# Adobe Managed Services の Cloud Manager 2025.6.0 のリリースノート {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Adobe Managed Services の [!UICONTROL Cloud Manager] 2025.6.0 のリリースについて説明します。

[Adobe Experience Manager as a Cloud Service の最新のリリースノート](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/release-notes/home)も参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] 2025.6.0 のリリース日は 2025年6月5日（PT）です。

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

次回のリリース予定は 2025年7月10日（PT）です。

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->


## 新機能 {#what-is-new}

* **ステージング専用パイプラインと実稼動専用パイプライン**

  Cloud Managerでは、ステージング専用パイプラインと実稼動専用パイプラインをサポートするようになりました。 この機能を使用すると、フルスタックの実稼動デプロイメントを、より小さな目的別のパイプラインに分割できます。<!-- This feature went into GA from Private beta in the June 5, 2025 CM release -->

  ![ 「フルスタックコード」ラジオボタンと「ステージ環境」が選択された状態の「実稼動以外のパイプラインを追加」ダイアログボックス ](/help/release-notes/assets/add-non-production-pipeline.png)

  [ ステージング専用および実稼動専用パイプライン ](/help/using/stage-prod-only.md) を参照してください。

* **お気に入りのパイプライン**

  このリリースでは、Cloud Managerでお気に入りのパイプラインをピン留めし、特定のパイプラインをお気に入りとしてマークして、「**パイプライン**」ページのリストの上部に表示できるようになりました。 この機能強化により、頻繁にアクセスするパイプラインをより容易に見つけて実行しやすくなっています。<!-- CMGR-68293 -->

  ![お気に入りとしてマークされたパイプライン](/help/release-notes/assets/pipeline-favorites.png)*お気に入りとしてマークされた 2 つのパイプライン。*

  [パイプラインのお気に入りをマークする](/help/using/managing-pipelines.md#pipeline-favorites)を参照してください。


## プライベートベータプログラム {#beta-program}

Cloud Managerの非公開ベータプログラムに参加すると、一般リリース前に今後リリースされる機能を独占的に利用できます。

現在、次のプライベートベータ版の機会を利用できます。


### 独自の Git の導入 - GitLab と Bitbucket をサポートするようになりました。 {#gitlab-bitbucket}

**独自の Git を持ち込む** （BYOG）機能が拡張され、GitLab や Bitbucket などの外部リポジトリがサポートされるようになりました。 この新しいサポートは、プライベートおよびエンタープライズ GitHub リポジトリに対する既存のサポートに追加されます。 これらの新しいリポジトリを追加すると、パイプラインに直接リンクすることもできます。 これらのリポジトリは、パブリッククラウドプラットフォーム上や、プライベートクラウドまたはインフラストラクチャ内でホストできます。 また、この統合により、Adobe リポジトリと常にコード同期を行う必要がなくなり、プルリクエストをメイン分岐に結合する前に検証できるようになります。

外部リポジトリ（GitHub でホストされているリポジトリを除く）を使用するパイプラインと、**Git 変更時**&#x200B;に設定した&#x200B;**デプロイメントトリガー**&#x200B;が自動的に開始されるようになりました。

[Cloud Manager でのプライベートリポジトリの追加](/help/managing-code/external-repositories.md)を参照してください。

![リポジトリを追加ダイアログボックス](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>現在、標準のプルリクエストコード品質チェックは、GitHub でホストされるリポジトリ専用ですが、この機能を他の Git ベンダーに拡張する更新が進行中です。

この新機能をテストしてフィードバックを共有することに興味がある場合は、Adobe ID に関連付けられたメールアドレスから [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) にメールを送信します。 使用する Git プラットフォームと、プライベート／パブリックまたはエンタープライズリポジトリ構造のいずれを使用するかを必ず含めてください。

#### アクセストークンを管理{#access-tokens}

BYOG で **アクセストークンの管理** を使用して、外部 GitHub Enterprise、GitLab、Bitbucket、Azure DevOps などの独自の Git リポジトリに関連付けられたアクセストークンを表示、名前変更、削除します。

[アクセストークンを管理](/help/managing-code/manage-access-tokens.md)をご覧ください。

この新機能をテストしてフィードバックを共有することに興味がある場合は、Adobe ID に関連付けられたメールアドレスから [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) にメールを送信します。 使用する Git プラットフォームと、プライベート／パブリックまたはエンタープライズリポジトリ構造のいずれを使用するかを必ず含めてください。


## バグ修正 {#bug-fixes}

* AEM Cloud Managerは、お客様のアーティファクトを取得する際に、409 エラー（競合）が原因で発生した Maven ビルドエラーをお客様が原因のエラーに正しくマッピングするようになりました。この変更により、内部エラーとお客様の環境の設定に関連する問題が区別され、エラーメッセージが改善されます。<!-- CMGR-66673 -->

<!--
Known Issues {#known-issues}

* A -->
