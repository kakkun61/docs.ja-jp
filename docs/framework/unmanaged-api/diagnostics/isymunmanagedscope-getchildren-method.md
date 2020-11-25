---
title: ISymUnmanagedScope::GetChildren メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetChildren
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetChildren
helpviewer_keywords:
- ISymUnmanagedScope::GetChildren method [.NET Framework debugging]
- GetChildren method [.NET Framework debugging]
ms.assetid: 0bed524e-cc48-4bf0-b9fa-25d665e63ddb
topic_type:
- apiref
ms.openlocfilehash: 8f3c83a7a89553ba600f3e0e368eec0ddd0350e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727610"
---
# <a name="isymunmanagedscopegetchildren-method"></a><span data-ttu-id="28dba-102">ISymUnmanagedScope::GetChildren メソッド</span><span class="sxs-lookup"><span data-stu-id="28dba-102">ISymUnmanagedScope::GetChildren Method</span></span>

<span data-ttu-id="28dba-103">このスコープの子を取得します。</span><span class="sxs-lookup"><span data-stu-id="28dba-103">Gets the children of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28dba-104">構文</span><span class="sxs-lookup"><span data-stu-id="28dba-104">Syntax</span></span>  
  
```cpp  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28dba-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="28dba-105">Parameters</span></span>  

 `cChildren`  
 <span data-ttu-id="28dba-106">から `ULONG32` 配列のサイズを示す `children` 。</span><span class="sxs-lookup"><span data-stu-id="28dba-106">[in] A `ULONG32` that indicates the size of the `children` array.</span></span>  
  
 `pcChildren`  
 <span data-ttu-id="28dba-107">入出力 `ULONG32` 子を格納するために必要なバッファーのサイズを受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="28dba-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the children.</span></span>  
  
 `children`  
 <span data-ttu-id="28dba-108">入出力返された子の配列。</span><span class="sxs-lookup"><span data-stu-id="28dba-108">[out] The returned array of children.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28dba-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="28dba-109">Return Value</span></span>  

 <span data-ttu-id="28dba-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="28dba-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28dba-111">要件</span><span class="sxs-lookup"><span data-stu-id="28dba-111">Requirements</span></span>  

 <span data-ttu-id="28dba-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="28dba-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28dba-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="28dba-113">See also</span></span>

- [<span data-ttu-id="28dba-114">ISymUnmanagedScope インターフェイス</span><span class="sxs-lookup"><span data-stu-id="28dba-114">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="28dba-115">GetParent メソッド</span><span class="sxs-lookup"><span data-stu-id="28dba-115">GetParent Method</span></span>](isymunmanagedscope-getparent-method.md)
