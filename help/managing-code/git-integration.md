---
title: Adobe Cloud Manager と Git の統合
description: このビデオシリーズでは、顧客が管理する（オンプレミスの）Git リポジトリとAdobeCloud Manager の設定および統合に関する手順を説明します。
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
source-git-commit: 91e909273bf2b21d7f6413731923011915079e45
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 53%

---


# Adobe Cloud Manager と Git の統合

Adobe Cloud Manager には、Cloud Manager の CI／CD パイプラインを使用したコードのデプロイに使用される単一の Git リポジトリーがプロビジョニングされます。Cloud Manager の Git リポジトリをそのまま使用することも、オンプレミスまたは顧客管理の Git リポジトリを Cloud Manager と統合することもできます。

## Git 統合の概要

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

このビデオシリーズでは、顧客が管理する Git リポジトリと Cloud Manager の統合に関する使用例をいくつか紹介します。

* [初期同期](#initial-sync)
* [基本分岐戦略](#branching-strategy)
* [機能ブランチの開発](#feature-development)
* [実稼動のデプロイメント](#production-deployment)
* [リリースタグの同期](#sync-tags)

このビデオシリーズは、Git とソース管理に関する基本的な知識を前提としています。 Git について詳しくは、以下の[その他のリソース](#additional-resources)を参照してください。

このビデオシリーズで概要を説明する手順と命名規則は、顧客管理 Git リポジトリーと Cloud Manager を使用する際のベストプラクティスです。規則とワークフローは、個々の開発チームに合わせて調整してください。

Cloud Manager の完全な概要については、ドキュメントを確認してください [Cloud Manager の概要です。](/help/introduction.md)

## 初期同期 {#initial-sync}

顧客が管理する Git リポジトリを Cloud Manager の Git リポジトリと同期するための最初の手順。

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## 基本分岐戦略 {#branching-strategy}

Cloud Manager の[実稼動パイプライン](/help/using/production-pipelines.md)と[実稼動以外のパイプライン](/help/using/non-production-pipelines.md)を活用するために、基本的なブランチ戦略を設定します。

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## 機能ブランチの開発 {#feature-development}

機能ブランチを使用して、顧客が管理する Git リポジトリー内のコード変更を分離し、Cloud Manager の Git リポジトリーと同期して、コードの品質と検証のテストに非実稼動パイプラインを使用します。

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## 実稼動のデプロイメント {#production-deployment}

顧客が管理する Git リポジトリで実稼動版リリースのコードを準備し、Cloud Manager の Git リポジトリと同期して、ステージング環境と実稼動環境にデプロイします。

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## リリースタグの同期 {#sync-tags}

Cloud Manager の Git リポジトリのリリースタグを、顧客が管理する Git リポジトリに同期して、ステージング環境と実稼動環境にデプロイされたコードを明確に把握できるようにします。

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## その他のリソース {#additional-resources}

* [Cloud Manager の概要](/help/introduction.md)
* [GitHub リソース](https://try.github.io)
* [Atlassian Git チュートリアル](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
