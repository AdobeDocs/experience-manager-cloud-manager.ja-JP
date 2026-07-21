---
title: セキュリティとプライバシー
description: Adobe Cloud Managerのコードとアーティファクトアセットのセキュリティとプライバシーについて説明します。
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
TQID: https://experienceleague.adobe.com/mtWOzJnzV8k403LlyD9Fn9WSE5XTgjHzyVuA4j62MMg
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: d5a34a9f6d050eaff241c0f42c9cf023cbc8036a
workflow-type: tm+mt
source-wordcount: 201
ht-degree: 26%

---

# セキュリティとプライバシー {#security-and-privacy}

Adobe Cloud Managerのコードとアーティファクトアセットのセキュリティとプライバシーについて説明します。

## 役割と権限 {#roles}

Cloud Manager には、適切な権限を持つ事前設定済みの役割が用意されています。

Admin Console で割り当てることができるロールおよび各ユーザーロールの権限については、[ロールに基づく権限](/help/requirements/role-based-permissions.md)を参照してください。

## リソースの分離 {#resource-isolation}

Cloud Managerに関連付けられたすべての権限がIMS組織に関連付けられているため、Cloud Managerのお客様はIMS資格情報を認証する必要があります。 オンボーディングプロセスでは、プロビジョニングチームがCloud Managerでリソースの分離を確実に実施します。

## データのセキュリティ {#data-security}

Cloud Managerコードは転送時に暗号化されています。 Cloud Managerは、送信時にも暗号化され、暗号化された形式で保存されるバイナリを構築します。

各顧客は独自のGit リポジトリを取得し、コードは保護され、他の組織とは共有されません。

## データのプライバシー {#data-privacy}

Cloud Managerは、Adobeで定義されたプライバシー原則に準拠しています。 開発者は、HTTPS でコードを Git リポジトリに安全にプッシュします。

Cloud Managerのユーザーインターフェイスは、Adobe Common Control Frameworkに準拠したサービスを使用します。 Cloud Managerのユーザーインターフェイスでは、複数のクラウドプロバイダーの安全なサービスを利用できます。
