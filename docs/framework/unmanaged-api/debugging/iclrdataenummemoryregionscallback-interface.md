---
title: ICLRDataEnumMemoryRegionsCallback インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback
helpviewer_keywords:
- ICLRDataEnumMemoryRegionsCallback interface [.NET Framework debugging]
ms.assetid: 3f1af8b0-8478-48e0-a7ec-3e90e0b97649
topic_type:
- apiref
ms.openlocfilehash: f080d852b190346740a3629f3b5d46a9f3808293
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703630"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="9d1c9-102">ICLRDataEnumMemoryRegionsCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9d1c9-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>

<span data-ttu-id="9d1c9-103">[ICLRDataEnumMemoryRegions:: EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md)のコールバックメソッドを提供し、指定されたメモリ領域を列挙しようとした結果をデバッガーに報告します。</span><span class="sxs-lookup"><span data-stu-id="9d1c9-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9d1c9-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="9d1c9-104">Methods</span></span>  
  
|<span data-ttu-id="9d1c9-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="9d1c9-105">Method</span></span>|<span data-ttu-id="9d1c9-106">説明</span><span class="sxs-lookup"><span data-stu-id="9d1c9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9d1c9-107">EnumMemoryRegion メソッド</span><span class="sxs-lookup"><span data-stu-id="9d1c9-107">EnumMemoryRegion Method</span></span>](iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="9d1c9-108">`ICLRDataEnumMemoryRegions::EnumMemoryRegions`指定されたメモリ領域を列挙しようとした結果をデバッガーに報告するために、によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="9d1c9-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9d1c9-109">要件</span><span class="sxs-lookup"><span data-stu-id="9d1c9-109">Requirements</span></span>  

 <span data-ttu-id="9d1c9-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d1c9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d1c9-111">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="9d1c9-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="9d1c9-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d1c9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d1c9-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d1c9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d1c9-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d1c9-114">See also</span></span>

- [<span data-ttu-id="9d1c9-115">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="9d1c9-115">Debugging Interfaces</span></span>](debugging-interfaces.md)
