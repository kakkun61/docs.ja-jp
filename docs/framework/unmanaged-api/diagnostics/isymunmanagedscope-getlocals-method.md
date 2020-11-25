---
title: ISymUnmanagedScope::GetLocals メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocals
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocals
helpviewer_keywords:
- GetLocals method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocals method [.NET Framework debugging]
ms.assetid: 17c45f15-8c44-44da-b070-f902077b36e4
topic_type:
- apiref
ms.openlocfilehash: 3a2045466340f92dd8421090c74a442068e8bfaf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731411"
---
# <a name="isymunmanagedscopegetlocals-method"></a><span data-ttu-id="fae7f-102">ISymUnmanagedScope::GetLocals メソッド</span><span class="sxs-lookup"><span data-stu-id="fae7f-102">ISymUnmanagedScope::GetLocals Method</span></span>

<span data-ttu-id="fae7f-103">このスコープ内で定義されているローカル変数を取得します。</span><span class="sxs-lookup"><span data-stu-id="fae7f-103">Gets the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fae7f-104">構文</span><span class="sxs-lookup"><span data-stu-id="fae7f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocals(  
    [in]  ULONG32  cLocals,  
    [out] ULONG32  *pcLocals,  
    [out, size_is(cLocals),  
        length_is(*pcLocals)] ISymUnmanagedVariable* locals[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fae7f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fae7f-105">Parameters</span></span>  

 `cLocals`  
 <span data-ttu-id="fae7f-106">から `ULONG32` 配列のサイズを示す `locals` 。</span><span class="sxs-lookup"><span data-stu-id="fae7f-106">[in] A `ULONG32` that indicates the size of the `locals` array.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="fae7f-107">入出力 `ULONG32` ローカル変数を格納するために必要なバッファーのサイズを受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fae7f-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the local variables.</span></span>  
  
 `locals`  
 <span data-ttu-id="fae7f-108">入出力ローカル変数を受け取る配列。</span><span class="sxs-lookup"><span data-stu-id="fae7f-108">[out] The array that receives the local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fae7f-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="fae7f-109">Return Value</span></span>  

 <span data-ttu-id="fae7f-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="fae7f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fae7f-111">要件</span><span class="sxs-lookup"><span data-stu-id="fae7f-111">Requirements</span></span>  

 <span data-ttu-id="fae7f-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="fae7f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fae7f-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="fae7f-113">See also</span></span>

- [<span data-ttu-id="fae7f-114">ISymUnmanagedScope インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fae7f-114">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
