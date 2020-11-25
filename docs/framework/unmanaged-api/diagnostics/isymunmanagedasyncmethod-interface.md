---
title: ISymUnmanagedAsyncMethod インターフェイス
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
ms.openlocfilehash: 02b1866f2b9e89cdc8c8795f399ecc0c733c7202
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707166"
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="58e1b-102">ISymUnmanagedAsyncMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="58e1b-102">ISymUnmanagedAsyncMethod Interface</span></span>

<span data-ttu-id="58e1b-103">このインターフェイスは、 [ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス](isymunmanagedasyncmethodpropertieswriter-interface.md)への読み取り補数です。</span><span class="sxs-lookup"><span data-stu-id="58e1b-103">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58e1b-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="58e1b-104">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="58e1b-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="58e1b-105">Methods</span></span>  

 <span data-ttu-id="58e1b-106">このインターフェイスには、次のメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="58e1b-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="58e1b-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="58e1b-107">Method</span></span>|<span data-ttu-id="58e1b-108">説明</span><span class="sxs-lookup"><span data-stu-id="58e1b-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="58e1b-109">GetAsyncStepInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="58e1b-109">GetAsyncStepInfo Method</span></span>](isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="58e1b-110">「 [DefineAsyncStepInfo メソッド](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58e1b-110">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="58e1b-111">GetAsyncStepInfoCount メソッド</span><span class="sxs-lookup"><span data-stu-id="58e1b-111">GetAsyncStepInfoCount Method</span></span>](isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="58e1b-112">「 [DefineAsyncStepInfo メソッド](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58e1b-112">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="58e1b-113">GetCatchHandlerILOffSet メソッド</span><span class="sxs-lookup"><span data-stu-id="58e1b-113">GetCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="58e1b-114">「 [DefineCatchHandlerILOffset メソッド](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58e1b-114">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="58e1b-115">GetKickoffMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="58e1b-115">GetKickoffMethod Method</span></span>](isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="58e1b-116">「 [DefineKickoffMethod メソッド](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58e1b-116">See [DefineKickoffMethod Method](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="58e1b-117">HasCatchHandlerILOffSet メソッド</span><span class="sxs-lookup"><span data-stu-id="58e1b-117">HasCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="58e1b-118">「 [DefineCatchHandlerILOffset メソッド](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58e1b-118">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="58e1b-119">IsAsyncMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="58e1b-119">IsAsyncMethod Method</span></span>](isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="58e1b-120">メソッドに非同期情報があるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="58e1b-120">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="58e1b-121">このメソッドがを返す場合 `FALSE` 、このインターフェイス内の他のメソッドを呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="58e1b-121">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="58e1b-122">これらはすべて、 `E_UNEXPECTED` この場合はを返します。</span><span class="sxs-lookup"><span data-stu-id="58e1b-122">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="58e1b-123">要件</span><span class="sxs-lookup"><span data-stu-id="58e1b-123">Requirements</span></span>  

 <span data-ttu-id="58e1b-124">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="58e1b-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58e1b-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="58e1b-125">See also</span></span>

- [<span data-ttu-id="58e1b-126">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="58e1b-126">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
