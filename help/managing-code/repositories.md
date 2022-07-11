---
title: Cloud Manager リポジトリー
description: Cloud Manager プログラムのリポジトリにアクセス、作成、編集する方法について説明します。
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 49%

---


# Cloud Manager リポジトリー {#cloud-manager-repos}

リポジトリーは、Git を使用してコードを管理する場所です。 Cloud Manager プログラム用のリポジトリを作成する方法を説明します。

## リポジトリへのアクセス {#accessing-repos}

Cloud Manager のセルフサービスで、Git リポジトリーにアクセスして管理できます。

リポジトリにアクセスするには、 **リポジトリ情報にアクセス** ボタンが Cloud Manager で使用でき、パイプラインカードで最も目立つ場所にあります。

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) で Cloud Manager にログインし、適切な組織とプログラムを選択します。

1. に移動します。 **パイプライン** カード **プログラムの概要** ページが開き、 **リポジトリ情報にアクセス** git リポジトリにアクセスして管理するオプション [このパイプラインで設定されます。](/help/using/production-pipelines.md)

   ![リポジトリ情報ボタンにアクセス](/help/assets/access-repo1.png)

1. 次に **非実稼動** 「パイプライン」タブ、 **リポジトリ情報にアクセス** オプションは、 [パイプライン用に設定されます。](/help/using/non-production-pipelines.md)

   ![実稼動以外のパイプライン](/help/assets/access-repo-nonprod.png)

1. をクリックします。 **リポジトリ情報にアクセス** ボタンをクリックして、次のダイアログを開きます。

   * Git リポジトリの URL
   * ユーザー名
   * パスワード
   * 実行する Git コマンドでリポジトリをローカルに複製

   ![リポジトリ情報ダイアログ](/help/assets/access-repo-create.png)

指定した情報を使用して、リポジトリのクローンをローカルで作成し、ローカル開発を開始できます。

>[!NOTE]
>
>「**リポジトリー情報にアクセス**」オプションは、デベロッパーまたはデプロイメントマネージャーの役割を持つユーザーに表示されます。********

## リポジトリの追加 {#add-repos}

Cloud Manager でリポジトリーを追加するには、次の手順に従います。

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) で Cloud Manager にログインし、適切な組織とプログラムを選択します。

1. **プログラムの概要**&#x200B;ページで、「**リポジトリー**」タブをクリックし、**リポジトリー**&#x200B;ページに移動します。

1. 「**リポジトリーを追加**」をクリックして、ウィザードを起動します。

   >[!NOTE]
   >
   >次を持っている必要があります： **デプロイメントマネージャー** または **ビジネスオーナー** ロールを使用してリポジトリを追加します。

   ![リポジトリを追加](/help/assets/create-repo2.png)

1. 必要に応じて名前と説明を入力し、「**保存**」をクリックします。

   ![リポジトリの詳細](/help/assets/repo-1.png)

1. 「**保存**」を選択します。

新しく作成されたリポジトリが表示されます。

![新しいリポジトリが作成されました](/help/assets/create-repo3.png)

Cloud Manager で作成されたリポジトリは、 [パイプラインを作成します。](/help/overview/ci-cd-pipelines.md)

## リポジトリの表示と編集 {#edit-repos}

Cloud Manager でリポジトリーを編集および表示するには、次の手順に従います。

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) で Cloud Manager にログインし、適切な組織とプログラムを選択します。

1. **プログラムの概要**&#x200B;ページで、「**リポジトリー**」タブをクリックし、**リポジトリー**&#x200B;ページに移動します。ここでは、既存のリポジトリの詳細を表示できます。

1. リポジトリを選択し、表の右端にある省略記号ボタンをクリックして、 **リポジトリ URL をコピー**, **表示と更新** または **削除** リポジトリー。

![リポジトリを編集](/help/assets/create-repo3.png)

## Git サブモジュールのサポート {#git-submodule-support}

Git サブモジュールを使用すると、ビルド時に Git リポジトリー間で複数のブランチのコンテンツを結合できます。

Cloud Manager のビルドプロセスを実行すると、パイプライン用に設定されたリポジトリーのクローンを作成し、設定されたブランチをチェックアウトした後に、ブランチのルートディレクトリに `.gitmodules` ファイルが含まれている場合は、コマンドが実行されます。

```
$ git submodule update --init
```

これにより、各サブモジュールが適切なディレクトリにチェックアウトされます。この手法は、Git サブモジュールの使用に慣れており、外部マージプロセスの管理を希望しない組織にとって、[複数のソース Git リポジトリーでの操作](/help/managing-code/multiple-git-repos.md)の代わりに使用できる可能性があります。

例えば、3 つのリポジトリがあり、それぞれにという名前の 1 つのブランチがあるとします。 `main`. 「プライマリ」リポジトリ（パイプラインで設定されたもの）では、 `main` ブランチに `pom.xml` 他の 2 つのリポジトリーに含まれるプロジェクトを宣言するファイル：

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

### 制限事項 {#limitations}

Git サブモジュールを使用する場合は、次の点に注意してください。

* Git の URL は、上記の構文で正確に指定する必要があります。
* セキュリティ上の理由から、これらの URL に資格情報を埋め込まないでください。
* ブランチのルートにあるサブモジュールのみがサポートされます。
* Git サブモジュール参照は、特定の Git コミットに保存されます。
   * その結果、サブモジュールリポジトリーに対して変更を加える場合、`git submodule update --remote` などを使用して、参照されるコミットを更新する必要があります。
* 特に必要がない限り、「シャロー」サブモジュールを使用することを強くお勧めします。
   * それには、サブモジュールごとに `git config -f .gitmodules submodule.<submodule path>.shallow true` を実行します。
