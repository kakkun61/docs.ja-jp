---
title: CorSymVarFlag 列挙体
ms.date: 03/30/2017
api_name:
- CorSymVarFlag
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymVarFlag
helpviewer_keywords:
- CorSymVarFlag enumeration [.NET Framework debugging]
ms.assetid: c3f7d307-4047-4f9a-be8c-f152fca42fd0
topic_type:
- apiref
ms.openlocfilehash: ed08d9f818f6fc180dbd655243488bf8a527ae11
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725288"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="284e2-102">CorSymVarFlag 列挙体</span><span class="sxs-lookup"><span data-stu-id="284e2-102">CorSymVarFlag Enumeration</span></span>

<span data-ttu-id="284e2-103">変数がコンパイラによって生成されたかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="284e2-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="284e2-104">構文</span><span class="sxs-lookup"><span data-stu-id="284e2-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSymVarFlag
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="284e2-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="284e2-105">Members</span></span>  
  
|<span data-ttu-id="284e2-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="284e2-106">Member</span></span>|<span data-ttu-id="284e2-107">説明</span><span class="sxs-lookup"><span data-stu-id="284e2-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="284e2-108">指定された変数がコンパイラによって生成されることを示します。</span><span class="sxs-lookup"><span data-stu-id="284e2-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="284e2-109">要件</span><span class="sxs-lookup"><span data-stu-id="284e2-109">Requirements</span></span>  

 <span data-ttu-id="284e2-110">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="284e2-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="284e2-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="284e2-111">See also</span></span>

- [<span data-ttu-id="284e2-112">シンボル ストア診断列挙型</span><span class="sxs-lookup"><span data-stu-id="284e2-112">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
