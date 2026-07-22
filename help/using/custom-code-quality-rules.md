---
title: カスタムコード品質ルール
description: コード品質テスト中に Cloud Manager で実行されるカスタムコード品質ルールの詳細を確認します。 これらのルールは、AEM Engineering のベストプラクティスに基づいています。
exl-id: 7d118225-5826-434e-8869-01ee186e0754
TQID: https://experienceleague.adobe.com/Iee3iEbblEV7TDJxtYpBH8F6oomtD9EJMPX1SSRGIGA
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a01bfd36-4ab8-4bf8-9dc0-5b45b890552e
  - id: ff09c71c-26a9-449a-85f8-2aeb8ce96100
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 3ecc950f1fc53c4c7bf4a079c08c33f6dd34fe23
workflow-type: tm+mt
source-wordcount: 4096
ht-degree: 80%

---

# カスタムコード品質ルール {#custom-code-quality-rules}

AEM Engineering のベストプラクティスに基づいて、Cloud Manager が[コード品質テスト](/help/using/code-quality-testing.md)の一環として実行するカスタムコード品質ルールについて詳しく説明します。

>[!NOTE]
>
>ここで提供されるコードサンプルは、例としてのみ使用されています。 その概念と品質ルールについて詳しくは、[SonarQubeのConcepts ドキュメント &#x200B;](https://docs.sonarsource.com/sonarqube-server)を参照してください。

完全な SonarQube ルールは、アドビ独自の情報が原因でダウンロードできません。 ルールの完全なリストをダウンロードするには、[このリンクを使用](/help/assets/CodeQuality-rules-latest-AMS.xlsx)します。 ルールの説明と例については、このドキュメントを引き続き参照してください。

>[!IMPORTANT]
>
>2025年2月13日木曜日（PT）（Cloud Manager 2025.2.0）以降、Cloud Manager コード品質では、更新された SonarQube 9.9 バージョンと、更新されたルールのリスト（[ここからダウンロード](/help/assets/CodeQuality-rules-latest-AMS-2024-12-0.xlsx)できます）が使用されます。

## SonarQube ルール {#sonarqube-rules}

以下の節では、Cloud Manager で実行される SonarQube ルールについて説明します。

### 問題が発生する可能性がある関数は使用しない {#do-not-use-potentially-dangerous-functions}

* **キー**: CQRules:CWE-676
* **タイプ**：脆弱性
* **深刻度**：重大
* **最初の対象バージョン**：バージョン 2018.4.0

`Thread.stop()` と `Thread.interrupt()` のメソッドは、再現が困難な問題を引き起こし、場合によってはセキュリティの脆弱性を生み出す可能性があります。 その使用状況は、厳密に監視および検証する必要があります。 一般的に、似た目標を達成するにはメッセージを渡すとより安全です。

#### 非準拠コード {#non-compliant-code}

```java
public class DontDoThis implements Runnable {
  private Thread thread;
 
  public void start() {
    thread = new Thread(this);
    thread.start();
  }
 
  public void stop() {
    thread.stop();  // UNSAFE!
  }
 
  public void run() {
    while (true) {
        somethingWhichTakesAWhileToDo();
    }
  }
}
```

#### 準拠コード {#compliant-code}

```java
public class DoThis implements Runnable {
  private Thread thread;
  private boolean keepGoing = true;
 
  public void start() {
    thread = new Thread(this);
    thread.start();
  }
 
  public void stop() {
    keepGoing = false;
  }
 
  public void run() {
    while (this.keepGoing) {
        somethingWhichTakesAWhileToDo();
    }
  }
}
```

### 外部で制御されている書式文字列は使用しないでください {#do-not-use-format-strings-which-may-be-externally-controlled}

* **キー**: CQRules:CWE-134
* **タイプ**：脆弱性
* **深刻度**：重大
* **最初の対象バージョン**：バージョン 2018.4.0

外部ソース（リクエストパラメーターやユーザー生成コンテンツなど）の書式指定文字列を使用すると、アプリケーションがサービス拒否（DoS）攻撃にさらされる可能性があります。 書式文字列は外部で制御されますが、信頼できるソースからのみ許可される場合があります。

#### 非準拠コード {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text"));
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### HTTP 要求には常にソケットおよび接続タイムアウトが必要 {#http-requests-should-always-have-socket-and-connect-timeouts}

* **キー**: CQRules:ConnectionTimeoutMechanism
* **タイプ**：バグ
* **深刻度**：致命的
* **最初の対象バージョン**：バージョン 2018.6.0

AEM アプリケーション内から HTTP リクエストを実行する場合、適切なタイムアウトを設定して、不要なスレッドの消費を防ぐことが重要です。 ただし、Java™ のデフォルトの HTTP クライアント（`java.net.HttpUrlConnection`）および広く使用されている Apache HTTP コンポーネントクライアントには、デフォルトのタイムアウトがありません。 したがって、タイムアウトを明示的に設定する必要があります。 ベストプラクティスとして、これらのタイムアウトは60秒以下です。

#### 非準拠コード {#non-compliant-code-2}

```java
@Reference
private HttpClientBuilderFactory httpClientBuilderFactory;
 
public void dontDoThis() {
  HttpClientBuilder builder = httpClientBuilderFactory.newBuilder();
  HttpClient httpClient = builder.build();

  // do something with the client
}

public void dontDoThisEither() {
  URL url = new URL("http://www.google.com");
  URLConnection urlConnection = url.openConnection();
 
  BufferedReader in = new BufferedReader(new InputStreamReader(
    urlConnection.getInputStream()));
 
  String inputLine;
  while ((inputLine = in.readLine()) != null) {
    logger.info(inputLine);
  }
 
  in.close();
}
```

#### 準拠コード {#compliant-code-1}

```java
@Reference
private HttpClientBuilderFactory httpClientBuilderFactory;
 
public void doThis() {
  HttpClientBuilder builder = httpClientBuilderFactory.newBuilder();
  RequestConfig requestConfig = RequestConfig.custom()
    .setConnectTimeout(5000)
    .setSocketTimeout(5000)
    .build();
  builder.setDefaultRequestConfig(requestConfig);
 
  HttpClient httpClient = builder.build();
   
  // do something with the client
}

public void orDoThis() {
  URL url = new URL("http://www.google.com");
  URLConnection urlConnection = url.openConnection();
  urlConnection.setConnectTimeout(5000);
  urlConnection.setReadTimeout(5000);
 
  BufferedReader in = new BufferedReader(new InputStreamReader(
    urlConnection.getInputStream()));
 
  String inputLine;
  while ((inputLine = in.readLine()) != null) {
    logger.info(inputLine);
  }
 
  in.close();
}
```

### オブジェクト `ResourceResolver` は常に閉じる必要がある {#resourceresolver-objects-should-always-be-closed}

* **キー**: CQRules:CQBP-72
* **タイプ**：`Code Smell`
* **深刻度**：重大
* **最初の対象バージョン**：バージョン 2018.4.0

`ResourceResolverFactory` から取得された `ResourceResolver` オブジェクトは、システムリソースを使用します。 `ResourceResolver` が使用されなくなった場合に、これらのリソースを再利用する指標がありますが、`close()` メソッドを呼び出し、開いている `ResourceResolver` オブジェクトを明示的に閉じるほうが効率的です。

既存の JCR セッションを使用して作成された `ResourceResolver` オブジェクトは明示的に閉じることはできないという一般的な誤解があります。 もう 1 つは、これらのオブジェクトを閉じると、基になる JCR セッションを閉じてしまうというの誤解があります。 そのようなことはありません。 どの方法で `ResourceResolver` を開いても、使用しなくなったら閉じる必要があります。 `ResourceResolver` は `Closeable` インターフェイスを実装するので、`close()` を明示的に呼び出す代わりに、`try-with-resources` 構文を使用することもできます。

#### 非準拠コード {#non-compliant-code-4}

```java
public void dontDoThis(Session session) throws Exception {
  ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
  // do some stuff with the resolver
}
```

#### 準拠コード {#compliant-code-2}

```java
public void doThis(Session session) throws Exception {
  ResourceResolver resolver = null;
  try {
    resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
    // do something with the resolver
  } finally {
    if (resolver != null) {
      resolver.close();
    }
  }
}

public void orDoThis(Session session) throws Exception {
  try (ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object) session))){
    // do something with the resolver
  }
}
```

### サーブレットの登録に Sling サーブレットパスを使用しない {#do-not-use-sling-servlet-paths-to-register-servlets}

* **キー**: CQRules:CQBP-75
* **タイプ**：`Code Smell`
* **深刻度**：重大
* **最初の対象バージョン**：バージョン 2018.4.0

[Sling ドキュメント &#x200B;](https://sling.apache.org/documentation/the-sling-engine/servlets.html)で説明しているように、パスによるサーブレットのバインドは推奨されません。 パスバインドサーブレットでは、標準 JCR アクセス制御を使用できないので、追加のセキュリティをより厳格にする必要があります。 パスバインドサーブレットを使用する代わりに、リポジトリにノードを作成し、リソースタイプによってサーブレットを登録することをお勧めします。

#### 非準拠コード {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### キャッチされた例外は、ログに記録またはスローする必要があるが、両方は行わない {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

* **キー**: CQRules:CQBP-44---CatchAndEitherLogOrThrow
* **タイプ**：`Code Smell`
* **深刻度**：軽度
* **最初の対象バージョン**：バージョン 2018.4.0

一般に、例外は 1 回だけログに記録する必要があります。 複数回ログに記録すると、例外が発生した回数がわからなくなるので、混乱が生じる可能性があります。 この問題を引き起こす最も一般的なパターンは、キャッチされた例外をログに記録してスローすることです。

#### 非準拠コード {#non-compliant-code-6}

```java
public void dontDoThis() throws Exception {
  try {
    someOperation();
  } catch (Exception e) {
    logger.error("something went wrong", e);
    throw e;
  }
}
```

#### 準拠コード {#compliant-code-3}

```java
public void doThis() {
  try {
    someOperation();
  } catch (Exception e) {
    logger.error("something went wrong", e);
  }
}

public void orDoThis() throws MyCustomException {
  try {
    someOperation();
  } catch (Exception e) {
    throw new MyCustomException(e);
  }
}
```

### ログステートメントの直後にスローステートメントを使用しない {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

* **キー**: CQRules:CQBP-44---ConsecutivelyLogAndThrow
* **タイプ**：`Code Smell`
* **深刻度**：軽度
* **最初の対象バージョン**：バージョン 2018.4.0

もうひとつの避けるべき一般的なパターンは、メッセージをログに記録してからすぐに例外をスローすることです。 この問題は、例外メッセージがログファイルに重複していることを示します。

#### 非準拠コード {#non-compliant-code-7}

```java
public void dontDoThis() throws Exception {
  logger.error("something went wrong");
  throw new RuntimeException("something went wrong");
}
```

#### 準拠コード {#compliant-code-4}

```java
public void doThis() throws Exception {
  throw new RuntimeException("something went wrong");
}
```

### GET または HEAD 要求の処理時に INFO でログに記録しない {#avoid-logging-at-info-when-handling-get-or-head-requests}

* **キー**: CQRules:CQBP-44---LogInfoInGetOrHeadRequests
* **タイプ**：`Code Smell`
* **深刻度**：軽度

一般的に、INFO ログレベルは重要なアクションを区切るために使用し、デフォルトでは、AEM は INFO レベル以上をログに記録するように設定されています。 GET および HEAD メソッドは読み取り専用操作に過ぎず、重要なアクションを構成しません。 GETまたはHEAD リクエストに応じてINFO レベルでログを記録すると、ログのノイズが大きくなり、ログファイル内の有用な情報を特定することが困難になります。 GET または HEAD リクエストを処理する際に、問題が発生した場合は、WARN または ERROR レベルでログを記録します。 トラブルシューティングの詳細については、DEBUG レベルまたはTRACE レベルにログインしてください。

>[!NOTE]
>
>このワークフローは、各リクエストの access.log-type ログには適用されません。

#### 非準拠コード {#non-compliant-code-8}

```java
public void doGet() throws Exception {
  logger.info("handling a request from the user");
}
```

#### 準拠コード {#compliant-code-5}

```java
public void doGet() throws Exception {
  logger.debug("handling a request from the user.");
}
```

### `Exception.getMessage()` をログステートメントの最初のパラメーターとして使用しない {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

* **キー**: CQRules:CQBP-44---ExceptionGetMessageIsFirstLogParam
* **タイプ**：`Code Smell`
* **深刻度**：軽度
* **最初の対象バージョン**：バージョン 2018.4.0

ベストプラクティスとして、ログメッセージは、アプリケーション内での問題の発生場所に関するコンテキスト情報を提供する必要があります。 スタックトレースを使用してコンテキストを判断する場合、一般的にログメッセージは読みやすく、理解しやすくなります。 その結果、例外をログに記録する際に、例外のメッセージをログメッセージとして使用するのは適切ではありません。 例外メッセージは、何が問題だったのかを詳細に説明します。 一方、ログメッセージは、例外が発生したときにアプリケーションが実行した内容をリーダーに通知します。 例外メッセージはログに記録されます。 独自のメッセージを指定すると、ログがわかりやすくなります。

#### 非準拠コード {#non-compliant-code-9}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error(e.getMessage(), e);
  }
}
```

#### 準拠コード {#compliant-code-6}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### キャッチブロックへのログインはWARN レベルまたはERROR レベルです {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

* **キー**: CQRules:CQBP-44---WrongLogLevelInCatchBlock
* **タイプ**：`Code Smell`
* **深刻度**：軽度
* **最初の対象バージョン**：バージョン 2018.4.0

名前が示すように、Java™ の例外は常に例外的な状況で使用する必要があります。 結果として、例外が検出されたときには、ログメッセージが適切なレベル（WARN または ERROR）で記録されるようにすることが重要です。 これにより、これらのメッセージがログに正しく表示されます。

#### 非準拠コード {#non-compliant-code-10}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.debug(e.getMessage(), e);
  }
}
```

