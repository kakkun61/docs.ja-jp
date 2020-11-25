---
title: CorSaveSize 列挙型
ms.date: 03/30/2017
api_name:
- CorSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSaveSize
helpviewer_keywords:
- CorSaveSize enumeration [.NET Framework metadata]
ms.assetid: eb95ce39-5688-43c1-a34d-578794b32faa
topic_type:
- apiref
ms.openlocfilehash: 81d47a3e4d72f991dc15924e7ff1ecc8df2e7322
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706057"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="3aefb-102">CorSaveSize 列挙型</span><span class="sxs-lookup"><span data-stu-id="3aefb-102">CorSaveSize Enumeration</span></span>

<span data-ttu-id="3aefb-103">保存操作のサイズの照会で要求される精度のレベルを示す値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="3aefb-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3aefb-104">構文</span><span class="sxs-lookup"><span data-stu-id="3aefb-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,
    cssQuick                   = 0x0001,
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="3aefb-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="3aefb-105">Members</span></span>  
  
|<span data-ttu-id="3aefb-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="3aefb-106">Member</span></span>|<span data-ttu-id="3aefb-107">説明</span><span class="sxs-lookup"><span data-stu-id="3aefb-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="3aefb-108">戻り値が正確であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="3aefb-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="3aefb-109">戻り値を推定することを指定します。</span><span class="sxs-lookup"><span data-stu-id="3aefb-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="3aefb-110">破棄可能な型を削除する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="3aefb-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3aefb-111">要件</span><span class="sxs-lookup"><span data-stu-id="3aefb-111">Requirements</span></span>  

 <span data-ttu-id="3aefb-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3aefb-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3aefb-113">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="3aefb-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="3aefb-114">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="3aefb-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3aefb-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3aefb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aefb-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="3aefb-116">See also</span></span>

- [<span data-ttu-id="3aefb-117">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="3aefb-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
