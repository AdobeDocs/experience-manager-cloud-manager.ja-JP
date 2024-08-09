---
title: ソースコードリポジトリ
description: Cloud Manager 内のプログラムごとにプロビジョニングされる Git リポジトリについて説明します。
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 83%

---


# ソースコードリポジトリ {#source-code-repository}

Cloud Manager 内のプログラムごとにプロビジョニングされる Git リポジトリについて説明します。

## Cloud Manager リポジトリ {#cloud-manager-repository}

[!UICONTROL AEM Managed Services] サブスクリプションには、アドビでプロビジョニングおよび管理されるソースコードリポジトリが含まれます。各プログラムには一意な Git リポジトリが 1 つ割り当てられ、関連するコードがそこで保存および保護されます。

ベストプラクティスとして、常に Cloud Manager の Git リポジトリを使用してください。このリポジトリは、ブランチの設定やサンプルプロジェクトがない空の状態で提供されます。Cloud Manager の Git リポジトリを使用するために、任意の Git クライアントを使用してブランチの作成、コードの保存および取得、コミット履歴の一覧表示などを行うためのプライベートアクセストークンが提供されます。

Git にブランチをセットアップする方法について詳しくは、[ リリースブランチの設定 ](/help/getting-started/configuring-branches.md) を参照してください。

Cloud Managerの Git リポジトリを CI/CD パイプラインで使用する方法について詳しくは、[ 実稼動パイプラインの設定 ](/help/using/production-pipelines.md) および [ 実稼動以外のパイプラインの設定 ](/help/using/non-production-pipelines.md) を参照してください。

## オンプレミスリポジトリ {#on-premise-repository}

既存の Git リポジトリがあり、それを引き続き使用したい場合は、複数のリモートリポジトリに対して Git の機能を使用できます。日々の開発は、Git リポジトリで引き続き行われます。リリースブランチを実稼動環境にデプロイする準備ができたら、最新のコードを Cloud Manager の Git リポジトリにプッシュし、Cloud Manager CI／CD パイプラインをトリガーすることができます。

よく使用される Git コマンドを確認するには、GitHub web サイトで [Git チートシート](https://education.github.com/git-cheat-sheet-education.pdf)を参照してください。
