---
title: CloseAssembly メソッド
ms.date: 03/30/2017
api_name:
- IALink.CloseAssembly
- CloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseAssembly
helpviewer_keywords:
- CloseAssembly method
ms.assetid: f66a43bc-a5c5-4190-acbe-63fd27640634
topic_type:
- apiref
ms.openlocfilehash: 4e8aeef3520c4d5c9735b2c8975ac1e39470ba93
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717021"
---
# <a name="closeassembly-method"></a><span data-ttu-id="77112-102">CloseAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="77112-102">CloseAssembly Method</span></span>

<span data-ttu-id="77112-103">アセンブリ操作を終了します。</span><span class="sxs-lookup"><span data-stu-id="77112-103">Finalizes assembly operations.</span></span> <span data-ttu-id="77112-104">新しいアセンブリまたは非バインドモジュールを開始する前に、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="77112-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77112-105">構文</span><span class="sxs-lookup"><span data-stu-id="77112-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="77112-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="77112-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="77112-107">アセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="77112-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77112-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="77112-108">Return Value</span></span>  

 <span data-ttu-id="77112-109">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="77112-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77112-110">要件</span><span class="sxs-lookup"><span data-stu-id="77112-110">Requirements</span></span>  

 <span data-ttu-id="77112-111">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="77112-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77112-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="77112-112">See also</span></span>

- [<span data-ttu-id="77112-113">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="77112-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="77112-114">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="77112-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="77112-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="77112-115">ALink API</span></span>](index.md)
