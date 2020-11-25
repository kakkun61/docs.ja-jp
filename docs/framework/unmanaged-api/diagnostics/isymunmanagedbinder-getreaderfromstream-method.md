---
title: ISymUnmanagedBinder::GetReaderFromStream メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderFromStream
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderFromStream
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderFromStream method [.NET Framework debugging]
- GetReaderFromStream method [.NET Framework debugging]
ms.assetid: aa38efd4-de7e-4482-a5d3-adc152093460
topic_type:
- apiref
ms.openlocfilehash: 2d927b02b7deebecb53a2218e2ec0275a07307b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706958"
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a><span data-ttu-id="28e80-102">ISymUnmanagedBinder::GetReaderFromStream メソッド</span><span class="sxs-lookup"><span data-stu-id="28e80-102">ISymUnmanagedBinder::GetReaderFromStream Method</span></span>

<span data-ttu-id="28e80-103">メタデータインターフェイスと、シンボルストアを含むストリームが指定された場合、は、指定されたシンボルストアからデバッグシンボルを読み取る正しい [ISymUnmanagedReader](isymunmanagedreader-interface.md) 構造体を返します。</span><span class="sxs-lookup"><span data-stu-id="28e80-103">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28e80-104">構文</span><span class="sxs-lookup"><span data-stu-id="28e80-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28e80-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="28e80-105">Parameters</span></span>  

 `importer`  
 <span data-ttu-id="28e80-106">からメタデータインポートインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="28e80-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `pstream`  
 <span data-ttu-id="28e80-107">からシンボルストアが格納されているストリームへのポインター。</span><span class="sxs-lookup"><span data-stu-id="28e80-107">[in] A pointer to the stream that contains the symbol store.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="28e80-108">入出力返された [ISymUnmanagedReader](isymunmanagedreader-interface.md) インターフェイスに設定されたポインター。</span><span class="sxs-lookup"><span data-stu-id="28e80-108">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28e80-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="28e80-109">Return Value</span></span>  

 <span data-ttu-id="28e80-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="28e80-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28e80-111">要件</span><span class="sxs-lookup"><span data-stu-id="28e80-111">Requirements</span></span>  

 <span data-ttu-id="28e80-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="28e80-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28e80-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="28e80-113">See also</span></span>

- [<span data-ttu-id="28e80-114">ISymUnmanagedBinder インターフェイス</span><span class="sxs-lookup"><span data-stu-id="28e80-114">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
