---
title: Cloud Manager 2025.1.0 のリリースノート
description: Adobe Managed Services の Cloud Manager 2025.1.0 のリリースについて説明します。
feature: Release Information
exlid: 669b1f2d8fc68526eb091e0f93f70ab93033d193
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: ca9a07354ff8316f531840a42d6ecdda5c072b9b
workflow-type: ht
source-wordcount: '196'
ht-degree: 100%

---

# Adobe Managed Services の Cloud Manager 2025.1.0 のリリースノート {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release -->

Adobe Managed Services の [!UICONTROL Cloud Manager] 2025.1.0 のリリースについて説明します。

>[!NOTE]
>
>詳しくは、[Adobe Experience Manager as a Cloud Service の最新のリリースノート](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/release-notes/home)を参照してください。

## リリース日 {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

[!UICONTROL Cloud Manager] 2025.1.0 のリリース日は 2024年1月22日（PT）です。

次回のリリース予定は 2025年2月13日木曜日（PT）です。

## 新機能 {#what-is-new}

**コード品質ルール - SonarQube Server のアップグレード：** Cloud Manager コード品質ステップは、2025 年2月13日木曜日（PT）に予定されている Cloud Manager 2025.2.0 リリースで SonarQube Server 9.9 を使用して開始されます。

準備のために、更新された SonarQube ルールが[コード品質ルール](/help/using/code-quality-testing.md#code-quality-testing-step)で使用できるようになりました。

次のパイプラインテキスト変数を設定して、新しいルールを「早期に確認」できます（以下のスクリーンショットを参照）。

`CM_BUILD_IMAGE_OVERRIDE` = `self-service-build:sonar-99-upgrade-java17or21`

さらに、コード品質ステップが同じコミットに対して実行されるように、次の変数を設定します（通常、同じ `commitId` の場合はスキップされます）。

`CM_DISABLE_BUILD_REUSE` = `true`

![変数設定ページ](/help/release-notes/assets/variables-config.png)

>[!NOTE]
>
>アドビでは、メインの実稼動パイプラインと同じ分岐に設定された、新しい CI/CD コード品質パイプラインを作成することをお勧めします。2025年2月13日（PT）のリリースの&#x200B;*前*&#x200B;に適切な変数を設定して、新しく適用されるルールによってブロッカーが導入されないことを検証します。

<!-- ## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features. -->


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
