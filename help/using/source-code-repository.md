---
title: ソースコードリポジトリー
seo-title: Source Code Repository for Adobe AEM Cloud Manager
description: このページでは、Cloud Manager で管理するプログラムごとにプロビジョニングされる Git リポジトリーについて説明します。
seo-description: Follow this page to learn about the git repository that is provisioned for each program you have in Adobe AEM Cloud Manager.
uuid: 2c42775f-8703-43f7-bad2-7dc086ea9dd7
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requirements
discoiquuid: f90f0f4c-c1ff-47f6-8d97-ff5018561bf2
feature: Provisioning
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 4f0e1d163001fd18cfa838256c813152d65c3b4c
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 87%

---

# ソースコードリポジトリー {#source-code-repository}

## Cloud Manager リポジトリー {#cloud-manager-repository}

[!UICONTROL AEM Managed Services] サブスクリプションには、アドビでプロビジョニングおよび管理されるソースコードリポジトリーが含まれます。各顧客のプログラムには、1 つの一意な **Git リポジトリー**&#x200B;が割り当てられ、関連するコードが保存および保護されます。

ベストプラクティスとしては、常に Cloud Manager の Git リポジトリーを使用してください。これは最初、設定済みのブランチやサンプルプロジェクトがない空の状態になっています。Cloud Manager の Git リポジトリーを使用するために、任意の Git 互換クライアントを使用してブランチの作成、コードの保存および取得、コミット履歴の一覧表示などをおこなえるようになる&#x200B;**プライベートアクセストークン**&#x200B;が提供されます。

Git でブランチを設定する方法について詳しくは、[リリースブランチの設定](configure-your-release-branches.md)を参照してください。

Cloud Manager の **Git リポジトリ** CI/CD Pipeline を使用する場合は、ドキュメントを参照してください。 [実稼動パイプラインの設定](configuring-production-pipelines.md) および [実稼動以外のパイプラインの設定](configuring-non-production-pipelines.md) を参照してください。

## オンプレミスリポジトリー {#on-premise-repository}

場合によっては、既存の Git リポジトリーがあり、それを引き続き使用したいことがあります。そのような場合、複数のリモートリポジトリーをサポートする Git の機能を使用できます。日々の開発は、お使いの Git リポジトリーで引き続きおこなわれます。リリースブランチを実稼動環境にデプロイする準備ができたら、最新のコードを Cloud Manager の Git リポジトリーにプッシュし、Cloud Manager CI／CD パイプラインをトリガーします。

>[!NOTE]
>
>よく使用される Git コマンドについては、[Git チートシート](https://education.github.com/git-cheat-sheet-education.pdf)を参照してください。
