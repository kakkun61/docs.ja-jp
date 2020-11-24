---
title: ISymUnmanagedReader::GetMethodsFromDocumentPosition メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodsFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodsFromDocumentPosition
helpviewer_keywords:
- GetMethodsFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodsFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 83605f1e-e4f3-49e6-859b-f13cad68bb54
topic_type:
- apiref
ms.openlocfilehash: 5298dd0f53693d96b748f6c839660838fdfad4ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689551"
---
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a><span data-ttu-id="c81a6-102">ISymUnmanagedReader::GetMethodsFromDocumentPosition メソッド</span><span class="sxs-lookup"><span data-stu-id="c81a6-102">ISymUnmanagedReader::GetMethodsFromDocumentPosition Method</span></span>

<span data-ttu-id="c81a6-103">メソッドの配列を返します。各メソッドには、ドキュメント内の指定された位置にあるブレークポイントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c81a6-103">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c81a6-104">構文</span><span class="sxs-lookup"><span data-stu-id="c81a6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodsFromDocumentPosition (  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32 line,  
    [in]  ULONG32 column,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is (cMethod),  
        length_is (*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c81a6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c81a6-105">Parameters</span></span>  

 `document`  
 <span data-ttu-id="c81a6-106">から指定されたドキュメント。</span><span class="sxs-lookup"><span data-stu-id="c81a6-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="c81a6-107">から指定したドキュメントの行。</span><span class="sxs-lookup"><span data-stu-id="c81a6-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="c81a6-108">から指定されたドキュメントの列。</span><span class="sxs-lookup"><span data-stu-id="c81a6-108">[in] The column of the specified document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="c81a6-109">[in] `pRetVal` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="c81a6-109">[in] The size of the `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="c81a6-110">入出力配列で返された要素の数を受け取る変数へのポインター `pRetVal` 。</span><span class="sxs-lookup"><span data-stu-id="c81a6-110">[out] A pointer to a variable that receives the number of elements returned in the `pRetVal` array.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="c81a6-111">入出力ポインターの配列。各ポインターは、ブレークポイントを含むメソッドを表す [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) オブジェクトを指します。</span><span class="sxs-lookup"><span data-stu-id="c81a6-111">[out] An array of pointers, each of which points to an [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) object that represents a method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c81a6-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="c81a6-112">Return Value</span></span>  

 <span data-ttu-id="c81a6-113">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="c81a6-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c81a6-114">要件</span><span class="sxs-lookup"><span data-stu-id="c81a6-114">Requirements</span></span>  

 <span data-ttu-id="c81a6-115">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="c81a6-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c81a6-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="c81a6-116">See also</span></span>

- [<span data-ttu-id="c81a6-117">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c81a6-117">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
