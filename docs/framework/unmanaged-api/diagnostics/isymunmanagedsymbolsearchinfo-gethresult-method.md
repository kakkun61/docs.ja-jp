---
title: ISymUnmanagedSymbolSearchInfo::GetHRESULT メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetHRESULT
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT method [.NET Framework debugging]
- GetHRESULT method [.NET Framework debugging]
ms.assetid: 6999dc3d-65d7-4bf6-bb0a-6efc0fc72588
topic_type:
- apiref
ms.openlocfilehash: a931c15b1c4a9f099d11c43edd324cfcc2793090
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722272"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="17839-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT メソッド</span><span class="sxs-lookup"><span data-stu-id="17839-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>

<span data-ttu-id="17839-103">HRESULT を取得します。</span><span class="sxs-lookup"><span data-stu-id="17839-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17839-104">構文</span><span class="sxs-lookup"><span data-stu-id="17839-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17839-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="17839-105">Parameters</span></span>  

 `phr`  
 <span data-ttu-id="17839-106">入出力HRESULT へのポインター。</span><span class="sxs-lookup"><span data-stu-id="17839-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17839-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="17839-107">Return Value</span></span>  

 <span data-ttu-id="17839-108">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="17839-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17839-109">要件</span><span class="sxs-lookup"><span data-stu-id="17839-109">Requirements</span></span>  

 <span data-ttu-id="17839-110">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="17839-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17839-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="17839-111">See also</span></span>

- [<span data-ttu-id="17839-112">ISymUnmanagedSymbolSearchInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="17839-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)
