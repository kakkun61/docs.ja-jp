---
title: IAppDomainBinding インターフェイス
ms.date: 03/30/2017
api_name:
- IAppDomainBinding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IAppDomainBinding
helpviewer_keywords:
- IAppDomainBinding interface [.NET Framework hosting]
ms.assetid: 368881ab-c4ea-4731-bf22-c596aac7c66c
topic_type:
- apiref
ms.openlocfilehash: 652739ad51e0a177f7b0fc6c0c9a11508c820bb3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721726"
---
# <a name="iappdomainbinding-interface"></a><span data-ttu-id="889cb-102">IAppDomainBinding インターフェイス</span><span class="sxs-lookup"><span data-stu-id="889cb-102">IAppDomainBinding Interface</span></span>

<span data-ttu-id="889cb-103">アプリケーションドメインが作成されたことをホストアプリケーションに通知するために、共通言語ランタイム (CLR) によって呼び出されるメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="889cb-103">Provides a method that is called by the common language runtime (CLR) to notify the host application that an application domain has been created.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="889cb-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="889cb-104">Methods</span></span>  
  
|<span data-ttu-id="889cb-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="889cb-105">Method</span></span>|<span data-ttu-id="889cb-106">説明</span><span class="sxs-lookup"><span data-stu-id="889cb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="889cb-107">OnAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="889cb-107">OnAppDomain Method</span></span>](iappdomainbinding-onappdomain-method.md)|<span data-ttu-id="889cb-108">アプリケーションドメインが作成されたことをホストに通知するために、共通言語ランタイム (CLR) によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="889cb-108">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="889cb-109">要件</span><span class="sxs-lookup"><span data-stu-id="889cb-109">Requirements</span></span>  

 <span data-ttu-id="889cb-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="889cb-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="889cb-111">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="889cb-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="889cb-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="889cb-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="889cb-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="889cb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="889cb-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="889cb-114">See also</span></span>

- [<span data-ttu-id="889cb-115">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="889cb-115">Hosting Interfaces</span></span>](hosting-interfaces.md)
