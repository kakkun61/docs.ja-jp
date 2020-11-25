---
title: ISymUnmanagedAsyncMethod::GetAsyncStepInfo メソッド
ms.date: 03/30/2017
ms.assetid: 3ef5b4b8-4ac7-4906-849b-f932c5e3db07
ms.openlocfilehash: f9392dae4119e59b4eb0fdb87e2b334b32b77109
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707257"
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfo-method"></a><span data-ttu-id="e5d56-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="e5d56-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Method</span></span>

<span data-ttu-id="e5d56-103">「 [DefineAsyncStepInfo メソッド](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5d56-103">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5d56-104">構文</span><span class="sxs-lookup"><span data-stu-id="e5d56-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfo(    [in] ULONG32 cStepInfo,    [out] ULONG32 *pcStepInfo,    [in, size_is(cStepInfo)] ULONG32 yieldOffsets[],    [in, size_is(cStepInfo)] ULONG32 breakpointOffset[],    [in, size_is(cStepInfo)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5d56-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e5d56-105">Parameters</span></span>  
  
|<span data-ttu-id="e5d56-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e5d56-106">Parameter</span></span>|<span data-ttu-id="e5d56-107">説明</span><span class="sxs-lookup"><span data-stu-id="e5d56-107">Description</span></span>|  
|---------------|-----------------|  
|`cStepInfo`||  
|`pcStepInfo`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="e5d56-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="e5d56-108">Return Value</span></span>  

 <span data-ttu-id="e5d56-109">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="e5d56-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5d56-110">要件</span><span class="sxs-lookup"><span data-stu-id="e5d56-110">Requirements</span></span>  

 <span data-ttu-id="e5d56-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="e5d56-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5d56-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="e5d56-112">See also</span></span>

- [<span data-ttu-id="e5d56-113">ISymUnmanagedAsyncMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e5d56-113">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)
