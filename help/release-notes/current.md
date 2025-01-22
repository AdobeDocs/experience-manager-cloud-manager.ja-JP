---
title: Cloud Manager 2025.1.0 のリリースノート
description: Adobe Managed Services の Cloud Manager 2025.1.0 のリリースについて説明します。
feature: Release Information
exlid: 669b1f2d8fc68526eb091e0f93f70ab93033d193
source-git-commit: 434740b5ad2dafd5a6c55d0272cf5effdfa6baac
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 39%

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

次回のリリース予定は 2025年2月13日（PT）です。

## 新機能 {#what-is-new}

**コード品質ルール - Sonar キューブのアップグレード：** Cloud Manager コード品質ステップでは、2025 年 2 月 13 日木曜日（PT）に予定されているCloud Manager 2025.2.0 リリースで SonarQube Server 9.9 の使用を開始します。

準備のために、更新された SonarQube ルールが [ コード品質ルール ](/help/using/code-quality-testing.md#code-quality-testing-step) で利用できるようになりました。

次のパイプラインテキスト変数を設定することにより、新しいルールを「アーリーチェック」することができます（下のスクリーンショットを参照）。

`CM_BUILD_IMAGE_OVERRIDE` = `self-service-build:sonar-99-upgrade-java17or21`

さらに、次の変数を設定して、コード品質ステップが同じコミットに対して実行されるようにします（通常、同じコ `commitId` ットに対してスキップされます）。

`CM_DISABLE_BUILD_REUSE` = `true`

![ 変数設定ページ ](/help/release-notes/assets/variables-config.png)

>[!NOTE]
>
>Adobeでは、メインの実稼動パイプラインと同じブランチに設定された新しい CI/CD コード品質パイプラインを作成することをお勧めします。 2025 年 2 月 13 日（PT）リリースより前に *適切な変数を設定し、新しく適用されたルールにブロッカーが導入されないことを検証します*。

<!-- ## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features. -->


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
