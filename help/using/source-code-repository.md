---
title: ソースコードリポジトリ
seo-title: Adobe AEM Cloud Manager のソースコードリポジトリ
description: このページでは、Cloud Manager で管理するプログラムごとにプロビジョニングされる Git リポジトリについて説明します。
seo-description: このページでは、Adobe AEM Cloud Manager で管理するプログラムごとにプロビジョニングされる Git リポジトリについて説明します。
uuid: 2c42775f-8703-43f7-bad2-7dc086ea9dd7
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER／CLOUDMANAGER
topic-tags: requirements
discoiquuid: f90f0f4c-c1ff-47f6-8d97-ff5018561bf2
translation-type: ht
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# ソースコードリポジトリ {#source-code-repository}

## Cloud Manager リポジトリ {#cloud-manager-repository}

[!UICONTROL AEM Managed Services] サブスクリプションには、アドビでプロビジョニングおよび管理されるソースコードリポジトリが含まれます。各顧客のプログラムには、1 つの一意な **Git リポジトリ** が割り当てられ、関連するコードが保存および保護されます。

ベストプラクティスとしては、常に Cloud Manager の Git リポジトリを使用してください。これは最初、設定済みのブランチやサンプルプロジェクトがない空の状態になっています。Cloud Manager の Git リポジトリを使用するために、任意の Git 互換クライアントを使用してブランチの作成、コードの保存および取得、コミット履歴の一覧表示などをおこなえるようになる **プライベートアクセストークン** が提供されます。

Git でブランチを設定する方法について詳しくは、[リリースブランチの設定](configure-your-release-branches.md)を参照してください。

Cloud Manager の **Git リポジトリ** を CI／CD パイプラインで使用する方法について詳しくは、[CI／CD パイプラインの設定](configuring-pipeline.md)を参照してください。

## オンプレミスリポジトリ {#on-premise-repository}

場合によっては、既存の Git リポジトリがあり、それを引き続き使用したいことがあります。そのような場合、複数のリモートリポジトリをサポートする Git の機能を使用できます。日々の開発は、お使いの Git リポジトリで引き続きおこなわれます。リリースブランチを実稼動環境にデプロイする準備ができたら、最新のコードを Cloud Manager の Git リポジトリにプッシュし、Cloud Manager CI／CD パイプラインをトリガーします。

>[!NOTE]
>
>よく使用される Git コマンドについては、[Git チートシート](https://education.github.com/git-cheat-sheet-education.pdf)を参照してください。

