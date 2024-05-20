---
title: Cloud Manager リポジトリー
description: Cloud Manager プログラムのリポジトリにアクセス、作成、編集する方法について説明します。
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
source-git-commit: 1d4ab9704fdb743b097e24be335fbf069d1e78bd
workflow-type: ht
source-wordcount: '762'
ht-degree: 100%

---


# Cloud Manager リポジトリ {#cloud-manager-repos}

リポジトリは、Git を使用してコードを管理する場所です。 Cloud Manager プログラムのリポジトリを作成する方法について説明します。

## リポジトリへのアクセス {#accessing-repos}

Cloud Manager からセルフサービスで Git リポジトリにアクセスして管理できます。

リポジトリにアクセスするには、Cloud Manager で利用可能な「**リポジトリ情報にアクセス**」ボタンを使用します。これは、パイプラインカードで最も目立つようになっています。

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) で Cloud Manager にログインし、適切な組織とプログラムを選択します。

1. **プログラムの概要**&#x200B;ページから&#x200B;**パイプライン**&#x200B;カードに移動すると、「**リポジトリ情報にアクセス**」オプションが表示され、[このパイプライン](/help/using/production-pipelines.md)で設定された Git リポジトリにアクセスして管理できます。

   ![「リポジトリ情報にアクセス」ボタン](/help/assets/access-repo1.png)

1. 「**リポジトリ情報にアクセス**」ボタンをタップまたはクリックして、表示されるダイアログを開きます。

   * Git リポジトリへの URL
   * ユーザー名
   * パスワード
   * リポジトリをローカルに複製するために実行する Git コマンド

   ![リポジトリ情報ダイアログ](/help/assets/access-repo-create.png)

指定した情報を使用してリポジトリのクローンをローカルに作成し、ローカル開発を開始できるようにします。

>[!NOTE]
>
>「**リポジトリ情報にアクセス**」オプションは、**デベロッパー**&#x200B;または&#x200B;**デプロイメントマネージャー**&#x200B;の役割を持つユーザーに表示されます。

## リポジトリの追加 {#add-repos}

Cloud Manager でリポジトリを追加するには、次の手順に従います。

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) で Cloud Manager にログインし、適切な組織とプログラムを選択します。

1. **プログラムの概要**&#x200B;ページで、「**リポジトリー**」タブをクリックし、**リポジトリー**&#x200B;ページに移動します。

1. 「**リポジトリーを追加**」をクリックして、ウィザードを起動します。

   >[!NOTE]
   >
   >リポジトリを追加するには、**デプロイメントマネージャー**&#x200B;または&#x200B;**ビジネスオーナー**&#x200B;の役割が必要です。

   ![リポジトリを追加](/help/assets/create-repo2.png)

1. 必要に応じて名前と説明を入力し、「**保存**」をクリックします。

   ![リポジトリの詳細](/help/assets/repo-1.png)

1. 「**保存**」を選択します。

新しく作成されたリポジトリが表示されます。

Cloud Manager で作成されたリポジトリは、[パイプラインを作成](/help/overview/ci-cd-pipelines.md)するときに選択できます。

## リポジトリの表示と編集 {#edit-repos}

Cloud Manager でリポジトリを編集および表示するには、次の手順に従います。

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) で Cloud Manager にログインし、適切な組織とプログラムを選択します。

1. **プログラムの概要**&#x200B;ページで、「**リポジトリ**」タブをクリックし、**リポジトリ**&#x200B;ページに移動します。ここでは、既存のリポジトリの詳細を表示できます。

1. リポジトリを選択し、表の右端にある「省略記号」ボタンをクリックして、**リポジトリ URL のコピー**&#x200B;またはリポジトリの&#x200B;**表示と更新**&#x200B;を実行します。

![リポジトリの編集](/help/assets/create-repo3.png)

## リポジトリの削除 {#delete-repos}

リポジトリを削除するには、[リポジトリの表示と編集](#edit-repos)と同じ手順に従いますが、**リポジトリ**&#x200B;ページで、削除するリポジトリの「省略記号」ボタンから「**削除**」を選択します。

Cloud Manager でリポジトリを削除すると、そのリポジトリは削除済みとしてマークされ、ユーザーはアクセスできなくなりますが、復元のためにシステム内で維持されます。

同じ名前のリポジトリを削除した後に新しいリポジトリを作成しようとすると、「リポジトリの作成中にエラーが発生しました。CSE またはアドビサポートにお問い合わせください」というエラーメッセージが表示されます。

このエラーメッセージが表示された場合は、アドビサポートに連絡し、削除したリポジトリの名前を変更するか、新しいリポジトリに対する別の名前を選択してください。

## Git サブモジュールのサポート {#git-submodule-support}

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

### 制限事項 {#limitations}

Git サブモジュールを使用する場合は、次の点に注意してください。

* Git の URL は、上記の構文に正確に一致している必要があります。
* セキュリティ上の理由から、これらの URL に資格情報を埋め込まないでください。
* ブランチのルートにあるサブモジュールのみがサポートされます。
* Git サブモジュール参照は、特定の Git コミットに保存されます。
   * その結果、サブモジュールリポジトリに対して変更を加える場合、`git submodule update --remote` などを使用して、参照されるコミットを更新する必要があります。
* 特に必要がない限り、「シャロー」サブモジュールを使用することを強くお勧めします。
   * それには、サブモジュールごとに `git config -f .gitmodules submodule.<submodule path>.shallow true` を実行します。
