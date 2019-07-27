---
title: アクセス権の付与
seo-title: AEM Cloud Manager でのアクセス権の付与
description: Adobe ID および Experience Cloud リソースについて詳しく説明します。
seo-description: このページでは、Adobe ID および AEM Experience Cloud リソースの詳細について説明します。
uuid: 9aa90a99-f049-422e-9e06-b00b843ed98b
products: SG_EXPERIENCEMANAGER／CLOUDMANAGER
topic-tags: requirements
discoiquuid: 072dbc1b-e608-4b1f-b0e8-0e4f88c8ad12
translation-type: ht
source-git-commit: 0f29b3f9cf4bd53d0e57c7793fe05cd3afeea5e1

---


# アクセス権の付与 {#access-rights-granted}

## ユーザーの ID タイプ {#user-identity-types}

アドビでは、オンボーディングプロセスの一部として、アドビの ID 管理システム（IMS）に会社の&#x200B;**組織** ID を作成します。このシステムで、すべてのユーザーとその権限を管理できます。各ユーザーがこの組織のメンバーになる必要があり、任意の [!UICONTROL Experience Cloud] サービスへのアクセス権を付与される場合、ユーザーには専用の **Adobe ID** が必要になります。

Adobe ID の使用を開始するには、[Adobe ID タイプの管理](https://helpx.adobe.com/enterprise/using/identity.html)を参照して、使用可能ないずれかの ID タイプを使用して Adobe ID を取得する方法の詳細を確認してください。

### ユーザーとロール {#users-and-roles}

会社の組織 ID が作成されたら、指定した管理者がこの組織の最初のメンバーとして追加されます。この管理者には、デフォルトで管理者権限が付与され、[!UICONTROL AEM Managed Services] **製品**&#x200B;および 1 つ以上の [!UICONTROL Cloud Manager]**製品プロファイル**&#x200B;が割り当てられます。Admin Console を使用してチームユーザーを設定および管理する方法について詳しくは、[ユーザーとロールの追加](setting-up-users-and-roles.md)を参照してください。

これらの権限を付与されると、管理者は、シングルサインオン（Adobe ID を使用）で [!UICONTROL Experience Cloud] サービスへのアクセス、AEM クラウド環境へのログイン、[!UICONTROL Cloud Manager] の使用をおこなえるように設定されます。
