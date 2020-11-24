---
title: ISymUnmanagedDocumentWriter::SetSource メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetSource
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetSource method [.NET Framework debugging]
- SetSource method [.NET Framework debugging]
ms.assetid: ea5b9d9f-ff06-4bd3-8de5-6435343aba59
topic_type:
- apiref
ms.openlocfilehash: 31475b08b569b925aab9cab869545f0912c4ecf8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95691592"
---
# <a name="isymunmanageddocumentwritersetsource-method"></a><span data-ttu-id="4478f-102">ISymUnmanagedDocumentWriter::SetSource メソッド</span><span class="sxs-lookup"><span data-stu-id="4478f-102">ISymUnmanagedDocumentWriter::SetSource Method</span></span>

<span data-ttu-id="4478f-103">書き込まれるドキュメントの埋め込み元を設定します。</span><span class="sxs-lookup"><span data-stu-id="4478f-103">Sets embedded source for a document that is being written.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4478f-104">構文</span><span class="sxs-lookup"><span data-stu-id="4478f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4478f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4478f-105">Parameters</span></span>  

 `sourceSize`  
 <span data-ttu-id="4478f-106">から `ULONG32` バッファーのサイズを格納している `source` 。</span><span class="sxs-lookup"><span data-stu-id="4478f-106">[in] A `ULONG32` that contains the size of the `source` buffer.</span></span>  
  
 `source`  
 <span data-ttu-id="4478f-107">から埋め込みソースを格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="4478f-107">[in] The buffer that stores the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4478f-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="4478f-108">Return Value</span></span>  

 <span data-ttu-id="4478f-109">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="4478f-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4478f-110">要件</span><span class="sxs-lookup"><span data-stu-id="4478f-110">Requirements</span></span>  

 <span data-ttu-id="4478f-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="4478f-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4478f-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="4478f-112">See also</span></span>

- [<span data-ttu-id="4478f-113">ISymUnmanagedDocumentWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4478f-113">ISymUnmanagedDocumentWriter Interface</span></span>](isymunmanageddocumentwriter-interface.md)
