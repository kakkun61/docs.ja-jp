---
title: ネットワーク アプリケーションでのキャッシュの構成
ms.date: 03/30/2017
helpviewer_keywords:
- cache [.NET Framework], configuring
ms.assetid: 3f694a1c-de5d-47cf-a6eb-cfc369fb8a9f
ms.openlocfilehash: 63340e6d7d8ef6b695050e24bc47cf1f0b9244c0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250581"
---
# <a name="configuring-caching-in-network-applications"></a><span data-ttu-id="c0fb9-102">ネットワーク アプリケーションでのキャッシュの構成</span><span class="sxs-lookup"><span data-stu-id="c0fb9-102">Configuring Caching in Network Applications</span></span>

<span data-ttu-id="c0fb9-103">キャッシュを構成するには、アプリケーションまたは <xref:System.Net.WebRequest> レベルでキャッシュ ポリシーを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0fb9-103">To configure caching, you must specify a cache policy at the application or <xref:System.Net.WebRequest> level.</span></span> <span data-ttu-id="c0fb9-104">以下のトピックでは、キャッシュを使用するようにアプリケーションと要求を構成するコード例が提供されています。</span><span class="sxs-lookup"><span data-stu-id="c0fb9-104">The following topics provide code examples that demonstrate configuring applications and requests to use caching.</span></span>  
  
- [<span data-ttu-id="c0fb9-105">方法: アプリケーションの場所ベースのキャッシュ ポリシーを設定する</span><span class="sxs-lookup"><span data-stu-id="c0fb9-105">How to: Set a Location-Based Cache Policy for an Application</span></span>](how-to-set-a-location-based-cache-policy-for-an-application.md)  
  
- [<span data-ttu-id="c0fb9-106">方法: アプリケーションの既定の時間ベースのキャッシュ ポリシーを設定する</span><span class="sxs-lookup"><span data-stu-id="c0fb9-106">How to: Set the Default Time-Based Cache Policy for an Application</span></span>](how-to-set-the-default-time-based-cache-policy-for-an-application.md)  
  
- [<span data-ttu-id="c0fb9-107">方法: 時間ベースのキャッシュ ポリシーをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="c0fb9-107">How to: Customize a Time-Based Cache Policy</span></span>](how-to-customize-a-time-based-cache-policy.md)  
  
- [<span data-ttu-id="c0fb9-108">方法: 要求のキャッシュ ポリシーを設定する</span><span class="sxs-lookup"><span data-stu-id="c0fb9-108">How to: Set Cache Policy for a Request</span></span>](how-to-set-cache-policy-for-a-request.md)  
  
 <span data-ttu-id="c0fb9-109">アプリケーションまたはマシン構成ファイルを使用して、キャッシュ ポリシーを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="c0fb9-109">You can also configure cache policy using application or machine configuration files.</span></span> <span data-ttu-id="c0fb9-110">詳細については、&#124;「[\<requestCaching> 要素 (ネットワーク設定)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c0fb9-110">For more information, see &#124; [\<requestCaching> Element (Network Settings)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0fb9-111">参照</span><span class="sxs-lookup"><span data-stu-id="c0fb9-111">See also</span></span>

- [<span data-ttu-id="c0fb9-112">ネットワーク アプリケーションのキャッシュ管理</span><span class="sxs-lookup"><span data-stu-id="c0fb9-112">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="c0fb9-113">キャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="c0fb9-113">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="c0fb9-114">場所ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="c0fb9-114">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="c0fb9-115">時間ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="c0fb9-115">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
