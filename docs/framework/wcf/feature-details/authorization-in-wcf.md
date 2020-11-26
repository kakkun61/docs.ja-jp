---
title: WCF での承認
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
ms.openlocfilehash: 67da01508fbb8f14b6405b79445bdef297e63288
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247487"
---
# <a name="authorization-in-wcf"></a><span data-ttu-id="eacff-102">WCF での承認</span><span class="sxs-lookup"><span data-stu-id="eacff-102">Authorization in WCF</span></span>

<span data-ttu-id="eacff-103">承認は、サービスやファイルなどのリソースへのアクセスと権限を制御するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="eacff-103">Authorization is the process of controlling access and rights to resources, such as services or files.</span></span> <span data-ttu-id="eacff-104">このセクションのトピックでは、さまざまな方法で Windows Communication Foundation (WCF) でこの基本的なタスクを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eacff-104">The topics in this section show you how to perform this basic task in Windows Communication Foundation (WCF) in a variety of ways.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eacff-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="eacff-105">In This Section</span></span>  

 [<span data-ttu-id="eacff-106">アクセス制御機構</span><span class="sxs-lookup"><span data-stu-id="eacff-106">Access Control Mechanisms</span></span>](access-control-mechanisms.md)  
 <span data-ttu-id="eacff-107">WCF の承認メカニズムの概要と、推奨される使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eacff-107">Provides a brief outline of the authorization mechanisms in WCF, and suggested uses.</span></span>  
  
 [<span data-ttu-id="eacff-108">方法: PrincipalPermissionAttribute クラスでアクセスを制限する</span><span class="sxs-lookup"><span data-stu-id="eacff-108">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 <span data-ttu-id="eacff-109"><xref:System.Security.Permissions.PrincipalPermissionAttribute> を使用してサービスへのアクセスを制限するプロセスを示します。</span><span class="sxs-lookup"><span data-stu-id="eacff-109">Shows the process of restricting access to a service with the <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span></span>  
  
 [<span data-ttu-id="eacff-110">方法: ASP.NET のロール プロバイダーとサービスを使用する</span><span class="sxs-lookup"><span data-stu-id="eacff-110">How to: Use the ASP.NET Role Provider with a Service</span></span>](how-to-use-the-aspnet-role-provider-with-a-service.md)  
 <span data-ttu-id="eacff-111">サービスの構成に従って、ASP.NET のロールプロバイダー機能を使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="eacff-111">Walks through the configuration of a service to enable it to use the role provider feature of ASP.NET.</span></span>  
  
 [<span data-ttu-id="eacff-112">方法: ASP.NET の承認マネージャー ロール プロバイダーとサービスを使用する</span><span class="sxs-lookup"><span data-stu-id="eacff-112">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>](how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 <span data-ttu-id="eacff-113">ASP.NET は、承認マネージャーを使用して、Web サイトの承認を管理できます。</span><span class="sxs-lookup"><span data-stu-id="eacff-113">ASP.NET can use the Authorization Manager to manage authorization for a Web site.</span></span> <span data-ttu-id="eacff-114">WCF では、クライアントの承認に ASP.NET/Authorization Manager の組み合わせを利用することもできます。</span><span class="sxs-lookup"><span data-stu-id="eacff-114">WCF can similarly leverage the ASP.NET/Authorization Manager combination for authorization of clients.</span></span>  
  
 [<span data-ttu-id="eacff-115">ID モデルを使用したクレームと承認の管理</span><span class="sxs-lookup"><span data-stu-id="eacff-115">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)  
 <span data-ttu-id="eacff-116">ID モデル インフラストラクチャをクレーム ベースの承認に使用する際の基本について説明します。</span><span class="sxs-lookup"><span data-stu-id="eacff-116">Explains the basics of using the Identity Model infrastructure for claims-based authorization.</span></span>  
  
 [<span data-ttu-id="eacff-117">委任と偽装</span><span class="sxs-lookup"><span data-stu-id="eacff-117">Delegation and Impersonation</span></span>](delegation-and-impersonation-with-wcf.md)  
 <span data-ttu-id="eacff-118">委任と偽装の違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="eacff-118">Explains the difference between delegation and impersonation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="eacff-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="eacff-119">Reference</span></span>  

 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a><span data-ttu-id="eacff-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="eacff-120">Related Sections</span></span>  

 [<span data-ttu-id="eacff-121">認証</span><span class="sxs-lookup"><span data-stu-id="eacff-121">Authentication</span></span>](authentication-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="eacff-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="eacff-122">See also</span></span>

- [<span data-ttu-id="eacff-123">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="eacff-123">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="eacff-124">[Windows Server AppFabric のセキュリティ モデル](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="eacff-124">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
