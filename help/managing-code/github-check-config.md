---
title: プライベートリポジトリの GitHub チェック設定
description: プライベートリポジトリへの各プルリクエストを検証するために自動的に作成されるパイプラインを制御する方法について説明します。
exl-id: 29c9e487-e196-411a-8cda-6751b0a56066
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 94%

---

# プライベートリポジトリの GitHub チェック設定 {#github-check-config}

プライベートリポジトリへの各プルリクエストを検証するために自動的に作成されるパイプラインを制御する方法について説明します。

## GitHub チェックの設定 {#configuration}

[ プライベートリポジトリ ](private-repositories.md#using) を使用する場合、[ フルスタックコード品質パイプライン ](/help/overview/ci-cd-pipelines.md) が自動的に作成されます。 このパイプラインは、プルリクエストの更新のたびに開始されます。

プライベートリポジトリのデフォルトブランチに `.cloudmanager/pr_pipelines.yml` ファイルを作成して、これらのチェックを制御できます。

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
| `shouldDeletePreviousComment` | `true` か `false` のいずれか | `false` | この GitHub プルリクエストで、コードスキャン結果の最後のコメントのみを保持するか、すべてを保持するか |
| `type` | `CI_CD` | n/a | CI/CD パイプラインの動作を定義します |
| `template.programID` | 整数 | パイプライン変数は再使用されない | 各 PR によって自動的に作成される既存のパイプラインの 1 つで設定されている、[パイプライン変数](/help/getting-started/build-environment.md#pipeline-variables)を再利用するために使用できます。 |
| `template.pipelineID` | 整数 | パイプライン変数は再使用されない | 各 PR によって自動的に作成される既存のパイプラインの 1 つで設定されている、[パイプライン変数](/help/getting-started/build-environment.md#pipeline-variables)を再利用するために使用できます。 |
| `namePrefix` | 文字列 | `Full Stack Code Quality Pipeline for PR` | 自動的に作成されるパイプライン名の設定に使用します |
| `importantMetricsFailureBehavior` | `CONTINUE` または `FAIL` または `PAUSE` | `CONTINUE` | パイプラインの重要な指標動作を設定します <br>`CONTINUE` = 重要な指標が失敗した場合、パイプラインは自動的に前方向へ移動します <br>`FAIL` = 重要な指標が失敗した場合、パイプラインは失敗ステータスで終了します <br>`PAUSE` = 重要な指標が失敗し、手動で再開する必要がある場合、コードスキャンステップでは待機中ステータスを受け取ります |
