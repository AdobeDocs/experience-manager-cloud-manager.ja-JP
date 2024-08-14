---
title: 複数の Git リポジトリーの操作
description: Cloud Managerの Git リポジトリを直接操作するのではなく、独自の Git リポジトリ（1 つまたは複数）を操作する方法を説明します。
exl-id: 53bf78bb-489a-4a83-8459-c361f532d54a
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 9%

---

# 複数のソース Git リポジトリの操作 {#working-with-multiple-source-git-repos}

Cloud Managerの Git リポジトリを直接操作するのではなく、独自の Git リポジトリ（1 つまたは複数）を操作する方法を説明します。

## 顧客が管理する Git リポジトリの同期 {#syncing-customer-managed-git-repositories}

Cloud Manager Git リポジトリを最新の状態に保つには、独自のリポジトリ（1 つまたは複数）を使用している場合は、自動同期プロセスを設定します。

Git リポジトリがホストされている場所に応じて、GitHub アクションまたは継続的統合ソリューション（Jenkins など）を使用して、自動処理を設定できます。 自動処理を導入すると、リポジトリにプッシュするたびにCloud Managerの Git リポジトリに自動転送できます。

顧客が所有する単一 Git リポジトリの場合のこうした自動処理は簡単ですが、複数のリポジトリの場合に自動処理を設定するには、より複雑な初期設定が必要になります。 複数の Git リポジトリのコンテンツは、1 つのCloud Manager Git リポジトリ内の異なるディレクトリにマッピングする必要があります。 Cloud Managerの Git リポジトリーは、ルートの Maven `pom.xml` を使用してプロビジョニングする必要があります。モジュールセクションに様々なサブプロジェクトが一覧表示されます。

顧客が所有する 2 つの Git リポジトリに対する `pom.xml` のサンプルは次の通りです。 1 つ目のプロジェクトは `project-a`、2 つ目のプロジェクトは `project-b` というディレクトリに配置されます。

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

このようなルート `pom.xml` は、Cloud Managerの Git リポジトリのブランチにプッシュされます。 次に、変更内容をCloud Manager Git リポジトリに自動的に転送するように、2 つのプロジェクトを設定する必要があります。

例えば、プロジェクト A のブランチへのプッシュは GitHub アクションをトリガーにすることができます。 このアクションは、プロジェクト A とCloud Manager Git リポジトリをチェックアウトします。 プロジェクト A のすべてのコンテンツが、Cloud Manager Git リポジトリの `project-a` ディレクトリにコピーされます。 その後、変更をコミットしてプッシュします。

例えば、プロジェクト A の `main` ブランチに対する変更は、Cloud Managerの Git リポジトリの `main` ブランチに自動的にプッシュされます。 もちろん、プロジェクト A の `dev` ブランチへのプッシュが、Cloud Managerの Git リポジトリの `development` ブランチにプッシュされるなど、ブランチ間でマッピングがおこなわれる場合があります。 プロジェクト B にも同様の手順が必要です。

ブランチの方法とワークフローに応じて、異なるブランチに対して同期を設定できます。使用する Git リポジトリが GitHub アクションと類似した概念を提供しない場合は、Jenkins （またはそれに類似のもの）を介した統合も可能です。 この場合、Webhook は、その作業を行う Jenkins ジョブをトリガーにします。

新しい（3 番目の）ソースまたはリポジトリを追加するには、次の手順を実行します。

1. 新しいリポジトリに、そのリポジトリからの変更をCloud Managerの Git リポジトリにプッシュする新しい GitHub アクションを追加します。
1. このアクションを少なくとも 1 回実行して、プロジェクトコードがCloud Managerの Git リポジトリにあることを確認します。
1. 新しいディレクトリへの参照をCloud Manager Git リポジトリのルート Maven `pom.xml` に追加します。

## GitHub アクションのサンプル {#sample-github-action}

`main` ブランチへのプッシュは、このサンプル GitHub アクションをトリガーとし、Cloud Managerの Git リポジトリのサブディレクトリにプッシュします。 Cloud Managerの Git リポジトリに接続してプッシュできるように、この GitHub アクションに `MAIN_USER` と `MAIN_PASSWORD` の 2 つのシークレットを提供する必要があります。

