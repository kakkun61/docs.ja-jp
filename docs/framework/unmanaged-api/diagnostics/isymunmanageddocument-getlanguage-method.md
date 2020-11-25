---
title: ISymUnmanagedDocument::GetLanguage メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetLanguage
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetLanguage
helpviewer_keywords:
- ISymUnmanagedDocument::GetLanguage method [.NET Framework debugging]
- GetLanguage method [.NET Framework debugging]
ms.assetid: c6639418-e9f2-4a99-8ce2-ec9876e0bc79
topic_type:
- apiref
ms.openlocfilehash: 075d46b0bbc68add0203daf7430afb712c998fe0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700978"
---
# <a name="isymunmanageddocumentgetlanguage-method"></a><span data-ttu-id="beb8c-102">ISymUnmanagedDocument::GetLanguage メソッド</span><span class="sxs-lookup"><span data-stu-id="beb8c-102">ISymUnmanagedDocument::GetLanguage Method</span></span>

<span data-ttu-id="beb8c-103">このドキュメントの言語識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="beb8c-103">Gets the language identifier of this document</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beb8c-104">構文</span><span class="sxs-lookup"><span data-stu-id="beb8c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLanguage(  
    [out, retval]  GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="beb8c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="beb8c-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="beb8c-106">入出力言語識別子を受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="beb8c-106">[out] A pointer to a variable that receives the language identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="beb8c-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="beb8c-107">Return Value</span></span>  

 <span data-ttu-id="beb8c-108">メソッドが成功した場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="beb8c-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beb8c-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="beb8c-109">See also</span></span>

- [<span data-ttu-id="beb8c-110">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="beb8c-110">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
