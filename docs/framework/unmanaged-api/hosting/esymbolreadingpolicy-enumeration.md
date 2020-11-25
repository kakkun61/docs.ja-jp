---
title: ESymbolReadingPolicy 列挙型
ms.date: 03/30/2017
api_name:
- ESymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ESymbolReadingPolicy
helpviewer_keywords:
- ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type:
- apiref
ms.openlocfilehash: 42ce1f02294db98c5c593a5f16de5226703d5f9d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733712"
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="68a29-102">ESymbolReadingPolicy 列挙型</span><span class="sxs-lookup"><span data-stu-id="68a29-102">ESymbolReadingPolicy Enumeration</span></span>

<span data-ttu-id="68a29-103">プログラムデータベース (PDB) ファイルを読み取るためのポリシーを設定する値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="68a29-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68a29-104">構文</span><span class="sxs-lookup"><span data-stu-id="68a29-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="68a29-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="68a29-105">Members</span></span>  
  
|<span data-ttu-id="68a29-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="68a29-106">Member</span></span>|<span data-ttu-id="68a29-107">説明</span><span class="sxs-lookup"><span data-stu-id="68a29-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="68a29-108">デバッガーが常に PDB ファイルを読み取る必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="68a29-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="68a29-109">デバッガーが、完全に信頼されたアセンブリに関連付けられている PDB ファイルのみを読み取るように指定します。</span><span class="sxs-lookup"><span data-stu-id="68a29-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="68a29-110">デバッガーが PDB ファイルを読み取らないように指定します。</span><span class="sxs-lookup"><span data-stu-id="68a29-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68a29-111">注釈</span><span class="sxs-lookup"><span data-stu-id="68a29-111">Remarks</span></span>  

 <span data-ttu-id="68a29-112">`ESymbolReadingPolicy`列挙体は、 [ICLRDebugManager:: SetSymbolReadingPolicy](iclrdebugmanager-setsymbolreadingpolicy-method.md)メソッドと共に使用されます。</span><span class="sxs-lookup"><span data-stu-id="68a29-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68a29-113">要件</span><span class="sxs-lookup"><span data-stu-id="68a29-113">Requirements</span></span>  

 <span data-ttu-id="68a29-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68a29-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68a29-115">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="68a29-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="68a29-116">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="68a29-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68a29-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68a29-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68a29-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="68a29-118">See also</span></span>

- [<span data-ttu-id="68a29-119">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="68a29-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
