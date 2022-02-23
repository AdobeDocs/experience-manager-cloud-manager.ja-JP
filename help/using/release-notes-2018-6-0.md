---
title: リリースノート（2018.6.0）
seo-title: AEM Cloud Manager Release Notes for 2018.6.0
description: このページでは、Cloud Manager リリース 2018.6.0 について説明します。
seo-description: Follow this page to get information for AEM Cloud Manager Release 2018.6.0.
uuid: 211b6e1b-10fb-46b0-b591-44d5e44abd77
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 8584f467-3e61-41ea-98e4-f79e68c86469
feature: Release Information
exl-id: 456f7892-c64c-4b3f-b845-15682d034aaa
source-git-commit: 4f0e1d163001fd18cfa838256c813152d65c3b4c
workflow-type: ht
source-wordcount: '321'
ht-degree: 100%

---

# リリースノート（2018.6.0） {#release-notes-for}

以下の節では、[!UICONTROL Cloud Manager] リリース 2018.6.0 の一般リリースノートの概要を説明し、デプロイメント中の Dispatcher の無効化、追加の通知およびユーザビリティの改善についても説明します。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2018.6.0 のリリース日は 2018年8月9日（PT）です。

## 新機能 {#what-s-new}

* **CI／CD パイプライン** - CI／CD パイプラインの実行中にステージング環境と実稼動環境の両方で Dispatcher の無効化とキャッシュのフラッシュを設定可能。詳しくは、[実稼動パイプラインの設定](configuring-production-pipelines.md)のドキュメントを参照してください。

* **CI／CD パイプライン** - 品質ゲートの 1 つで重大なエラーが発生した場合のパイプラインの動作を、パイプラインの設定時に定義できるようになりました。詳しくは、[実稼動パイプラインの設定](configuring-production-pipelines.md)のドキュメントを参照してください。

* **CI／CD パイプライン** - 担当の CSE または対応可能な CSE に CSE 管理を実行してもらうかどうかを、パイプラインの設定時に選択できるようになりました。詳しくは、[実稼動パイプラインの設定](configuring-production-pipelines.md)のドキュメントを参照してください。

* **CI／CD パイプライン** - CI／CD パイプラインがビジネス承認ステップに到達すると、デプロイメントを承認する権限を持っているユーザーに通知が送信されます。詳しくは、[通知](notifications.md)を参照してください。

* **CI／CD パイプライン** - CI／CD パイプラインが設定スケジュールに到達すると、スケジュールを設定する権限を持っているユーザーに通知が送信されます。詳しくは、[通知](notifications.md)を参照してください。

* **コード品質分析** - 誤って設定されたアウトバウンド HTTP／HTTPS 要求を識別するための新しいルールが導入されました。詳しくは、[カスタムコード品質ルール](custom-code-quality-rules.md)を参照してください。

## バグ修正 {#bug-fixes}

* 場合によっては、パフォーマンステストが複数のディスパッチャーおよびパブリッシュインスタンスに対して完全には配布されないことがありました。
* 狭いブラウザーウィンドウでは、ヘッダーナビゲーションが非表示になっていました。
* パイプラインの実行中に一部のパイプライン設定が無効になりませんでした。
* プログラムリスト画面で AEM および監視へのリンクを使用すると、現在のブラウザータブが置き換えられ、新しいタブが開きました。
* 状況によっては、承認期間が長く続くとデプロイメントに失敗することがありました。
