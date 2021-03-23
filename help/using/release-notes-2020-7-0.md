---
title: リリースノート（2020.7.0）
seo-title: AEM Cloud Manager リリースノート（2020.7.0）
description: このページでは、Cloud Manager リリース 2020.7.0 について説明します。
seo-description: このページでは、AEM Cloud Manager リリース 2020.7.0 について説明します。
feature: リリース情報
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 100%

---

# リリースノート（2020.7.0） {#release-notes-for}

以下の節では [!UICONTROL Cloud Manager] リリース 2020.7.0 の一般リリースノートの概要を説明します。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2020.7.0 のリリース日は 2020 年 7 月 09 日です。

## 新機能 {#whats-new}

* 実稼動環境でのデプロイメント中に、ロードバランサーから Dispatcher インスタンスをデタッチおよびアタッチする際、より一貫した方法で動作するようになりました。

* Cloud Manager ビルドコンテナで、Java 8 と Java 11 の両方がサポートされるようになりました。

* Cloud Manager のパイプラインで、カスタマーセットの変数とシークレットがサポートされるようになりました。
詳細は、「 [パイプライン変数](/help/using/build-environment-details.md#pipeline-variables)」を参照してください。

## バグ修正 {#bug-fixes}

* 非実稼動パイプライン編集ページの「**キャンセル**」および「**保存**」のオプションが常に表示されていませんでした。

* コード品質プロセスで特定のエラーが発生すると、ログファイルが正しく生成されない場合があります。

* 一部の大規模なパイプラインステップログは、ユーザーインターフェイスから一貫性のある方法でダウンロードできませんでした。

## 既知の問題 {#known-issues}

* AMS 環境にスタンバイインスタンスが含まれる場合、ログに記録されるメッセージには、そのインスタンスがスタンバイモードになっておらず、ダウンしていることが示されます。

* コードカバレッジの計算方法が変更されたことで、Jacoco プラグインの&#x200B;_最小_&#x200B;バージョンが 0.7.5.201505241946（2015 年 5 月リリース）になりました。古いバージョンを明示的に参照するお客様は、コード品質プロセスでエラーメッセージを受け取ります。