#### 準拠コード {#compliant-code-7}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### コンソールにスタックトレースをプリントしない {#do-not-print-stack-traces-to-the-console}

* **キー**: CQRules:CQBP-44---ExceptionPrintStackTrace
* **タイプ**：`Code Smell`
* **深刻度**：軽度
* **最初の対象バージョン**：バージョン 2018.4.0

ログメッセージを理解する際にはコンテキストが重要です。 `Exception.printStackTrace()`を使用すると、スタックトレースのみが標準のエラーストリームに出力され、すべてのコンテキストが省略されます。 さらに、AEMのようなマルチスレッドアプリケーションでは、並列スタックトレース出力で問題が発生します。 例外は、ログフレームワークによってのみ記録される必要があります。

#### 非準拠コード {#non-compliant-code-11}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    e.printStackTrace();
  }
}
```

#### 準拠コード {#compliant-code-8}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### 標準出力または標準エラーに出力しない {#do-not-output-to-standard-output-or-standard-error}

* **Key**: CQRules:CQBP-44—LogLevelConsolePrinters
* **タイプ**：`Code Smell`
* **深刻度**：軽度
* **最初の対象バージョン**：バージョン 2018.4.0

AEM にログインする場合は、常にログフレームワーク（SLF4J）を使用してログインする必要があります。 標準出力または標準エラーストリームに直接出力すると、ロギングフレームワークによって提供される構造情報とコンテクスト情報が失われ、パフォーマンスの問題が発生することがあります。

#### 非準拠コード {#non-compliant-code-12}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    System.err.println("Unable to do something");
  }
}
```

