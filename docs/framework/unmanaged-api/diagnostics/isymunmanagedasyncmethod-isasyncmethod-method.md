---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod メソッド
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
ms.openlocfilehash: af02aba1a0d390c103e8c6108f90b93fe2a98ff3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707153"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="8c4de-102">ISymUnmanagedAsyncMethod::IsAsyncMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="8c4de-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>

<span data-ttu-id="8c4de-103">メソッドに非同期情報があるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="8c4de-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="8c4de-104">このメソッドがを返す場合 `FALSE` 、このインターフェイス内の他のメソッドを呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="8c4de-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="8c4de-105">これらはすべて、 `E_UNEXPECTED` この場合はを返します。</span><span class="sxs-lookup"><span data-stu-id="8c4de-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c4de-106">構文</span><span class="sxs-lookup"><span data-stu-id="8c4de-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c4de-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c4de-107">Parameters</span></span>  
  
|<span data-ttu-id="8c4de-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c4de-108">Parameter</span></span>|<span data-ttu-id="8c4de-109">説明</span><span class="sxs-lookup"><span data-stu-id="8c4de-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="8c4de-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c4de-110">Return Value</span></span>  

 <span data-ttu-id="8c4de-111">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="8c4de-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c4de-112">要件</span><span class="sxs-lookup"><span data-stu-id="8c4de-112">Requirements</span></span>  

 <span data-ttu-id="8c4de-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="8c4de-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c4de-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c4de-114">See also</span></span>

- [<span data-ttu-id="8c4de-115">ISymUnmanagedAsyncMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c4de-115">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)
