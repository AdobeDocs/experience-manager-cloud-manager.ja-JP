---
title: リリースノート（2021.3.0）
description: このページでは、Cloud Manager リリース 2021.3.0 について説明します。
feature: リリース情報
translation-type: tm+mt
source-git-commit: 12a7d6199983e2d19ef401051f60e3f24bb6d4f8
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 18%

---


# リリースノート（2021.3.0） {#release-notes-for}

以下の節では、[!UICONTROL Cloud Manager] リリース 2021.3.0 の一般リリースノートの概要を説明します。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2021.3.0 のリリース日は 2021 年 3 月 11 日です。次回のリリースは2021年4月8日に予定されています。

## 新機能 {#whats-new}

* お客様のディスパッチャー設定を検証するために、新しいコード品質ツール[ディスパッチャー最適化ツール](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/custom-code-quality-rules.html?lang=en#dispatcher-optimization-tool-rules)が導入されました。

* 統合シェルのユーザープロファイルアイコン（右上）に移動した後、**表示Cloud Managerの役割**&#x200B;を選択すると、Cloud Managerの役割を表示できるようになりました。

* ラベル&#x200B;**承認申請**&#x200B;が&#x200B;**実稼動承認**&#x200B;にラベル変更され、より明確になりました。

* **バージョン**&#x200B;ラベルが、実稼動パイプライン実行画面の&#x200B;**Gitタグ**&#x200B;に再ラベル付けされました。

* 重要な指標が定義されたしきい値を満たさない場合の動作を定義するラベルのラベルが、その真の動作（**すぐにキャンセル**、**直ちに承認**）を反映するように再ラベル付けされました。 詳細は、[パイプライン設定の構成](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=en#configuring-the-pipeline-settings-from-cloud-manager)を参照してください。

* AEMCloud ServiceSDKのバージョン`2021.3.4997.20210303T022849Z-210225`に基づいて、クラスとメソッドの非推奨リストが更新されました。

## バグ修正 {#bug-fixes}

* 他のパッケージにパッケージが埋め込まれた場合に、品質の問題が正しく検出されない場合がありました。

* 場合によっては、パイプラインの開始直後にパイプラインの実行ページから移動すると、実際に実行が開始したにもかかわらず、アクションが失敗したことを示すエラーメッセージが表示されます。