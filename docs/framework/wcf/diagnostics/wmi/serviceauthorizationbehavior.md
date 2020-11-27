---
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: d3625865484568746888ef0638d9a8501e610bef
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273205"
---
# <a name="serviceauthorizationbehavior"></a><span data-ttu-id="c9c4e-102">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="c9c4e-102">ServiceAuthorizationBehavior</span></span>

<span data-ttu-id="c9c4e-103">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="c9c4e-103">ServiceAuthorizationBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9c4e-104">構文</span><span class="sxs-lookup"><span data-stu-id="c9c4e-104">Syntax</span></span>  
  
```csharp
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c9c4e-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="c9c4e-105">Methods</span></span>  

 <span data-ttu-id="c9c4e-106">ServiceAuthorizationBehavior クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="c9c4e-106">The ServiceAuthorizationBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c9c4e-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c9c4e-107">Properties</span></span>  

 <span data-ttu-id="c9c4e-108">ServiceAuthorizationBehavior クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="c9c4e-108">The ServiceAuthorizationBehavior class has the following properties:</span></span>  
  
### <a name="impersonatecallerforalloperations"></a><span data-ttu-id="c9c4e-109">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="c9c4e-109">ImpersonateCallerForAllOperations</span></span>  

 <span data-ttu-id="c9c4e-110">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="c9c4e-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="c9c4e-111">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c9c4e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c9c4e-112">受信メッセージによって提供される資格情報を使用してサービスが偽装を試みるかどうかを制御する値。</span><span class="sxs-lookup"><span data-stu-id="c9c4e-112">A value that controls whether the service attempts to impersonate using the credentials provided by the incoming message.</span></span>  
  
### <a name="principalpermissionmode"></a><span data-ttu-id="c9c4e-113">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="c9c4e-113">PrincipalPermissionMode</span></span>  

 <span data-ttu-id="c9c4e-114">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="c9c4e-114">Data type: string</span></span>  
  
 <span data-ttu-id="c9c4e-115">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c9c4e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c9c4e-116">サーバーでの操作を実行するために使用されるプリンシパル。</span><span class="sxs-lookup"><span data-stu-id="c9c4e-116">The principal used to carry out operations on the server.</span></span>  
  
### <a name="roleprovider"></a><span data-ttu-id="c9c4e-117">RoleProvider</span><span class="sxs-lookup"><span data-stu-id="c9c4e-117">RoleProvider</span></span>  

 <span data-ttu-id="c9c4e-118">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="c9c4e-118">Data type: string</span></span>  
  
 <span data-ttu-id="c9c4e-119">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c9c4e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c9c4e-120">ASP.NET ロール プロバイダーの名前。</span><span class="sxs-lookup"><span data-stu-id="c9c4e-120">The name of the ASP.NET role provider.</span></span>  
  
### <a name="serviceauthorizationmanager"></a><span data-ttu-id="c9c4e-121">ServiceAuthorizationManager</span><span class="sxs-lookup"><span data-stu-id="c9c4e-121">ServiceAuthorizationManager</span></span>  

 <span data-ttu-id="c9c4e-122">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="c9c4e-122">Data type: string</span></span>  
  
 <span data-ttu-id="c9c4e-123">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c9c4e-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c9c4e-124">カスタム承認で使用される承認マネージャー。</span><span class="sxs-lookup"><span data-stu-id="c9c4e-124">The authorization manager used for custom authorization.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9c4e-125">要件</span><span class="sxs-lookup"><span data-stu-id="c9c4e-125">Requirements</span></span>  
  
|<span data-ttu-id="c9c4e-126">MOF</span><span class="sxs-lookup"><span data-stu-id="c9c4e-126">MOF</span></span>|<span data-ttu-id="c9c4e-127">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="c9c4e-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c9c4e-128">名前空間</span><span class="sxs-lookup"><span data-stu-id="c9c4e-128">Namespace</span></span>|<span data-ttu-id="c9c4e-129">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="c9c4e-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c9c4e-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="c9c4e-130">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
