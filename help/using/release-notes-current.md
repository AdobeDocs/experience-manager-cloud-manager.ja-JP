---
title: リリースノート（2019.9.0）
seo-title: AEM Cloud Manager リリースノート（2019.9.0）
description: このページでは、Cloud Manager リリース 2019.9.0 について説明します。
seo-description: このページでは、AEM Cloud Manager リリース 2019.9.0 について説明します。
translation-type: tm+mt
source-git-commit: 26014cfabfee6226033ba2fc1167d8f5509e17c6

---

# リリースノート（2019.9.0） {#release-notes-for}

The [!UICONTROL Cloud Manager] 2019.9.0 Release updates the security test criteria, adds downloadable monitoring graphs, and fixes some customer-reported usability issues.

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2019.9.0 のリリース日は 2019 年 9 月 12 日です。

## 最新情報 {#whats-new}

* The categorization of the Sling Referrer Filter health check has been changed from Critical to Important.
* The categorization of the HTML Library Manager Config health check has been changed from Critical to Important.
* Monitoring graphs can now be downloaded. 詳しくは、[環境の監視](monitor-your-environments.md)を参照してください。
* If a program does not have a production AEM environment, clicking on the program card from the landing page will navigate to the Cloud Manager overview page, not produce an error dialog.
* The Pipeline Settings Card on the Overview page has been retitled to Production Pipeline Settings.************
* The Important Failure Behavior radio buttons have been removed from code-quality only pipelines.
* The Activity page now displays the name of the pipeline for each execution.****
* The execution page now displays the name of the pipeline.
* The Code Quality summary dialog now shows a description for each rating.

## バグ修正 {#bug-fixes}

* Some users could not view an execution details when it was waiting for approval.
* On Overview page, the right margin was not consistent.****
* ビルドコンテナーのメモリが大きなプロジェクトで不足する可能性があります。
* 状況によっては、BoundedPaths OakPALルールが/libsの下にインストールされたコンテンツを識別しない場合がありました。
* When a quality gate was rejected, the dialog heading still showed Partially Passed.**

## 既知の問題 {#known-issues}

* Downloading of monitoring graphs is not available in Safari.
