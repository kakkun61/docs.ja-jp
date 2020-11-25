---
title: ISymUnmanagedNamespace インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace
helpviewer_keywords:
- ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: d42bea4e-5848-4e43-a883-69af7a313ce9
topic_type:
- apiref
ms.openlocfilehash: d9b295060426acd7f925bcf19c05ba216fdc2a4d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707899"
---
# <a name="isymunmanagednamespace-interface"></a><span data-ttu-id="e228f-102">ISymUnmanagedNamespace インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e228f-102">ISymUnmanagedNamespace Interface</span></span>

<span data-ttu-id="e228f-103">名前空間を表します。</span><span class="sxs-lookup"><span data-stu-id="e228f-103">Represents a namespace.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e228f-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="e228f-104">Methods</span></span>  
  
|<span data-ttu-id="e228f-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="e228f-105">Method</span></span>|<span data-ttu-id="e228f-106">説明</span><span class="sxs-lookup"><span data-stu-id="e228f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e228f-107">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="e228f-107">GetName Method</span></span>](isymunmanagednamespace-getname-method.md)|<span data-ttu-id="e228f-108">この名前空間の名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="e228f-108">Gets the name of this namespace.</span></span>|  
|[<span data-ttu-id="e228f-109">GetNamespaces メソッド</span><span class="sxs-lookup"><span data-stu-id="e228f-109">GetNamespaces Method</span></span>](isymunmanagednamespace-getnamespaces-method.md)|<span data-ttu-id="e228f-110">この名前空間の子を取得します。</span><span class="sxs-lookup"><span data-stu-id="e228f-110">Gets the children of this namespace.</span></span>|  
|[<span data-ttu-id="e228f-111">GetVariables メソッド</span><span class="sxs-lookup"><span data-stu-id="e228f-111">GetVariables Method</span></span>](isymunmanagednamespace-getvariables-method.md)|<span data-ttu-id="e228f-112">この名前空間内のグローバルスコープで定義されているすべての変数を返します。</span><span class="sxs-lookup"><span data-stu-id="e228f-112">Returns all variables defined at global scope within this namespace.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e228f-113">要件</span><span class="sxs-lookup"><span data-stu-id="e228f-113">Requirements</span></span>  

 <span data-ttu-id="e228f-114">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="e228f-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e228f-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="e228f-115">See also</span></span>

- [<span data-ttu-id="e228f-116">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e228f-116">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
