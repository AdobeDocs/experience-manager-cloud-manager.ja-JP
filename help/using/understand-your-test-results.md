---
title: テスト結果の理解
description: パイプラインのコード品質テストの仕組みと、デプロイメントの品質を向上させる方法について説明します。
uuid: 93caa01f-0df2-4a6f-81dc-23dfee24dc93
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: 83299ed8-4b7a-4b1c-bd56-1bfc7e7318d4
feature: CI-CD Pipeline, Test Results
exl-id: 6a574858-a30e-4768-bafc-8fe79f928294
source-git-commit: 2179314120911cac8a0dd99a8b57974751959871
workflow-type: tm+mt
source-wordcount: '2901'
ht-degree: 27%

---

# テスト結果の理解 {#understand-your-test-results}

パイプラインのコード品質テストの仕組みと、デプロイメントの品質を向上させる方法について説明します。

## はじめに {#introduction}

パイプラインの実行中、多数の指標が取り込まれ、ビジネスオーナーが定義した主要業績評価指標 (KPI) または Adobe Managed Services で設定された標準と比較されます。

これらは、次の節で定義する 3 層評価システムを使用して報告されます

>[!NOTE]
>
>AEM as a Cloud Service向け Cloud Manager でサポートされているテストについて詳しくは、 [AEMas a Cloud Serviceドキュメント。](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/test-results/overview-test-results.html).


## 3 層の評価  {#three-tier-gates-while-running-a-pipeline}

パイプラインには次の 3 つのゲートがあります。

* コード品質
* パフォーマンステスト
* セキュリティテスト

これらの各ゲートには、ゲートで特定される問題に対して 3 層構造があります。

