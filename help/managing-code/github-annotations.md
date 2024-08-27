---
title: GitHub チェック注釈
description: GitHub がプライベートリポジトリの注釈 PR をチェックし、役立つフィードバックを提供する方法を説明します。
exl-id: 15178de8-8a8a-4300-8510-88875ad0fc8c
source-git-commit: 6f5d51ef59aef831574bd55cee6b12a29e3d70d2
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 47%

---


# GitHub チェック注釈 {#github-annotations}

GitHub がプライベートリポジトリの注釈 PR をチェックし、役立つフィードバックを提供する方法を説明します。

## 概要 {#overview}

Cloud Manager プログラムに [ プライベートリポジトリ ](private-repositories.md) を使用する場合、プルリクエストのたびに GitHub でのチェックが自動的に実行されます。 これらのチェックには、コードの問題をできるだけ早く理解するのに役立つ有用な情報が注釈として付けられています。

![GitHub チェック注釈の例](assets/github-check-annotations.png)

[SonarQube](/help/using/custom-code-quality-rules.md) によって検出された[コード品質](/help/using/code-quality-testing.md)の問題が明確にリストされます。

![コードに関する問題の注釈の例](assets/github-check-annotations-example.png)

問題のあるコードの正確な行が提供され、これをクリックすると、関連するコードを表示できます。これらの注釈は、プルリクエストで変更された問題だけでなく、すべてのコード問題に対して提供されます。

![コードに関する問題の注釈例](assets/github-check-annotations-example-code.png)

注釈付きの行はすべて、GitHub プルリクエストの「**変更済みファイル**」タブに集約されます。プルリクエストで変更されなかったファイルの注釈は、独自のセクションに表示されます。

![「変更済みファイル」タブの注釈の例](assets/github-check-annotations-files-changed.png)

## コード品質パイプライン {#code-quality-pipelines}

[ コード品質 ](/help/using/code-quality-testing.md) の結果は、パイプラインにも表示されます。このパイプラインは、Cloud Managerによって「**チェック**」タブの下部に自動トリガーされています。 また、プルリクエストのチェックの&#x200B;**詳細**&#x200B;からもアクセスできます。

![注釈の例](assets/github-check-annotations-code-quality.png)

![注釈の例](assets/github-check-annotations-code-quality-2.png)

また、問題を CSV 形式で視覚化することもできます。このメソッドは、[Cloud Managerでのパイプライン実行の詳細の表示 ](/help/using/managing-pipelines.md) によって取得できます。
