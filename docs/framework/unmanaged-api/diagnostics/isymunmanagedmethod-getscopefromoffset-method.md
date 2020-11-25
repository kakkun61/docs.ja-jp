---
title: ISymUnmanagedMethod::GetScopeFromOffset メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetScopeFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetScopeFromOffset
helpviewer_keywords:
- GetScopeFromOffset method [.NET Framework debugging]
- ISymUnmanagedMethod::GetScopeFromOffset method [.NET Framework debugging]
ms.assetid: d14cf210-81f8-46e1-8b19-6ddec0ba8b11
topic_type:
- apiref
ms.openlocfilehash: cf2784ce0ac6e614e75a341660808b9fe03ada0e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699444"
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="f1cf5-102">ISymUnmanagedMethod::GetScopeFromOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="f1cf5-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>

<span data-ttu-id="f1cf5-103">指定されたオフセットを囲む、このメソッド内で最も外側にある構文のスコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="f1cf5-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="f1cf5-104">これは、ローカル変数の検索を開始するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="f1cf5-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1cf5-105">構文</span><span class="sxs-lookup"><span data-stu-id="f1cf5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1cf5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f1cf5-106">Parameters</span></span>  

 `offset`  
 <span data-ttu-id="f1cf5-107">から `ULONG` オフセットを格納している。</span><span class="sxs-lookup"><span data-stu-id="f1cf5-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="f1cf5-108">入出力返された [ISymUnmanagedScope](isymunmanagedscope-interface.md) インターフェイスに設定されたポインター。</span><span class="sxs-lookup"><span data-stu-id="f1cf5-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1cf5-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="f1cf5-109">Return Value</span></span>  

 <span data-ttu-id="f1cf5-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="f1cf5-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1cf5-111">要件</span><span class="sxs-lookup"><span data-stu-id="f1cf5-111">Requirements</span></span>  

 <span data-ttu-id="f1cf5-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="f1cf5-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1cf5-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1cf5-113">See also</span></span>

- [<span data-ttu-id="f1cf5-114">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1cf5-114">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