* **重大**  — これらは、パイプラインの即時失敗を引き起こす問題です。
* **重要**  — これは、パイプラインの一時停止状態を引き起こす問題です。 デプロイメントマネージャー、プロジェクトマネージャーまたはビジネスオーナーは、問題をオーバーライドできます。この場合、パイプラインは続行されます。または、問題を承認できます。この場合、パイプラインはエラーで停止します。重要なエラーの上書きは、 [タイムアウト。](deploying-code.md#timeouts)
* **情報**  — これらは情報提供だけを目的とした問題で、パイプラインの実行には影響しません。

>[!NOTE]
>
>コード品質のみのパイプラインでは、コード品質テストステップがパイプラインの最後のステップなので、コード品質ゲートでの重要なエラーは上書きできません。

## コード品質テスト {#code-quality-testing}

この手順では、コード品質のみのパイプラインの主な目的であるアプリケーションコードの品質を評価し、非実稼動および実稼動のすべてのパイプラインのビルド手順の直後に実行します。 ドキュメントを参照してください [実稼動以外のパイプラインの設定](configuring-non-production-pipelines.md) を参照してください。

### コード品質テストの理解 {#understanding-code-quality-testing}

コード品質テストでは、ソースコードをスキャンして、特定の品質条件を満たしていることを確認します。 これは、SonarQube 分析、OakPAL を使用したコンテンツパッケージレベルの調査、Dispatcher 最適化ツールを使用した Dispatcher 検証の組み合わせによって実装されます。

汎用の Java ルールと AEM 固有のルールを組み合わせた 100 以上のルールがあります。AEM固有のルールの一部は、AEMエンジニアリングのベストプラクティスに基づいて作成され、 [カスタムコード品質ルールを参照してください。](/help/using/custom-code-quality-rules.md)

>[!NOTE]
>
>ルールの完全なリストをダウンロードできます [このリンクを使用して、](/help/using/assets/CodeQuality-rules-latest-AMS.xlsx)

コード品質テストの結果は、 **評価**. 次の表に、様々なテスト条件の評価の概要を示します。

| 名前 | 定義 | カテゴリ | 不合格のしきい値 |
|--- |--- |--- |--- |
| セキュリティ評価 | A =脆弱性なし<br/>B =軽度の脆弱性が 1 つ以上<br/>C = 1 つ以上の重大な脆弱性<br/>D = 1 つ以上の重大な脆弱性<br/>E = 1 つ以上の致命的脆弱性 | 重大 | &lt; B |
| 信頼性評価 | A =バグなし<br/>B =軽度のバグが 1 つ以上 <br/>C =重要なバグが 1 つ以上<br/>D =重要なバグが 1 つ以上ある<br/>E = 1 つ以上のブロッカーのバグ | 重要 | &lt; C |
| 保守性評価 | コードスメルの未処理の修正コストによって、アプリケーションに既に投入された時間の割合として定義されます。<br/><ul><li>A = 5%未満</li><li>B = 6～10%</li><li>C = 11～20%</li><li>D = 21～50%</li><li>E = 50%超</li></ul> | 重要 | &lt; A |
| カバレッジ | 次の式を使用して、単体テスト・ラインの有効範囲と条件の有効範囲を組み合わせて定義します。 <br/>`Coverage = (CT + CF + LC) / (2 * B + EL)`  <ul><li>`CT` =として評価された条件 `true` 単体テストの実行中に少なくとも 1 回</li><li>`CF` =として評価された条件 `false` 単体テストの実行中に少なくとも 1 回</li><li>`LC` =被覆線= lines_to_cover - uncovered_lines</li><li>`B` =条件の合計数</li><li>`EL` =実行可能な行の総数 (lines_to_cover)</li></ul> | 重要 | &lt; 50％ |
| スキップした単体テスト | スキップした単体テストの数 | 情報 | > 1 |
| 未解決の問題 | 問題の全体的なタイプ - 脆弱性、バグ、コードスメル | 情報 | > 0 |
| 重複行 | 重複したブロックに含まれる行の数として定義されます。 コードブロックは、次の条件下で重複していると見なされます。<br>Java 以外のプロジェクトの場合：<ul><li>100 個以上の連続した重複トークンが必要です。</li><li>これらのトークンは、少なくとも次の場所に分散する必要があります。 </li><li>30 行の COBOL コード </li><li>20 行の ABAP コード </li><li>10 行の他言語コード</li></ul>Java プロジェクト：<ul></li><li> トークンと行の数に関係なく、10 個以上の連続した重複ステートメントが必要です。</li></ul>重複を検出する際は、インデントの違いと文字列リテラルの違いは無視されます。 | 情報 | > 1％ |
| Cloud Service の互換性 | 識別されたCloud Service互換性の問題の数 | 情報 | > 0 |

>[!NOTE]
>
>参照： [SonarQube の指標の定義](https://docs.sonarqube.org/display/SONAR/Metric+Definitions) を参照してください。

>[!NOTE]
>
>で実行されるカスタムコード品質ルールの詳細を確認するには、以下を実行します。 [!UICONTROL Cloud Manager]（ドキュメントを参照してください） [カスタムコード品質ルールを参照してください。](custom-code-quality-rules.md)

### 偽陽性の処理 {#dealing-with-false-positives}

品質スキャンプロセスは完璧ではなく、実際には問題がないにもかかわらず問題として誤って特定することもあります。これは「**偽陽性**」と呼ばれます。

この場合、ルール ID を注釈属性として指定した標準の Java `@SuppressWarnings` 注釈を使用して、ソースコードに注釈を付けることができます。例えば、よくある偽陽性の 1 つとして、ハードコードされたパスワードを検出する SonarQube ルールは、ハードコードされたパスワードの識別方法に関して積極的におこなうことができます。

次のコードは、AEMプロジェクトではかなり一般的です。AEM プロジェクトには、一部の外部サービスに接続するコードが含まれています。

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

その後、SonarQube は致命的脆弱性を報告します。 ただし、コードを見直すと、これが脆弱性ではないことがわかり、適切なルール ID でコードに注釈を付けることができます。

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

ただし、コードが実際には次のような場合は、

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

ハードコードされたパスワードを削除するのが正しい解決策です。

>[!NOTE]
>
>`@SuppressWarnings` 注釈をできるだけ具体的にすることをお勧めします。つまり、問題の原因となっている特定のステートメントまたはブロックにのみ注釈を付けます。ただし、クラスレベルで注釈を付けることもできます。

## セキュリティテスト {#security-testing}

[!UICONTROL Cloud Manager] 既存の **AEM Security Heath Checks** ステージング環境で、デプロイメント後に、UI を通じてステータスを報告します。 結果は、環境内のすべての AEM インスタンスから集計されます。

同じヘルスチェックは、Web コンソールまたは操作ダッシュボードを通じて、いつでも実行できます。

いずれかのインスタンスが特定のヘルスチェックに対して失敗を報告した場合、環境全体がそのヘルスチェックに失敗します。 コード品質とパフォーマンスのテストと同様に、これらのヘルスチェックもカテゴリ別に整理され、3 層ゲートシステムを使用して報告されます。 セキュリティテストの場合にはしきい値がない点だけが異なります。すべてのヘルスチェックが合格または不合格となります。

次の表に、ヘルスチェックの一覧を示します。

| 名前 | ヘルスチェックの実装 | カテゴリ |
|---|---|---|
| デシリアライゼーションファイアウォール添付 API レディネスが、受け入れ可能な状態である. | [デシリアライゼーションファイアウォール添付 API レディネス](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html#security) | 重大 |
| デシリアライゼーションファイアウォールが機能している. | [デシリアライゼーションファイアウォール機能](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html#security) | 重大 |
| デシリアライゼーションファイアウォールが読み込まれている. | [デシリアライゼーションファイアウォール読み込み](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html#security) | 重大 |
| `AuthorizableNodeName` 実装において、認証可能な ID がノード名／パスで公開されていない | [認証可能なノード名生成](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html#security) | 重大 |
| デフォルトのパスワードが変更されている. | [デフォルトのログインアカウント](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html#users-and-groups-in-aem) | 重大 |
| Sling のデフォルトの GET サーブレットが DOS 攻撃から保護されている | Sling Get Servlet | 重大 |
| Sling Java Script Handler は、適切に設定されています。 | Sling Java Script Handler | 重大 |
| Sling JSP Script Handler が適切に設定されている。 | Sling JSP Script Handler | 重大 |
| SSL が正しく設定されている. | SSL 設定 | 重大 |
| 明らかに安全でないユーザープロファイルポリシーは見つかりません。 | ユーザープロファイルへのデフォルトアクセス | 重大 |
| Sling Referrer フィルターは、CSRF 攻撃を防ぐように設定されています。 | [Sling Referrer Filter](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html#security) | 重要 |
| Adobe Granite HTML Library Manager が適切に設定されている. | CQ HTML Library Manager 設定 | 重要 |
| CRXDE サポートバンドルが無効である. | CRXDE サポート | 重要 |
| Sling DavEx のバンドルおよびサーブレットが無効である. | DavEx ヘルスチェック | 重要 |
| サンプルコンテンツがインストールされていない. | サンプルコンテンツパッケージ | 重要 |
| WCM Request Filter と WCM Debug Filter が両方とも無効になっている. | [WCM フィルター設定](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/osgi-configuration-settings.html#configuring) | 重要 |
| Sling WebDAV のバンドルおよびサーブレットが適切に設定されている. | WebDAV ヘルスチェック | 重要 |
| Web サーバーが、クリックジャッキングを防止するように設定されている. | Web サーバー設定 | 重要 |
| レプリケーションは `admin` ユーザー。 | レプリケーションとトランスポートユーザー | 情報 |

## パフォーマンステスト {#performance-testing}

### AEM Sites {#aem-sites}

Cloud Manager は、AEM Sites プログラムのパフォーマンステストを実行します。パフォーマンステストは、実際のユーザーをシミュレートする仮想ユーザー（コンテナ）をスピンアップして、トラフィックをシミュレートするためにステージング環境でページにアクセスすることで、約 30 分間実行されます。 これらのページは、クローラーを使用して検出されます。

#### 仮想ユーザー {#virtual-users}

Cloud Manager でスパンアップされる仮想ユーザーまたはコンテナの数は、 **ビジネスオーナー** の役割が次のとき [プログラムを作成または編集する。](setting-up-program.md) 定義した KPI に基づいて、実際のユーザーをシミュレートする最大 10 個のコンテナがスパンアップされます。 テスト用に選択されたページが分割され、各仮想ユーザーに割り当てられます。

#### クローラ {#crawler}

30 分のテスト期間が開始される前に、Cloud Manager は、カスタマーサクセスエンジニアが設定した 1 つ以上のシード URL セットを使用してステージング環境をクロールします。 これらの URL から、各ページの HTML を調べ、幅優先方式でリンクが探索されます。このクロール処理は、最大 5000 ページに制限されています。クローラーからのリクエストのタイムアウトは 10 秒に固定されています。

#### テスト用ページセット {#page-sets}

ページは 3 つのページセットで選択されます。Cloud Manager は、実稼動環境とステージング環境全体でAEMインスタンスのアクセスログを使用して、以下のバケットを決定します。

* **頻度の高いライブページ**  — このオプションは、実稼働中の顧客が最も頻繁にアクセスするページをテストするために選択します。 Cloud Manager はアクセスログを読み取り、ライブユーザーによるアクセスが最も多かったページの上位 25 個を特定し、上位 `Popular Live Pages` のリストを生成します。その後、ステージング環境にも存在するこれらの積集合が、ステージング環境でクロールされます。

* **その他のライブページ**  — このオプションは、人気のある上位 25 ページ（人気のないライブページ）の外にあるがテストに重要なページが、確実にテストされるように選択されます。 人気の高いライブページと同様に、これらはアクセスログから抽出され、ステージング環境にも存在する必要があります。

* **新規ページ**  — このオプションは、ステージング環境にのみデプロイされ、まだ実稼動環境にはデプロイされていないが、テストが必要な新しいページをテストする場合に選択します。

##### 選択したページセット間のトラフィックの分布 {#distribution-of-traffic}

1 セットから 3 セットまで、 **テスト** 」タブから [パイプライン設定。](configuring-production-pipelines.md) トラフィックの配分は、選択したセット数に基づいておこなわれます。つまり、3 つすべてを選択した場合、ページビュー数の合計の 33%が各セットに配置されます。2 つを選択した場合、50%が各セットに割り当てられます。1 つを選択した場合、トラフィックの 100%がそのセットに割り当てられます。

この例を考えてみましょう。

* 頻度の高いライブページと新し50/50ページセットの間に分割があります。
* その他のライブページは使用されません。
* 新しいページセットには 3,000 ページが含まれています。
* 「1 分あたりのページビュー数」KPI は 200 に設定されます。

30 分間のテストの結果は次のようになります。

* 「頻度の高いライブページ」セットの 25 ページが各 120 回ヒットします。 `((200 * 0.5) / 25) * 30 = 120`
* 新しいページセットの 3,000 ページが各 1 回ヒットします。 `((200 * 0.5) / 3000) * 30 = 1`

#### テストとレポート {#testing-reporting}

Cloud Manager は、デフォルトで、ステージングパブリッシュサーバーで 30 分のテスト期間、ページを認証されていないユーザーとしてAEM Sitesプログラムのパフォーマンステストをリクエストすることで実行します。 仮想的なユーザー生成指標（応答時間、エラー率、1 分あたりのビュー数など）を測定します。 すべてのインスタンスに対して様々なシステムレベルの指標（CPU、メモリ、ネットワークデータ）を測定することで、AEM Sites プログラムのパフォーマンステストを実行します。

次の表に、3 層ゲートシステムを使用したパフォーマンステストマトリックスの概要を示します。

| 指標 | カテゴリ | 不合格のしきい値 |
|---|---|---|
| ページリクエストエラー率 | 重大 | >= 2% |
| CPU 使用率 | 重大 | >= 80% |
| ディスク I/O 待機時間 | 重大 | >= 50% |
| 第 95 百分位応答時間 | 重要 | >= プログラムレベルの KPI |
| ピーク応答時間 | 重要 | >= 18 秒 |
| 1 分あたりのページビュー数 | 重要 | &lt; プログラムレベルの KPI |
| ディスク帯域幅使用量 | 重要 | >= 90% |
| ネットワーク帯域幅使用量 | 重要 | >= 90% |
| 1 分あたりのリクエスト数 | 情報 | >= 6000 |

の節を参照してください。 [認証済みパフォーマンステスト](#authenticated-performance-testing) を参照してください。

>[!NOTE]
>
>テスト期間中は、オーサーインスタンスとパブリッシュインスタンスの両方が監視されます。 1 つのインスタンスの指標が取得されない場合、その指標は不明としてレポートされ、対応する手順が失敗します。

#### オプション — 認証済みパフォーマンステスト {#authenticated-performance-testing}

認証済みサイトを持つ AMS のお客様は、必要に応じて、Cloud Manager がサイトのパフォーマンステスト中に Web サイトにアクセスする際に使用するユーザー名とパスワードを指定できます。

ユーザー名とパスワードは、という名前で、パイプライン変数に指定します。 `CM_PERF_TEST_BASIC_USERNAME` および `CM_PERF_TEST_BASIC_PASSWORD`.

ユーザー名は、 `string` 変数を使用し、パスワードを `secretString` 変数を使用します。 これらの両方を指定した場合、パフォーマンステストクローラーとテスト仮想ユーザーからのリクエストすべてに、HTTP 基本認証としての資格情報が含まれます。

Cloud Manager CLI を使用してこれらの変数を設定するには、次のコマンドを実行します。

```shell
$ aio cloudmanager:set-pipeline-variables <pipeline id> --variable CM_PERF_TEST_BASIC_USERNAME <username> --secret CM_PERF_TEST_BASIC_PASSWORD <password>
```

ドキュメントを参照してください [ユーザーパイプライン変数のパッチ適用](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Variables/patchPipelineVariables) を参照してください。

### AEM Assets {#aem-assets}

Cloud Manager では、30 分間のテスト期間にわたってアセットを繰り返しアップロードすることで、AEM Assets プログラムのパフォーマンステストを実行します。

#### オンボーディング要件 {#onboarding-requirement}

Assets のパフォーマンステストの場合、カスタマーサクセスエンジニアが `cloudmanager` オーサー環境からステージング環境へのオンボーディング中のユーザーとパスワード。 パフォーマンステストの手順では、 `cloudmanager` および CSE が設定した関連パスワード。 これは、オーサーインスタンスから削除したり、権限を変更したりしないでください。 Assets のパフォーマンステストが失敗する可能性があります。

#### テスト用の画像とアセット {#assets-for-testing}

顧客は、独自のアセットをアップロードしてテストできます。これは、 **パイプライン設定** または **編集** 画面 JPEG、PNG、GIF、BMP などの一般的な画像形式のほか、Photoshop ファイル、Illustrator ファイル、Postscript ファイルがサポートされています。

画像がアップロードされない場合、Cloud Manager はデフォルトの画像およびPDFドキュメントをテストに使用します。

#### テスト用アセットの配分 {#distribution-of-assets}

1 分あたりにアップロードされる各タイプのアセット数の配分は、 **パイプライン設定** または **編集** 画面

例えば、70/30分割を使用し、1 分に 10 個のアセットがアップロードされる場合、1 分に 7 個の画像と 3 個のドキュメントがアップロードされます。

#### テストとレポート {#testing-and-reporting}

Cloud Manager は、CSE が設定したユーザー名とパスワードを使用して、オーサーインスタンス上にフォルダーを作成します ( [オンボーディング要件](#onboaring-requirements) 」セクションに入力します。 その後、オープンソースライブラリを使用してアセットがフォルダーにアップロードされます。 Assets のテスト手順で実行されるテストは、 [オープンソースライブラリ。](https://github.com/adobe/toughday2)30 分のテスト期間にわたって、各アセットの処理時間と、様々なシステムレベルの指標の両方が測定されます。この機能では、画像とPDF文書の両方をアップロードできます。

>[!TIP]
>
>ドキュメントを参照してください [実稼動パイプラインの設定](configuring-production-pipelines.md) を参照してください。 ドキュメントを参照します。 [プログラムの設定](setting-up-program.md) を参照してください。

### パフォーマンステスト結果のグラフ {#performance-testing-results-graphs}

様々な指標を **パフォーマンステストダイアログ**

![指標のリスト](assets/understand_test-results-screen1.png)

指標パネルを展開して、グラフを表示したり、ダウンロードへのリンクを提供したりできます。

![グラフとして展開された指標](assets/screen_shot_2018-09-05at83933pm.png)

この機能は、次の指標で使用できます。

* **CPU 使用率**
   * テスト期間中の CPU 使用率のグラフ

* **ディスク I/O 待機時間**
   * テスト期間中のディスク I/O 待機時間のグラフ

* **ページエラー率**
   * テスト期間中の 1 分あたりのページエラー数のグラフ
   * テスト中にエラーが発生したページの一覧を示す CSV ファイル

* **ディスク帯域幅使用量**
   * テスト期間中のディスク帯域幅使用量のグラフ

* **ネットワーク帯域幅使用量**
   * テスト期間中のネットワーク帯域幅使用量のグラフ

* **ピーク応答時間**
   * テスト期間中の 1 分あたりのピーク応答時間のグラフ

* **第 95 百分位応答時間**
   * テスト期間中の 1 分あたりの第 95 百分位応答時間のグラフ
   * 第 95 百分位応答時間が定義済みの KPI を超えたページの一覧を示す CSV ファイル

## コンテンツパッケージスキャンの最適化 {#content-package-scanning-optimization}

Cloud Manager は、品質分析プロセスの一環として、Maven ビルドで生成されたコンテンツパッケージの分析を実行します。 Cloud Manager は、このプロセスを高速化するための最適化を提供します。この最適化は、特定のパッケージ化の制約が観察された場合に有効です。 最も重要なのは、単一のコンテンツパッケージ（一般的に「すべて」パッケージと呼ばれます）を出力するプロジェクトで実行される最適化です。このパッケージには、ビルドで作成された他の多数のコンテンツパッケージが含まれ、スキップ済みとしてマークされます。 Cloud Manager がこのシナリオを検出すると、「すべて」パッケージを解凍するのではなく、個々のコンテンツパッケージが直接スキャンされ、依存関係に基づいて並べ替えられます。 例えば、次のビルド出力について考えてみましょう。

* `all/myco-all-1.0.0-SNAPSHOT.zip` (content-package)
* `ui.apps/myco-ui.apps-1.0.0-SNAPSHOT.zip` (skipped-content-package)
* `ui.content/myco-ui.content-1.0.0-SNAPSHOT.zip` (skipped-content-package)

次の中の唯一の項目： `myco-all-1.0.0-SNAPSHOT.zip` がスキップされた 2 つのコンテンツパッケージの場合、「すべて」のコンテンツパッケージの代わりに、2 つの埋め込みパッケージがスキャンされます。

数十の埋め込みパッケージを生成するプロジェクトの場合、この最適化により、パイプライン実行あたり 10 分以上の時間を節約できることが示されています。

「すべて」のコンテンツパッケージに、スキップされたコンテンツパッケージと OSGi バンドルの組み合わせが含まれている場合は、特殊なケースが発生する場合があります。 例えば、 `myco-all-1.0.0-SNAPSHOT.zip` には、前述の 2 つの埋め込みパッケージと 1 つ以上の OSGi バンドルが含まれていました。その後、OSGi バンドルのみを使用して、新しい最小限のコンテンツパッケージが構築されます。 このパッケージの名前は常にです `cloudmanager-synthetic-jar-package` 含まれるバンドルは、 `/apps/cloudmanager-synthetic-installer/install`.

>[!NOTE]
>
>* この最適化は、AEMにデプロイされるパッケージには影響しません。
>* 埋め込みコンテンツパッケージとスキップされたコンテンツパッケージの照合はファイル名に基づくので、スキップされたコンテンツパッケージの複数のファイル名が完全に同じ場合や、埋め込み中にファイル名が変更された場合は、この最適化を実行できません。