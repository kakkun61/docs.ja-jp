---
title: ISymUnmanagedWriter::DefineSequencePoints メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type:
- apiref
ms.openlocfilehash: af8beb1ec627b93faeb7329a03579319ca3880ed
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678325"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a><span data-ttu-id="11e75-102">ISymUnmanagedWriter::DefineSequencePoints メソッド</span><span class="sxs-lookup"><span data-stu-id="11e75-102">ISymUnmanagedWriter::DefineSequencePoints Method</span></span>

<span data-ttu-id="11e75-103">現在のメソッド内のシーケンス ポイントのグループを定義します。</span><span class="sxs-lookup"><span data-stu-id="11e75-103">Defines a group of sequence points within the current method.</span></span> <span data-ttu-id="11e75-104">開始行と開始列はそれぞれ、メソッド内のステートメントの開始を定義します。</span><span class="sxs-lookup"><span data-stu-id="11e75-104">Each starting line and starting column define the start of a statement within a method.</span></span> <span data-ttu-id="11e75-105">各終了行と終了列は、メソッド内のステートメントの末尾を定義します。</span><span class="sxs-lookup"><span data-stu-id="11e75-105">Each ending line and ending column define the end of a statement within a method.</span></span> <span data-ttu-id="11e75-106">配列は、オフセットの昇順で並べ替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="11e75-106">The arrays should be sorted in increasing order of offsets.</span></span> <span data-ttu-id="11e75-107">オフセットは、常にメソッドの先頭からバイト単位で測定されます。</span><span class="sxs-lookup"><span data-stu-id="11e75-107">The offset is always measured from the start of the method, in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11e75-108">構文</span><span class="sxs-lookup"><span data-stu-id="11e75-108">Syntax</span></span>  
  
```cpp  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11e75-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="11e75-109">Parameters</span></span>  

 `document`  
 <span data-ttu-id="11e75-110">からシーケンスポイントが定義されているドキュメントオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="11e75-110">[in] The document object for which the sequence points are being defined.</span></span>  
  
 `spCount`  
 <span data-ttu-id="11e75-111">から、、 `ULONG32` `offsets` `lines` `columns` 、 `endLines` 、および `endColumns` の各バッファーのサイズを示す。</span><span class="sxs-lookup"><span data-stu-id="11e75-111">[in] A `ULONG32` that indicates the size of each of the `offsets`, `lines`, `columns`, `endLines`, and `endColumns` buffers.</span></span>  
  
 `offsets`  
 <span data-ttu-id="11e75-112">からメソッドの先頭から計測されたシーケンスポイントのオフセット。</span><span class="sxs-lookup"><span data-stu-id="11e75-112">[in] The offset of the sequence points measured from the beginning of the method.</span></span>  
  
 `lines`  
 <span data-ttu-id="11e75-113">からシーケンスポイントの開始行番号。</span><span class="sxs-lookup"><span data-stu-id="11e75-113">[in] The starting line numbers of the sequence points.</span></span>  
  
 `columns`  
 <span data-ttu-id="11e75-114">からシーケンスポイントの開始列番号。</span><span class="sxs-lookup"><span data-stu-id="11e75-114">[in] The starting column numbers of the sequence points.</span></span>  
  
 `endLines`  
 <span data-ttu-id="11e75-115">からシーケンスポイントの終了行番号。</span><span class="sxs-lookup"><span data-stu-id="11e75-115">[in] The ending line numbers of the sequence points.</span></span> <span data-ttu-id="11e75-116">このパラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="11e75-116">This parameter is optional.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="11e75-117">からシーケンスポイントの終了列番号。</span><span class="sxs-lookup"><span data-stu-id="11e75-117">[in] The ending column numbers of the sequence points.</span></span> <span data-ttu-id="11e75-118">このパラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="11e75-118">This parameter is optional.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11e75-119">戻り値</span><span class="sxs-lookup"><span data-stu-id="11e75-119">Return Value</span></span>  

 <span data-ttu-id="11e75-120">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="11e75-120">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11e75-121">要件</span><span class="sxs-lookup"><span data-stu-id="11e75-121">Requirements</span></span>  

 <span data-ttu-id="11e75-122">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="11e75-122">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11e75-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="11e75-123">See also</span></span>

- [<span data-ttu-id="11e75-124">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="11e75-124">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
