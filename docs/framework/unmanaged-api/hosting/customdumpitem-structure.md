---
title: CustomDumpItem 構造体
ms.date: 03/30/2017
api_name:
- CustomDumpItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CustomDumpItem
helpviewer_keywords:
- CustomDumpItem structure [.NET Framework hosting]
ms.assetid: fd9085ff-7beb-4c38-97f0-037cd8ba4f65
topic_type:
- apiref
ms.openlocfilehash: c77e93686c7d121e9fe2a92f03970404ab823dc0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673242"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="abd91-102">CustomDumpItem 構造体</span><span class="sxs-lookup"><span data-stu-id="abd91-102">CustomDumpItem Structure</span></span>

<span data-ttu-id="abd91-103">エラー報告のカスタムダンプに追加するアイテムについて説明します。</span><span class="sxs-lookup"><span data-stu-id="abd91-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abd91-104">構文</span><span class="sxs-lookup"><span data-stu-id="abd91-104">Syntax</span></span>  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="abd91-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="abd91-105">Members</span></span>  
  
|<span data-ttu-id="abd91-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="abd91-106">Member</span></span>|<span data-ttu-id="abd91-107">説明</span><span class="sxs-lookup"><span data-stu-id="abd91-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="abd91-108">追加する項目の種類を示す [ECustomDumpItemKind](ecustomdumpitemkind-enumeration.md) 値。</span><span class="sxs-lookup"><span data-stu-id="abd91-108">An [ECustomDumpItemKind](ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="abd91-109">現在は使用しません。</span><span class="sxs-lookup"><span data-stu-id="abd91-109">Not currently used.</span></span> <span data-ttu-id="abd91-110">共用体に追加された項目は、ポインターサイズ以下である必要があります。</span><span class="sxs-lookup"><span data-stu-id="abd91-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="abd91-111">`struct`が必要な場合は、それを個別に割り当てて、それをポイントする必要があります。</span><span class="sxs-lookup"><span data-stu-id="abd91-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abd91-112">注釈</span><span class="sxs-lookup"><span data-stu-id="abd91-112">Remarks</span></span>  

 <span data-ttu-id="abd91-113">[ICLRErrorReportingManager:: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) は、型のパラメーターを受け取り `CustomDumpItem` ます。</span><span class="sxs-lookup"><span data-stu-id="abd91-113">[ICLRErrorReportingManager::BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abd91-114">要件</span><span class="sxs-lookup"><span data-stu-id="abd91-114">Requirements</span></span>  

 <span data-ttu-id="abd91-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abd91-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abd91-116">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="abd91-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="abd91-117">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="abd91-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="abd91-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abd91-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abd91-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="abd91-119">See also</span></span>

- [<span data-ttu-id="abd91-120">ホスト構造体</span><span class="sxs-lookup"><span data-stu-id="abd91-120">Hosting Structures</span></span>](hosting-structures.md)
