---
title: GitHub チェック注釈
description: GitHub チェックがプライベートリポジトリの PR に注釈を付けて、役立つフィードバックを提供する方法について説明します。
exl-id: 15178de8-8a8a-4300-8510-88875ad0fc8c
source-git-commit: 147eec6368875aabb252d759909c0309a82ef3db
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 32%

---


# GitHub チェック注釈 {#github-annotations}

GitHubがプライベートリポジトリの注釈PRをチェックしてフィードバックを提供する方法について説明します。

## 概要 {#overview}

Cloud Manager プログラムに[&#x200B; プライベートリポジトリ &#x200B;](private-repositories.md)を使用している場合、GitHubのチェックは、プルリクエストごとに自動的に実行されます。 これらのチェックには、コードの問題をできるだけ早く特定するのに役立つ情報が注釈されています。

![GitHub チェック注釈の例](assets/github-check-annotations.png)

[SonarQube](/help/using/custom-code-quality-rules.md) によって検出された[コード品質](/help/using/code-quality-testing.md)の問題が明確にリストされます。

![コードに関する問題の注釈の例](assets/github-check-annotations-example.png)

問題を含む正確なコード行が提供され、それを選択して関連するコードを表示できます。 これらの注釈は、プルリクエストの注釈だけでなく、すべてのコードの問題に対して提供されます。

![コードに関する問題の注釈例](assets/github-check-annotations-example-code.png)

注釈付きの行はすべて、GitHub プルリクエストの「**変更済みファイル**」タブに集約されます。 プルリクエストで変更されていないファイルの注釈は、別のセクションに表示されます。

![「変更済みファイル」タブの注釈の例](assets/github-check-annotations-files-changed.png)

## コード品質パイプライン {#code-quality-pipelines}

[&#x200B; コード品質](/help/using/code-quality-testing.md)の結果は、**チェック** タブの下部にあるCloud Managerが自動的にトリガーするパイプラインにも表示されます。 プルリクエストのチェックの&#x200B;**Details**&#x200B;からもアクセスできます。

![注釈の例](assets/github-check-annotations-code-quality.png)

![注釈の例](assets/github-check-annotations-code-quality-2.png)

また、イシューをCSV ファイルとして表示することもできます。 この情報には、[Cloud Managerでのパイプライン実行の詳細を表示](/help/using/managing-pipelines.md)することによってアクセスできます。
