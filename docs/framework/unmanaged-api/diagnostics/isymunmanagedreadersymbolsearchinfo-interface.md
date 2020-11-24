---
title: ISymUnmanagedReaderSymbolSearchInfo インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo
helpviewer_keywords:
- ISymUnmanagedReaderSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: fde7e21d-1169-4bed-a34d-792e69652bf9
topic_type:
- apiref
ms.openlocfilehash: af4124aed823a0a2475a181efe3fa68e1fae0bfe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678390"
---
# <a name="isymunmanagedreadersymbolsearchinfo-interface"></a><span data-ttu-id="b2bb8-102">ISymUnmanagedReaderSymbolSearchInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b2bb8-102">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>

<span data-ttu-id="b2bb8-103">シンボル検索情報を取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="b2bb8-103">Provides methods that get symbol search information.</span></span> <span data-ttu-id="b2bb8-104">このインターフェイスを取得するには `QueryInterface` 、 [ISymUnmanagedReader](isymunmanagedreader-interface.md) インターフェイスを実装するオブジェクトに対してを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b2bb8-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b2bb8-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="b2bb8-105">Methods</span></span>  
  
|<span data-ttu-id="b2bb8-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="b2bb8-106">Method</span></span>|<span data-ttu-id="b2bb8-107">説明</span><span class="sxs-lookup"><span data-stu-id="b2bb8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b2bb8-108">GetSymbolSearchInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="b2bb8-108">GetSymbolSearchInfo Method</span></span>](isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfo-method.md)|<span data-ttu-id="b2bb8-109">シンボルの検索情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="b2bb8-109">Gets symbol search information.</span></span>|  
|[<span data-ttu-id="b2bb8-110">GetSymbolSearchInfoCount メソッド</span><span class="sxs-lookup"><span data-stu-id="b2bb8-110">GetSymbolSearchInfoCount Method</span></span>](isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfocount-method.md)|<span data-ttu-id="b2bb8-111">シンボル検索情報の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="b2bb8-111">Gets a count of symbol search information.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2bb8-112">要件</span><span class="sxs-lookup"><span data-stu-id="b2bb8-112">Requirements</span></span>  

 <span data-ttu-id="b2bb8-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="b2bb8-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2bb8-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2bb8-114">See also</span></span>

- [<span data-ttu-id="b2bb8-115">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b2bb8-115">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
