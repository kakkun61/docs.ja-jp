---
title: EmitInternalExportedTypes メソッド
ms.date: 03/30/2017
api_name:
- EmitInternalExportedTypes
- IALink2.EmitInternalExportedTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitInternalExportedTypes
helpviewer_keywords:
- EmitInternalExportedTypes method
ms.assetid: 28c8b00d-2c14-40b4-aed5-a1db0e2428eb
topic_type:
- apiref
ms.openlocfilehash: faf1438f56cd49b235ffbb18a0154e3e20c202b9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684968"
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="32ac0-102">EmitInternalExportedTypes メソッド</span><span class="sxs-lookup"><span data-stu-id="32ac0-102">EmitInternalExportedTypes Method</span></span>

<span data-ttu-id="32ac0-103">アセンブリに追加された型を出力します。</span><span class="sxs-lookup"><span data-stu-id="32ac0-103">Emits types added to the assembly.</span></span> <span data-ttu-id="32ac0-104">既知の内部型が追加された後に、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="32ac0-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32ac0-105">構文</span><span class="sxs-lookup"><span data-stu-id="32ac0-105">Syntax</span></span>  
  
```cpp  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="32ac0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="32ac0-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="32ac0-107">アセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="32ac0-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32ac0-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="32ac0-108">Return Value</span></span>  

 <span data-ttu-id="32ac0-109">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="32ac0-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32ac0-110">要件</span><span class="sxs-lookup"><span data-stu-id="32ac0-110">Requirements</span></span>  

 <span data-ttu-id="32ac0-111">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="32ac0-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32ac0-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="32ac0-112">See also</span></span>

- [<span data-ttu-id="32ac0-113">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="32ac0-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="32ac0-114">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="32ac0-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="32ac0-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="32ac0-115">ALink API</span></span>](index.md)
