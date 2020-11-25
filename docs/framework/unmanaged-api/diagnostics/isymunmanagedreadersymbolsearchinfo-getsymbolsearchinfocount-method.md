---
title: ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo.GetSymbolSearchInfoCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount
helpviewer_keywords:
- GetSymbolSearchInfoCount method [.NET Framework debugging]
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount method [.NET Framework debugging]
ms.assetid: 4068b6ec-525f-4446-8818-0296178cbd19
topic_type:
- apiref
ms.openlocfilehash: 5883b35bb3f1fec24ec108c9839501f0e81881fc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708869"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfocount-method"></a><span data-ttu-id="9abd2-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount メソッド</span><span class="sxs-lookup"><span data-stu-id="9abd2-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount Method</span></span>

<span data-ttu-id="9abd2-103">シンボル検索情報の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="9abd2-103">Gets a count of symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9abd2-104">構文</span><span class="sxs-lookup"><span data-stu-id="9abd2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolSearchInfoCount(  
    [out] ULONG32 *pcSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9abd2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9abd2-105">Parameters</span></span>  

 `pcSearchInfo`  
 <span data-ttu-id="9abd2-106">] out] `ULONG32` 検索情報を格納するために必要なバッファーのサイズを受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9abd2-106">]out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9abd2-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="9abd2-107">Return Value</span></span>  

 <span data-ttu-id="9abd2-108">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="9abd2-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9abd2-109">要件</span><span class="sxs-lookup"><span data-stu-id="9abd2-109">Requirements</span></span>  

 <span data-ttu-id="9abd2-110">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="9abd2-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9abd2-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="9abd2-111">See also</span></span>

- [<span data-ttu-id="9abd2-112">ISymUnmanagedReaderSymbolSearchInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9abd2-112">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)
