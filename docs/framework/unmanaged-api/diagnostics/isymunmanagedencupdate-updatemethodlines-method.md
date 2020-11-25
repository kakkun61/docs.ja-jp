---
title: ISymUnmanagedENCUpdate::UpdateMethodLines メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.UpdateMethodLines
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateMethodLines
helpviewer_keywords:
- UpdateMethodLines method [.NET Framework debugging]
- ISymUnmanagedENCUpdate::UpdateMethodLines method [.NET Framework debugging]
ms.assetid: 275ef87b-0b53-49f9-af6b-58506335dc06
topic_type:
- apiref
ms.openlocfilehash: 99499b8717f219616b6b368e6393b4b7ca0a79d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699587"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a><span data-ttu-id="9c1f3-102">ISymUnmanagedENCUpdate::UpdateMethodLines メソッド</span><span class="sxs-lookup"><span data-stu-id="9c1f3-102">ISymUnmanagedENCUpdate::UpdateMethodLines Method</span></span>

<span data-ttu-id="9c1f3-103">再コンパイルされていないが、行が個別に移動したメソッドの行情報を更新できるようにします。</span><span class="sxs-lookup"><span data-stu-id="9c1f3-103">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="9c1f3-104">各ステートメントのデルタが許可されます。</span><span class="sxs-lookup"><span data-stu-id="9c1f3-104">A delta for each statement is allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c1f3-105">構文</span><span class="sxs-lookup"><span data-stu-id="9c1f3-105">Syntax</span></span>  
  
```cpp  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c1f3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9c1f3-106">Parameters</span></span>  

 `mdMethodToken`  
 <span data-ttu-id="9c1f3-107">からメソッドトークンのメタデータ。</span><span class="sxs-lookup"><span data-stu-id="9c1f3-107">[in] The metadata of the method token.</span></span>  
  
 `pDeltas`  
 <span data-ttu-id="9c1f3-108">から `INT32` メソッド内の各シーケンスポイントのデルタを示す値の配列。</span><span class="sxs-lookup"><span data-stu-id="9c1f3-108">[in] An array of `INT32` values that indicates deltas for each sequence point in the method.</span></span>  
  
 `cDeltas`  
 <span data-ttu-id="9c1f3-109">から `ULONG` パラメーターのサイズを格納している `pDeltas` 。</span><span class="sxs-lookup"><span data-stu-id="9c1f3-109">[in] A `ULONG` containing the size of the `pDeltas` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c1f3-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="9c1f3-110">Return Value</span></span>  

 <span data-ttu-id="9c1f3-111">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="9c1f3-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c1f3-112">要件</span><span class="sxs-lookup"><span data-stu-id="9c1f3-112">Requirements</span></span>  

 <span data-ttu-id="9c1f3-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="9c1f3-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c1f3-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c1f3-114">See also</span></span>

- [<span data-ttu-id="9c1f3-115">ISymUnmanagedENCUpdate インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9c1f3-115">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
