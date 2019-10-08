---
title: Adobe Cloud ManagerとのGitの統合
description: 顧客管理（オンプレミス）のgitリポジトリとAdobe Cloud Managerの設定と統合に関する手順を説明するビデオシリーズです。
seo-title: Adobe Cloud ManagerとのGitの統合
seo-description: 顧客管理（オンプレミス）のgitリポジトリとAdobe Cloud Managerの設定と統合に関する手順を説明するビデオシリーズです。
translation-type: tm+mt
source-git-commit: 519f43ff16e0474951f97798a8e070141e5c124b

---


# Adobe Cloud ManagerとのGitの統合

Adobe Cloud Managerには、Cloud ManagerのCI/CDパイプラインを使用したコードのデプロイに使用される単一のgitリポジトリがプロビジョニングされます。 お客様は、Cloud Managerのgitリポジトリをすぐに使用できます。 また、オンプレミスまたは顧客管理のGitリポジトリをCloud Manager **と統合するオ** プションもあります。

## Git統合の概要

>[!VIDEO](https://video.tv.adobe.com/v/28710/?captions=jpn)

このビデオシリーズでは、顧客が管理するGitリポジトリとCloud Managerの統合に関する使用例をいくつか紹介します。

* [初期同期](#initial-sync)
* [基本分岐戦略](#branching-strategy)
* [機能分岐の開発](#feature-development)
* [実稼動のデプロイメント](#production-deployment)
* [リリースタグの同期](#sync-tags)

概要については、 [Cloud Managerユーザーガイドを参照してください](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)。 このビデオシリーズは、gitとソース管理に関する基本的な知識を前提としています。 gitについて詳し [くは、以下の](#additional-resources) 「その他のリソース」を参照してください。

>[!NOTE]
>
> このビデオシリーズで概要を説明する手順と命名規則は、お客様が管理するGitリポジトリとCloud Managerを使用する際のベストプラクティスを表しています。 表示される規約とワークフローは、個々の開発チームに合わせて調整されると期待されます。

## 初期同期 {#initial-sync}

顧客が管理するGitリポジトリをCloud ManagerのGitリポジトリと同期する最初の手順。

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12&captions=jpn)

## 基本分岐戦略 {#branching-strategy}

Cloud Managerの実稼働用パイプラインと非実稼働用パイプラインを活用するために、基本的 [な分岐方法を設定します](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html)。

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12&captions=jpn)

## 機能分岐の開発 {#feature-development}

機能ブランチを使用して、顧客が管理するGitリポジトリ内のコード変更を分離し、Cloud ManagerのGitリポジトリと同期して、コードの品質と検証のテストに非実稼働パイプラインを使用します。

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12&captions=jpn)

## 実稼動のデプロイメント {#production-deployment}

お客様が管理するGitリポジトリで実稼働版リリースのコードを準備し、Cloud ManagerのGitリポジトリと同期して、ステージ環境と実稼働環境にデプロイします。

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12&captions=jpn)

## リリースタグの同期 {#sync-tags}

Cloud Managerのgitリポジトリのリリースタグを、お客様が管理するgitリポジトリに同期させて、ステージ環境と実稼働環境にデプロイされたコードを明確に把握できるようにします。

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12&captions=jpn)

## その他のリソース {#additional-resources}

* [Cloud Managerドキュメント](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)
* [GitHubリソース](https://try.github.io)
* [Atlassian Gitチュートリアル](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)