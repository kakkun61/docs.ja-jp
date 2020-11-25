---
title: IHostSecurityContext インターフェイス
ms.date: 03/30/2017
api_name:
- IHostSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext
helpviewer_keywords:
- IHostSecurityContext interface [.NET Framework hosting]
ms.assetid: 88e2eac0-8ccb-404f-abbc-287d55159842
topic_type:
- apiref
ms.openlocfilehash: aafaa1d648396ddaa76193fa15cf7f74394777a9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724807"
---
# <a name="ihostsecuritycontext-interface"></a><span data-ttu-id="8f691-102">IHostSecurityContext インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8f691-102">IHostSecurityContext Interface</span></span>

<span data-ttu-id="8f691-103">共通言語ランタイム (CLR) が、ホストによって実装されたセキュリティコンテキスト情報を維持できるようにします。</span><span class="sxs-lookup"><span data-stu-id="8f691-103">Allows the common language runtime (CLR) to maintain security context information implemented by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8f691-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="8f691-104">Methods</span></span>  
  
|<span data-ttu-id="8f691-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="8f691-105">Method</span></span>|<span data-ttu-id="8f691-106">説明</span><span class="sxs-lookup"><span data-stu-id="8f691-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8f691-107">Capture メソッド</span><span class="sxs-lookup"><span data-stu-id="8f691-107">Capture Method</span></span>](ihostsecuritycontext-capture-method.md)|<span data-ttu-id="8f691-108">`IHostSecurityContext` [IHostSecurityManager:: GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md)への呼び出しから返されたインスタンスの複製を取得します。</span><span class="sxs-lookup"><span data-stu-id="8f691-108">Gets a clone of the `IHostSecurityContext` instance returned from a call to [IHostSecurityManager::GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f691-109">注釈</span><span class="sxs-lookup"><span data-stu-id="8f691-109">Remarks</span></span>  

 <span data-ttu-id="8f691-110">ホストは、CLR とユーザーコードの両方によって、スレッドトークンへのすべてのコードアクセスを制御できます。</span><span class="sxs-lookup"><span data-stu-id="8f691-110">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="8f691-111">また、完全なセキュリティコンテキスト情報が、制限されたコードアクセスで非同期操作またはコードポイント全体に渡されるようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="8f691-111">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="8f691-112">`IHostSecurityContext` このセキュリティコンテキスト情報をカプセル化します。この情報は、ランタイムに対して非透過的です。</span><span class="sxs-lookup"><span data-stu-id="8f691-112">`IHostSecurityContext` encapsulates this security context information, which is opaque to the runtime.</span></span> <span data-ttu-id="8f691-113">ランタイムはを使用してこの情報をキャプチャ `Capture` し、スレッドプールのワーカー項目のディスパッチ、ファイナライザーの実行、およびモジュールコンストラクターとクラスコンストラクター間で移動します。</span><span class="sxs-lookup"><span data-stu-id="8f691-113">The runtime captures this information using `Capture`, and moves it across thread pool worker item dispatch, finalizer execution, and module and class constructors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f691-114">要件</span><span class="sxs-lookup"><span data-stu-id="8f691-114">Requirements</span></span>  

 <span data-ttu-id="8f691-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f691-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f691-116">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="8f691-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8f691-117">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="8f691-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f691-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f691-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f691-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="8f691-119">See also</span></span>

- [<span data-ttu-id="8f691-120">ICLRHostProtectionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8f691-120">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="8f691-121">IHostSecurityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8f691-121">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="8f691-122">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8f691-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
