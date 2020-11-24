---
title: ICLRAssemblyReferenceList インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList
helpviewer_keywords:
- ICLRAssemblyReferenceList interface [.NET Framework hosting]
ms.assetid: 5f890fdf-d22a-429e-a35f-135273d1a636
topic_type:
- apiref
ms.openlocfilehash: a75235cd0ac0e55412f0ba58881796e3ebc801f1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679238"
---
# <a name="iclrassemblyreferencelist-interface"></a><span data-ttu-id="938b5-102">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="938b5-102">ICLRAssemblyReferenceList Interface</span></span>

<span data-ttu-id="938b5-103">ホストではなく、共通言語ランタイム (CLR) によって読み込まれるアセンブリの一覧を管理します。</span><span class="sxs-lookup"><span data-stu-id="938b5-103">Manages a list of assemblies that are loaded by the common language runtime (CLR) and not by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="938b5-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="938b5-104">Methods</span></span>  
  
|<span data-ttu-id="938b5-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="938b5-105">Method</span></span>|<span data-ttu-id="938b5-106">説明</span><span class="sxs-lookup"><span data-stu-id="938b5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="938b5-107">IsAssemblyReferenceInList メソッド</span><span class="sxs-lookup"><span data-stu-id="938b5-107">IsAssemblyReferenceInList Method</span></span>](iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|<span data-ttu-id="938b5-108">指定されたポインターがリスト内のアセンブリを参照しているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="938b5-108">Gets a value that indicates whether the supplied pointer references an assembly in the list.</span></span>|  
|[<span data-ttu-id="938b5-109">IsStringAssemblyReferenceInList メソッド</span><span class="sxs-lookup"><span data-stu-id="938b5-109">IsStringAssemblyReferenceInList Method</span></span>](iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|<span data-ttu-id="938b5-110">指定された名前がリスト内のアセンブリの名前と一致するかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="938b5-110">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="938b5-111">注釈</span><span class="sxs-lookup"><span data-stu-id="938b5-111">Remarks</span></span>  

 <span data-ttu-id="938b5-112">[ICLRAssemblyIdentityManager:: GetCLRAssemblyReferenceList](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)メソッドを呼び出して、のインスタンスへのポインターを取得 `ICLRAssemblyReferenceList` します。</span><span class="sxs-lookup"><span data-stu-id="938b5-112">Call the [ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) method to get a pointer to an instance of `ICLRAssemblyReferenceList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="938b5-113">要件</span><span class="sxs-lookup"><span data-stu-id="938b5-113">Requirements</span></span>  

 <span data-ttu-id="938b5-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="938b5-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="938b5-115">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="938b5-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="938b5-116">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="938b5-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="938b5-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="938b5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="938b5-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="938b5-118">See also</span></span>

- [<span data-ttu-id="938b5-119">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="938b5-119">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="938b5-120">IHostAssemblyStore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="938b5-120">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="938b5-121">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="938b5-121">Hosting Interfaces</span></span>](hosting-interfaces.md)
