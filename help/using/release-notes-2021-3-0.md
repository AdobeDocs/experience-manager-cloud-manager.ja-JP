---
title: リリースノート（2021.3.0）
description: このページでは、Cloud Manager リリース 2021.3.0 について説明します。
feature: リリース情報
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 503d9b25855633737c49e3e278a3a76052ed84d1
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 18%

---

# リリースノート（2021.3.0） {#release-notes-for}

以下の節では、[!UICONTROL Cloud Manager] リリース 2021.3.0 の一般リリースノートの概要を説明します。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2021.3.0 のリリース日は 2021 年 3 月 11 日です。次回のリリースは2021年4月8日に予定されています。

## 新機能 {#whats-new}

* 顧客のDispatcher設定を検証するための新しいコード品質ツール[Dispatcher最適化ツール](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/custom-code-quality-rules.html?lang=en#dispatcher-optimization-tool-rules)が導入されました。

* 統合シェルのユーザープロファイルアイコン（右上）に移動した後、「 **Cloud Managerの役割を表示** 」オプションを選択すると、Cloud Managerの役割を表示できるようになりました。

* ラベル&#x200B;**承認の申請**&#x200B;が&#x200B;**実稼動の承認**&#x200B;に変更され、より明確になりました。

* 実稼動パイプラインの実行画面で、**Version**&#x200B;ラベルが&#x200B;**Gitタグ**&#x200B;にリラベルされました。

* 重要な指標が定義されたしきい値を満たさない場合の動作を定義するラベルが、真の動作（**即時にキャンセル**&#x200B;および&#x200B;**直ちに承認**）を反映するように再ラベル付けされました。 詳しくは、[パイプライン設定の指定](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=en#configuring-the-pipeline-settings-from-cloud-manager)を参照してください。

* クラスおよびメソッドの廃止リストは、AEMCloud ServiceSDKのバージョン`2021.3.4997.20210303T022849Z-210225`に基づいて更新されました。

## バグ修正 {#bug-fixes}

* 他のパッケージにパッケージが埋め込まれた場合に、品質の問題が正しく検出されない場合がありました。

* 場合によっては、ユーザーがパイプラインの開始直後にパイプライン実行ページから離れると、実際に実行が開始するにもかかわらず、アクションが失敗したことを示すエラーメッセージが表示されます。
