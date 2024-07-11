---
title: 2024.6.0 のリリースノート
description: Cloud Manager リリース 2024.6.0 のリリースノートです。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 851b556c0917d9f6d97d958a0c8e8aeff4141079
workflow-type: ht
source-wordcount: '288'
ht-degree: 100%

---


# Cloud Manager リリース 2024.6.0 のリリースノート {#release-notes}

このページは、[!UICONTROL Cloud Manager] リリース 2024.6.0 のリリースノートです。

>[!NOTE]
>
>AEM as a Cloud Service の Cloud Manager の最新リリースノートについては、[AEM as a Cloud Service の Cloud Manager の最新リリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja)を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] リリース 2024.6.0 のリリース日は 2024年6月6日（PT）です。次回のリリースは 2024年7月18日（PT）に予定されています。

## 新機能 {#what-is-new}

* フルスタックパイプラインのソースとして、[独自の GitHub リポジトリを使用](/help/managing-code/private-repositories.md)できるようになりました。
   * さらに、[Git サブモジュール](/help/managing-code/git-submodules.md)を備えた GitHub リポジトリを活用すると、プルリクエストの検証に使用される自動生成パイプラインのコントロールが強化され、コードスキャンフェーズ中に重要な指標の動作を定義できます。
   * [また](/help/managing-code/github-check-config.md)、ニーズに合わせて、GitHub にレポート履歴を保存し、パイプラインに名前を付け、パイプライン変数を設定することもできます。
* 新しい OakPal ルールが、[Cloud Manager コード品質スキャン](/help/using/custom-code-quality-rules.md#oakpal-ui-content-package)に追加されました。
   * 2024年6月の時点で追加されたすべての新しいルールは、重大な変更ではありません。
   * Cloud Manager 2024年8月リリース以降、これらの新しいルールによりパイプラインでエラーが発生する可能性があるので、できるだけ早くこれらのルールに対処することをお勧めします。

## 早期導入プログラム {#early-adoption}

早期導入プログラムに参加して、今後の機能をテストする機会を得ることができます

### ステージング専用パイプラインと実稼動専用パイプライン {#staging-production-only-pipelines}

[ステージング専用パイプラインと実稼動専用パイプライン](/help/using/stage-prod-only.md)のサポートが導入され、フルスタックの実稼動デプロイメントパイプラインをより小さな特殊なデプロイメントに分割できるようになりました。

この新機能をテストしてフィードバックを共有することに興味がある場合は、Adobe ID に関連付けられたメールアドレスから `Grp-cloudmanager_splitpipelines@adobe.com` にメールを送信してください。