#### 準拠コード {#compliant-code-9}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### ハードコードされた `/apps` および `/libs` パスを使用しない {#avoid-hardcoded-apps-and-libs-paths}

* **キー**: CQRules:CQBP-71
* **タイプ**：`Code Smell`
* **深刻度**：軽度
* **最初の対象バージョン**：バージョン 2018.4.0

`/libs`と`/apps`で始まるパスはハードコードされていません。 これらのパスは通常、`Sling`検索パスに対して保存されます。デフォルトは`/libs,/apps`です。 絶対パスを使用すると、プロジェクトのライフサイクルの後半でのみ発生する微妙な欠陥が発生します。

#### 非準拠コード {#non-compliant-code-13}

```java
public boolean dontDoThis(Resource resource) {
  return resource.isResourceType("/libs/foundation/components/text");
}
```

#### 準拠コード {#compliant-code-10}

```java
public void doThis(Resource resource) {
  return resource.isResourceType("foundation/components/text");
}
```

### Sling スケジューラーは使用しない {#sonarqube-sling-scheduler}

* **キー**: CQRules:AMSCORE-554
* **タイプ**：`Code Smell`／Cloud Service との互換性
* **深刻度**：軽度
* **最初の対象バージョン**：バージョン 2020.5.0

保証された実行を必要とするタスクには、Sling Schedulerを使用しないでください。 Sling Scheduled Jobsは、実行を保証し、クラスター環境と非クラスター環境の両方に適しています。

