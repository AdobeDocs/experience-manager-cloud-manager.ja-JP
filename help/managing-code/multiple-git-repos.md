---
title: 複数の Git リポジトリーの操作
description: Cloud Manager の Git リポジトリを直接操作する代わりに、独自の Git リポジトリ（1 つまたは複数）を操作する方法を学びます。
exl-id: 53bf78bb-489a-4a83-8459-c361f532d54a
source-git-commit: da9dff997a277c207e2c48207217cb30325f3c0d
workflow-type: tm+mt
source-wordcount: '756'
ht-degree: 14%

---

# 複数ソース Git リポジトリーの操作 {#working-with-multiple-source-git-repos}

Cloud Manager の Git リポジトリを直接操作する代わりに、独自の Git リポジトリ（1 つまたは複数）を操作する方法を学びます。

## 顧客が管理する Git リポジトリーの同期 {#syncing-customer-managed-git-repositories}

独自のリポジトリまたはリポジトリを操作する場合は、Cloud Manager の Git リポジトリを常に最新の状態に保つために、自動同期プロセスを設定する必要があります。

Git リポジトリがホストされている場所に応じて、GitHub アクションまたは Jenkins などの継続的統合ソリューションを使用して、自動処理を設定できます。 自動処理を実行すると、独自のリポジトリに対するすべてのプッシュを、Cloud Manager の Git リポジトリに自動的に転送できます。

顧客が所有する Git リポジトリーが 1 つだけの場合、このような自動処理は簡単ですが、複数のリポジトリーに対して自動処理を設定する場合は、より複雑な初期設定が必要になります。 複数の Git リポジトリーの内容を、Cloud Manager の 1 つの Git リポジトリー内の様々なディレクトリにマッピングする必要があります。 Cloud Manager の Git リポジトリーには、ルート Maven をプロビジョニングする必要があります `pom.xml`、モジュールセクションに様々なサブプロジェクトをリスト表示

以下にサンプルを示します `pom.xml` ユーザーが所有する 2 つの git リポジトリーの場合。 最初のプロジェクトは、 `project-a`を指定した場合、2 つ目のプロジェクトは、 `project-b`.

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

こんな根 `pom.xml` が Cloud Manager の Git リポジトリーのブランチにプッシュされます。 次に、変更を Cloud Manager の Git リポジトリに自動的に転送するように、2 つのプロジェクトを設定する必要があります。

例えば、プロジェクト A のブランチへのプッシュで GitHub アクションをトリガーできます。このアクションにより、プロジェクト A と Cloud Manager Git リポジトリがチェックアウトされ、プロジェクト A からディレクトリにすべてのコンテンツがコピーされます `project-a` Cloud Manager の Git リポジトリで変更をコミットし、コミットプッシュします。

例えば、 `main` プロジェクト A のブランチは、 `main` Cloud Manager の Git リポジトリのブランチ。 もちろん、という名前のブランチへのプッシュなど、ブランチ間のマッピングが存在する場合があります。 `dev` プロジェクト A 内で、 `development` Cloud Manager の git リポジトリ内。 プロジェクト B にも同様の手順が必要です。

ブランチの方法とワークフローに応じて、異なるブランチに対して同期を設定できます。使用している Git リポジトリに GitHub アクションと似た概念が用意されていない場合は、Jenkins（または類似の）を介した統合も可能です。 この場合、webhook が Jenkins ジョブをトリガーし、このジョブが動作します。

次の手順に従って、新しい（3 番目の）ソースまたはリポジトリーを追加します。

1. 新しいリポジトリの変更を Cloud Manager の Git リポジトリにプッシュする新しい GitHub アクションを新しいリポジトリに追加します。
1. このアクションを少なくとも 1 回実行して、プロジェクトコードが Cloud Manager の Git リポジトリーに確実に格納されるようにします。
1. 新しいディレクトリへの参照をルート Maven に追加します。 `pom.xml` Cloud Manager の git リポジトリ内。

## GitHub アクションの例 {#sample-github-action}

以下は、 `main` ブランチしてから、Cloud Manager の git リポジトリーのサブディレクトリにプッシュします。 GitHub アクションには、次の 2 つのシークレットを提供する必要があります。 `MAIN_USER` および `MAIN_PASSWORD`Cloud Manager の Git リポジトリに接続してプッシュできるようになります。

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

上に示すように、GitHub アクションの使用は非常に柔軟です。個別の Git プロジェクトをメインプロジェクトのディレクトリレイアウトにマッピングするだけでなく、Git リポジトリーのブランチ間のマッピングも実行できます。

>[!NOTE]
>
>上記のスクリプトでは、 `git add` ：削除が含まれていると想定されるリポジトリを更新する場合。 Git のデフォルト設定に応じて、次の項目に置き換える必要がある場合があります。 `git add --all`.

## Jenkins ジョブの例 {#sample-jenkins-job}

これは、Jenkins ジョブなどで使用できるスクリプトの例です。Git リポジトリー内の変更によってトリガーされます。 Jenkins ジョブは、そのプロジェクトまたはブランチの最新のステートをチェックアウトし、このスクリプトを実行します。

次に、このスクリプトは Cloud Manager の Git リポジトリーをチェックアウトし、プロジェクトコードをサブディレクトリにコミットします。

Jenkins ジョブには、2 つのシークレットを提供する必要があります。 `MAIN_USER` および `MAIN_PASSWORD`Cloud Manager の Git リポジトリに接続してプッシュできるようになります。

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

上に示すように、Jenkins ジョブの使用は非常に柔軟です。個別の Git プロジェクトをメインプロジェクトのディレクトリレイアウトにマッピングするだけでなく、Git リポジトリーのブランチ間のマッピングも実行できます。

>[!NOTE]
>
>上記のスクリプトでは、 `git add` 削除が含まれていると仮定してリポジトリを更新するには、git のデフォルト設定に応じて、次に置き換える必要があります。 `git add --all`.
