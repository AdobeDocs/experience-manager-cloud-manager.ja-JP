---
title: セキュリティとプライバシー
description: Cloud Manager でのコードおよびアーティファクトアセットのセキュリティとプライバシーについて説明します。
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
source-git-commit: d7751757c1d3bda3d60406a1d39cb41c61f5c863
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 25%

---


# セキュリティとプライバシー {#security-and-privacy}

Cloud Manager でのコードおよびアーティファクトアセットのセキュリティとプライバシーについて説明します。

## 役割と権限 {#roles}

[!UICONTROL Cloud Manager] には、適切な権限を持つ事前設定済みのロールが用意されています。

Admin Consoleおよびユーザーロールの権限で割り当てることができるロールについては、このドキュメントを参照してください [ロールベースの権限。](/help/requirements/role-based-permissions.md)

## リソースの分離 {#resource-isolation}

[!UICONTROL Cloud Manager] のお客様は、に関連するすべての権限として認証するために、IMS 資格情報が必要です [!UICONTROL Cloud Manager] は、IMS 組織に関連付けられています。 オンボーディングプロセス中、プロビジョニングチームは、 [!UICONTROL Cloud Manager].

## データのセキュリティ {#data-security}

[!UICONTROL Cloud Manager] では、コードは送信時に暗号化されます。Cod Manager でビルドされるバイナリは送信時および保存時に暗号化されます。

顧客ごとに専用の Git リポジトリを取得します。また、コードはセキュリティで保護され、他の組織とは共有されません。

## データのプライバシー {#data-privacy}

[!UICONTROL Cloud Manager] は、アドビが規定したプライバシー原則に従っています。開発者は、HTTPS 経由でコードを Git リポジトリに安全にプッシュします。

[!UICONTROL Cloud Manager]のユーザーインターフェイスは、という共通制御フレームワークに準拠するサービスに基づいて構築されています。Adobe共通制御フレームワークに準拠します。 [!UICONTROL Cloud Manager]のユーザーインターフェイスでは、複数のクラウドプロバイダーから提供されるセキュアなサービスを使用しています。
