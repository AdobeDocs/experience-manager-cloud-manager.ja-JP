---
title: Cloud Managerに関するFAQ
seo-title: Cloud Managerに関するFAQ
description: トラブルシューティングのヒントについては、 Cloud ManagerのFAQを参照してください
seo-description: このページでは、Cloud ManagerのFAQに関する回答を得る方法について説明します
feature: 開始
exl-id: 52c1ca23-5b42-4eae-b63a-4b22ef1a5aee
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 4%

---

# Cloud ManagerのFAQ {#cloud-manager-faqs}

次の節では、Cloud Managerに関するよくある質問に対する回答を示します。

## Cloud ManagerビルドでJava 11を使用することは可能ですか？{#java-11-cloud-manager}

Java 8から11にビルドを切り替えようとすると、AEM Cloud Managerのビルドが失敗します。 問題には多くの原因が考えられ、最も一般的な原因は以下のとおりです。

* [ここ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/create-application-project/using-the-wizard.html?lang=en#getting-started)に記載されているように、Java 11用の正しい設定でmaven-toolchains-pluginを追加します。  例えば、[wkndサンプルプロジェクトコード](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75)を参照してください。

* 以下のエラーが発生した場合は、`maven-scr-plugin`の使用を削除し、すべてのOSGi注釈をOSGi R6注釈に変換する必要があります。 手順については、[ここ](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/)を参照してください。

   `[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]`

* Cloud Managerビルドの場合、Maven Enforcerプラグインはエラー`"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion"`で失敗します。 これは、Cloud Managerが別のバージョンのJavaを使用してmavenコマンドを実行し、コードをコンパイルするのとは異なるため、既知の問題です。 現時点では、maven-enforcer-plugin設定から`requireJavaVersion`を省略します。

## コード品質の確認に失敗したため、デプロイメントが停止します。 このチェックをバイパスする方法はありますか？{#deployment-stuck}

*セキュリティ評価*&#x200B;を除くすべてのコード品質エラーは重要ではない指標なので、結果UIの項目を展開することで回避できます。

[Deployment Manager、プロジェクトマネージャー、またはビジネスオーナー](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=en#requirements)の役割を持つユーザーは、問題を上書きできます。この場合、パイプラインは進行し、問題を受け入れます。その場合、パイプラインは失敗して停止します。  詳しくは、[パイプライン実行時の3層ゲート](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=ja#how-to-use)を参照してください。

## Cloud Managerのデプロイメントは、Adobe Managed Services環境のパフォーマンステスト手順で失敗します。 重要な指標を渡すには、これをどのようにデバッグすればよいですか？{#debug-critical-metrics}

[テスト結果の理解](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use)を参照して、結果を理解してください。

パフォーマンステストの手順に関する注意事項：

* *パフォーマンスステップ*&#x200B;は、Webパフォーマンスステップ、つまり、Webブラウザーを使用してページを読み込む時間です。
* 結果の&#x200B;*CSV*&#x200B;ファイルにリストされたURLは、テスト中にCloud ManagerインフラストラクチャのChromeブラウザーに読み込まれます。
* 失敗する一般的な指標は、*エラー率*&#x200B;です。 URLを渡すには、メインURLが`200`ステータスで`20`秒未満で読み込まれる必要があります。 `20`秒を超えるページ読み込みは`504`エラーとしてマークされます。
* サイトでユーザー認証が必要な場合は、[認証済みパフォーマンステスト](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=ja#how-to-use)を参照して、サイトに対して認証するテストを設定します。

## MavenプロジェクトのバージョンでSNAPSHOTを使用できますか。 パッケージとバンドルのjarファイルのバージョン管理は、ステージング環境と実稼動環境のデプロイメントでどのように機能しますか。{#snapshot-version}

ステージデプロイメントと実稼動デプロイメント用のパッケージおよびバンドルjarファイルのバージョン管理については、次のシナリオを参照してください。

1. デベロッパーデプロイメントの場合、Gitブランチ`pom.xml`ファイルの`<version>`値の末尾に`-SNAPSHOT`を含める必要があります。 これにより、バージョンが変更されない場合でも、以降のデプロイメントをインストールできます。 デベロッパーデプロイメントでは、Mavenビルド用の自動バージョンが追加または生成されることはありません。

1. ステージ環境および実稼動環境のデプロイメントでは、[ここ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/activating-maven-project.html?lang=en#managing-code)に記載されているように、自動バージョンが生成されます。

1. ステージおよび実稼動環境のデプロイメントでカスタムバージョン管理をおこなう場合は、`1.0.0`のように、適切なmavenバージョンを3つのパートで設定します。 別の実稼動環境へのデプロイを実行するたびに、バージョンを増やします。

1. Cloud Managerは、ステージビルドと実稼動ビルドに自動的にバージョンを追加し、さらにGitブランチを作成します。 特別な設定は不要です。 上記の手順3をスキップした場合、デプロイメントは引き続き正常に動作し、バージョンが自動的に設定されます。

1. ステージングビルドおよび実稼動ビルドまたはデプロイメントで`-SNAPSHOT`のままにしておくと、問題は発生しません。 Cloud Managerは適切なバージョン番号を自動的に設定し、Gitでタグを作成します。 このタグは、必要に応じて後で参照できます。

1. 開発環境で実験的なコードを試す場合は、新しいGitブランチを作成し、その別のブランチを使用するようにパイプラインを設定できます。 これは、デプロイメントが失敗し始めた場合に、古いバージョンのコードでテストして、破損したタイミングを確認する場合に役立ちます。

   以下のGitコマンドは、特定の既存のコミット`485548e4fbafbc83b11c3cb12b035c9d26b6532b`に対して、*testbranch1*&#x200B;というリモートブランチを作成します。  この特別なブランチは、他のブランチに影響を与えることなく、Cloud Managerで使用できます。

   `git push origin 485548e4fbafbc83b11c3cb12b035c9d26b6532b:refs/heads/testbranch1`

   詳しくは、[Gitのドキュメント](https://git-scm.com/book/en/v2/Git-Internals-Git-References)を参照してください。

   後でテストブランチを削除する場合は、次のdeleteコマンドを使用します。

   `git push origin --delete testbranch1`

## Cloud ManagerのデプロイでMavenビルドが失敗し、エラーなくローカルにビルドされます。 デバッグの方法? {#maven-build-fail}

詳しくは、[Gitリソース](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md)を参照してください。

## aio cloud manager設定パイプライン変数を介して変数を設定できない。 これらの問題のデバッグ方法は？{#set-variable}

以下のようなコマンドを使用してパイプライン変数をリストまたは設定しようとすると`403`エラーが発生する場合は、Admin Consoleに&#x200B;*Deployment Manager* Cloud Manager製品ロールとして追加する必要があります。\
詳しくは、[API権限](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md)を参照してください。

関連するコマンドとエラー：

`$ aio cloudmanager:list-pipeline-variables 222`

*エラー*: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1`

*エラー*: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`
