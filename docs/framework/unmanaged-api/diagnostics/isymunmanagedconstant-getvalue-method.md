---
title: ISymUnmanagedConstant::GetValue メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetValue
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetValue
helpviewer_keywords:
- GetValue method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetValue method [.NET Framework debugging]
ms.assetid: 0036fc10-e768-47a8-b9cf-bf47faf8d194
topic_type:
- apiref
ms.openlocfilehash: 7a1c795f4a162699078e91bcaa274253169234e7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732841"
---
# <a name="isymunmanagedconstantgetvalue-method"></a><span data-ttu-id="2bcd5-102">ISymUnmanagedConstant::GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="2bcd5-102">ISymUnmanagedConstant::GetValue Method</span></span>

<span data-ttu-id="2bcd5-103">定数の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="2bcd5-103">Gets the value of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bcd5-104">構文</span><span class="sxs-lookup"><span data-stu-id="2bcd5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2bcd5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2bcd5-105">Parameters</span></span>  

 `pValue`  
 <span data-ttu-id="2bcd5-106">入出力値を受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="2bcd5-106">[out] A pointer to a variable that receives the value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2bcd5-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="2bcd5-107">Return Value</span></span>  

 <span data-ttu-id="2bcd5-108">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="2bcd5-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bcd5-109">要件</span><span class="sxs-lookup"><span data-stu-id="2bcd5-109">Requirements</span></span>  

 <span data-ttu-id="2bcd5-110">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="2bcd5-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bcd5-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="2bcd5-111">See also</span></span>

- [<span data-ttu-id="2bcd5-112">ISymUnmanagedConstant インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2bcd5-112">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="2bcd5-113">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="2bcd5-113">GetName Method</span></span>](isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="2bcd5-114">GetSignature メソッド</span><span class="sxs-lookup"><span data-stu-id="2bcd5-114">GetSignature Method</span></span>](isymunmanagedconstant-getsignature-method.md)
