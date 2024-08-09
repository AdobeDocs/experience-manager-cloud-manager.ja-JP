---
title: GitHub チェック注釈
description: GitHub チェックがプライベートリポジトリの PR を注釈して、役立つフィードバックを提供する方法について説明します。
exl-id: 15178de8-8a8a-4300-8510-88875ad0fc8c
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 86%

---


# GitHub チェック注釈 {#github-annotations}

GitHub チェックがプライベートリポジトリの PR を注釈して、役立つフィードバックを提供する方法について説明します。

## 概要 {#overview}

Cloud Manager プログラムに[プライベートリポジトリ](private-repositories.md)を使用している場合は、プルリクエストのたびに GitHub でのチェックが自動的に実行されます。これらには、コードに関する問題をできるだけ早く理解するのに役立つ有用な情報が注釈として付けられます。

![GitHub チェック注釈の例](assets/github-check-annotations.png)

[SonarQube](/help/using/custom-code-quality-rules.md) によって検出された[コード品質](/help/using/code-quality-testing.md)の問題が明確にリストされます。

![コードに関する問題の注釈の例](assets/github-check-annotations-example.png)

イシューと正確に一致するコード行が提供されるので、それをクリックして関連するコードを表示できます。 これらの注釈は、プルリクエストで変更された問題だけでなく、すべてのコードの問題に対して提供されます。

![コードに関する問題の注釈例](assets/github-check-annotations-example-code.png)

注釈付きの行はすべて、GitHub プルリクエストの「**変更済みファイル**」タブに集約されます。プルリクエストで変更されなかったファイルの注釈は、独自のセクションに表示されます。

![「変更済みファイル」タブの注釈の例](assets/github-check-annotations-files-changed.png)

## コード品質パイプライン {#code-quality-pipelines}

[コード品質](/help/using/code-quality-testing.md)の結果は、「**チェック**」タブの下部にある Cloud Manager によって自動的にトリガーされるパイプラインにも表示されます。また、プルリクエストのチェックの&#x200B;**詳細**&#x200B;からもアクセスできます。

![注釈の例](assets/github-check-annotations-code-quality.png)

![注釈の例](assets/github-check-annotations-code-quality-2.png)

また、問題を CSV 形式で視覚化することもできます。これを取得するには、[Cloud Managerでのパイプライン実行の詳細の表示 ](/help/using/managing-pipelines.md) を参照します。
