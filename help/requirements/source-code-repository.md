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
source-git-commit: 50eb58593d7f78492fd384c99c3727c5f731c989
workflow-type: tm+mt
source-wordcount: 254
ht-degree: 100%

---

# ソースコードリポジトリ {#source-code-repository}

Cloud Manager 内のプログラムごとにプロビジョニングされる Git リポジトリについて説明します。

## Cloud Manager リポジトリ {#cloud-manager-repository}

[!UICONTROL AEM Managed Services] サブスクリプションには、アドビでプロビジョニングおよび管理されるソースコードリポジトリが含まれます。 各プログラムには一意な Git リポジトリが 1 つ割り当てられ、関連するコードがそこで保存および保護されます。

ベストプラクティスとして、常に Cloud Manager の Git リポジトリを使用してください。このリポジトリは、分岐の設定やサンプルプロジェクトがない空の状態で提供されます。 Cloud Manager は Git リポジトリ用のプライベートアクセストークンを提供するので、任意の Git クライアントを使用して分岐の作成、コードの管理、コミット履歴の取得を行うことができます。

Git に分岐を設定する方法について詳しくは、[リリース分岐の設定](/help/getting-started/configuring-branches.md)を参照してください。

Cloud Manager の Git リポジトリを CI/CD パイプラインで使用する方法について詳しくは、[実稼動パイプラインの設定](/help/using/production-pipelines.md)および[実稼動以外のパイプラインの設定](/help/using/non-production-pipelines.md)を参照してください。

## オンプレミスリポジトリ {#on-premise-repository}

既存の Git リポジトリがあり、それを引き続き使用する場合は、複数のリモートリポジトリに対して Git の機能を使用できます。 日々の開発は、Git リポジトリで引き続き行われます。 リリース分岐を実稼動環境にデプロイする準備ができたら、最新のコードを Cloud Manager の Git リポジトリにプッシュし、Cloud Manager CI/CD パイプラインをトリガーできます。

よく使用される Git コマンドについて詳しくは、[Git チートシート](https://education.github.com/git-cheat-sheet-education.pdf)を参照してください。
