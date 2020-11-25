---
title: ISymUnmanagedWriter5::CloseMapTokensToSourceSpans メソッド
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
ms.openlocfilehash: b57174f9f76b174927b8f1997beac3dd1482583a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725912"
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="a3b20-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans メソッド</span><span class="sxs-lookup"><span data-stu-id="a3b20-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>

<span data-ttu-id="a3b20-103">トークンとソースの間のマッピング情報については、特別なカスタムデータセクションを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a3b20-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="a3b20-104">閉じた後は、マッピング情報を追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="a3b20-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3b20-105">構文</span><span class="sxs-lookup"><span data-stu-id="a3b20-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a3b20-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="a3b20-106">Return Value</span></span>  

 <span data-ttu-id="a3b20-107">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="a3b20-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3b20-108">要件</span><span class="sxs-lookup"><span data-stu-id="a3b20-108">Requirements</span></span>  

 <span data-ttu-id="a3b20-109">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="a3b20-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3b20-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="a3b20-110">See also</span></span>

- [<span data-ttu-id="a3b20-111">ISymUnmanagedWriter5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a3b20-111">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
