---
title: IGCHost2 インターフェイス
ms.date: 03/30/2017
api_name:
- IGCHost2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2
helpviewer_keywords:
- IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type:
- apiref
ms.openlocfilehash: 7529ecd215d74eb0eedbec8b90eba367ed20d56f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687744"
---
# <a name="igchost2-interface"></a><span data-ttu-id="dcb95-102">IGCHost2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dcb95-102">IGCHost2 Interface</span></span>

<span data-ttu-id="dcb95-103">ガベージコレクションシステムに関する情報を取得し、ガベージコレクションのいくつかの側面を制御するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="dcb95-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dcb95-104">新しい開発では、代わりに [ICLRGCManager2](iclrgcmanager2-interface.md) インターフェイスを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="dcb95-104">For new development, we recommend that you use the [ICLRGCManager2](iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dcb95-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="dcb95-105">Methods</span></span>  
  
|<span data-ttu-id="dcb95-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="dcb95-106">Method</span></span>|<span data-ttu-id="dcb95-107">説明</span><span class="sxs-lookup"><span data-stu-id="dcb95-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dcb95-108">SetGCStartupLimitsEx メソッド</span><span class="sxs-lookup"><span data-stu-id="dcb95-108">SetGCStartupLimitsEx Method</span></span>](igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="dcb95-109">ジェネレーション0のセグメントサイズと最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="dcb95-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="dcb95-110">より大きいジェネレーション0およびセグメントサイズを有効に `DWORD` します。</span><span class="sxs-lookup"><span data-stu-id="dcb95-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dcb95-111">要件</span><span class="sxs-lookup"><span data-stu-id="dcb95-111">Requirements</span></span>  

 <span data-ttu-id="dcb95-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dcb95-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcb95-113">**ヘッダー:** GCHost、GCHost</span><span class="sxs-lookup"><span data-stu-id="dcb95-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="dcb95-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="dcb95-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dcb95-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcb95-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcb95-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="dcb95-116">See also</span></span>

- [<span data-ttu-id="dcb95-117">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dcb95-117">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="dcb95-118">CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dcb95-118">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="dcb95-119">CorRuntimeHost コクラス</span><span class="sxs-lookup"><span data-stu-id="dcb95-119">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
