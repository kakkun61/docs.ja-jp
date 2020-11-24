---
title: ISymUnmanagedWriter::SetMethodSourceRange メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetMethodSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetMethodSourceRange
helpviewer_keywords:
- SetMethodSourceRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetMethodSourceRange method [.NET Framework debugging]
ms.assetid: c698b86e-ace7-4b21-9549-f52d6a034959
topic_type:
- apiref
ms.openlocfilehash: a918b5c2334683348adc6a7382527faedb52d7b6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683538"
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a><span data-ttu-id="07af4-102">ISymUnmanagedWriter::SetMethodSourceRange メソッド</span><span class="sxs-lookup"><span data-stu-id="07af4-102">ISymUnmanagedWriter::SetMethodSourceRange Method</span></span>

<span data-ttu-id="07af4-103">ソース ファイル内にメソッドの実際の先頭と末尾を指定します。</span><span class="sxs-lookup"><span data-stu-id="07af4-103">Specifies the true start and end of a method within a source file.</span></span> <span data-ttu-id="07af4-104">メソッドの範囲を、メソッド内に存在するシーケンスポイントとは別に指定するには、このメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="07af4-104">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07af4-105">構文</span><span class="sxs-lookup"><span data-stu-id="07af4-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07af4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="07af4-106">Parameters</span></span>  

 `startDoc`  
 <span data-ttu-id="07af4-107">から開始位置を格納しているドキュメントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="07af4-107">[in] A pointer to the document containing the starting position.</span></span>  
  
 `startLine`  
 <span data-ttu-id="07af4-108">から開始行番号。</span><span class="sxs-lookup"><span data-stu-id="07af4-108">[in] The starting line number.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="07af4-109">から開始列。</span><span class="sxs-lookup"><span data-stu-id="07af4-109">[in] The starting column.</span></span>  
  
 `endDoc`  
 <span data-ttu-id="07af4-110">から終了位置を含むドキュメントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="07af4-110">[in] A pointer to the document containing the ending position.</span></span>  
  
 `endLine`  
 <span data-ttu-id="07af4-111">から終了行番号。</span><span class="sxs-lookup"><span data-stu-id="07af4-111">[in] The ending line number.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="07af4-112">から終了列番号。</span><span class="sxs-lookup"><span data-stu-id="07af4-112">[in] The ending column number.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07af4-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="07af4-113">Return Value</span></span>  

 <span data-ttu-id="07af4-114">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="07af4-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07af4-115">要件</span><span class="sxs-lookup"><span data-stu-id="07af4-115">Requirements</span></span>  

 <span data-ttu-id="07af4-116">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="07af4-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07af4-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="07af4-117">See also</span></span>

- [<span data-ttu-id="07af4-118">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="07af4-118">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
