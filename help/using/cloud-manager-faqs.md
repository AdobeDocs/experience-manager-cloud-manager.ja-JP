---
title: Cloud Manager FAQ
seo-title: Cloud Manager FAQ
description: トラブルシューティングのヒントについては、Cloud Manager FAQを参照してください
seo-description: Cloud ManagerのFAQに関する回答を得るには、このページに従ってください
translation-type: tm+mt
source-git-commit: cb63a8bbe30b28668313dc851f17aa34fc166474
workflow-type: tm+mt
source-wordcount: '873'
ht-degree: 2%

---


# Cloud Manager FAQ {#cloud-manager-faqs}

次の節では、Cloud Managerに関してよくある質問に対する回答を示します。

## 1. Java 11をCloud Managerビルドと共に使用することは可能ですか？{#java-11-cloud-manager}

ビルドをJava 8からJava 11に切り替えようとすると、AEM Cloud Managerのビルドに失敗する。 この問題には多くの原因があり、ほとんどの一般的な原因は以下に記載されています。

* [追加](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/create-application-project/using-the-wizard.html?lang=en#getting-started)に記載されているように、maven-toolchains-pluginをJava 11用に正しい設定にして記述します。  例えば、[wkndサンプルプロジェクトコード](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75)を参照してください。

* 以下のエラーが発生した場合は、maven-scr-pluginの使用を削除し、すべてのOSGi注釈をOSGi R6注釈に変換する必要があります。 手順については、[ここ](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/)を参照してください。

   `[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]`

* Cloud Managerでは、Maven Enforcerプラグインのビルドはエラー`"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion"`で失敗します。 これは既知の問題です。Cloud Managerで、mavenコマンドを実行するのに別のバージョンのJavaを使用し、コードをコンパイルするのに使用しているためです。 ここでは、maven-enforcer-plugin設定から`requireJavaVersion`を省略します。

## 2.コードの質のチェックに失敗したため、デプロイメントが停止しています。 このチェックを回避する方法はありますか。{#deployment-stuck}

*セキュリティレーティング*&#x200B;を除くすべてのコード品質のエラーは重要ではない指標なので、結果UIの項目を展開すると、これらのエラーを回避できます。

[Deployment Manager、Project Manager、またはBusiness Owner](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=en#requirements)の役割を持つユーザーは、パイプラインが進行する問題を上書きできます。または、問題を受け入れることができます。この場合、パイプラインが失敗して停止します。  詳細は、[パイプラインの実行中の3層ゲート](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=ja#how-to-use)を参照してください。

## 3. Cloud Managerのデプロイメントは、Adobe Managed Services環境のパフォーマンステストの手順で失敗します。 重要な指標を渡すには、どのようにデバッグしますか。{#debug-critical-metrics}

結果を理解するには、[テスト結果を理解する](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use)を参照してください。

パフォーマンステストの手順に関する注意事項

* *パフォーマンスステップ*&#x200B;は、Webパフォーマンスステップです。つまり、Webブラウザーを使用してページを読み込むタイミングです。
* 結果のCSVファイルに一覧表示されるURLは、テスト中にCloud ManagerインフラストラクチャのChromeブラウザーに読み込まれます。
* 失敗する一般的な指標は、*エラー率*&#x200B;です。 URLを渡すには、メインURLが200ステータスで20秒未満で読み込まれる必要があります。 20秒を超えるページ読み込みは504エラーとしてマークされます。
* サイトでユーザー認証が必要な場合は、このドキュメントを参照して、サイトに対して認証するテストを設定します。

## 4. MavenプロジェクトのバージョンでSNAPSHOTを使用できますか？ パッケージとバンドルjarファイルのバージョン管理は、ステージ展開と実稼働展開でどのように機能しますか？{#snapshot-version}

1. 開発デプロイの場合、git branch pom.xmlファイルには、`<version>`値の末尾に —SNAPSHOTが含まれている必要があります。 これにより、バージョンが変更されない場合でも、以降のデプロイはインストールされます。 開発デプロイでは、Mavenビルドの自動バージョンの追加や生成は行われません。

1. ステージおよび実稼働環境でのデプロイでは、ここに記載されているように、自動バージョンが生成されます。

1. ステージでのカスタムバージョン管理と実稼働環境でのデプロイの場合は、`1.0.0`のように3つのパートの適切なmavenバージョンを設定します。 実稼働環境に別のデプロイを実行するたびに、バージョンを増やします。

1. Cloud Managerでは、ステージビルドと実稼働ビルドにバージョンが自動的に追加され、Gitブランチが作成されます。 特別な設定は必要ありません。 上記の手順3をスキップした場合、デプロイメントは引き続き問題なく動作し、バージョンが自動的に設定されます。

1. ステージ用に`-SNAPSHOT`を残し、実稼働用にビルドまたはデプロイする場合は、それでも問題ありません。 Cloud Managerでは、適切なバージョン番号が自動的に設定され、Gitでタグが作成されます。 このタグは、必要に応じて後で参照できます。

1. 開発に関する試験的なコードを試したい場合は、新しいgitブランチを作成し、その別のブランチを使用するようにパイプラインを設定します。  これは、デプロイメントの開始に失敗し、古いバージョンのコードを使用してテストし、コードが壊れたかどうかを確認する場合に便利です。

   以下のgitコマンドは、特定の既存のコミット`485548e4fbafbc83b11c3cb12b035c9d26b6532b`に対して、*testbranch1*&#x200B;という名前のリモートブランチを作成します。  この特別なブランチは、Cloud Managerで使用でき、他のブランチに影響を与えません。

   `git push origin 485548e4fbafbc83b11c3cb12b035c9d26b6532b:refs/heads/testbranch1`

   詳しくは、[Gitドキュメント](https://git-scm.com/book/en/v2/Git-Internals-Git-References)を参照してください。

   後でテストブランチを削除する場合は、削除コマンドを使用します（もちろん、このコマンドには注意が必要です）。

   `git push origin --delete testbranch1`

## 5. MavenのビルドはCloud Managerでデプロイされませんが、エラーなくローカルにビルドされます。 デバッグの方法? {#maven-build-fail}

詳しくは、[Git Resource](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md)を参照してください。

## 6. aio cloud managerでパイプライン変数を設定できません。 これらの問題のデバッグ方法{#set-variable}

以下に示すようなコマンドを使用してパイプライン変数をリストまたは設定しようとすると403エラーが発生する場合は、管理コンソールで&#x200B;*Deployment Manager* Cloud Manager製品ロールとして追加する必要があります。\
詳しくは、[API権限](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md)を参照してください。

関連するコマンドとエラー：

`$ aio cloudmanager:list-pipeline-variables 222`

エラー: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1`

エラー: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`
