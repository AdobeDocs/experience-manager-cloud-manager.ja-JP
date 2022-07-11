---
title: 主要な概念
description: すべての強力なツールと同様に、Cloud Manager には様々な概念や用語が含まれています。 このドキュメントでは、Cloud Manager の使用を開始する際に最も重要な事項の一部をまとめます。
exl-id: 86dfc976-f3da-479a-9faa-08f40ca909e0
source-git-commit: 73e322cf93dc7709b7581860974079c8d94034ba
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 10%

---


# 主要な概念 {#key-concepts}

すべての強力なツールと同様に、Cloud Manager には様々な概念や用語が含まれています。 このドキュメントでは、Cloud Manager の使用を開始する際に最も重要な事項の一部をまとめます。

## アプリケーション {#application}

また、アプリケーションは、基になるを適応させるために顧客が作成したカスタマイズと設定のセットです [ソリューション](#solution) (AEM SitesやAEM Assetsなど ) を使用して、特定の使用例やニーズに応じて変更できます。 アプリケーションは、複数の [アーティファクト。](#artifact)

アプリの例は架空です [WKND ライフスタイルアプリケーション。](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=ja)

## アーティファクト {#artifact}

アーティファクトはデプロイ可能なユニットで、ソースコードを 1 つのユニットに変換するビルドプロセスの結果です。 例えば、ソースコードを含む.zip ファイル。

## アーティファクトリポジトリ {#artifact-repository}

アーティファクトリポジトリは、顧客固有のストレージの場所です [artifacts](#artifact) は保存され、保護されます。

## 環境 {#environment}

1 つの環境は、1 つの [プログラム。](#program) AEMの場合、これは、オーサーインスタンス（オプションで追加のコールドスタンバイオーサリングインスタンスを含む）、0 個以上のパブリッシュインスタンス、1 つ以上の Dispatcher インスタンス、ロードバランサーで構成されます。

## git リポジトリ {#git-repository}

Git リポジトリは、顧客固有のソースコードが保存され、アクセス可能な場所です [git を使用します。](https://git-scm.com)

## インスタンス {#instance}

インスタンスは、AEMを実行している特定の仮想サーバーです [解決策](#solution)インスタンスは、デプロイメントの観点から見た単一の論理単位を表します。

## 組織 {#organization}

組織とは、企業Adobeを表す顧客構成体です。 AdobeのIdentity Managementシステム (IMS) でのプロビジョニング方法に応じて、1 つの会社に複数の組織が存在する場合があります。

## パイプライン {#pipeline}

パイプラインは、順に実行される一連のデプロイメントステップです。

## 製品 {#product}

製品は、 [ソリューション](#solution) ライセンスを取得しました。 異なる [プログラム](#program) 組織内で、AEM Sites、AEM Assets、AEM Formsなど、様々な製品セットに対する権利が付与される場合があります。

## プログラム {#program}

プログラムは、顧客の構想の論理的なグループをサポートする環境のセットで、通常は購入した SLA(Service Level Agreement) に対応します。 各プログラムには 1 つの実稼動環境があり、場合によっては、実稼動環境以外の環境も多数あります。

## 解決策 {#solution}

解決策はAdobeの 1 つ [!UICONTROL Experience Cloud] ソリューション 例：Adobe Experience Manager、Adobe Target、Adobe Analytics。

## 手順 {#step}

ステップとは、ある作業単位を、 [パイプライン。](#pipeline)