```java
name: SYNC
env:
  # Username/email used to commit to Cloud Manager's Git repository
  USER_NAME: <NAME>
  USER_EMAIL: <EMAIL>
  # Directory within the Cloud Manager Git repository
  PROJECT_DIR: project-a
  # Cloud Manager's Git repository
  MAIN_REPOSITORY: https://$MAIN_USER:$MAIN_PASSWORD@git.cloudmanager.adobe.com/<PATH>
  # The branch in Cloud Manager's Git repository to push to
  MAIN_BRANCH : <BRANCH_NAME>
 
# Only run on a push to this branch
on:
  push:
     branches: [ main ]
 
jobs:
  build:
    runs-on: ubuntu-latest
 
    steps:
      # Checkout this project into a sub folder
      - uses: actions/checkout@v2
        with:
          path: sub
      # Cleanup sub project
      - name: Clean project
        run: |
          git -C sub log --format="%an : %s" -n 1 > commit.txt
          rm -rf sub/.git
          rm -rf sub/.github
      # Set global git configuration
      - name: Set git config
        run: |
          git config --global credential.helper cache
          git config --global user.email ${USER_EMAIL}
          git config --global user.name ${USER_NAME}
      # Checkout the main project
      - name: Checkout main project
        run:
          git clone -b ${MAIN_BRANCH} https://${{ secrets.PAT }}@github.com/${MAIN_REPOSITORY}.git main 
      # Move sub project
      - name: Move project to main project
        run: |
          rm -rf main/${PROJECT_DIR} 
          mv sub main/${PROJECT_DIR}
      - name: Commit Changes
        run: |
          git -C main add -f ${PROJECT_DIR}
          git -C main commit -F ../commit.txt
          git -C main push
```

上に示すように、GitHub アクションの使用は柔軟です。 Git リポジトリのブランチ間のマッピングを実行したり、個別の Git プロジェクトをメインプロジェクトのディレクトリレイアウトにマッピングしたりできます。

>[!NOTE]
>
>上記のスクリプトは、削除が含まれていると想定されるリポジトリの更新に `git add` を使用します。 Git のデフォルト設定によっては、この要件を `git add --all` に置き換える必要がある場合があります。

## Jenkins ジョブの例 {#sample-jenkins-job}

このスクリプトは、Jenkins ジョブなどで使用できるサンプルです。 Git リポジトリ内の変更がトリガーになります。 Jenkins ジョブは、そのプロジェクトまたはブランチの最新のステートをチェックアウトし、このスクリプトを実行します。

このスクリプトはCloud Managerの Git リポジトリをチェックアウトし、プロジェクトコードをサブディレクトリにコミットします。

Cloud Manager の Git リポジトリーに接続してプッシュできるようにするには、Jenkins ジョブに `MAIN_USER` と ｓ`MAIN_PASSWORD` の 2 つのシークレットが必要です。

```java
# Username/email used to commit to Cloud Manager's Git repository
export USER_NAME=<NAME>
export USER_EMAIL=<EMAIL>
# Directory within the Cloud Manager Git repository
export PROJECT_DIR=project-a
# Cloud Manager's Git repository
export MAIN_REPOSITORY=https://$MAIN_USER:$MAIN_PASSWORD@git.cloudmanager.adobe.com/<PATH>
# The branch in Cloud Manager's Git repository to push to
export MAIN_BRANCH=<BRANCH_NAME>
 
# clean up and init
rm -rf target
mkdir target
 
# mv project to sub folder
mkdir target/sub
for f in .* *
do
    if [ "$f" != "." -a "$f" != ".." -a "$f" != "target" ]
    then
        mv "$f" target/sub
    fi
done
cd target
 
# capture log and remove git info
cd sub
git log --format="%an : %s" -n 1 > ../commit.txt
rm -rf .git
rm -rf .github
cd ..
 
# checkout main repository
git clone -b $MAIN_BRANCH $MAIN_REPOSITORY main
cd main
 
# configure main repository
git config credential.helper cache
git config user.email $USER_EMAIL
git config user.name $USER_NAME
 
# update project in main
rm -rf $PROJECT_DIR
mv ../sub $PROJECT_DIR
 
# commit changes to main
git add -f $PROJECT_DIR
git commit -F ../commit.txt
git push
```

上に示すように、Jenkins ジョブの使用は非常に柔軟です。Git リポジトリのブランチ間のマッピングを実行したり、個別の Git プロジェクトをメインプロジェクトのディレクトリレイアウトにマッピングしたりできます。

>[!NOTE]
>
>上記のスクリプトは、削除が含まれていると想定されるリポジトリの更新に `git add` を使用します。 Git のデフォルト設定に応じて、`git add` を `git add --all` に置き換える必要がある場合があります。
