---
title: プライベートリポジトリの GitHub チェック設定
description: プライベートリポジトリへの各プルリクエストを検証するために自動的に作成されるパイプラインを制御する方法を説明します。
source-git-commit: 85c1e22609dc5646d3de0ccc71e9423d4243e13a
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 7%

---


# プライベートリポジトリの GitHub チェック設定 {#github-check-config}

プライベートリポジトリへの各プルリクエストを検証するために自動的に作成されるパイプラインを制御する方法を説明します。

## GitHub チェックの設定 {#configuration}

使用時 [プライベートリポジトリ、](private-repositories.md#using) a [フルスタックコード品質パイプライン](/help/overview/ci-cd-pipelines.md) は自動的に作成されます。 このパイプラインは、プルリクエストの更新のたびに開始されます。

これらのチェックを制御するには、以下を作成します。 `.cloudmanager/pr_pipelines.yml` プライベートリポジトリのデフォルトブランチにあるファイル。

```yaml
github:
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
|---|---|---|---|
| `shouldDeletePreviousComment` | `true` か `false` のどちらかにする必要があります。 | `false` | この GitHub プルリクエストで、コードスキャンの結果を含んだ最後のコメントのみを保持するか、すべてを保持するか |
| `type` | `CI_CD` | n/a | CI/CD パイプラインの動作を定義します。 |
| `template.programID` | 整数 | 再利用されるパイプライン変数はありません | を再利用するために使用可能 [パイプライン変数](/help/getting-started/build-environment.md#pipeline-variables) これは、各 PR によって自動的に作成された既存のパイプラインの 1 つに設定されます。 |
| `template.pipelineID` | 整数 | 再利用されるパイプライン変数はありません | を再利用するために使用可能 [パイプライン変数](/help/getting-started/build-environment.md#pipeline-variables) これは、各 PR によって自動的に作成された既存のパイプラインの 1 つに設定されます。 |
| `namePrefix` | 文字列 | `Full Stack Code Quality Pipeline for PR` | 自動作成されるパイプラインの名前を設定するために使用されます |
| `importantMetricsFailureBehavior` | `CONTINUE` または `FAIL` または `PAUSE` | `CONTINUE` | パイプラインの重要な指標動作を設定します<br>`CONTINUE` =重要な指標が失敗した場合、パイプラインは自動的に先に進みます<br>`FAIL` =重要な指標が失敗した場合、パイプラインは失敗ステータスで終了します<br>`PAUSE` =重要な指標が失敗し、手動で再開する必要がある場合、コードスキャンステップは待機中ステータスを受け取ります |
