---
title: ISymUnmanagedENCUpdate インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate
helpviewer_keywords:
- ISymUnmanagedENCUpdate interface [.NET Framework debugging]
ms.assetid: 63a9ef45-01a6-46da-b958-5c6dc2dc232c
topic_type:
- apiref
ms.openlocfilehash: 5e3c2ecd1bdd5c1181223c7500eb7473e20fa5d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731346"
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="3472d-102">ISymUnmanagedENCUpdate インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3472d-102">ISymUnmanagedENCUpdate Interface</span></span>

<span data-ttu-id="3472d-103">エディットコンティニュ機能の関数を提供します。</span><span class="sxs-lookup"><span data-stu-id="3472d-103">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3472d-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="3472d-104">Methods</span></span>  
  
|<span data-ttu-id="3472d-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="3472d-105">Method</span></span>|<span data-ttu-id="3472d-106">説明</span><span class="sxs-lookup"><span data-stu-id="3472d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3472d-107">GetLocalVariableCount メソッド</span><span class="sxs-lookup"><span data-stu-id="3472d-107">GetLocalVariableCount Method</span></span>](isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="3472d-108">ローカル変数の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="3472d-108">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="3472d-109">GetLocalVariables メソッド</span><span class="sxs-lookup"><span data-stu-id="3472d-109">GetLocalVariables Method</span></span>](isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="3472d-110">ローカル変数を取得します。</span><span class="sxs-lookup"><span data-stu-id="3472d-110">Gets the local variables.</span></span>|  
|[<span data-ttu-id="3472d-111">InitializeForEnc メソッド</span><span class="sxs-lookup"><span data-stu-id="3472d-111">InitializeForEnc Method</span></span>](isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="3472d-112">[ISymUnmanagedENCUpdate:: UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md)メソッドの最初の呼び出しの前にメソッドの境界を計算できるようにします。</span><span class="sxs-lookup"><span data-stu-id="3472d-112">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="3472d-113">UpdateMethodLines メソッド</span><span class="sxs-lookup"><span data-stu-id="3472d-113">UpdateMethodLines Method</span></span>](isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="3472d-114">再コンパイルされていないが、行が個別に移動したメソッドの行情報を更新できるようにします。</span><span class="sxs-lookup"><span data-stu-id="3472d-114">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="3472d-115">各ステートメントのデルタが許可されます。</span><span class="sxs-lookup"><span data-stu-id="3472d-115">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="3472d-116">UpdateSymbolStore2 メソッド</span><span class="sxs-lookup"><span data-stu-id="3472d-116">UpdateSymbolStore2 Method</span></span>](isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="3472d-117">行情報が要件を満たしている場合に、コンパイラがプログラムデータベース (PDB) ストリームから変更されていない関数を省略できるようにします。</span><span class="sxs-lookup"><span data-stu-id="3472d-117">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="3472d-118">正しい行情報は、古い PDB 行情報と、関数内のすべての行に対して1つのデルタで判別できます。</span><span class="sxs-lookup"><span data-stu-id="3472d-118">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3472d-119">要件</span><span class="sxs-lookup"><span data-stu-id="3472d-119">Requirements</span></span>  

 <span data-ttu-id="3472d-120">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="3472d-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3472d-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="3472d-121">See also</span></span>

- [<span data-ttu-id="3472d-122">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3472d-122">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
