---
title: ICLRAssemblyReferenceList::IsAssemblyReferenceInList メソッド
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList.IsAssemblyReferenceInList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList method [.NET Framework hosting]
- IsAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: 8a570813-21be-407e-92a6-7ae8de3bc728
topic_type:
- apiref
ms.openlocfilehash: f74e0f111ff7869d0bfed61d420f3788f65876dc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679157"
---
# <a name="iclrassemblyreferencelistisassemblyreferenceinlist-method"></a><span data-ttu-id="1aa62-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList メソッド</span><span class="sxs-lookup"><span data-stu-id="1aa62-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Method</span></span>

<span data-ttu-id="1aa62-103">指定されたポインターがリスト内のアセンブリを参照しているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="1aa62-103">Gets a value that indicates whether the supplied pointer refers to an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1aa62-104">構文</span><span class="sxs-lookup"><span data-stu-id="1aa62-104">Syntax</span></span>  
  
```cpp  
HRESULT IsAssemblyReferenceInList (  
    [in] IUnknown *pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1aa62-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1aa62-105">Parameters</span></span>  

 `pName`  
 <span data-ttu-id="1aa62-106">から検索対象のアセンブリへのインターフェイスポインター。</span><span class="sxs-lookup"><span data-stu-id="1aa62-106">[in] An interface pointer to the assembly for which to search.</span></span> <span data-ttu-id="1aa62-107">有効な値は `IAssemblyName` 、型または型です `IReferenceIdentity` 。</span><span class="sxs-lookup"><span data-stu-id="1aa62-107">Valid values are of type `IAssemblyName` or `IReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1aa62-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="1aa62-108">Return Value</span></span>  
  
|<span data-ttu-id="1aa62-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1aa62-109">HRESULT</span></span>|<span data-ttu-id="1aa62-110">説明</span><span class="sxs-lookup"><span data-stu-id="1aa62-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1aa62-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="1aa62-111">S_OK</span></span>|<span data-ttu-id="1aa62-112">文字列が一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="1aa62-112">The string appears in the list.</span></span>|  
|<span data-ttu-id="1aa62-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1aa62-113">S_FALSE</span></span>|<span data-ttu-id="1aa62-114">文字列は一覧に表示されません。</span><span class="sxs-lookup"><span data-stu-id="1aa62-114">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="1aa62-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1aa62-115">E_FAIL</span></span>|<span data-ttu-id="1aa62-116">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="1aa62-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1aa62-117">メソッドが E_FAIL を返すと、そのプロセス内で共通言語ランタイムは使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="1aa62-117">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="1aa62-118">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="1aa62-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1aa62-119">要件</span><span class="sxs-lookup"><span data-stu-id="1aa62-119">Requirements</span></span>  

 <span data-ttu-id="1aa62-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1aa62-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1aa62-121">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="1aa62-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1aa62-122">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="1aa62-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1aa62-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1aa62-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aa62-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="1aa62-124">See also</span></span>

- [<span data-ttu-id="1aa62-125">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1aa62-125">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="1aa62-126">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1aa62-126">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="1aa62-127">IHostAssemblyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1aa62-127">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="1aa62-128">IHostAssemblyStore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1aa62-128">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