クラスター環境でのSling ジョブの処理方法について詳しくは、[Apache Sling イベントおよびジョブ処理に関するドキュメント &#x200B;](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html)を参照してください。

### AEM非推奨APIを使用しない {#sonarqube-aem-deprecated}

* **キー**：AMSCORE-553
* **タイプ**：`Code Smell`／Cloud Service との互換性
* **深刻度**：軽度
* **最初の対象バージョン**：バージョン 2020.5.0

AEM API の表面は、使用が推奨されず非推奨と見なされる API を識別するために継続的に見直しされます。

多くの場合、これらのAPIは、標準のJava™ *@Deprecated*&#x200B;注釈を使用して非推奨（廃止予定）になっています。この注釈は`squid:CallToDeprecatedMethod`と認識されます。

ただし、AEMのコンテキストではAPIが非推奨ですが、他のコンテキストでは非推奨ではない場合があります。 このルールは、この 2 番目のクラスを識別します。

## OakPAL コンテンツルール {#oakpal-rules}

以下の節では、Cloud Manager が実行する OakPAL チェックについて説明します。

>[!NOTE]
>
>OakPAL は、スタンドアロンの Oak リポジトリを使用してコンテンツパッケージを検証するフレームワークです。 2019年の「AEMロックスター北米」賞の受賞者であるAEMパートナーが開発しました。

### @ProviderTypeで注釈を付けた製品APIを実装または拡張しない {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

* **キー**：CQBP-84
* **タイプ**：バグ
* **深刻度**：致命的
* **最初の対象バージョン**：バージョン 2018.7.0

AEM API には、カスタムコードで使用されることを意図していますが実装できない Java™ インターフェイスとクラスが含まれています。 例えば、インターフェイス `com.day.cq.wcm.api.Page` を実装するのは AEM のみです。

これらのインターフェイスに新しいメソッドを追加しても、既存のコードには影響しないので、新しいメソッドの追加には後方互換性があります。 ただし、カスタムコードがこれらのインターフェイスのいずれかを実装する場合、そのカスタムコードによってお客様に後方互換性のリスクがもたらされます。

AEM では、実装専用のインターフェイスとクラスに `org.osgi.annotation.versioning.ProviderType` で注釈を付けたり、場合によっては従来の注釈 `aQute.bnd.annotation.ProviderType` を付けたりします。 このルールでは、カスタムコードがこのようなインターフェイスを実装したり、クラスを拡張したりするインスタンスを検出します。

#### 非準拠コード {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### 顧客パッケージの`/libs`の下にノードを作成または編集しないでください {#oakpal-customer-package}

* **キー**：BannedPath
* **タイプ**：バグ
* **重大度**：ブロッカー
* **最初の対象バージョン**：バージョン 2019.6.0

AEM コンテンツリポジトリ内の `/libs` コンテンツツリーを読み取り専用と見なすことは長年のベストプラクティスとなっています。 `/libs` 下のノードやプロパティを変更すると、メジャーアップデートおよびマイナーアップデートの際に重大な問題が発生する可能性があります。 Adobeは、公式チャンネルを通じてのみ`/libs`に編集を行います。

### パッケージには重複する OSGi 設定を含めない {#oakpal-package-osgi}

* **キー**：DuplicateOsgiConfigurations
* **タイプ**：バグ
* **深刻度**：重大
* **最初の対象バージョン**：バージョン 2019.6.0

複雑なプロジェクトでよく発生する問題は、同じ OSGi コンポーネントが複数回設定されることです。 この問題により、どの設定が操作可能かがあいまいになります。 このルールは「実行モード対応」です。つまり、同じコンポーネントが同じ実行モード（または実行モードの組み合わせ）で複数回設定されている問題のみを特定します。

#### 非準拠コード {#non-compliant-code-osgi}

```text
+ apps
  + projectA
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
  + projectB
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

#### 準拠コード {#compliant-code-osgi}

```text
+ apps
  + shared-config
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

### config および install フォルダーには OSGi ノードのみを含める {#oakpal-config-install}

* **キー**：ConfigAndInstallShouldOnlyContainOsgiNodes
* **タイプ**：バグ
* **深刻度**：重大
* **最初の対象バージョン**：バージョン 2019.6.0

セキュリティ上の理由から、`/config/` と `/install/` を含むパスを判読できるのは AEM の管理者ユーザーのみで、これらは OSGi 設定と OSGi バンドルにのみ使用する必要があります。 これらのセグメントを含むパスの下に他のタイプのコンテンツを配置すると、アプリケーションの動作が管理者ユーザーと非管理者ユーザーとで意図せず異なることになります。

よくある問題としては、コンポーネントダイアログボックス内や、インライン編集にリッチテキストエディター設定を指定する際に、`config` というノードを使用するケースがあります。 この問題を解決するには、問題のノードを準拠した名前に変更する必要があります。 リッチテキストエディター設定については、`cq:inplaceEditing` ノードの `configPath` プロパティを使用して新しい場所を指定します。

#### 非準拠コード {#non-compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    + config [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

#### 準拠コード {#compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    ./configPath = inplaceEditingConfig (String)
    + inplaceEditingConfig [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

### パッケージは重なってはいけません {#oakpal-no-overlap}

* **キー**：PackageOverlaps
* **タイプ**：バグ
* **深刻度**：重大
* **最初の対象バージョン**：バージョン 2019.6.0

[&#x200B; パッケージに重複したOSGi設定ルールを含めないでください](#oakpal-package-osgi)と同様に、この問題は、複数の個別のコンテンツパッケージが同じノードパスに書き込まれる複雑なプロジェクトで一般的な問題です。 コンテンツパッケージの依存関係を使用すると、一貫性のある結果を得ることができますが、その際には、パッケージがまったく重複しないようにすることをお勧めします。

### デフォルトのオーサリングモードはクラシック UIではありません {#oakpal-default-authoring}

* **キー**：ClassicUIAuthoringMode
* **タイプ**：`Code Smell`／Cloud Service との互換性
* **深刻度**：軽度
* **最初の対象バージョン**：バージョン 2020.5.0

OSGi 設定 `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` は、AEM 内でデフォルトのオーサリングモードを定義します。 AEM 6.4 以降、クラシック UI は非推奨となったので、デフォルトのオーサリングモードがクラシック UI に設定されている場合、問題が発生するようになりました。

### ダイアログボックスを含むコンポーネントには、タッチ UI ダイアログボックスが必要です {#oakpal-components-dialogs}

* **キー**：ComponentWithOnlyClassicUIDialog
* **タイプ**：`Code Smell`／Cloud Service との互換性
* **深刻度**：軽度
* **最初の対象バージョン**：バージョン 2020.5.0

クラシック UI ダイアログを使用する AEM コンポーネントには、クラシック UI をサポートしていない Cloud Service デプロイメントモデルとの最適なオーサリングと互換性を確保するのに、タッチ UI ダイアログも必要です。 このルールは、次のシナリオを検証します。

* クラシック UI ダイアログ（`dialog` 子ノード）を持つコンポーネントには、対応するタッチ UI ダイアログ（`cq:dialog` 子ノード）が必要です。
* クラシック UI デザインダイアログ（`design_dialog` ノード）を使用しているコンポーネントには、対応するタッチ UI デザインダイアログ（`cq:design_dialog` 子ノード）が必要です。
* クラシック UI ダイアログとクラシック UI デザインダイアログの両方を持つコンポーネントには、対応するタッチ UI ダイアログと対応するタッチ UI デザインダイアログの両方が必要です。

AEM 最新化ツールのドキュメントには、コンポーネントをクラシック UI からタッチ UI に変換する方法に関する詳細とツールが記載されています。 詳しくは、[AEM Modernization Tools のドキュメント](https://opensource.adobe.com/aem-modernize-tools/)を参照してください。

### リバースレプリケーションエージェントは使用しない {#oakpal-reverse-replication}

* **キー**：ReverseReplication
* **タイプ**：`Code Smell`／Cloud Service との互換性
* **深刻度**：軽度
* **最初の対象バージョン**：バージョン 2020.5.0

リバースレプリケーションのサポートは、[リリースノート：レプリケーションエージェントの削除](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/release-notes/aem-cloud-changes#replication-agents)で説明しているように、Cloud Service のデプロイメントでは利用できません。

リバースレプリケーションを使用するお客様は、アドビに問い合わせて、代替ソリューションをご利用ください。

### プロキシ対応クライアントライブラリに含まれるリソースは、resourcesという名前のフォルダーに格納されます {#oakpal-resources-proxy}

* **キー**：ClientlibProxyResource
* **タイプ**：バグ
* **深刻度**：軽度
* **最初の対象バージョン**：バージョン 2021.2.0

AEM クライアントライブラリには、画像やフォントなどの静的リソースを含めることができます。 [クライアントサイドライブラリの使用のドキュメント](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/implementing/developing/introduction/clientlibs#using-preprocessors)で説明されるように、プロキシ化されたクライアントライブラリを使用する場合、パブリッシュインスタンスで効果的に参照するために、これらの静的リソースを `resources` という名前の子フォルダーに格納する必要があります。

#### 非準拠コード {#non-compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + images
        + myimage.jpg
```

#### 準拠コード {#compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + resources
        + myimage.jpg
```

### Cloud Service と互換性のないワークフロープロセスの使用 {#oakpal-usage-cloud-service}

* **キー**：CloudServiceIncompatibleWorkflowProcess
* **タイプ**：`Code Smell`
* **重大度**：ブロッカー
* **最初の対象バージョン**：バージョン 2021.2.0

AEM Cloud Service 上でアセット処理を行う Assets マイクロサービスに移行すると、AEM のオンプレミスバージョンと AMS バージョンで使用されていたワークフロープロセスが、サポートされなくなる、または不要になります。

[AEM Assets as a Cloud Service GitHub リポジトリ](https://github.com/adobe/aem-cloud-migration)の移行ツールを使用すると、AEM as a Cloud Service への移行中にワークフローモデルを更新できます。

### 静的なテンプレートより編集可能なテンプレートの使用を推奨 {#oakpal-static-template}

* **キー**：StaticTemplateUsage
* **タイプ**：`Code Smell`
* **深刻度**：軽度
* **最初の対象バージョン**：バージョン 2021.2.0

従来、AEM プロジェクトでは静的テンプレートを使用するのが一般的でしたが、最も柔軟性が高く、静的なテンプレートにはない追加機能をサポートしている編集可能なテンプレートを強くお勧めします。 詳しくは、[&#x200B; ページテンプレート – 編集可能なドキュメント &#x200B;](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/implementing/developing/platform/templates/page-templates-editable)を参照してください。

静的なテンプレートから編集可能なテンプレートへの移行は、[AEM 最新化ツール](https://opensource.adobe.com/aem-modernize-tools/)を使用して、大幅に自動化できます。

### 従来の基盤コンポーネントの使用は推奨されない {#oakpal-usage-legacy}

* **キー**：LegacyFoundationComponentUsage
* **タイプ**：`Code Smell`
* **深刻度**：軽度
* **最初の対象バージョン**：バージョン 2021.2.0

一部の AEM リリースでは、従来の基盤コンポーネント（`/libs/foundation` 下のコンポーネントなど）は廃止され、[コアコンポーネント](https://experienceleague.adobe.com/ja/docs/experience-manager-core-components/using/introduction)に置き換わりました。 使用する方法がオーバーレイであろうと継承であろうと、従来の基盤コンポーネントに基づいてカスタムコンポーネントを使用することは、お勧めしません。対応するコアコンポーネントに変換してください。

[AEM Modernization Tools](https://opensource.adobe.com/aem-modernize-tools/) を使用すると、この変換が容易になります。

### カスタム検索インデックス定義ノードは、`/oak:index` の直接の子にする必要がある {#oakpal-custom-search}

* **キー**：OakIndexLocation
* **タイプ**：`Code Smell`
* **深刻度**：軽度
* **最初の対象バージョン**：バージョン 2021.2.0

AEM Cloud Service では、カスタム検索インデックス定義（`oak:QueryIndexDefinition` タイプのノードなど）が `/oak:index` の直接の子ノードである必要があります。 AEM Cloud Service と互換性を持たせるため、他の場所にあるインデックスは移動する必要があります。 検索インデックスについて詳しくは、[コンテンツ検索とインデックス作成のドキュメント](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/operations/indexing)を参照してください。

### カスタム検索インデックス定義ノードの compatVersion は 2 にする {#oakpal-custom-search-compatVersion}

* **キー**：IndexCompatVersion
* **タイプ**：`Code Smell`
* **深刻度**：軽度
* **最初の対象バージョン**：バージョン 2021.2.0

AEM Cloud Service では、カスタム検索インデックス定義（`oak:QueryIndexDefinition` タイプのノード）の `compatVersion` プロパティを `2` に設定する必要があります。 AEM Cloud Service は、その他の値をサポートしていません。 検索インデックスについて詳しくは、[コンテンツ検索とインデックス作成のドキュメント](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/operations/indexing)を参照してください。

### カスタム検索インデックス定義ノードの子孫ノードのタイプは、`nt:unstructured` にする {#oakpal-descendent-nodes}

* **キー**：IndexDescendantNodeType
* **タイプ**：`Code Smell`
* **深刻度**：軽度
* **最初の対象バージョン**：バージョン 2021.2.0

カスタム検索インデックス定義ノードに順序なしの子ノードがある場合、トラブルシューティングしにくい問題が発生するおそれがあります。 このようなノードを避けるために、`oak:QueryIndexDefinition` ノードのすべての子孫ノードは、タイプを `nt:unstructured` にすることをお勧めします。

### カスタム検索インデックス定義ノードには、子を持つ `indexRules` という名前の子ノードを含める {#oakpal-custom-search-index}

* **キー**：IndexRulesNode
* **タイプ**：`Code Smell`
* **深刻度**：軽度
* **最初の対象バージョン**：バージョン 2021.2.0

適切に定義されたカスタム検索インデックス定義ノードには、`indexRules` という名前の子ノードが含まれている必要があり、このノードに少なくとも 1 つの子が必要です。 詳しくは、[Oak ドキュメント](https://jackrabbit.apache.org/oak/docs/query/lucene.html)を参照してください。

### カスタム検索インデックス定義ノードは命名規則に従う {#oakpal-custom-search-definitions}

* **キー**：IndexName
* **タイプ**：`Code Smell`
* **深刻度**：軽度
* **最初の対象バージョン**：バージョン 2021.2.0

AEM Cloud Service では、カスタム検索インデックス定義（ノードのタイプが `oak:QueryIndexDefinition`）に、[コンテンツ検索とインデックス作成](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use)に記載されているパターンに従った名前を付ける必要があります。

### カスタム検索インデックス定義ノードでは lucene 型のインデックスを使用する {#oakpal-index-type-lucene}

* **キー**：IndexType
* **タイプ**：`Code Smell`
* **深刻度**：軽度
* **最初の対象バージョン**：バージョン 2021.2.0

AEM Cloud Service では、カスタム検索インデックス定義（`oak:QueryIndexDefinition` タイプのノード）に、値が `lucene` に設定された `type` プロパティが必要です。 AEM Cloud Service に移行する前に、従来のインデックスタイプを使用したインデックス作成を更新する必要があります。 詳しくは、[コンテンツの検索とインデックス作成のドキュメント](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use)を参照してください。

### カスタム検索インデックス定義ノードに `seed` という名前のプロパティを含めない {#oakpal-property-name-seed}

* **キー**：IndexSeedProperty
* **タイプ**：`Code Smell`
* **深刻度**：軽度
* **最初の対象バージョン**：バージョン 2021.2.0

AEM Cloud Service では、カスタム検索インデックス定義（ノードのタイプが `oak:QueryIndexDefinition`）に `seed` という名前のプロパティを含めることが禁止されています。 AEM Cloud Service に移行する前に、このプロパティを使用しているインデックス作成を更新する必要があります。 詳しくは、[コンテンツの検索とインデックス作成のドキュメント](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use)を参照してください。

### カスタム検索インデックス定義ノードに `reindex` という名前のプロパティを含めない {#oakpal-reindex-property}

* **キー**：IndexReindexProperty
* **タイプ**：`Code Smell`
* **深刻度**：軽度
* **最初の対象バージョン**：バージョン 2021.2.0

AEM Cloud Service では、カスタム検索インデックス定義（ノードのタイプが `oak:QueryIndexDefinition`）に `reindex` という名前のプロパティを含めることが禁止されています。 AEM Cloud Service に移行する前に、このプロパティを使用しているインデックス作成を更新する必要があります。 詳しくは、[コンテンツの検索とインデックス作成のドキュメント](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/operations/indexing#how-to-use)を参照してください。

### インデックス定義ノードを UI コンテンツパッケージにデプロイしない {#oakpal-ui-content-package}

* **キー**：IndexNotUnderUIContent
* **タイプ**：改善点
* **深刻度**：重大
* **最初の対象バージョン**：バージョン 2024.6.0

AEM Cloud Service では、UI コンテンツパッケージでカスタム検索インデックス定義（タイプ `oak:QueryIndexDefinition` のノード）をデプロイすることは禁止されています。

>[!WARNING]
>
>[Cloud Manager 2024年8月リリース](/help/release-notes/current.md)以降、パイプラインでエラーが発生する可能性があるので、できるだけ早く対処することをお勧めします。

### `damAssetLucene` タイプのカスタムフルテキストインデックス定義には、`damAssetLucene` という接頭辞を正しく付ける {#oakpal-dam-asset-lucene}

* **キー**：CustomFulltextIndexesOfTheDamAssetCheck
* **タイプ**：改善点
* **深刻度**：重大
* **最初の対象バージョン**：バージョン 2024.6.0

AEM Cloud Service では、`damAssetLucene` タイプのカスタムフルテキストインデックス定義に `damAssetLucene` 以外の接頭辞を付けることが禁止されています。

>[!WARNING]
>
>[Cloud Manager 2024年8月リリース](/help/release-notes/current.md)以降、パイプラインでエラーが発生する可能性があるので、できるだけ早く対処することをお勧めします。

### インデックス定義ノードに同じ名前のプロパティを含めない {#oakpal-index-property-name}

* **キー**：DuplicateNameProperty
* **タイプ**：改善点
* **深刻度**：重大
* **最初の対象バージョン**：バージョン 2024.6.0

AEM Cloud Service では、カスタム検索インデックス定義（つまり、タイプ `oak:QueryIndexDefinition` のノード）に同じ名前のプロパティを含めることが禁止されています。

>[!WARNING]
>
>[Cloud Manager 2024年8月リリース](/help/release-notes/current.md)以降、パイプラインでエラーが発生する可能性があるので、できるだけ早く対処することをお勧めします。

### 特定の標準インデックス定義のカスタマイズは禁止されています {#oakpal-customizing-ootb-index}

* **キー**：RestrictIndexCustomization
* **タイプ**：改善点
* **深刻度**：重大
* **最初の対象バージョン**：バージョン 2024.6.0

AEM Cloud Serviceでは、次の標準インデックスの不正な変更が禁止されています。

* `nodetypeLucene`
* `slingResourceResolver`
* `socialLucene`
* `appsLibsLucene`
* `authorizables`
* `pathReference`

>[!WARNING]
>
>[Cloud Manager 2024年8月リリース](/help/release-notes/current.md)以降、パイプラインでエラーが発生する可能性があるので、できるだけ早く対処することをお勧めします。

### アナライザーの tokenizer の設定は、「`tokenizer`」という名前で作成する {#oakpal-tokenizer}

* **キー**：AnalyzerTokenizerConfigCheck
* **タイプ**：改善点
* **深刻度**：軽度
* **最初の対象バージョン**：バージョン 2024.6.0

AEM Cloud Service では、アナライザーで正しくない名前の tokenizer を作成することが禁止されています。 Tokenizer は、常に `tokenizer` として定義する必要があります。

### インデックス作成定義の設定にスペースを含めることはできない {#oakpal-indexing-definitions-spaces}

* **キー**：PathSpacesCheck
* **タイプ**：改善点
* **深刻度**：軽度
* **最初の対象バージョン**：バージョン 2024.7.0

AEM Cloud Service では、プロパティにスペースを使用したインデックス作成定義の作成が禁止されています。

### インデックス作成定義の設定に haystack0 プロパティを含めることはできない {#oakpal-indexing-haystack0-property}

* **キー**：HayStackPropertyCheck
* **タイプ**：改善点
* **深刻度**：軽度
* **最初の対象バージョン**：バージョン 2024.12.0

AEM Cloud Service では、haystack プロパティを含むインデックス作成定義の作成が禁止されています。

### インデックス作成定義の設定に async-previous プロパティを含めることはできません {#oakpal-indexing-unsupported-async-properties}

* **Key**: IndexUnsupportedAsyncPropertiesCheck
* **タイプ**：改善点
* **深刻度**：軽度
* **最初の対象バージョン**：バージョン 2025.3.0

AEM Cloud Serviceでは、サポートされていない非同期プロパティを使用したインデックス定義の作成が禁止されています。

### インデックス定義の設定では、複数のインデックスで同じタグを使用しないでください {#oakpal-indexing-same-tag-multiple-indexes}

* **Key**: SameTagInMultipleIndexes
* **タイプ**：改善点
* **深刻度**：軽度
* **最初の対象バージョン**：バージョン 2025.3.0

AEM Cloud Serviceでは、同じタグを複数のインデックスに含むインデックス定義の作成を禁止しています。

### インデックス定義の設定に、禁止されたパスのモード置換を含めないでください {#oakpal-xml-mode-analysis}

* **Key**: FilterXmlModeAnalysis
* **タイプ**：改善点
* **深刻度**：重大
* **最初の対象バージョン**：バージョン 2025.4.0

ファイル Vaultで「置換」モードを使用することは、`/content`より下のパスには許可されていません。`/etc`および`/var.`より下のパスには使用しないでください。 「置換」モードは、既存のリポジトリコンテンツをパッケージから取得したコンテンツで上書きします。 この操作をトリガーするパッケージは、Cloud Managerを通じてデプロイされたパッケージには含めないでください。

## Dispatcher 最適化ツール {#dispatcher-optimization-tool-rules}

以下の節では、Cloud Manager で実行される Dispatcher 最適化ツール（DOT）チェックを示します。 各チェックの GitHub 定義と詳細については、リンクを参照してください。

* [Dispatcher設定の予期しないトークン](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unexpected-tokens)

* [Dispatcher設定の引用符が一致しません](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unmatched-quote)

* [Dispatcher設定に中括弧がありません](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-brace)

* [Dispatcher設定の追加ブレース](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-extra-brace)

* [Dispatcher設定に必須プロパティがありません](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-mandatory-property)

* [Dispatcher設定の非推奨プロパティ](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-deprecated-property)

* [Dispatcher設定が見つかりません](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-not-found)

* [Httpd設定に含まれるファイルが見つかりません](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---httpd-configuration-include-file-not-found)

* [Dispatcherの設定の一般](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-general)

* [Dispatcher パブリッシュファームキャッシュで`serveStaleOnError`が有効になっています](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-servestaleonerror-enabled)

* [Dispatcher パブリッシュファームフィルターには、AEM アーキタイプの6.x.x バージョンのデフォルトの拒否ルールを含める必要があります](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-contain-the-default-deny-rules-from-the-6xx-version-of-the-aem-archetype)

* [Dispatcher パブリッシュファームキャッシュ `statfileslevel` プロパティは>= 2です](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-statfileslevel-property-should-be--2)

* [Dispatcher パブリッシュ ファーム `gracePeriod` プロパティは>= 2です](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-graceperiod-property-should-be--2)

* [各Dispatcher ファームには一意の名前があります](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---each-dispatcher-farm-should-have-a-unique-name)

* [Dispatcher パブリッシュ ファームキャッシュには、`ignoreUrlParams` ルールが許可リストに加える方式で設定されています](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-its-ignoreurlparams-rules-configured-in-an-allow-list-manner)

* [Dispatcher パブリッシュファームフィルターは、許可されたSling セレクターを許可リスト方式で指定します](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-selectors-in-an-allow-list-manner)

* [Dispatcher パブリッシュファームフィルターは、許可されたSling サフィックス パターンを許可リスト方式で指定します](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-suffix-patterns-in-an-allow-list-manner)

* [ルート ディレクトリのパスを持つVirtualHost Directory セクションでは、「すべての付与を必要とする」ディレクティブを使用しないでください](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-require-all-granted-directive-should-not-be-used-in-a-virtualhost-directory-section-with-a-root-directory-path)
