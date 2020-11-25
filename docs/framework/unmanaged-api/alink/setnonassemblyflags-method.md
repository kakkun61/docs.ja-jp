---
title: SetNonAssemblyFlags メソッド
ms.date: 03/30/2017
api_name:
- IALink.SetNonAssemblyFlags
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetNonAssemblyFlags
helpviewer_keywords:
- SetNonAssemblyFlags method
ms.assetid: f8ba6fc8-f5aa-4066-ac96-56332758f5ec
topic_type:
- apiref
ms.openlocfilehash: b7bcf530947c161decc9c01c07df310550d69738
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733764"
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="551be-102">SetNonAssemblyFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="551be-102">SetNonAssemblyFlags Method</span></span>

<span data-ttu-id="551be-103">アセンブリ固有ではないフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="551be-103">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="551be-104">構文</span><span class="sxs-lookup"><span data-stu-id="551be-104">Syntax</span></span>  
  
```cpp  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="551be-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="551be-105">Parameters</span></span>  

 `afFlags`  
 <span data-ttu-id="551be-106">ALink フラグ。</span><span class="sxs-lookup"><span data-stu-id="551be-106">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="551be-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="551be-107">Return Value</span></span>  

 <span data-ttu-id="551be-108">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="551be-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="551be-109">要件</span><span class="sxs-lookup"><span data-stu-id="551be-109">Requirements</span></span>  

 <span data-ttu-id="551be-110">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="551be-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="551be-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="551be-111">See also</span></span>

- [<span data-ttu-id="551be-112">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="551be-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="551be-113">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="551be-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="551be-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="551be-114">ALink API</span></span>](index.md)
