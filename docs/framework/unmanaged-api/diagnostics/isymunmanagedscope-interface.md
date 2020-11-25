---
title: ISymUnmanagedScope インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope
helpviewer_keywords:
- ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 3db7a220-cfe9-4810-8ca8-a094bb8e0f5b
topic_type:
- apiref
ms.openlocfilehash: 9256342ad3a91e6770d6fd19d9d2f94fab267d3e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725886"
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="00cc4-102">ISymUnmanagedScope インターフェイス</span><span class="sxs-lookup"><span data-stu-id="00cc4-102">ISymUnmanagedScope Interface</span></span>

<span data-ttu-id="00cc4-103">メソッド内の構文のスコープを表します。</span><span class="sxs-lookup"><span data-stu-id="00cc4-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="00cc4-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="00cc4-104">Methods</span></span>  
  
|<span data-ttu-id="00cc4-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="00cc4-105">Method</span></span>|<span data-ttu-id="00cc4-106">説明</span><span class="sxs-lookup"><span data-stu-id="00cc4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="00cc4-107">GetChildren メソッド</span><span class="sxs-lookup"><span data-stu-id="00cc4-107">GetChildren Method</span></span>](isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="00cc4-108">このスコープの子を取得します。</span><span class="sxs-lookup"><span data-stu-id="00cc4-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="00cc4-109">GetEndOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="00cc4-109">GetEndOffset Method</span></span>](isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="00cc4-110">このスコープの終了オフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="00cc4-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="00cc4-111">GetLocalCount メソッド</span><span class="sxs-lookup"><span data-stu-id="00cc4-111">GetLocalCount Method</span></span>](isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="00cc4-112">このスコープ内で定義されているローカル変数の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="00cc4-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="00cc4-113">GetLocals メソッド</span><span class="sxs-lookup"><span data-stu-id="00cc4-113">GetLocals Method</span></span>](isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="00cc4-114">このスコープ内で定義されているローカル変数を取得します。</span><span class="sxs-lookup"><span data-stu-id="00cc4-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="00cc4-115">GetMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="00cc4-115">GetMethod Method</span></span>](isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="00cc4-116">このスコープを格納しているメソッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="00cc4-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="00cc4-117">GetNamespaces メソッド</span><span class="sxs-lookup"><span data-stu-id="00cc4-117">GetNamespaces Method</span></span>](isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="00cc4-118">このスコープ内で使用されている名前空間を取得します。</span><span class="sxs-lookup"><span data-stu-id="00cc4-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="00cc4-119">GetParent メソッド</span><span class="sxs-lookup"><span data-stu-id="00cc4-119">GetParent Method</span></span>](isymunmanagedscope-getparent-method.md)|<span data-ttu-id="00cc4-120">このスコープの親スコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="00cc4-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="00cc4-121">GetStartOffSet メソッド</span><span class="sxs-lookup"><span data-stu-id="00cc4-121">GetStartOffset Method</span></span>](isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="00cc4-122">このスコープの開始オフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="00cc4-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="00cc4-123">要件</span><span class="sxs-lookup"><span data-stu-id="00cc4-123">Requirements</span></span>  

 <span data-ttu-id="00cc4-124">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="00cc4-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00cc4-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="00cc4-125">See also</span></span>

- [<span data-ttu-id="00cc4-126">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="00cc4-126">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="00cc4-127">ISymUnmanagedScope2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="00cc4-127">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)
