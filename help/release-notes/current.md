---
title: リリースノート（2023.10.0）
description: Cloud Manager リリース 2023.10.0 のリリースノートです。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: a5a304541409bc1775090eef2a669e1e0bcf005e
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 58%

---


# Cloud Manager リリース 2023.10.0 のリリースノート {#release-notes}

このページは、[!UICONTROL Cloud Manager] リリース 2023.10.0 のリリースノートです。

>[!NOTE]
>
>AEM as a Cloud Service の Cloud Manager の最新リリースノートについては、[AEM as a Cloud Service の Cloud Manager の最新リリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja)を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] リリース 2023.10.0 のリリース日は 2023年10月5日（PT）です。次回のリリースは 2023年11月2日（PT）に予定されています。

## 新着情報 {#what-is-new}

* The **デプロイメントマネージャー** 役割が可能です [実稼動以外のパイプラインの実行時にAEM Dispatcher キャッシュから無効化またはフラッシュする一連のコンテンツパスを設定します。](/help/using/non-production-pipelines.md)
   * これらのキャッシュアクションは、コンテンツパッケージがデプロイされた直後に、デプロイメントパイプラインステップの一部として実行されます。
   * これらの設定では、AEM Dispatcher の標準的な動作を使用します。
* 2023 年 10 月の Cloud Manager リリースでは、段階的なロールアウトにより Java バージョンが更新されます。
   * Java のバージョンは、OracleJDK 8u371 およびOracleJDK 11.0.20 に更新されています。
   * [OpenJDK のアドバイザリを参照](https://openjdk.org/groups/vulnerability/advisories/) セキュリティおよびバグ修正の詳細については、これらの JDK の更新を参照してください。
