---
title: Adobe Cloud Manager と Git の統合
description: このビデオシリーズでは、顧客管理（オンプレミス）の Git リポジトリと Adobe Cloud Manager の設定および統合について順を追って説明します。
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
TQID: https://experienceleague.adobe.com/fyGrLuc1bIBY9ZAgYiULxxJQy-ZZBLYtAAdYgqzSLAM
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 2011f63c513689f571d21772752348388c2f342a
workflow-type: tm+mt
source-wordcount: 356
ht-degree: 76%

---

# Adobe Cloud Manager と Git の統合

Adobe Cloud Manager には、Cloud Manager の CI/CD パイプラインを使用したコードのデプロイに使用される単一の Git リポジトリがプロビジョニングされます。 提供されているCloud ManagerのGit リポジトリを使用するか、オンプレミスまたは顧客管理のGit リポジトリをCloud Managerと統合するオプションがあります。

## Git 統合の概要

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

このビデオシリーズでは、顧客が管理する Git リポジトリと Cloud Manager の統合に関するユースケースをいくつか紹介します。

* [初期同期](#initial-sync)
* [基本分岐戦略](#branching-strategy)
* [機能分岐の開発](#feature-development)
* [実稼動のデプロイメント](#production-deployment)
* [リリースタグの同期](#sync-tags)

このビデオシリーズでは、Gitとソース管理に関する基本的な知識が必要です。 Git について詳しくは、[以下のその他のリソース](#additional-resources)を参照してください。

このビデオシリーズで概要を説明する手順と命名規則は、顧客管理 Git リポジトリと Cloud Manager を使用する際のベストプラクティスです。 ここで示す規則とワークフローは、個々の開発チームに合わせて調整されています。

Cloud Manager の完全な概要については、[Cloud Manager の概要](/help/introduction.md)を参照してください。

## 初期同期 {#initial-sync}

顧客が管理する Git リポジトリを Cloud Manager の Git リポジトリと同期する最初の手順。

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## 基本分岐戦略 {#branching-strategy}

Cloud Managerの[実稼動環境](/help/using/production-pipelines.md)および[実稼動以外のパイプライン &#x200B;](/help/using/non-production-pipelines.md)を使用するように、基本的な分岐を設定します。

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## 機能分岐の開発 {#feature-development}

機能分岐を使用して、顧客が管理する Git リポジトリ内のコード変更を分離し、Cloud Manager の Git リポジトリと同期して、コードの品質と検証テストに実稼動以外のパイプラインを使用します。

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## 実稼動デプロイメント {#production-deployment}

顧客管理 Git リポジトリで本番リリースのコードを準備し、Cloud Manager の Git リポジトリと同期して、ステージング環境と本番環境にデプロイします。

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## リリースタグの同期 {#sync-tags}

Cloud Manager Git リポジトリのリリースタグを、顧客管理 Git リポジトリに同期できます。 この機能により、ステージング環境と本番環境の両方にデプロイされたコードを把握できます。

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## その他のリソース {#additional-resources}

* [Cloud Manager の概要](/help/introduction.md)
* [GitHubのリソース](https://docs.github.com/en/get-started/git-basics/set-up-git)
* [Atlassian Git Tutorials](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
