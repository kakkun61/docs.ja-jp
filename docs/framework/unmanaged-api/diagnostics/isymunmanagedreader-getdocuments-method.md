---
title: ISymUnmanagedReader::GetDocuments メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocuments
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocuments
helpviewer_keywords:
- GetDocuments method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocuments method [.NET Framework debugging]
ms.assetid: e3b73a3f-d089-4101-a9a9-5e0765d05b61
topic_type:
- apiref
ms.openlocfilehash: 757b7fecbbb187da079c8a5c51462ec58431966f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707621"
---
# <a name="isymunmanagedreadergetdocuments-method"></a><span data-ttu-id="fb497-102">ISymUnmanagedReader::GetDocuments メソッド</span><span class="sxs-lookup"><span data-stu-id="fb497-102">ISymUnmanagedReader::GetDocuments Method</span></span>

<span data-ttu-id="fb497-103">シンボルストアに定義されているすべてのドキュメントの配列を返します。</span><span class="sxs-lookup"><span data-stu-id="fb497-103">Returns an array of all the documents defined in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb497-104">構文</span><span class="sxs-lookup"><span data-stu-id="fb497-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocuments (  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,  
    [out, size_is (cDocs),  
        length_is (*pcDocs)] ISymUnmanagedDocument *pDocs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb497-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fb497-105">Parameters</span></span>  

 `cDocs`  
 <span data-ttu-id="fb497-106">[in] `pDocs` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="fb497-106">[in] The size of the `pDocs` array.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="fb497-107">入出力配列長を受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="fb497-107">[out] A pointer to a variable that receives the array length.</span></span>  
  
 `pDocs`  
 <span data-ttu-id="fb497-108">入出力ドキュメント配列を受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="fb497-108">[out] A pointer to a variable that receives the document array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb497-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="fb497-109">Return Value</span></span>  

 <span data-ttu-id="fb497-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="fb497-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb497-111">要件</span><span class="sxs-lookup"><span data-stu-id="fb497-111">Requirements</span></span>  

 <span data-ttu-id="fb497-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="fb497-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb497-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="fb497-113">See also</span></span>

- [<span data-ttu-id="fb497-114">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fb497-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
