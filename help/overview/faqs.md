---
title: Cloud Manager FAQ
description: このドキュメントでは、AMS のお客様向け Cloud Manager に関するよくある質問に対する回答を示します。
exl-id: 52c1ca23-5b42-4eae-b63a-4b22ef1a5aee
source-git-commit: 6be659e02df0657ec7d3dbce8c18c44a327a36f4
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 28%

---


# Cloud Manager FAQ {#cloud-manager-faqs}

このドキュメントでは、AMS のお客様向け Cloud Manager に関するよくある質問に対する回答を示します。

## Cloud Manager ビルドで Java 11 を使用することは可能ですか？ {#java-11}

はい。次の項目を追加する必要があります： `maven-toolchains-plugin` Java 11 用の正しい設定を使用します。

* このプロセスについては、 [こちら。](/help/getting-started/using-the-wizard.md)
* 例については、 [wknd サンプルプロジェクトコードです。](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75)

## Java 8 から Java 11 に切り替えた後、maven-scr-plugin に関するエラーでビルドが失敗します。 何ができる？ {#maven-src-plugin}

ビルドを Java 8 から 11 に切り替えようとすると、AEM Cloud Manager のビルドが失敗する場合があります。 次のエラーが発生した場合は、 `maven-scr-plugin` すべての OSGi 注釈を OSGi R6 注釈に変換します。

```text
[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]
```

このプラグインの削除方法については、 [こちらを参照してください。](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/)

## Java 8 から Java 11 に切り替えた後、RequireJavaVersion に関するエラーでビルドが失敗しました。 何ができる？ {#requirejavaversion}

Cloud Manager ビルドの場合、 `maven-enforcer-plugin` このエラーで失敗する場合があります

```text
[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion
```

これは既知の問題です。Cloud Manager では、maven コマンドの実行に、コードをコンパイルした際と異なるバージョンの Java を使用しているためです。単に省略する `requireJavaVersion` から `maven-enforcer-plugin` 設定。

## コード品質チェックに失敗し、デプロイメントが停止しています。 このチェックを回避する方法はありますか？ {#deployment-stuck}

はい。セキュリティ評価を除くすべてのコード品質エラーは、重要ではない指標なので、結果 UI の項目を展開することで、デプロイメントパイプラインの一部としてバイパスできます。

[デプロイメントマネージャー、プロジェクトマネージャーまたはビジネスオーナー](/help/requirements/users-and-roles.md#role-definitions)の役割を持つユーザーは、問題をオーバーライドでき、その場合、パイプラインは続行されます。または、問題を受け入れることもでき、その場合、パイプラインはエラーで停止します。

詳しくは、[パイプライン実行中の 3 層ゲート](/help/using/code-quality-testing.md#three-tier-gates-while-running-a-pipeline)および[実稼動以外のパイプラインの設定](/help/using/non-production-pipelines.md#understanding-the-flow)を参照してください。

## Cloud Manager のデプロイメントが、Adobe Managed Services 環境のパフォーマンステストステップで失敗します。重要な指標を渡すには、どのようにデバッグすればよいでしょうか？ {#debug-critical-metrics}

この質問に対する答えは一つもありません。 ただし、次の点に注意する必要があるパフォーマンステスト手順の重要なポイントがあります。

* この手順は、Web パフォーマンスの手順です。Web ブラウザーを使用してページを読み込む時間です。
* 結果の.csv ファイルに一覧表示される URL は、テスト中に Cloud Manager インフラストラクチャの Chrome ブラウザーに読み込まれます。
* 一般的な失敗指標は、エラー率です。
   * URL を渡すには、メイン URL が `200` ステータスかつ `20` 秒未満で読み込まれる必要があります。
   * `20` 秒を超えるページ読み込みは `504` エラーとなります。
* サイトでユーザー認証が必要な場合は、 [テスト結果の理解](/help/using/code-quality-testing.md#authenticated-performance-testing) サイトに対する認証を行うようにテストを設定する場合。

ドキュメントを参照してください [テスト結果について](/help/using/code-quality-testing.md) を参照してください。

## Maven プロジェクトのバージョンに SNAPSHOT を使用できますか？ {#snapshot}

はい。デベロッパーデプロイメントの場合、Git ブランチ `pom.xml` ファイルに含める必要がある `-SNAPSHOT` ～の終わりに `<version>` の値です。

これにより、バージョンが変更されなかった場合でも、以降のデプロイメントを引き続きインストールできます。 デベロッパーデプロイメントでは、maven ビルドの自動バージョンは追加または生成されません。

また、バージョンを `-SNAPSHOT` ステージング環境および実稼動環境のビルドまたはデプロイメントの場合。 Cloud Manager は適切なバージョン番号を自動的に設定し、Git でタグを作成します。 このタグは、必要に応じて後で参照できます。

バージョン処理の詳細は次のとおりです。 [ここで説明します。](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/project-version-handling.html)

## パッケージとバンドルのバージョン管理は、ステージング環境と実稼動環境のデプロイメントでどのように機能しますか？ {#staging-production}

ステージング環境および実稼動環境でのデプロイメントでは、自動バージョンが生成されます [ここに記載されているように。](/help/managing-code/maven-project-version.md)

ステージおよび実稼動環境でのデプロイメントのカスタムバージョン管理の場合は、次のような適切な 3 部構成の Maven バージョンを設定します。 `1.0.0`. 実稼動環境にデプロイするたびに、バージョンを増やします。

Cloud Manager は、ステージビルドと実稼動ビルドにバージョンを自動的に追加し、Git ブランチを作成します。 特別な設定は必要ありません。前述のように Maven バージョンを設定しない場合、デプロイメントは成功し、バージョンが自動的に設定されます。

## Cloud Manager デプロイメントで Maven ビルドが失敗しましたが、エラーなくローカルにビルドされます。 どうしたの？ {#maven-build-fail}

参照 [git リソース](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) を参照してください。

## aio コマンドを使用して変数を設定できません。 何ができる？ {#set-variable}

を介してパイプライン変数をリストまたは設定しようとすると、次のような 403 エラーが発生する場合があります。 `aio` コマンド

```shell
$ aio cloudmanager:list-pipeline-variables 222

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1

setting variables... !

Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)
```

この場合、これらのコマンドを実行するユーザーを **デプロイメントマネージャー** Admin Consoleの

詳しくは、[API の権限](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/)を参照してください。
