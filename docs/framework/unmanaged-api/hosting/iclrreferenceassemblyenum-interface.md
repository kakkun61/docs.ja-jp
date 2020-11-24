---
title: ICLRReferenceAssemblyEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRReferenceAssemblyEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRReferenceAssemblyEnum
helpviewer_keywords:
- ICLRReferenceAssemblyEnum interface [.NET Framework hosting]
ms.assetid: 8adbf092-c3ba-4bee-b25b-0de6e43a4ce5
topic_type:
- apiref
ms.openlocfilehash: 189fbb1943d049dc4f52ea6cb626c02e9e25b3c7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686143"
---
# <a name="iclrreferenceassemblyenum-interface"></a><span data-ttu-id="bb6a3-102">ICLRReferenceAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb6a3-102">ICLRReferenceAssemblyEnum Interface</span></span>

<span data-ttu-id="bb6a3-103">共通言語ランタイム (CLR) の内部にあるアセンブリ id データを使用して、ファイルまたはストリームによって参照されるアセンブリのセットをホストが操作できるようにするメソッドを提供します。これらの id を作成したり、理解したりする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="bb6a3-103">Provides methods that allow the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the common language runtime (CLR), without needing to create or understand those identities.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bb6a3-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="bb6a3-104">Methods</span></span>  
  
|<span data-ttu-id="bb6a3-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="bb6a3-105">Method</span></span>|<span data-ttu-id="bb6a3-106">説明</span><span class="sxs-lookup"><span data-stu-id="bb6a3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bb6a3-107">Get メソッド</span><span class="sxs-lookup"><span data-stu-id="bb6a3-107">Get Method</span></span>](iclrreferenceassemblyenum-get-method.md)|<span data-ttu-id="bb6a3-108">指定されたインデックス位置にあるアセンブリ id を取得します。</span><span class="sxs-lookup"><span data-stu-id="bb6a3-108">Gets the assembly identity at the supplied index.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bb6a3-109">要件</span><span class="sxs-lookup"><span data-stu-id="bb6a3-109">Requirements</span></span>  

 <span data-ttu-id="bb6a3-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb6a3-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb6a3-111">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="bb6a3-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bb6a3-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="bb6a3-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb6a3-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb6a3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb6a3-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb6a3-114">See also</span></span>

- [<span data-ttu-id="bb6a3-115">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb6a3-115">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="bb6a3-116">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb6a3-116">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="bb6a3-117">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb6a3-117">Hosting Interfaces</span></span>](hosting-interfaces.md)
