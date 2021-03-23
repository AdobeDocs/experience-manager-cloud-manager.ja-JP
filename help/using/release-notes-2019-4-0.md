---
title: リリースノート（2019.4.0）
seo-title: AEM Cloud Manager リリースノート（2019.4.0）
description: このページでは、Cloud Manager リリース 2019.4.0 について説明します。
seo-description: このページでは、AEM Cloud Manager リリース 2019.4.0 について説明します。
feature: リリース情報
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 100%

---


# リリースノート（2019.4.0） {#release-notes-for}

[!UICONTROL Cloud Manager] 2019.4.0 リリースには、重要な機能変更は含まれていません。詳しくは、以下の節を参照してください。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2019.4.0 のリリース日は 2019 年 4 月 18 日です。

## 最新情報 {#whats-new}

* Cloud Manager の UI は、英語、フランス語、ドイツ語、日本語で利用できるようになりました。
* デプロイメントの手順に、現在実行中（バックアップの実行中、パッケージのインストール中、ロードバランサーの再設定中）のプロセスが含まれるようになりました。

## バグ修正 {#bug-fixes}

* Dispatcher の変更をデプロイする場合のアプローチが改善され、追加の使用例が処理されるようになりました。
* 一部のインスタンスサイズタイプが環境ページに正しく表示されていませんでした。
* コード品質ルール CQBP-84-dependencies では、WCM Core Components や Asset Share Commons などのアドビの埋め込みライブラリが誤判定されていました。
* 詳細が使用できない場合でも、コードスキャンステップ用の詳細ボタンが有効になっていました。
* 1 分あたりのページビュー数に無効な値が指定されると表示されるエラーメッセージで、KPI の下限が正しくありませんでした。
* 実稼動以外のパイプラインのデプロイメントカテゴリが、間違って大文字になっていました。
* Git リポジトリが正しく設定されていない場合、**概要**&#x200B;ページのコールトゥアクションカードに間違ったテキストが表示されていました。

## 既知の問題 {#known-issues}

* SLA 値が正しく四捨五入されない場合があります。
