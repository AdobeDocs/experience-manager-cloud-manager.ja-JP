---
title: ソースコードリポジトリー
description: Cloud Manager内のプログラムごとにプロビジョニングされる Git リポジトリについて説明します。
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 7%

---


# Source コードリポジトリー {#source-code-repository}

Cloud Manager内のプログラムごとにプロビジョニングされる Git リポジトリについて説明します。

## Cloud Manager リポジトリ {#cloud-manager-repository}

[!UICONTROL AEM Managed Services] サブスクリプションには、アドビでプロビジョニングおよび管理されるソースコードリポジトリが含まれます。各プログラムには一意な Git リポジトリーが 1 つ割り当てられ、関連するコードがそこで保存および保護されます。

ベストプラクティスとしては、常にCloud Managerの Git リポジトリーを使用してください。このリポジトリーは、設定済みのブランチやサンプルプロジェクトがない空の状態で提供されます。 Cloud Managerは、任意の Git クライアントを使用してブランチの作成、コードの管理、コミット履歴の取得などを行うことができる、Git リポジトリー用のプライベートアクセストークンを提供します。

Git にブランチを設定する方法について詳しくは、[ リリースブランチの設定 ](/help/getting-started/configuring-branches.md) を参照してください。

Cloud Managerの Git リポジトリを CI/CD パイプラインで使用する方法について詳しくは、[ 実稼動パイプラインの設定 ](/help/using/production-pipelines.md) および [ 実稼動以外のパイプラインの設定 ](/help/using/non-production-pipelines.md) を参照してください。

## オンプレミスリポジトリ {#on-premise-repository}

既存の Git リポジトリがあり、それを引き続き使用したい場合は、複数のリモートリポジトリに対して Git の機能を使用できます。 日々の開発は、お使いの Git リポジトリで引き続きおこなわれます。 リリースブランチを実稼動環境にデプロイする準備ができたら、最新のコードをCloud Managerの Git リポジトリにプッシュし、Cloud Manager CI/CD パイプラインをトリガーできます。

よく使用される Git コマンドについては、[Git チートシート ](https://education.github.com/git-cheat-sheet-education.pdf) を参照してください。
