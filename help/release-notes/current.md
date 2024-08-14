---
title: Cloud Manager 2024.8.0 のリリースノート
description: Cloud Manager 2024.8.0 のリリースノートについて説明します。
feature: Release Information
source-git-commit: dd764bb17127ba0a1e88e85592329cc9ddff42e3
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 5%

---


# Cloud Manager 2024.8.0 のリリースノート {#release-notes}

このページは、[!UICONTROL Cloud Manager] 2024.8.0 のリリースノートです。

>[!NOTE]
>
>AEM as a Cloud ServiceのCloud Managerの最新のリリースノートについては、[AEM as a Cloud ServiceのCloud Managerの最新のリリースノート ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current) を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] 2024.8.0 のリリース日は 2024 年 8 月 14 日です。 次回のリリースは 2024年9月14日（PT）に予定されています。

## 新機能 {#what-is-new}

* ステージング専用パイプラインと実稼動専用パイプライン（（早期導入プログラム [ の一部として利用可能 ](#staging-production-only-pipelines)）の場合、ステージテストをスキップして [ 緊急モード ](/help/using/stage-prod-only.md#emergency-mode) で実行できるようになりました。

## 早期導入プログラム {#early-adoption}

Adobeの早期導入プログラムに参加して、今後の機能をテストする機会を得ます。

### ステージング専用パイプラインと実稼動専用パイプライン {#staging-production-only-pipelines}

Adobeは、（ステージング専用パイプラインと実稼動専用パイプライン [ のサポートを導入しましたので、お知らせ ](/help/using/stage-prod-only.md) ます。 この新機能を使用すると、フルスタックの実稼動デプロイメントパイプラインを、より小さく、より特殊なデプロイメントに分割できます。

この機能をテストしてフィードバックを提供したい場合は、Adobe IDに関連付けられたメールアドレスを使用して `Grp-cloudmanager_splitpipelines@adobe.com` ールを送信します。

## バグ修正

* パイプラインが削除された後、パイプラインステップが実行中であることが判明するまれな問題を修正しました。
* パイプラインの再実行が最初の試行で動作するようになりました。再実行を複数回開始しなければならない稀な問題を修正しました。
* フルスタックパイプラインのスケジュールされたデプロイメントステップで、選択したスケジュール日が適用されるようになり、「今すぐ **に戻さなくなりました**。
* コンテンツのコピータスクの失敗したステータスが正しく反映されるようになり、まれに誤って `In Progress` ステータスが表示されなくなりました。

## 既知の問題 {#known-issues}

{{content-copy-known-issues}}
