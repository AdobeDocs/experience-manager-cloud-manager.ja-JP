---
title: Git サブモジュールのサポート
description: Git サブモジュールを使用して、ビルド時に Git リポジトリ間で複数のブランチのコンテンツを結合する方法について説明します。
source-git-commit: aa30c0024e422c96f0dfbaa2804e75143faf14dc
workflow-type: ht
source-wordcount: '417'
ht-degree: 100%

---


# Adobe リポジトリに対する Git サブモジュールのサポート {#git-submodule-support}

Git サブモジュールを使用すると、ビルド時に Git リポジトリ間で複数のブランチのコンテンツを結合できます。

Cloud Manager のビルドプロセスを実行すると、パイプライン用に設定されたリポジトリのクローンを作成し、設定されたブランチをチェックアウトした後に、ブランチのルートディレクトリに `.gitmodules` ファイルが含まれている場合は、コマンドが実行されます。

```
$ git submodule update --init
```

これにより、各サブモジュールが適切なディレクトリにチェックアウトされます。この手法は、Git サブモジュールの使用に慣れており、外部マージプロセスの管理を希望しない組織にとって、[複数のソース Git リポジトリーでの操作](/help/managing-code/multiple-git-repos.md)の代わりに使用できる可能性があります。

例えば、3 つのリポジトリがあり、それぞれに `main` という名前のブランチが 1 つあるとします。「プライマリ」リポジトリ（パイプラインで設定されたもの）の `main` ブランチには、他の 2 つのリポジトリに含まれるプロジェクトを宣言する `pom.xml` ファイルが含まれます。

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
   
    <groupId>customer.group.id</groupId>
    <artifactId>customer-reactor</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <packaging>pom</packaging>
   
    <modules>
        <module>project-a</module>
        <module>project-b</module>
    </modules>
   
</project>
```

次に、他の 2 つのリポジトリー用のサブモジュールを追加します。

```shell
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectA/ project-a
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectB/ project-b
```

その結果、`.gitmodules` ファイルは次のようになります。

```text
[submodule "project-a"]
    path = project-a
    url = https://git.cloudmanager.adobe.com/ProgramName/projectA/
    branch = main
[submodule "project-b"]
    path = project-b
    url = https://git.cloudmanager.adobe.com/ProgramName/projectB/
    branch = main
```

Git サブモジュールの詳細については、[Git リファレンスマニュアル](https://git-scm.com/book/ja/v2/Git-Tools-Submodules)を参照してください。

## 制限事項 {#limitations}

Git サブモジュールを使用する場合は、次の点に注意してください。

* Git の URL は、上記の構文に正確に一致している必要があります。
* セキュリティ上の理由から、これらの URL に資格情報を埋め込まないでください。
* ブランチのルートにあるサブモジュールのみがサポートされます。
* Git サブモジュール参照は、特定の Git コミットに保存されます。
   * その結果、サブモジュールリポジトリに対して変更を加える場合、`git submodule update --remote` などを使用して、参照されるコミットを更新する必要があります。
* 特に必要がない限り、「シャロー」サブモジュールを使用することを強くお勧めします。
   * それには、サブモジュールごとに `git config -f .gitmodules submodule.<submodule path>.shallow true` を実行します。


## プライベートリポジトリに対する Git サブモジュールのサポート {#private-repositories}

[プライベートリポジトリ](private-repositories.md)を使用する場合の Git サブモジュールのサポートは、Adobe リポジトリを使用する場合とほとんど同じです。

ただし、`pom.xml` ファイルを設定して `git submodule` コマンドを実行した後、Cloud Manager でサブモジュールの設定を検出するために、集積リポジトリのルートディレクトリに `.gitmodules` ファイルを追加する必要があります。

![.gitmodules ファイル](assets/gitmodules.png)

![集積](assets/aggregator.png)

### 制限事項とレコメンデーション {#limitations-recommendations-private-repos}

プライベートリポジトリで Git サブモジュールを使用する場合は、次の制限事項に注意してください。

* サブモジュールの Git URL は、HTTPS 形式または SSH 形式のいずれかになりますが、github.com リポジトリにリンクする必要があります。
   * Adobe リポジトリサブモジュールを GitHub 集積リポジトリに追加したり、その逆を行ったりすることはできません。
* GitHub サブモジュールでは、Adobe GitHub アプリにアクセスできる必要があります。
* また、[アドビが管理するリポジトリで Git サブモジュールを使用する場合の制限事項](#limitations-recommendations)も適用されます。