---
title: ISymENCUnmanagedMethod::GetDocumentsForMethodCount メソッド
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetDocumentsForMethodCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetDocumentsForMethodCount
helpviewer_keywords:
- GetDocumentsForMethodCount method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetDocumentsForMethodCount method [.NET Framework debugging]
ms.assetid: cc1a823a-3ff3-4a33-b641-96edc93d2b17
topic_type:
- apiref
ms.openlocfilehash: 53897b6f964afb1f8ca95bc8f93c532e148ad129
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730514"
---
# <a name="isymencunmanagedmethodgetdocumentsformethodcount-method"></a><span data-ttu-id="512d7-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount メソッド</span><span class="sxs-lookup"><span data-stu-id="512d7-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount Method</span></span>

<span data-ttu-id="512d7-103">このメソッドに行があるドキュメントの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="512d7-103">Gets the number of documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="512d7-104">構文</span><span class="sxs-lookup"><span data-stu-id="512d7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethodCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="512d7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="512d7-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="512d7-106">入出力 `ULONG32` ドキュメントを格納するために必要なバッファーのサイズを受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="512d7-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="512d7-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="512d7-107">Return Value</span></span>  

 <span data-ttu-id="512d7-108">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="512d7-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="512d7-109">要件</span><span class="sxs-lookup"><span data-stu-id="512d7-109">Requirements</span></span>  

 <span data-ttu-id="512d7-110">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="512d7-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="512d7-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="512d7-111">See also</span></span>

- [<span data-ttu-id="512d7-112">ISymENCUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="512d7-112">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
