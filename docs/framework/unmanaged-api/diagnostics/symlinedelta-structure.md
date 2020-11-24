---
title: SYMLINEDELTA 構造体
ms.date: 03/30/2017
api_name:
- SYMLINEDELTA
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SYMLINEDELTA
helpviewer_keywords:
- SYMLINEDELTA structure [.NET Framework debugging]
ms.assetid: 9634e995-d46d-4397-ab66-cc5781d11e4e
topic_type:
- apiref
ms.openlocfilehash: dd45703540f8dc41b746ca03b4f09d74186aa9aa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690942"
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="0da5d-102">SYMLINEDELTA 構造体</span><span class="sxs-lookup"><span data-stu-id="0da5d-102">SYMLINEDELTA Structure</span></span>

<span data-ttu-id="0da5d-103">編集の結果として移動されたメソッドについて、シンボルハンドラーに情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="0da5d-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0da5d-104">構文</span><span class="sxs-lookup"><span data-stu-id="0da5d-104">Syntax</span></span>  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="0da5d-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="0da5d-105">Members</span></span>  
  
|<span data-ttu-id="0da5d-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="0da5d-106">Member</span></span>|<span data-ttu-id="0da5d-107">説明</span><span class="sxs-lookup"><span data-stu-id="0da5d-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="0da5d-108">メソッドのメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="0da5d-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="0da5d-109">メソッドが移動された行の数。</span><span class="sxs-lookup"><span data-stu-id="0da5d-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0da5d-110">要件</span><span class="sxs-lookup"><span data-stu-id="0da5d-110">Requirements</span></span>  

 <span data-ttu-id="0da5d-111">**ヘッダー:** CorSym .idl</span><span class="sxs-lookup"><span data-stu-id="0da5d-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0da5d-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="0da5d-112">See also</span></span>

- [<span data-ttu-id="0da5d-113">シンボル ストア診断構造体</span><span class="sxs-lookup"><span data-stu-id="0da5d-113">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)
