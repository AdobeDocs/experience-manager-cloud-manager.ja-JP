---
title: プライベートリポジトリのプルリクエストチェック
description: プライベートリポジトリへの各プルリクエストを検証する自動的に作成されるパイプラインを制御する方法について説明します。
exl-id: 29c9e487-e196-411a-8cda-6751b0a56066
source-git-commit: 1ae6792f8bc628c3530a63004c3d38f215c72778
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 92%

---

# プライベートリポジトリのプルリクエストチェック {#github-check-config}

<!--OLD TITLE THAT I THOUGHT WAS BETTER Check configuration for private repositories -->

プライベートリポジトリへの各プルリクエストを検証する自動的に作成されるパイプラインを制御する方法について説明します。

## プライベートリポジトリのチェックの設定 {#configuration}

[プライベートリポジトリ](private-repositories.md#using)を使用すると、[フルスタックコード品質パイプライン](/help/overview/ci-cd-pipelines.md)が自動的に作成されます。このパイプラインは、プルリクエストを更新するたびに開始されます。

プライベートリポジトリのデフォルトブランチに `.cloudmanager/pr_pipelines.yml` ファイルを作成して、これらのチェックを制御できます。

```yaml
pullRequest:
  shouldDeletePreviousComment: false
pipelines:
  - type: CI_CD
    template:
      programId: 1234
      pipelineId: 456
    namePrefix: Full Stack Code Quality Pipeline for PR
    importantMetricsFailureBehavior: CONTINUE
```

| パラメーター | 可能な値 | デフォルト | 説明 |
| --- | --- | --- | --- |
| `shouldDeletePreviousComment` | `true` または `false` | `false` | この GitHub プルリクエストで、コードスキャン結果の最後のコメントのみを保持するか、すべてを保持するか。 |
| `type` | `CI_CD` | 該当なし | CI/CD パイプラインの動作を定義します。 |
| `template.programID` | 整数 | パイプライン変数は再使用されない | 既存のパイプラインに設定されている[パイプライン変数](/help/getting-started/build-environment.md#pipeline-variables)は再利用できます。このパイプラインは各 PR で自動的に作成されるものです。 |
| `template.pipelineID` | 整数 | パイプライン変数は再使用されない | 既存のパイプラインに設定されている[パイプライン変数](/help/getting-started/build-environment.md#pipeline-variables)は再利用できます。このパイプラインは各 PR で自動的に作成されるものです。 |
| `namePrefix` | 文字列 | `Full Stack Code Quality Pipeline for PR` | 自動的に作成されるパイプラインの名前を設定するのに使用されます。 |
| `importantMetricsFailureBehavior` | `CONTINUE` または `FAIL` または `PAUSE` | `CONTINUE` | パイプラインの重要な指標動作を設定します <br>`CONTINUE` = 重要な指標が失敗した場合、パイプラインは自動的に前方向へ移動します <br>`FAIL` = 重要な指標が失敗した場合、パイプラインは失敗ステータスで終了します <br>`PAUSE` = 重要な指標が失敗し、手動で再開する必要がある場合、コードスキャンステップでは待機中ステータスを受け取ります |
