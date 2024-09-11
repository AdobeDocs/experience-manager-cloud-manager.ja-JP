---
title: セキュリティとプライバシー
description: Cloud Manager でのコードおよびアーティファクトアセットのセキュリティとプライバシーについて説明します。
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '202'
ht-degree: 100%

---


# セキュリティとプライバシー {#security-and-privacy}

Cloud Manager でのコードおよびアーティファクトアセットのセキュリティとプライバシーについて説明します。

## 役割と権限 {#roles}

[!UICONTROL Cloud Manager] には、適切な権限を持つ事前設定済みの役割が用意されています。

Admin Console で割り当てることができるロールおよび各ユーザーロールの権限については、[ロールに基づく権限](/help/requirements/role-based-permissions.md)を参照してください。

## リソースの分離 {#resource-isolation}

[!UICONTROL Cloud Manager] に関連付けられているすべての権限は、IMS 組織に関連付けられているため、[!UICONTROL Cloud Manager] のお客様は認証のために IMS 資格情報が必要です。オンボーディングプロセス中、プロビジョニングチームは、[!UICONTROL Cloud Manager] でリソース分離が確実に適用されるようにします。

## データのセキュリティ {#data-security}

[!UICONTROL Cloud Manager] では、コードは送信時に暗号化されます。Cloud Manager でビルドされるバイナリは送信時および保存時に暗号化されます。

顧客ごとに専用の Git リポジトリを取得します。コードはセキュリティで保護され、他の組織とは共有されません。

## データのプライバシー {#data-privacy}

[!UICONTROL Cloud Manager] は、アドビが定義したプライバシー原則に従っています。開発者は、HTTPS でコードを Git リポジトリに安全にプッシュします。

[!UICONTROL Cloud Manager] のユーザーインターフェイスは、アドビの共通制御フレームワークに準拠するサービスに基づいて構築されています。[!UICONTROL Cloud Manager] のユーザーインターフェイスでは、複数のクラウドプロバイダーから提供されるセキュアなサービスを使用しています。
