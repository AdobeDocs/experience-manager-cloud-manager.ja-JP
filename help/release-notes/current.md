---
title: Cloud Manager 2024.11.0 のリリースノート
description: Cloud Manager 2024.11.0 のリリースについて説明します。
feature: Release Information
source-git-commit: 4c22de9fa675edcd743d7acce6c7a1def8efa414
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 65%

---

# Cloud Manager 2024.11.0 のリリースノート {#release-notes}

[!UICONTROL Cloud Manager] 2024.11.0 のリリースについて説明します。

>[!NOTE]
>
>詳しくは、[Adobe Experience Manager as a Cloud Service の最新のリリースノート](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/release-notes/home)を参照してください。

## リリース日 {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

[!UICONTROL Cloud Manager] 2024.11.0 のリリース日は 2024 年 11 月 7 日です。

次回の予定リリースは 2024 年 12 月 5 日（PT）です。

## 新機能 {#what-is-new}

* パフォーマンステスト中にページが別のドメインにリダイレクトされた場合、これらのページのテスト結果は、実際のパフォーマンスを正確に表しているわけではないので、除外されます。<!-- (CMGR-5637) -->

## 早期導入プログラム {#early-adoption}

Cloud Manager の早期導入プログラムに参加すると、今後の機能をテストする機会を得ることができます。

### 独自の Git の導入 - GitLab と Bitbucket をサポートするようになりました {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

**独自の Git の導入**&#x200B;機能が拡張され、GitLab や Bitbucket などの外部リポジトリのサポートが含まれるようになりました。この新しいサポートは、プライベートおよびエンタープライズ GitHub リポジトリに対する既存のサポートに追加されます。これらの新しいリポジトリを追加すると、パイプラインに直接リンクすることもできます。これらのリポジトリは、パブリッククラウドプラットフォーム上や、プライベートクラウドまたはインフラストラクチャ内でホストできます。また、この統合により、Adobe リポジトリと常にコード同期を行う必要がなくなり、プルリクエストをメイン分岐に結合する前に検証できるようになります。

[Cloud Manager でのプライベートリポジトリの追加](/help/managing-code/external-repositories.md)を参照してください。

![リポジトリを追加ダイアログボックス](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>現在、標準のプルリクエストコード品質チェックは、GitHub でホストされるリポジトリ専用ですが、この機能を他の Git ベンダーに拡張する更新が進行中です。

この新機能をテストしてフィードバックを共有することに興味がある場合は、Adobe ID に関連付けられたメールアドレスから [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) にメールを送信します。使用する Git プラットフォームと、プライベート／パブリックまたはエンタープライズリポジトリ構造のいずれを使用するかを必ず含めてください。

### ステージング専用パイプラインと実稼動専用パイプライン {#staging-production-only-pipelines}

[ステージング専用パイプラインと実稼動専用パイプライン](/help/using/stage-prod-only.md)のサポートの導入をお知らせします。この新機能により、フルスタックの実稼動デプロイメントパイプラインをより小さな、より特殊なデプロイメントに分割できます。

この機能をテストしてフィードバックを提供する場合は、Adobe ID に関連付けられているメールアドレスから [Grp-cloudmanager_splitpipelines@adobe.com](mailto:Grp-cloudmanager_splitpipelines@adobe.com) にメールを送信してください。

## バグ修正

* コンテンツのコピー操作のステータス更新中に「403」エラーを引き起こしたAEM Cloud Managerのバグが解決されました。 この問題は、入力 IP アドレスの設定が誤っていたことが原因で、ステータスの伝達が妨げられ、一部のコンテンツコピーアクティビティが停止して無期限に実行されているように見え、手動でのキャンセルが必要になったためです。 この修正により、適切なステータスレポートが確実に生成され、コンテンツのコピータスクがよりスムーズに実行されるようになりました。<!-- (CMGR-62739) -->
* 最近のアップデートでは、SonarQube で、特定のケースでハードコードされたパスワードが検出されない問題が修正されました。 この修正には、拡張されたパターンチェックが含まれ、SonarQube のデフォルトの検出標準に従っています。<!-- CMGR-62682 -->

<!-- Known Issues {#known-issues}

* A -->
