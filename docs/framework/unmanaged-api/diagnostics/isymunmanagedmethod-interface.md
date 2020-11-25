---
title: ISymUnmanagedMethod インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod
helpviewer_keywords:
- ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: f204d74c-cc79-4092-83bb-60654be95649
topic_type:
- apiref
ms.openlocfilehash: b72a77fecd15a43efbddd9dfd4618897c3372f88
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699275"
---
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="87dc6-102">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="87dc6-102">ISymUnmanagedMethod Interface</span></span>

<span data-ttu-id="87dc6-103">シンボル ストア内のメソッドを表します。</span><span class="sxs-lookup"><span data-stu-id="87dc6-103">Represents a method within the symbol store.</span></span> <span data-ttu-id="87dc6-104">このインターフェイスは、型関連の属性ではなく、メソッドのシンボル関連の属性にのみアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="87dc6-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="87dc6-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="87dc6-105">Methods</span></span>  
  
|<span data-ttu-id="87dc6-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="87dc6-106">Method</span></span>|<span data-ttu-id="87dc6-107">説明</span><span class="sxs-lookup"><span data-stu-id="87dc6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="87dc6-108">GetNamespace メソッド</span><span class="sxs-lookup"><span data-stu-id="87dc6-108">GetNamespace Method</span></span>](isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="87dc6-109">このメソッドが定義されている名前空間を取得します。</span><span class="sxs-lookup"><span data-stu-id="87dc6-109">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="87dc6-110">GetOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="87dc6-110">GetOffset Method</span></span>](isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="87dc6-111">ドキュメント内の指定された位置に対応する、このメソッド内のオフセットを返します。</span><span class="sxs-lookup"><span data-stu-id="87dc6-111">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="87dc6-112">GetParameters メソッド</span><span class="sxs-lookup"><span data-stu-id="87dc6-112">GetParameters Method</span></span>](isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="87dc6-113">このメソッドのパラメーターを取得します。</span><span class="sxs-lookup"><span data-stu-id="87dc6-113">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="87dc6-114">GetRanges メソッド</span><span class="sxs-lookup"><span data-stu-id="87dc6-114">GetRanges Method</span></span>](isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="87dc6-115">ドキュメント内の位置が指定されている場合、は、位置がこのメソッド内でカバーする Microsoft 中間言語 (MSIL) の範囲に対応する開始オフセットと終了オフセットのペアの配列を返します。</span><span class="sxs-lookup"><span data-stu-id="87dc6-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="87dc6-116">GetRootScope メソッド</span><span class="sxs-lookup"><span data-stu-id="87dc6-116">GetRootScope Method</span></span>](isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="87dc6-117">このメソッド内のルート構文のスコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="87dc6-117">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="87dc6-118">このスコープはメソッド全体を囲みます。</span><span class="sxs-lookup"><span data-stu-id="87dc6-118">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="87dc6-119">GetScopeFromOffSet メソッド</span><span class="sxs-lookup"><span data-stu-id="87dc6-119">GetScopeFromOffset Method</span></span>](isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="87dc6-120">指定されたオフセットを囲む、このメソッド内で最も外側にある構文のスコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="87dc6-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="87dc6-121">GetSequencePointCount メソッド</span><span class="sxs-lookup"><span data-stu-id="87dc6-121">GetSequencePointCount Method</span></span>](isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="87dc6-122">このメソッド内のシーケンスポイントの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="87dc6-122">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="87dc6-123">GetSequencePoints メソッド</span><span class="sxs-lookup"><span data-stu-id="87dc6-123">GetSequencePoints Method</span></span>](isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="87dc6-124">このメソッド内のすべてのシーケンスポイントを取得します。</span><span class="sxs-lookup"><span data-stu-id="87dc6-124">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="87dc6-125">GetSourceStartEnd メソッド</span><span class="sxs-lookup"><span data-stu-id="87dc6-125">GetSourceStartEnd Method</span></span>](isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="87dc6-126">このメソッドのソースのドキュメントの開始位置と終了位置を取得します。</span><span class="sxs-lookup"><span data-stu-id="87dc6-126">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="87dc6-127">GetToken メソッド</span><span class="sxs-lookup"><span data-stu-id="87dc6-127">GetToken Method</span></span>](isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="87dc6-128">このメソッドのメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="87dc6-128">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="87dc6-129">要件</span><span class="sxs-lookup"><span data-stu-id="87dc6-129">Requirements</span></span>  

 <span data-ttu-id="87dc6-130">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="87dc6-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87dc6-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="87dc6-131">See also</span></span>

- [<span data-ttu-id="87dc6-132">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="87dc6-132">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
