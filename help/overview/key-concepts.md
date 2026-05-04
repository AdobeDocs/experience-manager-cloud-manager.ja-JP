---
title: 主な概念
description: すべての強力なツールと同様に、Cloud Manager には様々な概念や用語が含まれています。 このドキュメントでは、Cloud Manager の使用を開始する際に最も重要な事項の一部をまとめます。
exl-id: 86dfc976-f3da-479a-9faa-08f40ca909e0
TQID: https://experienceleague.adobe.com/usnXqDujeZ04U5hOtiI76aemlj-ceToAOtAYS9U0UuM
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 50eb58593d7f78492fd384c99c3727c5f731c989
workflow-type: tm+mt
source-wordcount: 431
ht-degree: 95%

---

# 主な概念 {#key-concepts}

すべての強力なツールと同様に、Cloud Manager には様々な概念や用語が含まれています。 このドキュメントでは、Cloud Manager の使用を開始する際に最も重要な事項の一部をまとめます。

## アプリケーション {#application}

また、アプリケーションは、特定の使用例とニーズに応じて基盤となる[ソリューション](#solution)（AEM Sites や AEM Assets など）を適応させるために顧客が作成したカスタマイズと設定のセットです。 アプリケーションは、複数の[アーティファクト](#artifact)で構成される論理単位です。

アプリケーションの例は、架空の [WKND ライフスタイルアプリケーション](https://experienceleague.adobe.com/ja/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview)です。

## アーティファクト {#artifact}

アーティファクトはデプロイ可能なユニットで、ソースコードを 1 つのユニットに変換するビルドプロセスの結果です。 例えば、ソースコードを格納した .zip ファイルなどです。

## アーティファクトリポジトリ {#artifact-repository}

アーティファクトリポジトリは、顧客固有の[アーティファクト](#artifact)が保存および保護される格納場所です。

## 環境 {#environment}

環境は、[プログラム](#program)内の仮想マシンの単一クラスターです。 AEM の場合は、1 つのオーサーインスタンス（オプションでコールドスタンバイオーサーインスタンスも追加）、0 または 1 つ以上のパブリッシュインスタンス、1 つ以上の Dispatcher インスタンス、1 つのロードバランサーで構成されます。

## Git リポジトリ {#git-repository}

Git リポジトリは、顧客固有のソースコードが保存されている場所であり、[Git を使用して](https://git-scm.com)アクセスできます。

## インスタンス {#instance}

インスタンスは、AEM [ソリューション](#solution)を実行している特定の仮想サーバーです。 インスタンスは、デプロイメントの観点から見た単一の論理単位を表します。

## 組織 {#organization}

組織は、企業顧客を表すアドビの構成要素です。 1つの企業では、AdobeのIdentity Management System （IMS）でのプロビジョニング方法に応じて、複数の組織が存在する場合があります。

## パイプライン {#pipeline}

パイプラインは、順に実行される一連のデプロイメントステップです。

## 製品 {#product}

製品は、組織でライセンスされた[ソリューション](#solution)に含まれる機能の特定のセットです。 組織内の様々な[プログラム](#program)には、AEM Sites、AEM Assets、AEM Forms などの異なる製品セットに対する権利が付与される場合があります。

## プログラム {#program}

プログラムは、通常、購入したサービス契約（SLA）に対応する顧客の構想の論理的なグループ化をサポートする環境のセットです。 各プログラムには 1 つの本番環境があり、本番環境以外の環境が多数あることもあります。

## ソリューション {#solution}

ソリューションは、Adobe [!UICONTROL Experience Cloud] ソリューションの 1 つです。 例えば、Adobe Experience Manager、Adobe Target、Adobe Analytics などです。

## ステップ {#step}

ステップは、[パイプライン](#pipeline)の構成要素としていくつかの作業単位を実行する設定済みの命令セットです。
