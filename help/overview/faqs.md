---
title: Cloud Manager に関する FAQ
description: AMS のお客様向けに Cloud Manager に関する最もよくある質問に対する回答について説明します。
exl-id: 52c1ca23-5b42-4eae-b63a-4b22ef1a5aee
TQID: https://experienceleague.adobe.com/aBIiazPCm-krE6rew6k-HSl-Uvc79eagMzM7uYciWdc
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 4dcc367f82c51626ca449ff389a9c9574a562ff7
workflow-type: tm+mt
source-wordcount: 764
ht-degree: 69%

---

# Cloud Manager に関する FAQ {#cloud-manager-faqs}

このドキュメントでは、AMS のお客様向けに Cloud Manager に関する最もよくある質問に対する回答を示します。

<!-- 
## Is it possible to use Java 11 with Cloud Manager builds? {#java-11}

Yes. You need to add the `maven-toolchains-plugin` with the correct settings for Java 11.

* This process is documented [here](/help/getting-started/using-the-wizard.md).
* For an example, see the [WKND sample project code](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75). 
-->

## Java 8 から Java 11 に切り替えた後、maven-scr-plugin に関するエラーでビルドが失敗します。 どうすればいいですか？ {#maven-src-plugin}

Java 8からJava 11への切り替えを試みると、AEM Cloud Managerのビルドが失敗します。 次のエラーが発生した場合は、`maven-scr-plugin` を削除し、すべての OSGi 注釈を OSGi R6 注釈に変換する必要があります。

```text
[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]
```

このプラグインを削除する方法について詳しくは、[こちら](https://cqdump.joerghoh.de/2019/01/03/from-scr-annotations-to-osgi-annotations/)を参照してください。

## Java 8 から Java 11 に切り替えた後、RequireJavaVersion に関するエラーでビルドが失敗します。 どうしたらいいでしょうか。 {#requirejavaversion}

Cloud Manager ビルドの場合、`maven-enforcer-plugin` がこのエラーで失敗する場合があります。

```text
[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion
```

この問題は、Cloud Managerが別のバージョンのJavaを使用してMaven コマンドを実行するために発生します。 このバージョンは、コードのコンパイルに使用するバージョンとは異なります。 `maven-enforcer-plugin` 設定から `requireJavaVersion` を省略します。

## コード品質チェックが失敗し、デプロイメントが停止しました。 このチェックを回避する方法はありますか？ {#deployment-stuck}

はい。 セキュリティ評価以外のコード品質エラーはすべて重要指標ではありません。 そのため、結果の UI で項目を展開することで、デプロイメントパイプラインの一部として考慮しないようにできます。

[デプロイメントマネージャー、プロジェクトマネージャーまたはビジネスオーナー](/help/requirements/users-and-roles.md#role-definitions)の役割を持つユーザーは、問題をオーバーライドできます。 この場合、パイプラインは続行されます。 または、問題を受け入れて、パイプラインがエラーで停止する可能性もあります。

詳しくは、[パイプライン実行中の 3 層ゲート](/help/using/code-quality-testing.md#three-tier-gates-while-running-a-pipeline)および[実稼動以外のパイプラインの設定](/help/using/non-production-pipelines.md#understanding-the-flow)を参照してください。

## Cloud Manager のデプロイメントが、Adobe Managed Services 環境のパフォーマンステストステップで失敗します。 この問題を解決してクリティカル指標を渡すにはどうすればよいですか？ {#debug-critical-metrics}

この質問には決定的な答えはありません。 ただし、パフォーマンステスト手順については、次の点が役立ちます。

* この手順は web パフォーマンスの手順です。 つまり、web ブラウザーでページを読み込むのに要する時間のことです。
* 結果.csv ファイルにリストされているURLは、テスト中にCloud Manager インフラストラクチャ内のChrome ブラウザーに読み込まれます。
* よく失敗する指標は、エラー率です。 そのため、URL を渡すには、メイン URL が `200` ステータスで、かつ `20` 秒未満に読み込まれる必要があります。 ページの読み込みが `20` 秒を超えると、`504` エラーとマークされます。
* サイトでユーザー認証が必要な場合は、サイトに対する認証のテスト設定に関する[テスト結果の理解](/help/using/code-quality-testing.md#authenticated-performance-testing)を参照してください。

品質チェックについて詳しくは、[テスト結果について](/help/using/code-quality-testing.md)を参照してください。

## Maven プロジェクトのバージョンに SNAPSHOT を使用できますか？ {#snapshot}

はい。 開発者向けデプロイメントの場合、Git 分岐の `pom.xml` ファイルには、`<version>` 値の最後に `-SNAPSHOT` を含める必要があります。

これにより、バージョンが変更されていない場合に、後続のデプロイメントをインストールできます。 開発者デプロイメントでは、Maven ビルドに自動バージョンは追加または生成されません。

また、ステージおよび実稼働ビルドまたはデプロイメントのバージョンを `-SNAPSHOT` に設定することもできます。 Cloud Manager は、適切なバージョン番号を自動的に設定し、Git でタグを作成します。 このタグは、必要に応じて後で参照できます。

バージョン処理について詳しくは、[こちらを参照してください](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/project-version-handling)。

## パッケージとバンドルのバージョン管理は、ステージングと実稼動のデプロイメントでどのように機能しますか？ {#staging-production}

ステージングおよび実稼動のデプロイメントでは、自動バージョンが生成されます（[こちら](/help/managing-code/maven-project-version.md)を参照）。

ステージング環境および実稼動環境でのカスタムバージョン管理の場合は、`1.0.0`のような適切な3つの部分のMaven バージョンを設定します。 実稼動にデプロイするたびに、バージョンを増やします。

Cloud Manager では、自らのバージョンをステージビルドと実稼動ビルドに自動的に追加し、Git ブランチを作成します。 特別な設定は必要ありません。 前述のようにMaven バージョンを設定しない場合、デプロイメントは引き続き成功し、バージョンは自動的に設定されます。

## Cloud Manager デプロイメントでMaven ビルドが失敗しますが、エラーなしでローカルにビルドされます。 原因は何か？ {#maven-build-fail}

詳しくは、この [Git リソース](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md)を参照してください。

## aio コマンドを使用して変数を設定できません。 どうすればいいですか？ {#set-variable}

`aio` コマンドを使用してパイプライン変数を一覧表示または設定しようとすると、次のような403 エラーが表示されます。

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

詳しくは、[API の権限](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions)を参照してください。
