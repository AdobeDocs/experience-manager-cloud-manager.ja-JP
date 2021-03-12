---
title: リリースノート（2021.3.0）
seo-title: AEM Cloud Manager リリースノート（2021.3.0）
description: このページでは、Cloud Manager リリース 2021.3.0 について説明します。
seo-description: このページでは、AEM Cloud Manager リリース 2021.3.0 について説明します。
translation-type: tm+mt
source-git-commit: 090505e737b8cb224d87f117a9b5e786a4f99851
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 19%

---

# リリースノート（2021.3.0） {#release-notes-for}

以下の節では、[!UICONTROL Cloud Manager] リリース 2021.3.0 の一般リリースノートの概要を説明します。

## リリース日 {#release-date}

[!UICONTROL Cloud Manager] バージョン 2021.3.0 のリリース日は 2021 年 3 月 11 日です。

## 新機能 {#whats-new}

* 必要な権限を持つユーザーは、プログラムを編集でき、セルフサービスの方法で次の操作を実行できます。

   * アセットを追加持つ既存のプログラム（またはその逆）に対するサイトソリューション
   * サイトとアセットの両方を含む既存のプログラムからサイト（またはアセット）を削除します。
   * ソリューションの追加（戻す）は、既存のプログラムに対して行うことも、新しいプログラムとして行うこともできます。

* お客様のディスパッチャー設定を検証するために、新しいコード品質ツール[ディスパッチャー最適化ツール](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/custom-code-quality-rules.html?lang=en#dispatcher-optimization-tool-rules)が導入されました。

* 統合シェルのユーザープロファイルアイコン（右上）に移動した後、**表示Cloud Managerの役割**&#x200B;を選択すると、Cloud Managerの役割を表示できるようになりました。

* ラベル&#x200B;**承認申請**&#x200B;が&#x200B;**実稼動承認**&#x200B;にラベル変更され、より明確になりました。

* **バージョン**&#x200B;ラベルが、実稼動パイプライン実行画面の&#x200B;**Gitタグ**&#x200B;に再ラベル付けされました。

* 重要な指標が定義されたしきい値を満たさない場合の動作を定義するラベルのラベルが、その真の動作（**すぐにキャンセル**、**直ちに承認**）を反映するように再ラベル付けされました。 詳しくは、[Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=en#configuring-the-pipeline-settings-from-cloud-manager)からのパイプライン設定の設定を参照してください。

* AEMCloud ServiceSDKのバージョン`2021.3.4997.20210303T022849Z-210225`に基づいて、クラスとメソッドの非推奨リストが更新されました。

## バグ修正 {#bug-fixes}

* 他のパッケージにパッケージが埋め込まれた場合に、品質の問題が正しく検出されない場合がありました。

* 場合によっては、パイプラインの開始直後にパイプラインの実行ページから移動すると、実際に実行が開始したにもかかわらず、アクションが失敗したことを示すエラーメッセージが表示されます。