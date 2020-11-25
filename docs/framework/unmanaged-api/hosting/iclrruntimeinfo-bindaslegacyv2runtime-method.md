---
title: ICLRRuntimeInfo::BindAsLegacyV2Runtime メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.BindAsLegacyV2Runtime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime
helpviewer_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime method [.NET Framework hosting]
- BindAsLegacyV2Runtime method [.NET Framework hosting]
ms.assetid: 65fd55ac-4a24-4479-9384-a2e8013bfb2b
topic_type:
- apiref
ms.openlocfilehash: f0a03ecce49bbc3c1c03d037c9be31a8e994259d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732095"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a><span data-ttu-id="7a10c-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime メソッド</span><span class="sxs-lookup"><span data-stu-id="7a10c-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime Method</span></span>

<span data-ttu-id="7a10c-103">すべてのレガシ共通言語ランタイム (CLR) バージョン2アクティブ化ポリシーの決定に現在のランタイムをバインドします。</span><span class="sxs-lookup"><span data-stu-id="7a10c-103">Binds the current runtime for all legacy common language runtime (CLR) version 2 activation policy decisions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a10c-104">構文</span><span class="sxs-lookup"><span data-stu-id="7a10c-104">Syntax</span></span>  
  
```cpp  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="7a10c-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="7a10c-105">Return Value</span></span>  

 <span data-ttu-id="7a10c-106">このメソッドは、次の特定の Hresult を返します。</span><span class="sxs-lookup"><span data-stu-id="7a10c-106">This method returns the following specific HRESULTs:</span></span>  
  
|<span data-ttu-id="7a10c-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7a10c-107">HRESULT</span></span>|<span data-ttu-id="7a10c-108">説明</span><span class="sxs-lookup"><span data-stu-id="7a10c-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7a10c-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="7a10c-109">S_OK</span></span>|<span data-ttu-id="7a10c-110">バインドが成功したか、またはこのランタイムが従来の CLR バージョン2アクティブ化ポリシーのランタイムとして既にバインドされています。</span><span class="sxs-lookup"><span data-stu-id="7a10c-110">Either binding succeeded, or this runtime was already bound as the legacy CLR version 2 activation policy runtime.</span></span>|  
|<span data-ttu-id="7a10c-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="7a10c-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="7a10c-112">以前の CLR バージョン2のアクティブ化ポリシーに、別のランタイムが既にバインドされています。</span><span class="sxs-lookup"><span data-stu-id="7a10c-112">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a10c-113">注釈</span><span class="sxs-lookup"><span data-stu-id="7a10c-113">Remarks</span></span>  

 <span data-ttu-id="7a10c-114">現在のランタイムが、従来の CLR バージョン2アクティブ化ポリシーの決定 (構成ファイルの要素で属性を使用するなど) に対して既にバインドされている場合 `useLegacyV2RuntimeActivationPolicy` 、このメソッドはエラー結果を返しません。メソッドが従来のアクティブ化ポリシーに正常にバインドされている場合と同じように、結果が S_OK されます。 [ \<startup> ](../../configure-apps/file-schema/startup/startup-element.md)</span><span class="sxs-lookup"><span data-stu-id="7a10c-114">If the current runtime is already bound for all legacy CLR version 2 activation policy decisions (for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../configure-apps/file-schema/startup/startup-element.md) in the configuration file), this method does not return an error result; instead, the result is S_OK, just as it would be if the method had successfully bound legacy activation policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a10c-115">要件</span><span class="sxs-lookup"><span data-stu-id="7a10c-115">Requirements</span></span>  

 <span data-ttu-id="7a10c-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a10c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a10c-117">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="7a10c-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7a10c-118">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="7a10c-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7a10c-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a10c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a10c-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a10c-120">See also</span></span>

- [<span data-ttu-id="7a10c-121">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7a10c-121">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="7a10c-122">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7a10c-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="7a10c-123">ホスティング</span><span class="sxs-lookup"><span data-stu-id="7a10c-123">Hosting</span></span>](index.md)
- [<span data-ttu-id="7a10c-124">\<startup> 要素</span><span class="sxs-lookup"><span data-stu-id="7a10c-124">\<startup> Element</span></span>](../../configure-apps/file-schema/startup/startup-element.md)
