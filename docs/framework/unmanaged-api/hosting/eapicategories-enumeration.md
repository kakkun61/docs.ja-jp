---
title: EApiCategories 列挙型
ms.date: 03/30/2017
api_name:
- EApiCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EApiCategories
helpviewer_keywords:
- EApiCategories enumeration [.NET Framework hosting]
ms.assetid: 3c4a8a5a-8a46-4ac9-947f-4959bc9d6ac6
topic_type:
- apiref
ms.openlocfilehash: f90e08373c0497201816bc7eead89b83b84be255
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726874"
---
# <a name="eapicategories-enumeration"></a><span data-ttu-id="062ec-102">EApiCategories 列挙型</span><span class="sxs-lookup"><span data-stu-id="062ec-102">EApiCategories Enumeration</span></span>

<span data-ttu-id="062ec-103">部分的に信頼されたコードでホストが実行をブロックできる機能のカテゴリについて説明します。</span><span class="sxs-lookup"><span data-stu-id="062ec-103">Describes the categories of capabilities that the host can block from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="062ec-104">構文</span><span class="sxs-lookup"><span data-stu-id="062ec-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eNoCategory               = 0,  
    eSynchronization          = 0x1,  
    eSharedState              = 0x2,  
    eExternalProcessMgmt      = 0x4,  
    eSelfAffectingProcessMgmt = 0x8,  
    eExternalThreading        = 0x10,  
    eSelfAffectingThreading   = 0x20,  
    eSecurityInfrastructure   = 0x40,  
    eUI                       = 0x80,  
    eMayLeakOnAbort           = 0x100,  
    eAll                      = 0x1ff  
} EHostProtectionCategories;  
```  
  
## <a name="members"></a><span data-ttu-id="062ec-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="062ec-105">Members</span></span>  
  
|<span data-ttu-id="062ec-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="062ec-106">Member</span></span>|<span data-ttu-id="062ec-107">説明</span><span class="sxs-lookup"><span data-stu-id="062ec-107">Description</span></span>|  
|------------|-----------------|  
|`eAll`|<span data-ttu-id="062ec-108">他のフィールドの対象となるすべてのマネージクラスおよびメンバーが、 `EApiCategories` 部分的に信頼されたコードでの実行をブロックされるように指定します。</span><span class="sxs-lookup"><span data-stu-id="062ec-108">Specifies that all managed classes and members that are covered by other `EApiCategories` fields be blocked from running in partially trusted code.</span></span>|  
|`eExternalProcessMgmt`|<span data-ttu-id="062ec-109">外部プロセスの作成、操作、および破棄を許可するマネージクラスおよびメンバーが、部分的に信頼されたコードでの実行をブロックされることを指定します。</span><span class="sxs-lookup"><span data-stu-id="062ec-109">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external processes be blocked from running in partially trusted code.</span></span>|  
|`eExternalThreading`|<span data-ttu-id="062ec-110">外部スレッドの作成、操作、および破棄を許可するマネージクラスおよびメンバーが、部分的に信頼されたコードでの実行をブロックされることを指定します。</span><span class="sxs-lookup"><span data-stu-id="062ec-110">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external threads be blocked from running in partially trusted code.</span></span>|  
|`eMayLeakOnAbort`|<span data-ttu-id="062ec-111">中止時にメモリをリークする可能性のあるマネージ型およびメンバーが、部分的に信頼されたコードで実行されないようにブロックすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="062ec-111">Specifies that managed types and members that could potentially leak memory on abort be blocked from running in partially trusted code.</span></span>|  
|`eNoCategory`|<span data-ttu-id="062ec-112">部分的に信頼されたコードでは、マネージコードのカテゴリの実行をブロックしないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="062ec-112">Specifies that no managed code categories be blocked from running in partially trusted code.</span></span>|  
|`eSecurityInfrastructure`|<span data-ttu-id="062ec-113">共通言語ランタイム (CLR) のセキュリティインフラストラクチャが、部分的に信頼されたコードによって使用されるのをブロックすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="062ec-113">Specifies that the common language runtime (CLR) security infrastructure be blocked from being used by partially trusted code.</span></span>|  
|`eSelfAffectingProcessMgmt`|<span data-ttu-id="062ec-114">ホストされるプロセスに影響を与える可能性があるマネージクラスおよびメンバーが、部分的に信頼されたコードで実行されないように指定します。</span><span class="sxs-lookup"><span data-stu-id="062ec-114">Specifies that managed classes and members whose capabilities can affect the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSelfAffectingThreading`|<span data-ttu-id="062ec-115">ホストされているプロセスのスレッドに影響を与える可能性のあるマネージクラスおよびメンバーが、部分的に信頼されたコードでの実行をブロックされるように指定します。</span><span class="sxs-lookup"><span data-stu-id="062ec-115">Specifies that managed classes and members whose capabilities can affect threads in the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSharedState`|<span data-ttu-id="062ec-116">マネージクラスおよび共有状態を公開するメンバーが、部分的に信頼されたコードで実行されないようにブロックすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="062ec-116">Specifies that managed classes and members that expose shared state be blocked from running in partially trusted code.</span></span>|  
|`eSynchronization`|<span data-ttu-id="062ec-117">ユーザーコードがロックを保持することを許可する共通言語ランタイムクラスおよびメンバーが、部分的に信頼されたコードでの実行をブロックするように指定します。</span><span class="sxs-lookup"><span data-stu-id="062ec-117">Specifies that common language runtime classes and members that allow user code to hold locks be blocked from running in partially trusted code.</span></span>|  
|`eUI`|<span data-ttu-id="062ec-118">人間の操作を許可または必要とするマネージクラスおよびメンバーが、部分的に信頼されたコードでの実行をブロックされることを指定します。</span><span class="sxs-lookup"><span data-stu-id="062ec-118">Specifies that managed classes and members that allow or require human interaction be blocked from running in partially trusted code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="062ec-119">注釈</span><span class="sxs-lookup"><span data-stu-id="062ec-119">Remarks</span></span>  

 <span data-ttu-id="062ec-120">[ICLRHostProtectionManager:: SetProtectedCategories](iclrhostprotectionmanager-setprotectedcategories-method.md)メソッドは、型のパラメーターを受け取り `EApiCategories` ます。</span><span class="sxs-lookup"><span data-stu-id="062ec-120">The [ICLRHostProtectionManager::SetProtectedCategories](iclrhostprotectionmanager-setprotectedcategories-method.md) method takes a parameter of type `EApiCategories`.</span></span>  
  
 <span data-ttu-id="062ec-121">`EApiCategories`列挙体とメソッドは、 `SetProtectedCategories` マネージクラスに直接関連付けられ <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="062ec-121">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="062ec-122">マネージクラスは、値に直接対応する値を持つ列挙体と共に使用され、 <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> `EApiCategories` によって記述されたカテゴリに対応する機能を公開するマネージ型およびメンバーをマークし `EApiCategories` ます。</span><span class="sxs-lookup"><span data-stu-id="062ec-122">The managed class is used with the <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeration, whose values correspond directly to the `EApiCategories` values, to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="062ec-123">要件</span><span class="sxs-lookup"><span data-stu-id="062ec-123">Requirements</span></span>  

 <span data-ttu-id="062ec-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="062ec-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="062ec-125">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="062ec-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="062ec-126">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="062ec-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="062ec-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="062ec-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="062ec-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="062ec-128">See also</span></span>

- [<span data-ttu-id="062ec-129">ICLRHostProtectionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="062ec-129">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="062ec-130">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="062ec-130">Hosting Enumerations</span></span>](hosting-enumerations.md)
