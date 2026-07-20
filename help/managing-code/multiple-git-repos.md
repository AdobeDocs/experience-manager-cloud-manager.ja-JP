---
title: 複数 Git リポジトリの操作
description: Cloud Manager の Git リポジトリを直接操作するのではなく、独自の Git リポジトリまたは複数の Git リポジトリを操作する方法について説明します。
exl-id: 53bf78bb-489a-4a83-8459-c361f532d54a
TQID: https://experienceleague.adobe.com/xKzqOfbi12A0POy-C7Gm7-n649DEBX9JP3LfXA5UC3Y
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: a07522b4a3c0619bb57b414de58633c65d9c7b5c
workflow-type: tm+mt
source-wordcount: 727
ht-degree: 60%

---

# 複数ソース Git リポジトリの操作 {#working-with-multiple-source-git-repos}

Cloud Manager の Git リポジトリを直接操作するのではなく、独自の Git リポジトリまたは複数の Git リポジトリを操作する方法について説明します。

## 顧客の管理による Git リポジトリの同期 {#syncing-customer-managed-git-repositories}

Cloud Manager の Git リポジトリを最新の状態に保つには、独自のリポジトリまたは複数のレポジトリを使用している場合、自動同期プロセスを設定します。

Git リポジトリがホストされている場所に応じて、GitHub アクションまたはJenkinsなどの継続的な統合ソリューションを使用して、自動化を設定します。 自動化を導入すれば、独自のリポジトリへのプッシュ通知はすべて、Cloud ManagerのGit リポジトリに自動的に転送されます。

単一の顧客所有のGit リポジトリに対するこのような自動化は簡単ですが、複数のリポジトリ用に設定するには、より関与した初期設定が必要です。 複数の Git リポジトリのコンテンツは、1 つの Cloud Manager の Git リポジトリ内の異なるディレクトリにマッピングする必要があります。 Cloud ManagerのGit リポジトリは、ルート Maven `pom.xml`でプロビジョニングする必要があり、「モジュール」セクションに様々なサブプロジェクトが一覧表示されます

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

このようなルート `pom.xml` が、Cloud Manager の Git リポジトリのブランチにプッシュされます。 次に、変更内容を Cloud Manager の Git リポジトリに自動的に転送するように、2 つのプロジェクトを設定する必要があります。

例えば、プロジェクト A のブランチへのプッシュによって GitHub アクションをトリガーできます。 このアクションでは、プロジェクト A とCloud Manager Git リポジトリがチェックアウトされます。 これにより、すべてのコンテンツがプロジェクト A から Cloud Manager の Git リポジトリの `project-a` ディレクトリにコピーされます。 その後、変更内容がコミットおよびプッシュされます。

例えば、プロジェクト A の `main` ブランチに対する変更は、Cloud Manager の Git リポジトリの `main` ブランチに自動的にプッシュされます。 もちろん、プロジェクト Aの`dev`という名前のブランチへのプッシュがCloud ManagerのGit リポジトリの`development`という名前のブランチにプッシュされるなど、ブランチ間のマッピングが可能です。 プロジェクト B にも同様の手順が必要です。

分岐戦略とワークフローに応じて、異なるブランチに対して同期を設定できます。 使用中のGit リポジトリーがGitHub アクションと類似した概念を提供しない場合は、Jenkins （または類似の）を使用した統合も可能です。 この場合、Webhookはタスクを実行するJenkins ジョブをトリガーします。

新しい（3 番目の）ソースまたはリポジトリを追加するには、次の手順に従います。

1. 新しいリポジトリに、そのリポジトリからの変更を Cloud Manager の Git リポジトリにプッシュする新しい GitHub アクション追加します。
1. プロジェクトコードがCloud ManagerのGit リポジトリにあることを確認するには、少なくとも1回はそのアクションを実行します。
1. Cloud Manager の Git リポジトリのルート Maven `pom.xml` に新しいディレクトリへの参照を追加します。

## GitHub アクションの例 {#sample-github-action}

`main` ブランチへのプッシュにより、この GitHub アクションの例がトリガーされ、Cloud Manager の Git リポジトリのサブディレクトリにプッシュされます。 Cloud ManagerのGit リポジトリに接続してプッシュするには、GitHub アクションに`MAIN_USER`と`MAIN_PASSWORD`の2つのシークレットを指定する必要があります。

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

上に示すように、GitHub アクションの使用は柔軟です。 Git リポジトリのブランチ間のマッピングは、個別のGit プロジェクトをメインプロジェクトのディレクトリレイアウトにマッピングするのと同様に、実行できます。

>[!NOTE]
>
>上記のスクリプトは、削除が含まれていると想定されるリポジトリの更新に `git add` を使用します。 Gitのデフォルト設定に応じて、この要件を`git add --all`に置き換えます。

## Jenkins ジョブの例 {#sample-jenkins-job}

このスクリプトは、Jenkins ジョブまたは同種のジョブで使用できる例です。 Git リポジトリの変更によってトリガーされます。 Jenkins ジョブは、そのプロジェクトまたはブランチの最新のステートをチェックアウトし、このスクリプトをトリガーします。

このスクリプトは、Cloud ManagerのGit リポジトリをチェックアウトし、プロジェクトコードをサブディレクトリにコミットします。

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

Jenkins ジョブは柔軟に使用できます。 Git リポジトリのブランチ間のマッピングは、個別のGit プロジェクトをメインプロジェクトのディレクトリレイアウトにマッピングするのと同様に、実行できます。

>[!NOTE]
>
>上記のスクリプトは、削除が含まれていると想定されるリポジトリの更新に `git add` を使用します。 Gitのデフォルト設定に応じて、`git add`を`git add --all`に置き換えます。
