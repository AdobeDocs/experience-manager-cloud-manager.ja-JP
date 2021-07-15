---
title: リリースノート（2021.7.0）
description: このページでは、Cloud Manager リリース 2021.7.0 について説明します。
feature: リリース情報
source-git-commit: fec742eb023e9811ee80951bd25fc2023df52d66
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# リリースノート（2021.7.0） {#release-notes-for}

以下の節では、[!UICONTROL Cloud Manager] リリース 2021.7.0 の一般リリースノートの概要を説明します。

>[!NOTE]
>AEM as a Cloud Service での Cloud Manager の最新のリリースノートについては、[現在のリリースノート](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=ja#getting-access)を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2021.7.0 のリリース日は 2021 年 7 月 15 日（PT）です。次回のリリースは2021年8月13日に予定されています。

## 新機能 {#whats-new}

* お客様は、Cloud ManagerのビルドプロセスにAzul 8および11 JDKを使用できるようになり、ツールチェーン互換のMavenプラグインに対してこれらのJDKの1つを使用するか、Mavenプロセスの実行全体を&#x200B;*または*&#x200B;使用するかを選択できます。

* 送信エグレスIPがビルドステップログファイルに記録されます。

* **「Gitを管理」**&#x200B;ボタンのタイトルが&#x200B;**「Git情報にアクセス」**&#x200B;に変更され、ダイアログが視覚的に更新されました。

* Cloud Managerで使用されるAEMプロジェクトアーキタイプのバージョンがバージョン28に更新されました。

* 予期しないトポロジの再設定が発生すると、詳細なテストレポートがパイプライン実行の詳細ページから使用できなくなる場合がありました。

## バグ修正 {#bug-fixes}

* 存在しない実行の実行の詳細ページに手動で移動しても、エラーが表示されず、無限の読み込み画面のみが表示されていた問題を修正しました。

* 場合によっては、Sitesのパフォーマンスで使用される失敗したコンテナの自動再試行が2時間有効にならず、テストエラーが発生することがありました。

## 既知の問題 {#known-issues}

Azul JDKを使用するように切り替えるお客様は、Azul JDKでエラーなしにコンパイルされるとは限らないことに注意する必要があります。 切り替える前に、ローカルでテストすることを強くお勧めします。