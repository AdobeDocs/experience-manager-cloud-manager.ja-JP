---
title: リリースノート（2020.7.0）
seo-title: AEM Cloud Manager リリースノート（2020.7.0）
description: このページでは、Cloud Manager リリース 2020.7.0 について説明します。
seo-description: このページでは、AEM Cloud Manager リリース 2020.7.0 について説明します。
translation-type: tm+mt
source-git-commit: 02515ac6e3ac54909e23a276a78f571ea5c249c4
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 35%

---

# リリースノート（2020.7.0） {#release-notes-for}

以下の節では [!UICONTROL Cloud Manager] リリース 2020.7.0 の一般リリースノートの概要を説明します。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2020.7.0 のリリース日は 2020 年 7 月 09 日です。

## 新機能 {#whats-new}

* 実稼働環境でのデプロイメント中に、ディスパッチャーインスタンスをロードバランサーからデタッチおよびアタッチする際に、動作がより一貫した方法になりました。

* Cloud Managerビルドコンテナで、Java 8とJava 11の両方がサポートされるようになりました。

* Cloud Managerのパイプラインで、カスタマーセットの変数とシークレットがサポートされるようになりました。 詳細は、「 [パイプライン変数](/help/using/create-an-application-project.md#pipeline-variables) 」を参照してください。

## バグ修正 {#bug-fixes}

* 非実稼働パイプライン編集ページの **「キャンセル** 」(Cancel)と「 **保存** 」(Save)のオプションが常に表示されていませんでした。

* コード品質プロセスで一部のエラーが発生すると、ログファイルが正しく生成されない場合があります。

* 一部の大規模なパイプラインステップログは、ユーザーインターフェイスを通じて一貫性のある方法でダウンロードできませんでした。

## 既知の問題 {#known-issues}

* AMS環境にスタンバイインスタンスが含まれる場合、ログに記録されるメッセージには、そのインスタンスがスタンバイモードではなくダウンしていることが示されます。
