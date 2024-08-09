---
title: Adobe Cloud Manager と Git の統合
description: このビデオシリーズでは、顧客管理（オンプレミス）の Git リポジトリと Adobe Cloud Manager のセットアップおよび統合について順を追って説明します。
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 91%

---


# Adobe Cloud Manager と Git の統合

Adobe Cloud Manager には、Cloud Manager の CI／CD パイプラインを使用したコードのデプロイに使用される単一の Git リポジトリーがプロビジョニングされます。Cloud Manager の Git リポジトリをそのまま使用することもできますし、オンプレミスまたは顧客が管理する Git リポジトリを Cloud Manager と統合することもできます。

## Git 統合の概要

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

このビデオシリーズでは、顧客が管理する Git リポジトリと Cloud Manager の統合に関するユースケースをいくつか紹介します。

* [初期同期](#initial-sync)
* [基本分岐戦略](#branching-strategy)
* [機能ブランチの開発](#feature-development)
* [実稼動のデプロイメント](#production-deployment)
* [リリースタグの同期](#sync-tags)

このビデオシリーズでは、Git とソース管理に関する基本的な知識を前提としています。Git について詳しくは、以下の[その他のリソース](#additional-resources)を参照してください。

このビデオシリーズで概要を説明する手順と命名規則は、顧客管理 Git リポジトリーと Cloud Manager を使用する際のベストプラクティスです。規則とワークフローは、個々の開発チームに合わせて調整してください。

Cloud Managerの概要については、[Cloud Managerの概要 ](/help/introduction.md) を参照してください。

## 初期同期 {#initial-sync}

顧客が管理する Git リポジトリを Cloud Manager の Git リポジトリと同期するための最初の手順。

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## 基本分岐戦略 {#branching-strategy}

Cloud Managerの [ 実稼動用パイプライン ](/help/using/production-pipelines.md) および [ 実稼動以外のパイプライン ](/help/using/non-production-pipelines.md) を活用するために、基本的なブランチ戦略を設定します。

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## 機能ブランチの開発 {#feature-development}

機能ブランチを使用して、顧客が管理する Git リポジトリー内のコード変更を分離し、Cloud Manager の Git リポジトリーと同期して、コードの品質と検証のテストに非実稼動パイプラインを使用します。

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## 実稼動のデプロイメント {#production-deployment}

顧客が管理する Git リポジトリで実稼働版リリースのコードを準備したあと、ステージング環境と実稼働環境にデプロイするために Cloud Manager の Git リポジトリと同期します。

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## リリースタグの同期 {#sync-tags}

Cloud Manager の Git リポジトリのリリースタグを、顧客が管理する Git リポジトリと同期させて、ステージング環境と実稼動環境にデプロイされたコードを把握できるようにします。

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## その他のリソース {#additional-resources}

* [Cloud Manager の概要](/help/introduction.md)
* [GitHub リソース](https://try.github.io)
* [Atlassian Git チュートリアル](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
