---
title: ソースコードリポジトリー
description: Cloud Manager 内のプログラムごとにプロビジョニングされる Git リポジトリについて説明します。
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
TQID: https://experienceleague.adobe.com/hdEpqKW0NluPs-w37SeLzpd-EHJNqb2nfSAMQ35man8
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: b24e9550f11486e7ed8da31d5da27f85ad5acaf2
workflow-type: tm+mt
source-wordcount: 236
ht-degree: 44%

---

# ソースコードリポジトリ {#source-code-repository}

Cloud Manager 内のプログラムごとにプロビジョニングされる Git リポジトリについて説明します。

## Cloud Manager リポジトリ {#cloud-manager-repository}

[!UICONTROL AEM Managed Services] サブスクリプションには、アドビでプロビジョニングおよび管理されるソースコードリポジトリが含まれます。 各プログラムには一意のGit リポジトリが割り当てられ、関連するコードが保存され、保護されます。

ベストプラクティスとして、ブランチを設定したり、サンプルプロジェクトを作成したりすることなく、常に空のCloud Manager Git リポジトリを使用します。 Cloud Manager は Git リポジトリ用のプライベートアクセストークンを提供するので、任意の Git クライアントを使用して分岐の作成、コードの管理、コミット履歴の取得を行うことができます。

Git に分岐を設定する方法について詳しくは、[リリース分岐の設定](/help/getting-started/configuring-branches.md)を参照してください。

Cloud Manager Git リポジトリをCI/CD パイプラインと共に使用する方法について詳しくは、[実稼動パイプラインの設定](/help/using/production-pipelines.md)および[実稼動以外のパイプラインの設定](/help/using/non-production-pipelines.md)を参照してください。

## オンプレミスリポジトリ {#on-premise-repository}

既存のGit リポジトリがあり、それを引き続き使用する場合は、複数のリモートリポジトリにGitの機能を使用します。 開発はGit リポジトリで続行されます。 リリースブランチを実稼動環境にデプロイする準備ができたら、最新のコードをCloud Manager Git リポジトリにプッシュして、Cloud Manager CI/CD パイプラインをトリガーできます。

一般的なGit コマンドを表示するには、[Git リファレンスガイド &#x200B;](https://education.github.com/git-cheat-sheet-education.pdf)を参照してください。
