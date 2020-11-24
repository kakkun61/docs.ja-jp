---
title: ISymUnmanagedDocument::GetDocumentType メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetDocumentType
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetDocumentType
helpviewer_keywords:
- ISymUnmanagedDocument::GetDocumentType method [.NET Framework debugging]
- GetDocumentType method [.NET Framework debugging]
ms.assetid: 2d381ab1-7e7c-4281-af2b-e54d879b3ef8
topic_type:
- apiref
ms.openlocfilehash: d30ee9318d76aaf3ad2cde789ae292aed54f457e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689681"
---
# <a name="isymunmanageddocumentgetdocumenttype-method"></a><span data-ttu-id="750ba-102">ISymUnmanagedDocument::GetDocumentType メソッド</span><span class="sxs-lookup"><span data-stu-id="750ba-102">ISymUnmanagedDocument::GetDocumentType Method</span></span>

<span data-ttu-id="750ba-103">このドキュメントのドキュメントの種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="750ba-103">Gets the document type of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="750ba-104">構文</span><span class="sxs-lookup"><span data-stu-id="750ba-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentType(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="750ba-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="750ba-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="750ba-106">入出力ドキュメント型を受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="750ba-106">[out] Pointer to a variable that receives the document type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="750ba-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="750ba-107">Return Value</span></span>  

 <span data-ttu-id="750ba-108">メソッドが成功した場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="750ba-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="750ba-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="750ba-109">See also</span></span>

- [<span data-ttu-id="750ba-110">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="750ba-110">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
