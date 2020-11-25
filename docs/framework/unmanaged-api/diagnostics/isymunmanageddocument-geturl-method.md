---
title: ISymUnmanagedDocument::GetURL メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetURL
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetURL
helpviewer_keywords:
- GetURL method [.NET Framework debugging]
- ISymUnmanagedDocument::GetURL method [.NET Framework debugging]
ms.assetid: 60600178-c2b5-4cab-b3a5-f0f61acebaf1
topic_type:
- apiref
ms.openlocfilehash: c862b6d3bfa415b622b68898db1ff30c6759e8f2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726939"
---
# <a name="isymunmanageddocumentgeturl-method"></a><span data-ttu-id="77183-102">ISymUnmanagedDocument::GetURL メソッド</span><span class="sxs-lookup"><span data-stu-id="77183-102">ISymUnmanagedDocument::GetURL Method</span></span>

<span data-ttu-id="77183-103">このドキュメントの URL (uniform resource locator) を返します。</span><span class="sxs-lookup"><span data-stu-id="77183-103">Returns the uniform resource locator (URL) for this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77183-104">構文</span><span class="sxs-lookup"><span data-stu-id="77183-104">Syntax</span></span>  
  
```cpp  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77183-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="77183-105">Parameters</span></span>  

 `cchUrl`  
 <span data-ttu-id="77183-106">[入力] `szURL` バッファーのサイズ (文字単位)。</span><span class="sxs-lookup"><span data-stu-id="77183-106">[in] The size, in characters, of the `szURL` buffer.</span></span>  
  
 `pcchUrl`  
 <span data-ttu-id="77183-107">入出力Null 終了を含む、URL のサイズを受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="77183-107">[out] A pointer to a variable that receives the size of the URL, including the null termination.</span></span>  
  
 `szUrl`  
 <span data-ttu-id="77183-108">入出力URL を格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="77183-108">[out] The buffer containing the URL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77183-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="77183-109">Return Value</span></span>  

 <span data-ttu-id="77183-110">メソッドが成功した場合は S_OK。それ以外の場合は、エラーコード。</span><span class="sxs-lookup"><span data-stu-id="77183-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77183-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="77183-111">See also</span></span>

- [<span data-ttu-id="77183-112">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="77183-112">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
