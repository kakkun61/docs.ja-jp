---
title: ISymUnmanagedDocument::HasEmbeddedSource メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.HasEmbeddedSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::HasEmbeddedSource
helpviewer_keywords:
- HasEmbeddedSource method [.NET Framework debugging]
- ISymUnmanagedDocument::HasEmbeddedSource method [.NET Framework debugging]
ms.assetid: 385fc4d3-365c-4645-b7b0-6c4c5344b79f
topic_type:
- apiref
ms.openlocfilehash: 09bc0f87cd35f12a15566fb525c2ce42990ac69b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688199"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="e1709-102">ISymUnmanagedDocument::HasEmbeddedSource メソッド</span><span class="sxs-lookup"><span data-stu-id="e1709-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>

<span data-ttu-id="e1709-103">`true`ドキュメントがデバッグシンボルに埋め込まれている場合はを返します。それ以外の場合はを返し `false` ます。</span><span class="sxs-lookup"><span data-stu-id="e1709-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1709-104">構文</span><span class="sxs-lookup"><span data-stu-id="e1709-104">Syntax</span></span>  
  
```cpp  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1709-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e1709-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="e1709-106">入出力ドキュメントにデバッグシンボルに埋め込まれたソースがあるかどうかを示す変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e1709-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1709-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="e1709-107">Return Value</span></span>  

 <span data-ttu-id="e1709-108">メソッドが成功した場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="e1709-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1709-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="e1709-109">See also</span></span>

- [<span data-ttu-id="e1709-110">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e1709-110">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
