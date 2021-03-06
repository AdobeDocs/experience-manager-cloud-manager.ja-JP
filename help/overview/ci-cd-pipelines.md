---
title: CI／CD パイプライン
description: CI/CD パイプラインと、Cloud Manager でのステージング環境および実稼動環境へのデプロイメントを処理する方法について説明します。
exl-id: 7130e5b7-6986-48c8-900c-90f3e4187f91
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 30%

---


# CI／CD パイプライン {#ci-cd-pipeline}

CI/CD パイプラインと、Cloud Manager でのステージング環境および実稼動環境へのデプロイメントを処理する方法について説明します。

## 概要 {#overview}

[!UICONTROL Cloud Manager] 継続的統合/継続的配信 (CI/CD) フレームワークが含まれるので、実装チームは新しいコードや更新されたコードを迅速にテストして配信できます。 例えば、コーディングに関するアドビのベストプラクティスを活用して綿密なコードスキャンを実行し最高のコード品質を確保する自動 CI／CD パイプラインを、実装チームが設定および開始できます。

また、CI/CD パイプラインは、単体テストおよびパフォーマンステストプロセスを自動化して、デプロイメントの効率を高め、デプロイ後の修正にコストがかかる重要な問題をプロアクティブに特定します。 実装チームは、包括的なコードパフォーマンスレポートにアクセスして、コードが実稼動環境にデプロイされた場合の KPI への潜在的な影響や重要なセキュリティ検証を見通すことができます。

## パイプラインプロセス {#pipeline-process}

次の図は、 [!UICONTROL Cloud Manager] パイプラインを使用して。

![パイプラインプロセス](/help/assets/screen_shot_2018-05-30at82457pm.png)

| パイプラインステップ | 説明 |
|---|---|
| 1. リリースの開始 | デプロイメントマネージャーは、手動で、Git コミットを使用して、または定期的なスケジュールに基づいて、リリースをトリガーします。 |
| 2.リリースタグを作成する | [!UICONTROL Cloud Manager] は git タグを作成し、自動生成されたバージョン番号 ( 例： `2018.531.245527.0000001222`. |
| 3.自動生成されたバージョンを含むリリースとしてビルドされます。 | [!UICONTROL Cloud Manager] が、新しく割り当てたバージョン番号を使用してアプリケーションをビルドします。 |
| 4.コード品質の評価 | [!UICONTROL Cloud Manager] コードをステージング環境にデプロイする前に、ソースコードをスキャンし概要の情報を提供します。 |
| 5.バージョン管理されたアーティファクト（複数可）の保存 | リリースアーティファクトは、デプロイメントステップで後で使用するために保存されます。 |
| 6. AMS AEMステージングへのアーティファクトの自動デプロイメント | リリースアーティファクトは、ステージング環境にデプロイされます。 |
| 7.トリガー自動テスト | [!UICONTROL Cloud Manager] は、アーティファクトに対してパフォーマンステストとセキュリティテストを実行します。 |
| 8.実稼動トリガーのデプロイ | 自動テストの完了後、 [!UICONTROL Cloud Manager] 実稼動環境へのデプロイメントを開始します。 |
| 9. [!UICONTROL Cloud Manager] デプロイするアーティファクトを取得します | 保存したリリースアーティファクトを [!UICONTROL Cloud Manager] が取り込みます。 |
| 10.アーティファクトを実稼動環境にデプロイする | リリースアーティファクトが実稼動環境にデプロイされます。 |

### CI/CD パイプラインの設定方法 {#how-to-setup-a-ci-cd-pipeline}

パイプラインの設定について詳しくは、[実稼動パイプラインの設定](/help/using/production-pipelines.md)および[実稼動以外のパイプラインの設定](/help/using/non-production-pipelines.md)のドキュメントを参照してください。 

## 品質ゲート {#quality-gates}

CI/CD パイプラインは、品質ゲート（受け入れ条件）を提供します。コードをステージング環境からデプロイメント環境に移行する前に、この条件を満たす必要があります。 パイプラインには次の 3 つのゲートがあります。

* コード品質
* パフォーマンステスト
* セキュリティテスト

これらのゲートごとに、次の 3 つのレベルの問題を識別できます。

* **重大**  — ゲートで特定される重大な問題により、パイプラインが即時に失敗します。
* **重要**  — ゲートで特定される重要な問題により、パイプラインの一時停止状態が発生します。 デプロイメントマネージャー、プロジェクトマネージャーまたはビジネスオーナーは、問題をオーバーライドできます。この場合、パイプラインは続行されます。または、問題を承認できます。この場合、パイプラインはエラーで停止します。
* **情報**  — ゲートで特定される情報の問題は情報提供だけを目的としており、パイプラインの実行には影響しません。

これは、特定された問題を含むコードスキャンの例です。

![コードスキャンの例](/help/assets/quality-gate-failed.png)

### ゲートの設定方法 {#how-to-setup-gates}

コード、品質およびパフォーマンスに関するゲートの設定について詳しくは、[実稼動パイプラインの設定](/help/using/production-pipelines.md)のドキュメントを参照してください。
