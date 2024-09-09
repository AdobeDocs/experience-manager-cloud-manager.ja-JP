---
title: Adobe Cloud Manager と Git の統合
description: このビデオシリーズでは、顧客管理（オンプレミス）の Git リポジトリーとAdobeのCloud Managerのセットアップおよび統合について順を追って説明します。
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
source-git-commit: 51bd685a17eb9d68b1ec8245e6167cab02101fc1
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 23%

---


# Git とAdobeCloud Managerの統合

Adobe Cloud Managerには、Cloud Managerの CI/CD パイプラインを使用したコードのデプロイに使用される単一の Git リポジトリーがプロビジョニングされます。 Cloud Managerの Git リポジトリをそのまま使用することもできますし、オンプレミスまたは顧客管理の Git リポジトリをCloud Managerと統合することもできます。

## Git 統合の概要

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

このビデオシリーズでは、顧客が管理する Git リポジトリーとCloud Managerの統合に関するユースケースをいくつか紹介します。

* [初期同期](#initial-sync)
* [基本分岐戦略](#branching-strategy)
* [機能ブランチの開発](#feature-development)
* [実稼動のデプロイメント](#production-deployment)
* [リリースタグの同期](#sync-tags)

このビデオシリーズでは、Git とソース管理に関する基本的な知識を前提としています。 Git について詳しくは、[ 以下のその他のリソース ](#additional-resources) を参照してください。

このビデオシリーズで概要を説明する手順と命名規則は、顧客管理 Git リポジトリーとCloud Managerを使用する際のベストプラクティスです。 規則とワークフローは、個々の開発チームに合わせて調整してください。

Cloud Manager の完全な概要については、[Cloud Manager の概要](/help/introduction.md)を参照してください。

## 初期同期 {#initial-sync}

顧客が管理する Git リポジトリーを Cloud Manager の Git リポジトリーと同期するための最初の手順。

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## 基本ブランチ戦略 {#branching-strategy}

Cloud Managerの [ 実稼動用パイプライン ](/help/using/production-pipelines.md) および [ 実稼動以外のパイプライン ](/help/using/non-production-pipelines.md) を活用する基本的なブランチ戦略を設定します。

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## 機能ブランチの開発 {#feature-development}

機能ブランチを使用して、顧客が管理する Git リポジトリー内のコード変更を分離し、Cloud Managerの Git リポジトリーと同期して、コードの品質と検証のテストに実稼動以外のパイプラインを使用します。

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## 実稼動のデプロイメント {#production-deployment}

お客様が管理する Git リポジトリーで実稼動リリースのコードを準備し、Cloud Managerの Git リポジトリーと同期して、ステージング環境と実稼動環境にデプロイします。

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## リリースタグの同期 {#sync-tags}

Cloud Manager Git リポジトリのリリースタグを、顧客管理 Git リポジトリに同期できます。 この機能により、ステージング環境と実稼動環境の両方にデプロイされたコードを可視化できます。

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## その他のリソース {#additional-resources}

* [Cloud Manager の概要](/help/introduction.md)
* [GitHub リソース](https://docs.github.com/en/get-started/getting-started-with-git/set-up-git)
* [Atlassian Git チュートリアル](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
