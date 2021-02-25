---
title: Cloud Manager FAQ
seo-title: Cloud Manager FAQ
description: トラブルシューティングのヒントについては、Cloud Manager FAQを参照してください
seo-description: Cloud ManagerのFAQに関する回答を得るには、このページに従ってください
translation-type: tm+mt
source-git-commit: da3346852df4e421a69321830d7efee81d58e20c
workflow-type: tm+mt
source-wordcount: '880'
ht-degree: 2%

---


# Cloud Manager FAQ {#cloud-manager-faqs}

次の節では、Cloud Managerに関するよくある質問と、その回答を示します。

## Java 11をCloud Managerビルドと共に使用することは可能ですか？{#java-11-cloud-manager}

ビルドをJava 8から11に切り替えようとすると、AEM Cloud Managerのビルドに失敗する。 この問題には多くの原因があり、ほとんどの一般的な原因は以下に記載されています。

* [追加](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/create-application-project/using-the-wizard.html?lang=en#getting-started)に記載されているように、maven-toolchains-pluginをJava 11用に正しい設定にして記述します。  例えば、[wkndサンプルプロジェクトコード](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75)を参照してください。

* 以下のエラーが発生した場合は、`maven-scr-plugin`の使用を削除し、すべてのOSGi注釈をOSGi R6注釈に変換する必要があります。 手順については、[ここ](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/)を参照してください。

   `[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]`

* Cloud Managerビルドの場合、Maven Enforcerプラグインはエラー`"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion"`で失敗します。 これは既知の問題です。Cloud Managerで、mavenコマンドを実行するのに別のバージョンのJavaを使用し、コードをコンパイルするのに対して、既知の問題です。 ここでは、maven-enforcer-plugin設定から`requireJavaVersion`を省略します。

## コードの質のチェックに失敗したため、展開が停止します。 このチェックを回避する方法はありますか。{#deployment-stuck}

*セキュリティレーティング*&#x200B;を除くすべてのコード品質のエラーは重要ではない指標なので、結果UIの項目を展開すると、これらのエラーを回避できます。

[Deployment Manager、Project Manager、またはBusiness Owner](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=en#requirements)の役割を持つユーザーは、問題を上書きできます。この場合、パイプラインは続行するか、問題を受け入れることができます。この場合、パイプラインは失敗して停止します。  詳細は、[パイプラインの実行中の3層ゲート](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=ja#how-to-use)を参照してください。

## Cloud Managerのデプロイメントは、Adobe Managed Services環境のパフォーマンステストの手順で失敗します。 重要な指標を渡すには、どのようにデバッグしますか。{#debug-critical-metrics}

結果を理解するには、[テスト結果を理解する](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use)を参照してください。

パフォーマンステストの手順に関する注意事項

* *パフォーマンスステップ*&#x200B;は、Webパフォーマンスステップ、つまり、Webブラウザーを使用してページを読み込む時間です。
* 結果&#x200B;*CSV*&#x200B;ファイルに示されているURLは、テスト中にCloud ManagerインフラストラクチャのChromeブラウザーに読み込まれます。
* 失敗する一般的な指標は、*エラー率*&#x200B;です。 URLを渡すには、メインURLが`200`ステータスで`20`秒未満で読み込まれる必要があります。 `20`秒を超えるページ読み込みは`504`エラーとしてマークされます。
* サイトでユーザー認証が必要な場合は、[認証済みパフォーマンステスト](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=en#how-to-use)で、サイトに対して認証を行うようにテストを設定します。

## MavenプロジェクトのバージョンでSNAPSHOTを使用できますか。 パッケージとバンドルjarファイルのバージョン管理は、ステージ展開と実稼働展開でどのように機能しますか？{#snapshot-version}

1. 開発者のデプロイメントでは、Gitブランチ`pom.xml`ファイルの`<version>`値の末尾に`-SNAPSHOT`を含める必要があります。 これにより、バージョンが変更されない場合でも、以降のデプロイメントは引き続きインストールされます。 開発者デプロイメントでは、Mavenビルドの自動バージョンは追加または生成されません。

1. ステージおよび実稼働環境でのデプロイメントでは、[ここ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/activating-maven-project.html?lang=en#managing-code)に記載されているように、自動バージョンが生成されます。

1. ステージおよび実稼働環境でのカスタムバージョン設定の場合は、`1.0.0`のように、適切なmavenバージョンを3つのパーツに設定します。 実稼働環境に別のデプロイを実行するたびに、バージョンを増やします。

1. Cloud Managerは、自動的にStageビルドとProductionビルドにバージョンを追加し、Gitブランチを作成します。 特別な設定は必要ありません。 上記の手順3をスキップした場合、デプロイメントは引き続き問題なく動作し、バージョンが自動的に設定されます。

1. ステージ版と実稼働版のビルドまたはデプロイメント用に`-SNAPSHOT`を残しておくと問題はありません。 Cloud Managerは、適切なバージョン番号を自動的に設定し、Gitにタグを作成します。 このタグは、必要に応じて後で参照できます。

1. 開発環境で試験的なコードを試す場合は、新しいGitブランチを作成し、その異なるブランチを使用するようにパイプラインを設定します。 これは、デプロイメントの開始に失敗し、古いバージョンのコードを使用してテストし、コードが壊れたかどうかを確認する場合に便利です。

   以下のGitコマンドは、特定の既存のコミット`485548e4fbafbc83b11c3cb12b035c9d26b6532b`に対して、*testbranch1*&#x200B;という名前のリモートブランチを作成します。  この特別なブランチは、Cloud Managerで使用でき、他のブランチに影響を与えません。

   `git push origin 485548e4fbafbc83b11c3cb12b035c9d26b6532b:refs/heads/testbranch1`

   詳しくは、[Gitドキュメント](https://git-scm.com/book/en/v2/Git-Internals-Git-References)を参照してください。

   後でテストブランチを削除する場合は、次のdeleteコマンドを使用します。

   `git push origin --delete testbranch1`

## MavenのビルドはCloud Managerでは失敗しますが、ローカルにビルドされ、エラーは発生しません。 デバッグの方法? {#maven-build-fail}

詳しくは、[Git Resource](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md)を参照してください。

## Aio Cloud Managerが設定したパイプライン変数を介して変数を設定できません。 これらの問題のデバッグ方法{#set-variable}

以下に示すようなコマンドを使用してパイプライン変数をリストまたは設定しようとすると`403`エラーが発生する場合は、Admin Consoleに&#x200B;*Deployment Manager* Cloud Manager製品ロールとして追加する必要があります。\
詳しくは、[API権限](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md)を参照してください。

関連するコマンドとエラー：

`$ aio cloudmanager:list-pipeline-variables 222`

*エラー*: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1`

*エラー*: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`
