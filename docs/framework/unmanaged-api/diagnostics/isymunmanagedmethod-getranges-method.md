---
title: ISymUnmanagedMethod::GetRanges メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRanges
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRanges
helpviewer_keywords:
- ISymUnmanagedMethod::GetRanges method [.NET Framework debugging]
- GetRanges method [.NET Framework debugging]
ms.assetid: a85283d8-379c-417a-9736-ddeeef9bcf50
topic_type:
- apiref
ms.openlocfilehash: 8ed492b573215736c82ab6c231cc5f2e188ea013
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732152"
---
# <a name="isymunmanagedmethodgetranges-method"></a><span data-ttu-id="37029-102">ISymUnmanagedMethod::GetRanges メソッド</span><span class="sxs-lookup"><span data-stu-id="37029-102">ISymUnmanagedMethod::GetRanges Method</span></span>

<span data-ttu-id="37029-103">ドキュメント内の位置が指定されている場合、は、位置がこのメソッド内でカバーする Microsoft 中間言語 (MSIL) の範囲に対応する開始オフセットと終了オフセットのペアの配列を返します。</span><span class="sxs-lookup"><span data-stu-id="37029-103">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span> <span data-ttu-id="37029-104">配列は整数の配列であり、[開始、終了、開始、終了] の形式です。</span><span class="sxs-lookup"><span data-stu-id="37029-104">The array is an array of integers and has the format [start, end, start, end].</span></span> <span data-ttu-id="37029-105">範囲ペアの数は、配列の長さを2で除算した値です。</span><span class="sxs-lookup"><span data-stu-id="37029-105">The number of range pairs is the length of the array divided by 2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37029-106">構文</span><span class="sxs-lookup"><span data-stu-id="37029-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRanges(  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32                line,  
    [in]  ULONG32                column,  
    [in]  ULONG32                cRanges,  
    [out] ULONG32                *pcRanges,  
    [out, size_is(cRanges),  
        length_is(*pcRanges)] ULONG32 ranges[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37029-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="37029-107">Parameters</span></span>  

 `document`  
 <span data-ttu-id="37029-108">からオフセットが要求されるドキュメント。</span><span class="sxs-lookup"><span data-stu-id="37029-108">[in] The document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="37029-109">から範囲に対応するドキュメント行。</span><span class="sxs-lookup"><span data-stu-id="37029-109">[in] The document line corresponding to the ranges.</span></span>  
  
 `column`  
 <span data-ttu-id="37029-110">から範囲に対応するドキュメント列。</span><span class="sxs-lookup"><span data-stu-id="37029-110">[in] The document column corresponding to the ranges.</span></span>  
  
 `cRanges`  
 <span data-ttu-id="37029-111">[in] `ranges` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="37029-111">[in] The size of the `ranges` array.</span></span>  
  
 `pcRanges`  
 <span data-ttu-id="37029-112">入出力 `ULONG32` 範囲を格納するために必要なバッファーのサイズを受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="37029-112">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the ranges.</span></span>  
  
 `ranges`  
 <span data-ttu-id="37029-113">入出力範囲を受け取るバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="37029-113">[out] A pointer to the buffer that receives the ranges.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37029-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="37029-114">Return Value</span></span>  

 <span data-ttu-id="37029-115">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="37029-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37029-116">要件</span><span class="sxs-lookup"><span data-stu-id="37029-116">Requirements</span></span>  

 <span data-ttu-id="37029-117">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="37029-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37029-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="37029-118">See also</span></span>

- [<span data-ttu-id="37029-119">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="37029-119">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
