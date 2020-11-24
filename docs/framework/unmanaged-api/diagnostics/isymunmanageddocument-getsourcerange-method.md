---
title: ISymUnmanagedDocument::GetSourceRange メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceRange
helpviewer_keywords:
- ISymUnmanagedDocument::GetSourceRange method [.NET Framework debugging]
- GetSourceRange method [.NET Framework debugging]
ms.assetid: 20fefee7-1040-41ba-93dc-bd42f68b90c2
topic_type:
- apiref
ms.openlocfilehash: f5d7df60a7b9c728b73fe6592226a8b6734b1e66
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95692151"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a><span data-ttu-id="e98bb-102">ISymUnmanagedDocument::GetSourceRange メソッド</span><span class="sxs-lookup"><span data-stu-id="e98bb-102">ISymUnmanagedDocument::GetSourceRange Method</span></span>

<span data-ttu-id="e98bb-103">指定されたバッファーに、埋め込みソースの指定された範囲を返します。</span><span class="sxs-lookup"><span data-stu-id="e98bb-103">Returns the specified range of the embedded source into the given buffer.</span></span> <span data-ttu-id="e98bb-104">バッファーは、ソースを保持するのに十分な大きさである必要があります。</span><span class="sxs-lookup"><span data-stu-id="e98bb-104">The buffer must be large enough to hold the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e98bb-105">構文</span><span class="sxs-lookup"><span data-stu-id="e98bb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceRange(  
    [in]  ULONG32  startLine,  
    [in]  ULONG32  startColumn,  
    [in]  ULONG32  endLine,  
    [in]  ULONG32  endColumn,  
    [in]  ULONG32  cSourceBytes,  
    [out] ULONG32  *pcSourceBytes,  
    [out, size_is(cSourceBytes),  
        length_is(*pcSourceBytes)] BYTE source[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e98bb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e98bb-106">Parameters</span></span>  

 `startLine`  
 <span data-ttu-id="e98bb-107">から現在のドキュメントの開始行。</span><span class="sxs-lookup"><span data-stu-id="e98bb-107">[in] The starting line in the current document.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="e98bb-108">から現在のドキュメントの開始列。</span><span class="sxs-lookup"><span data-stu-id="e98bb-108">[in] The starting column in the current document.</span></span>  
  
 `endLine`  
 <span data-ttu-id="e98bb-109">から現在のドキュメントの最終行。</span><span class="sxs-lookup"><span data-stu-id="e98bb-109">[in] The final line in the current document.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="e98bb-110">から現在のドキュメントの最後の列。</span><span class="sxs-lookup"><span data-stu-id="e98bb-110">[in] The final column in the current document.</span></span>  
  
 `cSourceBytes`  
 <span data-ttu-id="e98bb-111">からソースのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="e98bb-111">[in] The size of the source, in bytes.</span></span>  
  
 `pcSourceBytes`  
 <span data-ttu-id="e98bb-112">入出力ソースサイズを受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e98bb-112">[out] A pointer to a variable that receives the source size.</span></span>  
  
 `source`  
 <span data-ttu-id="e98bb-113">入出力ソースドキュメントの指定した範囲のサイズと長さ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="e98bb-113">[out] The size and length of the specified range of the source document, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e98bb-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="e98bb-114">Return Value</span></span>  

 <span data-ttu-id="e98bb-115">メソッドが成功した場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="e98bb-115">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e98bb-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="e98bb-116">See also</span></span>

- [<span data-ttu-id="e98bb-117">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e98bb-117">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
