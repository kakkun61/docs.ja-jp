---
title: EndMerge メソッド
ms.date: 03/30/2017
api_name:
- IALink.EndMerge
- EndMerge
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EndMerge
helpviewer_keywords:
- EndMerge method
ms.assetid: 1d03bb15-a2c8-4a04-8fc6-b126c89c3778
topic_type:
- apiref
ms.openlocfilehash: ed4ac7b12caa0dd78b79554258de62b8752553e0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684929"
---
# <a name="endmerge-method"></a><span data-ttu-id="0e8bb-102">EndMerge メソッド</span><span class="sxs-lookup"><span data-stu-id="0e8bb-102">EndMerge Method</span></span>

<span data-ttu-id="0e8bb-103">すべてのカスタム属性が生成スコープにマージされたことを示します。</span><span class="sxs-lookup"><span data-stu-id="0e8bb-103">Indicates that all custom attributes have been merged into the emit scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e8bb-104">構文</span><span class="sxs-lookup"><span data-stu-id="0e8bb-104">Syntax</span></span>  
  
```cpp  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e8bb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0e8bb-105">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="0e8bb-106">アセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="0e8bb-106">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e8bb-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="0e8bb-107">Return Value</span></span>  

 <span data-ttu-id="0e8bb-108">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="0e8bb-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e8bb-109">要件</span><span class="sxs-lookup"><span data-stu-id="0e8bb-109">Requirements</span></span>  

 <span data-ttu-id="0e8bb-110">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="0e8bb-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e8bb-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="0e8bb-111">See also</span></span>

- [<span data-ttu-id="0e8bb-112">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0e8bb-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="0e8bb-113">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0e8bb-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="0e8bb-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="0e8bb-114">ALink API</span></span>](index.md)
