---
title: IHostControl インターフェイス
ms.date: 03/30/2017
api_name:
- IHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl
helpviewer_keywords:
- IHostControl interface [.NET Framework hosting]
ms.assetid: a4ae0d1f-ade9-4b0a-a122-93ed11a5e6b3
topic_type:
- apiref
ms.openlocfilehash: 1bffef31702aa051d9ca865b18a67ac90c00cd00
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680660"
---
# <a name="ihostcontrol-interface"></a><span data-ttu-id="37c24-102">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="37c24-102">IHostControl Interface</span></span>

<span data-ttu-id="37c24-103">アセンブリの読み込みを構成し、ホストがサポートするホストインターフェイスを決定するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="37c24-103">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="37c24-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="37c24-104">Methods</span></span>  
  
|<span data-ttu-id="37c24-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="37c24-105">Method</span></span>|<span data-ttu-id="37c24-106">説明</span><span class="sxs-lookup"><span data-stu-id="37c24-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="37c24-107">GetHostManager メソッド</span><span class="sxs-lookup"><span data-stu-id="37c24-107">GetHostManager Method</span></span>](ihostcontrol-gethostmanager-method.md)|<span data-ttu-id="37c24-108">指定したを使用して、ホストのインターフェイスの実装へのインターフェイスポインターを取得し `IID` ます。</span><span class="sxs-lookup"><span data-stu-id="37c24-108">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>|  
|[<span data-ttu-id="37c24-109">SetAppDomainManager メソッド</span><span class="sxs-lookup"><span data-stu-id="37c24-109">SetAppDomainManager Method</span></span>](ihostcontrol-setappdomainmanager-method.md)|<span data-ttu-id="37c24-110">アプリケーションドメインが作成されたことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="37c24-110">Notifies the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="37c24-111">要件</span><span class="sxs-lookup"><span data-stu-id="37c24-111">Requirements</span></span>  

 <span data-ttu-id="37c24-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37c24-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37c24-113">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="37c24-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="37c24-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="37c24-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37c24-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37c24-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37c24-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="37c24-116">See also</span></span>

- <xref:System.AppDomainManager>
- [<span data-ttu-id="37c24-117">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="37c24-117">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- [<span data-ttu-id="37c24-118">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="37c24-118">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="37c24-119">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="37c24-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
