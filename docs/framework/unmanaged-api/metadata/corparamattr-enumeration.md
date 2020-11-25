---
title: CorParamAttr 列挙型
ms.date: 03/30/2017
api_name:
- CorParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorParamAttr
helpviewer_keywords:
- CorParamAttr enumeration [.NET Framework metadata]
ms.assetid: a7ff90ad-dad8-48e8-917d-4aa9a118cbc8
topic_type:
- apiref
ms.openlocfilehash: 6f5d022a96fa021cb28dbbb67d0b53e08f77498c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729287"
---
# <a name="corparamattr-enumeration"></a><span data-ttu-id="ee34b-102">CorParamAttr 列挙型</span><span class="sxs-lookup"><span data-stu-id="ee34b-102">CorParamAttr Enumeration</span></span>

<span data-ttu-id="ee34b-103">メソッド パラメーターのメタデータを記述する値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="ee34b-103">Contains values that describe the metadata of a method parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee34b-104">構文</span><span class="sxs-lookup"><span data-stu-id="ee34b-104">Syntax</span></span>  
  
```cpp  
typedef enum CorParamAttr {  
  
    pdIn                        =   0x0001,  
    pdOut                       =   0x0002,  
    pdOptional                  =   0x0010,  
  
    pdReservedMask              =   0xf000,  
    pdHasDefault                =   0x1000,  
    pdHasFieldMarshal           =   0x2000,  
  
    pdUnused                    =   0xcfe0  
  
} CorParamAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="ee34b-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="ee34b-105">Members</span></span>  
  
|<span data-ttu-id="ee34b-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="ee34b-106">Member</span></span>|<span data-ttu-id="ee34b-107">説明</span><span class="sxs-lookup"><span data-stu-id="ee34b-107">Description</span></span>|  
|------------|-----------------|  
|`pdIn`|<span data-ttu-id="ee34b-108">パラメーターがメソッドの呼び出しに渡されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="ee34b-108">Specifies that the parameter is passed into the method call.</span></span>|  
|`pdOut`|<span data-ttu-id="ee34b-109">パラメーターがメソッドの戻り値から渡されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="ee34b-109">Specifies that the parameter is passed from the method return.</span></span>|  
|`pdOptional`|<span data-ttu-id="ee34b-110">パラメーターが省略可能であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="ee34b-110">Specifies that the parameter is optional.</span></span>|  
|`pdReservedMask`|<span data-ttu-id="ee34b-111">共通言語ランタイムによる内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="ee34b-111">Reserved for internal use by the common language runtime.</span></span>|  
|`pdHasDefault`|<span data-ttu-id="ee34b-112">パラメーターが既定の値を使用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="ee34b-112">Specifies that the parameter has a default value.</span></span>|  
|`pdHasFieldMarshal`|<span data-ttu-id="ee34b-113">パラメーターにマーシャリング情報があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="ee34b-113">Specifies that the parameter has marshaling information.</span></span>|  
|`pdUnused`|<span data-ttu-id="ee34b-114">未使用。</span><span class="sxs-lookup"><span data-stu-id="ee34b-114">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ee34b-115">要件</span><span class="sxs-lookup"><span data-stu-id="ee34b-115">Requirements</span></span>  

 <span data-ttu-id="ee34b-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee34b-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee34b-117">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="ee34b-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="ee34b-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee34b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee34b-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="ee34b-119">See also</span></span>

- [<span data-ttu-id="ee34b-120">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="ee34b-120">Metadata Enumerations</span></span>](metadata-enumerations.md)
