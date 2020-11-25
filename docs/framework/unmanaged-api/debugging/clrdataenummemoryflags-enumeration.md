---
title: CLRDataEnumMemoryFlags 列挙型
ms.date: 03/30/2017
api_name:
- CLRDataEnumMemoryFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLRDataEnumMemoryFlags
helpviewer_keywords:
- CLRDataEnumMemoryFlags enumeration [.NET Framework debugging]
ms.assetid: e249f9fc-e24a-4506-903c-92781f6eab7c
topic_type:
- apiref
ms.openlocfilehash: 9a82162023fa05e85fc9bbeb16961f2aafd9a4ec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729799"
---
# <a name="clrdataenummemoryflags-enumeration"></a><span data-ttu-id="a25ea-102">CLRDataEnumMemoryFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="a25ea-102">CLRDataEnumMemoryFlags Enumeration</span></span>

<span data-ttu-id="a25ea-103">[ICLRDataEnumMemoryRegions:: EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md)メソッドへの呼び出しに含まれるメモリ領域を示します。</span><span class="sxs-lookup"><span data-stu-id="a25ea-103">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a25ea-104">構文</span><span class="sxs-lookup"><span data-stu-id="a25ea-104">Syntax</span></span>  
  
```cpp  
typedef enum CLRDataEnumMemoryFlags {  
    CLRDATA_ENUM_MEM_DEFAULT  = 0x0,  
    CLRDATA_ENUM_MEM_MINI     = CLRDATA_ENUM_MEM_DEFAULT,  
    CLRDATA_ENUM_MEM_HEAP     = 0x1  
} CLRDataEnumMemoryFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="a25ea-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="a25ea-105">Members</span></span>  
  
|<span data-ttu-id="a25ea-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="a25ea-106">Member</span></span>|<span data-ttu-id="a25ea-107">説明</span><span class="sxs-lookup"><span data-stu-id="a25ea-107">Description</span></span>|  
|------------|-----------------|  
|`CLRDATA_ENUM_MEM_DEFAULT`|<span data-ttu-id="a25ea-108">ミニダンプ (スパースメモリダンプ)。</span><span class="sxs-lookup"><span data-stu-id="a25ea-108">A minidump, that is, a sparse memory dump.</span></span>|  
|`CLRDATA_ENUM_MEM_HEAP`|<span data-ttu-id="a25ea-109">完全なヒープダンプ。</span><span class="sxs-lookup"><span data-stu-id="a25ea-109">A full heap dump.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a25ea-110">要件</span><span class="sxs-lookup"><span data-stu-id="a25ea-110">Requirements</span></span>  

 <span data-ttu-id="a25ea-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a25ea-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a25ea-112">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="a25ea-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="a25ea-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a25ea-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a25ea-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a25ea-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a25ea-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="a25ea-115">See also</span></span>

- [<span data-ttu-id="a25ea-116">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="a25ea-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
