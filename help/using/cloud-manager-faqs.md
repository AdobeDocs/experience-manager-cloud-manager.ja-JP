---
title: Cloud Manager に関する FAQ
seo-title: Cloud Manager FAQs
description: トラブルシューティングのヒントについては、Cloud Manager に関する FAQ を参照してください
seo-description: Follow this page to get answers on Cloud Manager FAQs
feature: Getting Started
exl-id: 52c1ca23-5b42-4eae-b63a-4b22ef1a5aee
source-git-commit: 71d44c7e3673ca62fcd2203ecc0bc4ed9fa22002
workflow-type: tm+mt
source-wordcount: '881'
ht-degree: 97%

---

# Cloud Manager FAQ {#cloud-manager-faqs}

以下の節では、Cloud Manager に関するよくある質問と、その回答を示します。

## Cloud Manager ビルドで Java 11 を使用することは可能ですか？  {#java-11-cloud-manager}

ビルドを Java 8 から 11 に切り替えようとすると、AEM Cloud Manager のビルドに失敗します。この問題には多くの原因があり、ほとんどの一般的な原因は以下のとおりです。

* [ここ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/create-application-project/using-the-wizard.html?lang=ja#getting-started)に記載されているように、maven-toolchains-plugin を Java 11 用の正しい設定で追加します。例えば、[wknd サンプルプロジェクトコード](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75)を参照してください。

* 以下のエラーが発生した場合は、`maven-scr-plugin` の使用を削除し、すべての OSGi 注釈を OSGi R6 注釈に変換する必要があります。手順については、[ここ](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/)を参照してください。

   `[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]`

* Cloud Manager ビルドの場合、Maven Enforcer プラグインはエラー `"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion"` で失敗します。これは既知の問題です。Cloud Manager では、maven コマンドの実行に、コードをコンパイルした際と異なるバージョンの Java を使用しているためです。ひとまず、maven-enforcer-plugin 設定から `requireJavaVersion` を省略します。

## コード品質のチェックの失敗が原因で、デプロイメントが停止します。このチェックを回避する方法はありますか  {#deployment-stuck}

*セキュリティ評価*&#x200B;以外のコード品質エラー指標は重要ではありません。結果として生成される UI の項目を展開すると、これらのエラーを回避できます。

[デプロイメントマネージャー、プロジェクトマネージャーまたはビジネスオーナー](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=ja#requirements)は、問題をオーバーライドできます。この場合、パイプラインは続行されます。または、問題を承認できます。この場合、パイプラインはエラーで停止します。詳細は、[パイプラインの実行中の 3 層ゲート](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=ja#how-to-use)を参照してください。

## Cloud Manager のデプロイメントが、Adobe Managed Services 環境のパフォーマンステストの手順で失敗します。重要な指標を渡すには、どのようにデバッグすればよいでしょうか  {#debug-critical-metrics}

結果を理解するには、[テスト結果の理解](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use)を参照してください。

パフォーマンステストの手順に関する注意事項

* *パフォーマンスステップ*&#x200B;は、Web パフォーマンスステップ（Web ブラウザーを使用してページを読み込むのにかかる時間）です。
* 結果として出力される *CSV* ファイルにリストされる URL は、テスト中に Cloud Manager インフラストラクチャの Chrome ブラウザーに読み込まれます。
* 一般的な失敗指標は、*エラー率*&#x200B;です。URL を渡すには、メイン URL が `200` ステータスかつ `20` 秒未満で読み込まれる必要があります。`20` 秒を超えるページ読み込みは `504` エラーとなります。
* サイトでユーザー認証が必要な場合は、 [テスト結果の理解](understand-your-test-results.md#authenticated-performance-testing) サイトに対する認証を行うためのテストを設定する場合。

## Maven プロジェクトのバージョンでは SNAPSHOT を使用できますか。パッケージとバンドル jar ファイルのバージョン管理は、ステージング環境および実稼動環境でのデプロイメントでどのように機能しますか  {#snapshot-version}

ステージング環境および実稼動環境でのデプロイメント向けパッケージおよびバンドル jar ファイルのバージョン管理については、次のシナリオを参照してください。

1. デベロッパーデプロイメントでは、Git ブランチの `pom.xml` ファイルで、`<version>` 値の末尾に `-SNAPSHOT` を含める必要があります。これにより、バージョンが変更されない場合でも、以降のデプロイメントは引き続きインストールされます。デベロッパーデプロイメントでは、maven ビルドの自動バージョンは追加または生成されません。

1. ステージング環境および実稼動環境でのデプロイメントでは、[ここ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/activating-maven-project.html?lang=ja#managing-code)に記載されているように、自動バージョンが生成されます。

1. ステージング環境および実稼動環境でカスタムバージョンを設定する場合は、`1.0.0` のように、maven のバージョンを 3 つのパーツに設定します。実稼動環境に別のデプロイを実行するたびに、バージョンを増やします。

1. Cloud Manager は、ステージング環境および実稼動環境のビルドへ自動的にバージョンを追加し、Git ブランチを作成します。特別な設定は必要ありません。上記の手順 3 をスキップした場合でも、デプロイメントは引き続き問題なく動作し、バージョンが自動的に設定されます。

1. ステージングおよび実稼動ビルドまたはデプロイメントの場合は、バージョンに `-SNAPSHOT` が付いたままにしておいても問題はありません。Cloud Manager は、適切なバージョン番号を自動的に設定し、Git でタグを作成します。このタグは、必要に応じて後で参照できます。

1. 開発環境で試験的なコードを試す場合は、新しい Git ブランチを作成し、そのブランチを使用するようにパイプラインを設定します。これは、デプロイメントの開始に失敗したときに、コードがどこで壊れているか確認するために、古いバージョンのコードを使用してテストする場合に便利です。

   以下の Git コマンドは、特定の既存のコミット `485548e4fbafbc83b11c3cb12b035c9d26b6532b` に対して、*testbranch1* という名前のリモートブランチを作成します。この特別なブランチは、Cloud Manager で使用でき、他のブランチには影響を与えません。

   `git push origin 485548e4fbafbc83b11c3cb12b035c9d26b6532b:refs/heads/testbranch1`

   詳しくは、[Git ドキュメント](https://git-scm.com/book/en/v2/Git-Internals-Git-References)を参照してください。

   後でテストブランチを削除する場合は、次の delete コマンドを使用します。

   `git push origin --delete testbranch1`

## Cloud Manager での maven のビルド失敗はデプロイされますが、ローカルではビルドされ、エラーは発生しません。デバッグの方法? {#maven-build-fail}

詳しくは、[Git リソース](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md)を参照してください。

## aio cloud manager set pipeline variablesで変数を設定できません。これらの問題をデバッグするにはどうすればよいですか  {#set-variable}

以下に示すようなコマンドでパイプライン変数をリストまたは設定しようとして `403` エラーが発生した場合は、Admin Console で、Cloud Manager 製品の役割の 1 つである&#x200B;*デプロイメントマネージャー*&#x200B;として自分自身を追加する必要があります。\
詳しくは、[API の権限](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md)を参照してください。

関連するコマンドとエラー：

`$ aio cloudmanager:list-pipeline-variables 222`

*エラー*: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1`

*エラー*: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`
