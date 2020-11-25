---
title: ICLRHostProtectionManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager
helpviewer_keywords:
- ICLRHostProtectionManager interface [.NET Framework hosting]
ms.assetid: ce2770ae-23d0-45d9-8bcf-46504ac5020e
topic_type:
- apiref
ms.openlocfilehash: e8ead998907d55b0bfbf82e5f6f4e7c504f657ec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714160"
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="5c696-102">ICLRHostProtectionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c696-102">ICLRHostProtectionManager Interface</span></span>

<span data-ttu-id="5c696-103">ホストが、部分的に信頼されたコードで実行される特定のマネージクラス、メソッド、プロパティ、およびフィールドをブロックできるようにします。</span><span class="sxs-lookup"><span data-stu-id="5c696-103">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5c696-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="5c696-104">Methods</span></span>  
  
|<span data-ttu-id="5c696-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="5c696-105">Method</span></span>|<span data-ttu-id="5c696-106">説明</span><span class="sxs-lookup"><span data-stu-id="5c696-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5c696-107">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="5c696-107">SetEagerSerializeGrantSets</span></span>](iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="5c696-108">致命的な共通言語ランタイム (CLR) エラーを引き起こす可能性のあるまれな競合状態が発生しないことを保証します。</span><span class="sxs-lookup"><span data-stu-id="5c696-108">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="5c696-109">SetProtectedCategories メソッド</span><span class="sxs-lookup"><span data-stu-id="5c696-109">SetProtectedCategories Method</span></span>](iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="5c696-110">部分的に信頼されたコードでの実行をブロックする必要がある、マネージ型とメンバーのカテゴリを指定します。</span><span class="sxs-lookup"><span data-stu-id="5c696-110">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5c696-111">要件</span><span class="sxs-lookup"><span data-stu-id="5c696-111">Requirements</span></span>  

 <span data-ttu-id="5c696-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c696-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c696-113">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="5c696-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5c696-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="5c696-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c696-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c696-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c696-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="5c696-116">See also</span></span>

- [<span data-ttu-id="5c696-117">EApiCategories 列挙型</span><span class="sxs-lookup"><span data-stu-id="5c696-117">EApiCategories Enumeration</span></span>](eapicategories-enumeration.md)
- [<span data-ttu-id="5c696-118">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c696-118">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
