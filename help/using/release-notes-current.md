---
title: リリースノート（2022.4.0）
description: Cloud Manager リリース 2022.4.0 のリリースノートです。
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 3d4eea13c0f2e9c4030bbfd3b7c5c25336548498
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 27%

---


# Cloud Manager リリース 2022.4.0 のリリースノート {#release-notes}

このページは、[!UICONTROL Cloud Manager] リリース 2022.4.0 のリリースノートです。

>[!NOTE]
>
>AEM as a Cloud Service の Cloud Manager の最新リリースノートについては、[AEM as a Cloud Service の Cloud Manager の最新リリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja)を参照してください。

## リリース日 {#release-date}

のリリース日 [!UICONTROL Cloud Manager] リリース 2022.4.0 は 2022 年 4 月 7 日です。 次回のリリースは 2022 年 5 月 5 日に予定されています。

## 新機能 {#what-is-new}

* パイプラインビルド手順の期間と成功率が改善され、4 月を通じてすべてのお客様に段階的に展開される予定です。
* パイプラインの追加と編集ウィザードの入力フィールドに名前の最初の数文字を入力し、推奨される一致から選択することで、Git ブランチを簡単に見つけることができるようになりました。
* この **パイプライン** 多数のパイプラインを持つプログラムのユーザビリティを向上させるために、ページネーションが追加されました。
   * 1 ページにつき 50 行が表に表示されます。
* のバージョン。 [AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=ja) Cloud Manager で使用されているをバージョン 36 に更新しました。
* OracleJDK は、AEMアプリケーションの開発と操作のためのデフォルト JDK になりました。 Cloud Manager のビルドプロセスは、Maven ツールチェーンで代替オプションが明示的に選択されている場合でも、OracleJDK を使用してに自動的に切り替わります。
   * oracleJDK への切り替え方法の詳細については、 [ビルド環境に関するドキュメント](/help/using/build-environment-details.md#using-java-support)
   * 詳しくは、 [Adobe Experience Manager FAQ の Java サポートポリシー](https://experienceleague.adobe.com/docs/experience-manager-65/assets/Java_Policy_for_Adobe_Experience_Manager.pdf) を使用して、この変更に関するよくある質問に対処します。
