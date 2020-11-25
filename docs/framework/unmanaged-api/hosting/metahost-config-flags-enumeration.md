---
title: METAHOST_CONFIG_FLAGS 列挙体
ms.date: 03/30/2017
api_name:
- METAHOST_CONFIG_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_CONFIG_FLAGS
helpviewer_keywords:
- METAHOST_CONFIG_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 6f1e389f-ed99-4d6a-a0ba-72d7d869a01d
topic_type:
- apiref
ms.openlocfilehash: 01e55659bf2a348ec763f51112cbdcd706f27c84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730007"
---
# <a name="metahost_config_flags-enumeration"></a><span data-ttu-id="488c6-102">METAHOST_CONFIG_FLAGS 列挙体</span><span class="sxs-lookup"><span data-stu-id="488c6-102">METAHOST_CONFIG_FLAGS Enumeration</span></span>

<span data-ttu-id="488c6-103">`pdwConfigFlags` [ICLRMetaHostPolicy:: GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md)メソッドのパラメーターで返されるフラグについて説明します。これは、 `useLegacyV2RuntimeActivationPolicy` 構成ファイルの[ \<startup> 要素](../../configure-apps/file-schema/startup/startup-element.md)内の属性の存在と設定を示します。</span><span class="sxs-lookup"><span data-stu-id="488c6-103">Describes the possible flags returned in the `pdwConfigFlags` parameter of the [ICLRMetaHostPolicy::GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method, indicating the presence and setting of the `useLegacyV2RuntimeActivationPolicy` attribute in the [\<startup> element](../../configure-apps/file-schema/startup/startup-element.md) of the configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="488c6-104">構文</span><span class="sxs-lookup"><span data-stu-id="488c6-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="488c6-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="488c6-105">Members</span></span>  
  
|<span data-ttu-id="488c6-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="488c6-106">Member</span></span>|<span data-ttu-id="488c6-107">説明</span><span class="sxs-lookup"><span data-stu-id="488c6-107">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|<span data-ttu-id="488c6-108">`useLegacyV2RuntimeActivationPolicy`属性が[ \<startup> 要素](../../configure-apps/file-schema/startup/startup-element.md)内に存在しませんでした。</span><span class="sxs-lookup"><span data-stu-id="488c6-108">The `useLegacyV2RuntimeActivationPolicy` attribute was not present in the [\<startup> Element](../../configure-apps/file-schema/startup/startup-element.md).</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|<span data-ttu-id="488c6-109">`useLegacyV2RuntimeActivationPolicy`属性が存在し、がに設定されて `true` います。</span><span class="sxs-lookup"><span data-stu-id="488c6-109">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `true`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|<span data-ttu-id="488c6-110">`useLegacyV2RuntimeActivationPolicy`属性が存在し、がに設定されて `false` います。</span><span class="sxs-lookup"><span data-stu-id="488c6-110">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `false`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|<span data-ttu-id="488c6-111">に関連する値を取得するには、このマスクをで返される値に適用 `pdwConfigFlags` `useLegacyV2RuntimeActivationPolicy` します。</span><span class="sxs-lookup"><span data-stu-id="488c6-111">Apply this mask to the value returned in `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="488c6-112">解説</span><span class="sxs-lookup"><span data-stu-id="488c6-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="488c6-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="488c6-113">Requirements</span></span>  

 <span data-ttu-id="488c6-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="488c6-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="488c6-115">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="488c6-115">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="488c6-116">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="488c6-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="488c6-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="488c6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="488c6-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="488c6-118">See also</span></span>

- [<span data-ttu-id="488c6-119">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="488c6-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="488c6-120">GetRequestedRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="488c6-120">GetRequestedRuntime Method</span></span>](iclrmetahostpolicy-getrequestedruntime-method.md)
- [<span data-ttu-id="488c6-121">\<startup> 要素</span><span class="sxs-lookup"><span data-stu-id="488c6-121">\<startup> Element</span></span>](../../configure-apps/file-schema/startup/startup-element.md)
