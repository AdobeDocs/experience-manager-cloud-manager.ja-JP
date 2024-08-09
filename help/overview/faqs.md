---
title: Cloud Manager FAQ
description: このドキュメントでは、AMS のお客様向けに Cloud Manager に関する最もよくある質問に対する回答を示します。
exl-id: 52c1ca23-5b42-4eae-b63a-4b22ef1a5aee
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '746'
ht-degree: 93%

---


# Cloud Manager FAQ {#cloud-manager-faqs}

このドキュメントでは、AMS のお客様向けに Cloud Manager に関する最もよくある質問に対する回答を示します。

## Cloud Manager ビルドで Java 11 を使用することは可能ですか？ {#java-11}

はい。Java 11 の正しい設定で `maven-toolchains-plugin` を追加する必要があります。

* このプロセスについては、[ こちら ](/help/getting-started/using-the-wizard.md) を参照してください。
* 例として、[wknd サンプルプロジェクトコード ](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75) を参照してください。

## Java 8 から Java 11 に切り替えた後、maven-scr-plugin に関するエラーでビルドが失敗します。どうすればいいですか？ {#maven-src-plugin}

ビルドを Java 8 から 11 に切り替えようとすると、AEM Cloud Manager のビルドに失敗する場合があります。次のエラーが発生した場合は、`maven-scr-plugin` を削除し、すべての OSGi 注釈を OSGi R6 注釈に変換する必要があります。

```text
[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]
```

このプラグインを削除する手順については、[ こちらを参照 ](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/) してください。

## Java 8 から Java 11 に切り替えた後、RequireJavaVersion に関するエラーでビルドが失敗します。 どうすればいいですか？ {#requirejavaversion}

Cloud Manager のビルドの場合、`maven-enforcer-plugin` は次のエラーで失敗する場合があります。

```text
[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion
```

これは既知の問題です。Cloud Manager で、コードのコンパイル時と異なるバージョンの Java を使用して maven コマンドを実行することが原因です。この問題を解決するには、`maven-enforcer-plugin` の設定から `requireJavaVersion` を省略するだけです。

## コード品質チェックに失敗し、デプロイメントが停止しています。このチェックを回避する方法はありますか？ {#deployment-stuck}

はい。セキュリティ評価以外のコード品質エラーはすべて重要指標ではないので、結果の UI で項目を展開することで、デプロイメントパイプラインの一部として考慮しないようにできます。

[デプロイメントマネージャー、プロジェクトマネージャーまたはビジネスオーナー](/help/requirements/users-and-roles.md#role-definitions)の役割を持つユーザーは、問題をオーバーライドでき、その場合、パイプラインは続行されます。または、問題を受け入れることもでき、その場合、パイプラインはエラーで停止します。

詳しくは、[パイプライン実行中の 3 層ゲート](/help/using/code-quality-testing.md#three-tier-gates-while-running-a-pipeline)および[実稼動以外のパイプラインの設定](/help/using/non-production-pipelines.md#understanding-the-flow)を参照してください。

## Cloud Manager のデプロイメントが、Adobe Managed Services 環境のパフォーマンステストステップで失敗します。重要な指標を渡すには、どのようにデバッグすればよいでしょうか？ {#debug-critical-metrics}

この質問に対する答えは一つではありません。 ただし、これらはパフォーマンステストステップに関する重要なポイントであり、留意する必要があります。

* このステップは web パフォーマンスステップです。つまり、このステップで、web ブラウザーを使用してページが読み込まれます。
* 結果の .csv ファイルにリストされている URL が、テスト中に Cloud Manager インフラストラクチャの Chrome ブラウザーに読み込まれます。
* よく失敗する指標は、エラー率です。
   * URL を渡すには、メイン URL が `200` ステータスで、かつ `20` 秒未満に読み込まれる必要があります。
   * `20` 秒を超えるページ読み込みは `504` エラーとなります。
* サイトでユーザー認証が必要な場合、サイトに対する認証のテストを設定する方法については、[テスト結果について](/help/using/code-quality-testing.md#authenticated-performance-testing)のドキュメントを参照してください。

品質チェックについて詳しくは、[ テスト結果について ](/help/using/code-quality-testing.md) を参照してください。

## Maven プロジェクトのバージョンに SNAPSHOT を使用できますか？ {#snapshot}

はい。開発者向けデプロイメントの場合、Git ブランチの `pom.xml` ファイルには、`<version>` 値の最後に `-SNAPSHOT` が含まれている必要があります。

これにより、バージョンが変更されなかった場合でも、その後のデプロイメントを引き続きインストールできます。デベロッパーデプロイメントでは、maven ビルドの自動バージョンは追加または生成されません。

また、ステージおよび実稼働ビルドまたはデプロイメントのバージョンを `-SNAPSHOT` に設定することもできます。Cloud Manager では、適切なバージョン番号を自動的に設定し、Git にタグを作成します。このタグは、必要に応じて後で参照できます。

バージョン処理の詳細は、[こちらで説明しています](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/project-version-handling.html?lang=ja)。

## パッケージとバンドルのバージョン管理は、ステージングと実稼動のデプロイメントでどのように機能しますか？ {#staging-production}

ステージングおよび実稼働のデプロイメントでは、自動バージョンが生成されます [ こちらを参照 ](/help/managing-code/maven-project-version.md)。

ステージングと実稼働のデプロイメントでカスタムバージョン管理を行うには、`1.0.0` のように、3 つの部分から成る適切な Maven バージョンを設定します。実稼動にデプロイするたびに、バージョンを増やします。

Cloud Manager では、自らのバージョンをステージビルドと実稼動ビルドに自動的に追加し、Git ブランチを作成します。特別な設定は必要ありません。前述のように Maven バージョンを設定しない場合でも、デプロイメントは成功し、バージョンが自動的に設定されます。

## Maven ビルドが Cloud Manager デプロイメントでは失敗しますが、ローカルではエラーなしでビルドされます。何が問題ですか？ {#maven-build-fail}

詳しくは、こちらの [Git リソース](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md)を参照してください。

## aio コマンドを使用して変数を設定できません。どうすればいいですか？ {#set-variable}

`aio` コマンドでパイプライン変数を一覧表示または設定しようとすると、次のような 403 エラーが発生する場合があります。

```shell
$ aio cloudmanager:list-pipeline-variables 222

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1

setting variables... !

Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)
```

この場合、これらのコマンドを実行するユーザーを Admin Console の&#x200B;**デプロイメントマネージャー**&#x200B;の役割に追加する必要があります。

詳しくは、[API の権限](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/)を参照してください。
