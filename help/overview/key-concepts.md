---
title: 主な概念
description: すべての強力なツールと同様に、Cloud Manager には様々な概念や用語が含まれています。このドキュメントでは、Cloud Manager の使用を開始する際に最も重要な事項の一部をまとめます。
exl-id: 86dfc976-f3da-479a-9faa-08f40ca909e0
source-git-commit: 73e322cf93dc7709b7581860974079c8d94034ba
workflow-type: ht
source-wordcount: '419'
ht-degree: 100%

---


# 主な概念 {#key-concepts}

すべての強力なツールと同様に、Cloud Manager には様々な概念や用語が含まれています。このドキュメントでは、Cloud Manager の使用を開始する際に最も重要な事項の一部をまとめます。

## アプリケーション {#application}

また、アプリケーションは、特定の使用例とニーズに応じて基盤となる[ソリューション](#solution)（AEM Sites や AEM Assets など）を適応させるために顧客が作成したカスタマイズと設定のセットです。アプリケーションは、複数の[アーティファクト](#artifact)で構成される論理単位です。

アプリケーションの例は、架空の [WKND ライフスタイルアプリケーション](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=ja)です。

## アーティファクト {#artifact}

アーティファクトはデプロイ可能なユニットで、ソースコードを 1 つのユニットに変換するビルドプロセスの結果です。例えば、ソースコードを格納した .zip ファイルなどです。

## アーティファクトリポジトリ {#artifact-repository}

アーティファクトリポジトリは、顧客固有の[アーティファクト](#artifact)が保存および保護される格納場所です。

## 環境 {#environment}

環境は、プログラム内の仮想マシンの単一クラスターです。[](#program) AEM の場合は、1 つのオーサーインスタンス（オプションでコールドスタンバイオーサーインスタンスも追加）、0 または 1 つ以上のパブリッシュインスタンス、1 つ以上のディスパッチャーインスタンス、1 つのロードバランサーで構成されます。

## Git リポジトリ {#git-repository}

Git リポジトリは、顧客固有のソースコードが保存されている場所であり、[Git を使用して](https://git-scm.com)アクセスできます。

## インスタンス {#instance}

インスタンスは、AEM [ソリューションを実行している特定の仮想サーバーです。](#solution) インスタンスは、デプロイメントの観点から見た単一の論理単位を表します。

## 組織 {#organization}

組織は、企業顧客を表すアドビの構成要素です。アドビの Identity Management System (IMS) でのプロビジョニング方法によっては、1 つの会社に複数の組織が存在することがあります。

## パイプライン {#pipeline}

パイプラインは、順に実行される一連のデプロイメントステップです。

## 製品 {#product}

製品は、組織でライセンスされた[ソリューション](#solution)に含まれる機能の特定のセットです。組織内の様々な[プログラム](#program)には、AEM Sites、AEM Assets、AEM Forms などの異なる製品セットに対する権利が付与される場合があります。

## プログラム {#program}

プログラムは、通常、購入したサービス契約（SLA）に対応する顧客の構想の論理的なグループ化をサポートする環境のセットです。各プログラムには 1 つの実稼動環境があり、実稼動環境以外の環境が多数あることもあります。

## ソリューション {#solution}

ソリューションは、Adobe [!UICONTROL Experience Cloud] ソリューションの 1 つです。例えば、Adobe Experience Manager、Adobe Target、Adobe Analytics などです。

## 手順 {#step}

ステップは、[パイプライン](#pipeline)の構成要素としていくつかの作業単位を実行する設定済みの命令セットです。
