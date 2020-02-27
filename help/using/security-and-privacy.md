---
title: セキュリティとプライバシー
seo-title: AEM Cloud Manager のセキュリティとプライバシー
description: このページでは、アセット（コード／アーティファクト）のセキュリティとプライバシーについて説明します。
seo-description: このページでは、AEM Cloud Manager を使用したアセット（コード／アーティファクト）のセキュリティとプライバシーについて説明します。
uuid: 68bc2330-a62c-4c2c-925c-daa6788b143a
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
translation-type: tm+mt
source-git-commit: 7cbc42108a6ccc8f7303eb76fd8ca2e9027f49e0

---


# セキュリティとプライバシー {#security-and-privacy}

[!UICONTROL Cloud Manager] には、適切な権限を持つ事前設定済みのロールが含まれています。 この節では、AEM Cloud Managerを使用したアセット（コード/アーティファクト）のセキュリティとプライバシーについて説明します。 Additionally, [!UICONTROL Cloud Manager] has pre-configured roles with appropriate permissions.

管理コンソールで割り当てることができる役割とユーザの役割の権限については、「役割に基づく権限」を参 [照してください](/help/using/role-based-permissions.md)。


## リソースの分離 {#resource-isolation}

[!UICONTROL Cloud Manager] に関連付けられているすべての権限が設定され、IMS 組織に関連付けられる場合、[!UICONTROL Cloud Manager] を使用するお客様が認証をおこなうには、IMS 資格情報が必要になります。オンボーディングプロセス中、プロビジョニングチームは、[!UICONTROL Cloud Manager] でリソース分離が確実に適用されるようにします。

## データのセキュリティ {#data-security}

Code in [!UICONTROL Cloud Manager] is encrypted in transit. Cod Manager でビルドされるバイナリは送信時および保存時に暗号化されます。

顧客ごとに専用の **Git** リポジトリを取得します。顧客のコードはセキュリティで保護され、他の&#x200B;**組織**&#x200B;とは共有されません。

## データのプライバシー {#data-privacy}

[!UICONTROL Cloud Manager] アドビが定義するプライバシー原則に従います。 デベロッパーは、HTTPS でコードを **Git リポジトリ**&#x200B;に安全にプッシュします。

[!UICONTROL Cloud Manager] のユーザーインターフェイス（UI）は、アドビが規定した共通のコントロールフレームワークに準拠するサービスに基づいて構築されています。[!UICONTROL Cloud Manager] のユーザーインターフェイス（UI）では、複数のクラウドプロバイダーから提供されるセキュアなサービスを使用しています。
