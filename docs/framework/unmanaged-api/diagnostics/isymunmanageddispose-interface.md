---
title: ISymUnmanagedDispose インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDispose
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDispose
helpviewer_keywords:
- ISymUnmanagedDispose interface [.NET Framework debugging]
ms.assetid: b1d74e83-a200-4d00-8fbd-27918808616d
topic_type:
- apiref
ms.openlocfilehash: 932e76e73d5d40b36abcb17d8a53e6745927d873
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719607"
---
# <a name="isymunmanageddispose-interface"></a><span data-ttu-id="a661b-102">ISymUnmanagedDispose インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a661b-102">ISymUnmanagedDispose Interface</span></span>

<span data-ttu-id="a661b-103">アンマネージリソースを破棄します。</span><span class="sxs-lookup"><span data-stu-id="a661b-103">Disposes of unmanaged resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a661b-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="a661b-104">Methods</span></span>  
  
|<span data-ttu-id="a661b-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a661b-105">Method</span></span>|<span data-ttu-id="a661b-106">説明</span><span class="sxs-lookup"><span data-stu-id="a661b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a661b-107">destroy メソッド</span><span class="sxs-lookup"><span data-stu-id="a661b-107">Destroy Method</span></span>](isymunmanageddispose-destroy-method.md)|<span data-ttu-id="a661b-108">基になるオブジェクトがすべての内部参照を解放し、後続のメソッド呼び出しの失敗を返します。</span><span class="sxs-lookup"><span data-stu-id="a661b-108">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a661b-109">要件</span><span class="sxs-lookup"><span data-stu-id="a661b-109">Requirements</span></span>  

 <span data-ttu-id="a661b-110">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="a661b-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a661b-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="a661b-111">See also</span></span>

- [<span data-ttu-id="a661b-112">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a661b-112">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
