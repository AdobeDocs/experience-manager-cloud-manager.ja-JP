---
title: 2023.10.0 のリリースノート
description: Cloud Manager リリース 2023.10.0 のリリースノートです。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 851364e74864c28b3bcd9285dfbe06ddb530eb10
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 49%

---


# Cloud Manager リリース 2023.10.0 のリリースノート {#release-notes}

このページは、[!UICONTROL Cloud Manager] リリース 2023.10.0 のリリースノートです。

>[!NOTE]
>
>AEM as a Cloud Service の Cloud Manager の最新リリースノートについては、[AEM as a Cloud Service の Cloud Manager の最新リリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja)を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] リリース 2023.10.0 のリリース日は 2023年10月5日（PT）です。次回のリリースは 2023年11月2日（PT）に予定されています。

## 新機能 {#what-is-new}

* The **デプロイメントマネージャー** 役割が可能です [実稼動以外のパイプラインの実行時にAEM Dispatcher キャッシュから無効化またはフラッシュする一連のコンテンツパスを設定します。](/help/using/non-production-pipelines.md)
   * これらのキャッシュアクションは、コンテンツパッケージがデプロイされた直後に、デプロイメントパイプラインステップの一部として実行されます。
   * これらの設定では、AEM Dispatcher の標準的な動作を使用します。
* 2023 年 10 月の Cloud Manager リリースでは、段階的なロールアウトにより Java バージョンが更新されます。
   * Java 8 および 11 および Maven のマイナーバージョンが更新され、今後 2 ヶ月間で段階的に展開される予定です。 新しいバージョンには、複数のセキュリティ修正とバグ修正が含まれています。 新しいバージョンは次のとおりです。
   * *Maven: 3.8.8*
   * *Java 8 バージョン： /usr/lib/jvm/jdk1.8.0_371*
   * *Java 11 バージョン： /usr/lib/jvm/jdk-11.0.20*
   * [OpenJDK のアドバイザリを参照](https://openjdk.org/groups/vulnerability/advisories/) セキュリティおよびバグ修正の詳細については、これらの JDK の更新を参照してください。
