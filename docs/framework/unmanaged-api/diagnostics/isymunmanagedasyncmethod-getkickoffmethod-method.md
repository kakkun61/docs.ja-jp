---
title: ISymUnmanagedAsyncMethod::GetKickoffMethod メソッド
ms.date: 03/30/2017
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
ms.openlocfilehash: 2d4515087812b2b7c9303228ac5e5bbf34e8aa91
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707192"
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="20fda-102">ISymUnmanagedAsyncMethod::GetKickoffMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="20fda-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>

<span data-ttu-id="20fda-103">「 [DefineKickoffMethod メソッド](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20fda-103">See [DefineKickoffMethod Method](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20fda-104">構文</span><span class="sxs-lookup"><span data-stu-id="20fda-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20fda-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="20fda-105">Parameters</span></span>  
  
|<span data-ttu-id="20fda-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="20fda-106">Parameter</span></span>|<span data-ttu-id="20fda-107">説明</span><span class="sxs-lookup"><span data-stu-id="20fda-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="20fda-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="20fda-108">Return Value</span></span>  

 <span data-ttu-id="20fda-109">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="20fda-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20fda-110">要件</span><span class="sxs-lookup"><span data-stu-id="20fda-110">Requirements</span></span>  

 <span data-ttu-id="20fda-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="20fda-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20fda-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="20fda-112">See also</span></span>

- [<span data-ttu-id="20fda-113">ISymUnmanagedAsyncMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="20fda-113">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)
