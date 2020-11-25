---
title: ICLRControl インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl
helpviewer_keywords:
- ICLRControl interface [.NET Framework hosting]
ms.assetid: a24fd905-1fa6-45a0-ad65-e9e2ee58861e
topic_type:
- apiref
ms.openlocfilehash: acf449014f5bf5683d5488f8ed2ead963676fe6b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728342"
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="8560e-102">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8560e-102">ICLRControl Interface</span></span>

<span data-ttu-id="8560e-103">共通言語ランタイム (CLR) に対してホストが参照を取得し、その側面を構成できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="8560e-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8560e-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="8560e-104">Methods</span></span>  
  
|<span data-ttu-id="8560e-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="8560e-105">Method</span></span>|<span data-ttu-id="8560e-106">説明</span><span class="sxs-lookup"><span data-stu-id="8560e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8560e-107">GetCLRManager メソッド</span><span class="sxs-lookup"><span data-stu-id="8560e-107">GetCLRManager Method</span></span>](iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="8560e-108">ホストが CLR を構成するために使用できる任意のマネージャー型のインスタンスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="8560e-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="8560e-109">SetAppDomainManagerType メソッド</span><span class="sxs-lookup"><span data-stu-id="8560e-109">SetAppDomainManagerType Method</span></span>](iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="8560e-110">から派生した型を、 <xref:System.AppDomainManager> アプリケーションドメインマネージャーの型として設定します。</span><span class="sxs-lookup"><span data-stu-id="8560e-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8560e-111">要件</span><span class="sxs-lookup"><span data-stu-id="8560e-111">Requirements</span></span>  

 <span data-ttu-id="8560e-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8560e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8560e-113">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="8560e-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8560e-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="8560e-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8560e-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8560e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8560e-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="8560e-116">See also</span></span>

- [<span data-ttu-id="8560e-117">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8560e-117">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="8560e-118">ICLRDebugManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8560e-118">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="8560e-119">ICLRGCManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8560e-119">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="8560e-120">ICLRHostBindingPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8560e-120">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="8560e-121">ICLRHostProtectionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8560e-121">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="8560e-122">ICLROnEventManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8560e-122">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="8560e-123">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8560e-123">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="8560e-124">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8560e-124">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="8560e-125">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8560e-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
