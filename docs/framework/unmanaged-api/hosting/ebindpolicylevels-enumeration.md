---
title: EBindPolicyLevels 列挙型
ms.date: 03/30/2017
api_name:
- EBindPolicyLevels
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EBindPolicyLevels
helpviewer_keywords:
- EBindPolicyLevels enumeration [.NET Framework hosting]
ms.assetid: a9e00b4f-b6d0-4257-bd88-4fe9af97b8fa
topic_type:
- apiref
ms.openlocfilehash: a0992ca8ac4bfffef681c74de455a0eeb627a042
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726848"
---
# <a name="ebindpolicylevels-enumeration"></a><span data-ttu-id="b7fc5-102">EBindPolicyLevels 列挙型</span><span class="sxs-lookup"><span data-stu-id="b7fc5-102">EBindPolicyLevels Enumeration</span></span>

<span data-ttu-id="b7fc5-103">アセンブリポリシーを適用または変更するレベルを指定するフラグを提供します。</span><span class="sxs-lookup"><span data-stu-id="b7fc5-103">Provides flags to specify the level at which to apply or modify assembly policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7fc5-104">構文</span><span class="sxs-lookup"><span data-stu-id="b7fc5-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    ePolicyLevelNone         = 0x0,  
    ePolicyLevelRetargetable = 0x1,  
    ePolicyUnifiedToCLR      = 0x2,  
    ePolicyLevelApp          = 0x4,  
    ePolicyLevelPublisher    = 0x8,  
    ePolicyLevelHost         = 0x10,  
    ePolicyLevelAdmin        = 0x20  
    ePolicyPortability       = 0x40  
} EBindPolicyLevels;  
```  
  
## <a name="members"></a><span data-ttu-id="b7fc5-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="b7fc5-105">Members</span></span>  
  
|<span data-ttu-id="b7fc5-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b7fc5-106">Member</span></span>|<span data-ttu-id="b7fc5-107">説明</span><span class="sxs-lookup"><span data-stu-id="b7fc5-107">Description</span></span>|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|<span data-ttu-id="b7fc5-108">ポリシーを管理者レベルで適用する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="b7fc5-108">Specifies that policy should be applied at the administrator level.</span></span>|  
|`ePolicyLevelApp`|<span data-ttu-id="b7fc5-109">ポリシーをアプリケーションレベルで適用する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="b7fc5-109">Specifies that policy should be applied at the application level.</span></span>|  
|`ePolicyLevelHost`|<span data-ttu-id="b7fc5-110">ポリシーをホストレベルで適用する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="b7fc5-110">Specifies that policy should be applied at the host level.</span></span>|  
|`ePolicyLevelNone`|<span data-ttu-id="b7fc5-111">ポリシーレベルのフラグを指定しません。</span><span class="sxs-lookup"><span data-stu-id="b7fc5-111">Specifies no policy-level flags.</span></span>|  
|`ePolicyLevelPublisher`|<span data-ttu-id="b7fc5-112">ポリシーをパブリッシャーレベルで適用する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="b7fc5-112">Specifies that policy should be applied at the publisher level.</span></span>|  
|`ePolicyLevelRetargetable`|<span data-ttu-id="b7fc5-113">ポリシーを変数レベルで適用できることを指定します。</span><span class="sxs-lookup"><span data-stu-id="b7fc5-113">Specifies that policy should be applicable at variable levels.</span></span>|  
|`ePolicyPortability`|<span data-ttu-id="b7fc5-114">ポリシーで .NET Framework アセンブリの実装間の移植性をサポートする必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="b7fc5-114">Specifies that policy should support portability between implementations of a .NET Framework assembly.</span></span> <span data-ttu-id="b7fc5-115">構成ファイルの要素を参照してください [\<supportPortability>](../../configure-apps/file-schema/runtime/supportportability-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="b7fc5-115">See the [\<supportPortability>](../../configure-apps/file-schema/runtime/supportportability-element.md) configuration file element.</span></span>|  
|`ePolicyUnifiedToCLR`|<span data-ttu-id="b7fc5-116">ポリシーを共通言語ランタイム (CLR) のポリシーに統合することを指定します。</span><span class="sxs-lookup"><span data-stu-id="b7fc5-116">Specifies that policy should be unified to that of the common language runtime (CLR).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7fc5-117">注釈</span><span class="sxs-lookup"><span data-stu-id="b7fc5-117">Remarks</span></span>  

 <span data-ttu-id="b7fc5-118">この列挙体は、アプリケーションポリシーの変更を指定するために、 [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) インターフェイスのメソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="b7fc5-118">This enumeration is passed to methods of the [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) interface to specify changes in application policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7fc5-119">要件</span><span class="sxs-lookup"><span data-stu-id="b7fc5-119">Requirements</span></span>  

 <span data-ttu-id="b7fc5-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7fc5-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7fc5-121">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b7fc5-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b7fc5-122">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b7fc5-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b7fc5-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7fc5-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7fc5-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7fc5-124">See also</span></span>

- [<span data-ttu-id="b7fc5-125">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7fc5-125">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="b7fc5-126">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="b7fc5-126">Hosting Enumerations</span></span>](hosting-enumerations.md)
