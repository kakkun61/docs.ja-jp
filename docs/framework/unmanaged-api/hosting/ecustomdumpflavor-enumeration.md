---
title: ECustomDumpFlavor 列挙型
ms.date: 03/30/2017
api_name:
- ECustomDumpFlavor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ECustomDumpFlavor
helpviewer_keywords:
- ECustomDumpFlavor enumeration [.NET Framework hosting]
ms.assetid: b39b3320-fac7-41f1-9a03-ab6fb0cd89c7
topic_type:
- apiref
ms.openlocfilehash: 1b8440ed6e878aac3dd08d9f8ed528c93739a724
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686320"
---
# <a name="ecustomdumpflavor-enumeration"></a><span data-ttu-id="3389a-102">ECustomDumpFlavor 列挙型</span><span class="sxs-lookup"><span data-stu-id="3389a-102">ECustomDumpFlavor Enumeration</span></span>

<span data-ttu-id="3389a-103">エラーを報告するときに、ヒープダンプのカスタムサブセットに含めるアイテムを示す値を格納します。</span><span class="sxs-lookup"><span data-stu-id="3389a-103">Contains values that indicate which items to include in a custom subset of a heap dump when reporting errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3389a-104">構文</span><span class="sxs-lookup"><span data-stu-id="3389a-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a><span data-ttu-id="3389a-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="3389a-105">Members</span></span>  
  
|<span data-ttu-id="3389a-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="3389a-106">Member</span></span>|<span data-ttu-id="3389a-107">説明</span><span class="sxs-lookup"><span data-stu-id="3389a-107">Description</span></span>|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|<span data-ttu-id="3389a-108">カスタムヒープダンプをミニダンプとして起動し、同じメソッドに渡される [Customdumpitem](customdumpitem-structure.md) インスタンスによって指定された追加データを含めるように指定します。</span><span class="sxs-lookup"><span data-stu-id="3389a-108">Specifies that the custom heap dump should start as a minidump and include extra data specified by any [CustomDumpItem](customdumpitem-structure.md) instances passed to the same method.</span></span>|  
|`DUMP_FLAVOR_NonHeapCLRState`|<span data-ttu-id="3389a-109">カスタムヒープダンプで、動的に割り当てられていないすべての実行時状態データを収集するように指定します。</span><span class="sxs-lookup"><span data-stu-id="3389a-109">Specifies that the custom heap dump should gather all run-time state data that was not dynamically allocated.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3389a-110">注釈</span><span class="sxs-lookup"><span data-stu-id="3389a-110">Remarks</span></span>  

 <span data-ttu-id="3389a-111">型のパラメーター `ECustomDumpFlavor` は、 [ICLRErrorReportingManager:: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="3389a-111">A parameter of type `ECustomDumpFlavor` is passed to the [ICLRErrorReportingManager::BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3389a-112">要件</span><span class="sxs-lookup"><span data-stu-id="3389a-112">Requirements</span></span>  

 <span data-ttu-id="3389a-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3389a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3389a-114">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="3389a-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3389a-115">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3389a-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3389a-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3389a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3389a-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="3389a-117">See also</span></span>

- [<span data-ttu-id="3389a-118">ECustomDumpItemKind 列挙型</span><span class="sxs-lookup"><span data-stu-id="3389a-118">ECustomDumpItemKind Enumeration</span></span>](ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="3389a-119">ICLRErrorReportingManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3389a-119">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="3389a-120">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="3389a-120">Hosting Enumerations</span></span>](hosting-enumerations.md)
