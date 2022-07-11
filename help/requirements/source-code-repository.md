---
title: ソースコードリポジトリー
description: Cloud Manager で管理するプログラムごとにプロビジョニングされる Git リポジトリについて説明します。
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 4%

---


# ソースコードリポジトリ {#source-code-repository}

Cloud Manager で管理するプログラムごとにプロビジョニングされる Git リポジトリについて説明します。

## Cloud Manager リポジトリ {#cloud-manager-repository}

お使いの [!UICONTROL AEM Managed Services] subscription には、Adobeがプロビジョニングおよび管理するソースコードリポジトリが含まれます。 各プログラムには、1 つの一意な Git リポジトリが割り当てられ、関連するコードが保存および保護されます。

ベストプラクティスとしては、常に Cloud Manager の Git リポジトリを使用する必要があります。このリポジトリには、設定済みのブランチやサンプルプロジェクトがない空の状態で表示されます。 Cloud Manager の Git リポジトリを使用するには、任意の Git クライアントを使用してブランチを作成、コードを保存および取得、コミット履歴をリスト化できるプライベートアクセストークンが提供されます。

Git でブランチを設定する方法について詳しくは、 [リリースブランチの設定](/help/getting-started/configuring-branches.md)

Cloud Manager の Git リポジトリを CI/CD パイプラインで使用する方法の詳細については、ドキュメントを参照してください [実稼動パイプラインの設定](/help/using/production-pipelines.md) および [実稼動以外のパイプラインの設定](/help/using/non-production-pipelines.md) を参照してください。

## オンプレミスリポジトリ {#on-premise-repository}

既存の Git リポジトリがあり、それを引き続き使用したい場合は、複数のリモートリポジトリに対して Git の機能を使用できます。 日々の開発は、Git リポジトリで引き続きおこなわれます。 リリースブランチを実稼動環境にデプロイする準備が整ったら、最新のコードを Cloud Manager の Git リポジトリにプッシュして、Cloud Manager CI/CD パイプラインをトリガー化できます。

一般的な Git コマンドについては、 [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf) を GitHub Web サイトに追加します。
