---
title: Adobe Cloud Manager と Git の統合
description: このビデオシリーズでは、顧客管理（オンプレミス）の Git リポジトリと Adobe Cloud Manager の設定および統合について順を追って説明します。
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
source-git-commit: 51bd685a17eb9d68b1ec8245e6167cab02101fc1
workflow-type: ht
source-wordcount: '331'
ht-degree: 100%

---


# Adobe Cloud Manager と Git の統合

Adobe Cloud Manager には、Cloud Manager の CI/CD パイプラインを使用したコードのデプロイに使用される単一の Git リポジトリがプロビジョニングされます。Cloud Manager の Git リポジトリをそのまま使用することもできますし、オンプレミスまたは顧客が管理する Git リポジトリを Cloud Manager と統合することもできます。

## Git 統合の概要

>[!VIDEO](https://video.tv.adobe.com/v/31425?captions=jpn)

このビデオシリーズでは、顧客が管理する Git リポジトリと Cloud Manager の統合に関するユースケースをいくつか紹介します。

* [初期同期](#initial-sync)
* [基本分岐戦略](#branching-strategy)
* [機能ブランチの開発](#feature-development)
* [実稼動のデプロイメント](#production-deployment)
* [リリースタグの同期](#sync-tags)

このビデオシリーズでは、Git とソース管理に関する基本的な知識を前提としています。Git について詳しくは、[以下のその他のリソース](#additional-resources)を参照してください。

このビデオシリーズで概要を説明する手順と命名規則は、顧客管理 Git リポジトリと Cloud Manager を使用する際のベストプラクティスです。規則とワークフローは、個々の開発チームに合わせて調整してください。

Cloud Manager の完全な概要については、[Cloud Manager の概要](/help/introduction.md)を参照してください。

## 初期同期 {#initial-sync}

顧客が管理する Git リポジトリを Cloud Manager の Git リポジトリと同期する最初の手順。

>[!VIDEO](https://video.tv.adobe.com/v/31424/?quality=12&captions=jpn)

## 基本分岐戦略 {#branching-strategy}

Cloud Manager の[実稼動パイプライン](/help/using/production-pipelines.md)と[実稼動以外のパイプライン](/help/using/non-production-pipelines.md)を活用するには、基本的な分岐戦略を設定します。

>[!VIDEO](https://video.tv.adobe.com/v/31423/?quality=12&captions=jpn)

## 機能分岐の開発 {#feature-development}

機能分岐を使用して、顧客が管理する Git リポジトリ内のコード変更を分離し、Cloud Manager の Git リポジトリと同期して、コードの品質と検証テストに実稼動以外のパイプラインを使用します。

>[!VIDEO](https://video.tv.adobe.com/v/31422/?quality=12&captions=jpn)

## 実稼動デプロイメント {#production-deployment}

顧客管理 Git リポジトリで実稼動版リリースのコードを準備し、Cloud Manager の Git リポジトリと同期して、ステージング環境と実稼動環境にデプロイします。

>[!VIDEO](https://video.tv.adobe.com/v/31421/?quality=12&captions=jpn)

## リリースタグの同期 {#sync-tags}

Cloud Manager Git リポジトリのリリースタグを、顧客管理 Git リポジトリに同期できます。この機能により、ステージング環境と実稼動環境の両方にデプロイされたコードを把握できます。

>[!VIDEO](https://video.tv.adobe.com/v/31420/?quality=12&captions=jpn)

## その他のリソース {#additional-resources}

* [Cloud Manager の概要](/help/introduction.md)
* [GitHub リソース](https://docs.github.com/ja/get-started/getting-started-with-git/set-up-git)
* [Atlassian Git チュートリアル](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
