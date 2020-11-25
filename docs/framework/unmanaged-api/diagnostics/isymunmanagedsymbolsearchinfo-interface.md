---
title: ISymUnmanagedSymbolSearchInfo インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: 30817373-0a21-49c1-a0c4-8e8daeecb8db
topic_type:
- apiref
ms.openlocfilehash: 95ad3cbea4269173f22e662d15772ff97f7ee900
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705450"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="5df59-102">ISymUnmanagedSymbolSearchInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5df59-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>

<span data-ttu-id="5df59-103">検索パスに関する情報を取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="5df59-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="5df59-104">このインターフェイスを取得するには `QueryInterface` 、 [ISymUnmanagedReader](isymunmanagedreader-interface.md) インターフェイスを実装するオブジェクトに対してを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5df59-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5df59-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="5df59-105">Methods</span></span>  
  
|<span data-ttu-id="5df59-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="5df59-106">Method</span></span>|<span data-ttu-id="5df59-107">説明</span><span class="sxs-lookup"><span data-stu-id="5df59-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5df59-108">GetHRESULT メソッド</span><span class="sxs-lookup"><span data-stu-id="5df59-108">GetHRESULT Method</span></span>](isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="5df59-109">HRESULT を取得します。</span><span class="sxs-lookup"><span data-stu-id="5df59-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="5df59-110">GetSearchPath メソッド</span><span class="sxs-lookup"><span data-stu-id="5df59-110">GetSearchPath Method</span></span>](isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="5df59-111">検索パスを取得します。</span><span class="sxs-lookup"><span data-stu-id="5df59-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="5df59-112">GetSearchPathLength メソッド</span><span class="sxs-lookup"><span data-stu-id="5df59-112">GetSearchPathLength Method</span></span>](isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="5df59-113">検索パスの長さを取得します。</span><span class="sxs-lookup"><span data-stu-id="5df59-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5df59-114">要件</span><span class="sxs-lookup"><span data-stu-id="5df59-114">Requirements</span></span>  

 <span data-ttu-id="5df59-115">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="5df59-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5df59-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="5df59-116">See also</span></span>

- [<span data-ttu-id="5df59-117">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5df59-117">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
