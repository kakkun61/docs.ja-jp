---
title: 4802 - DiscoveryClientProtocolExceptionSuppressed
ms.date: 03/30/2017
ms.assetid: 568212f7-1060-4f5c-a7a0-1352c7cc743b
ms.openlocfilehash: e840c5d2e28a5240570a11e8edffe963d54b1e2c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242618"
---
# <a name="4802---discoveryclientprotocolexceptionsuppressed"></a><span data-ttu-id="03f0b-102">4802 - DiscoveryClientProtocolExceptionSuppressed</span><span class="sxs-lookup"><span data-stu-id="03f0b-102">4802 - DiscoveryClientProtocolExceptionSuppressed</span></span>

## <a name="properties"></a><span data-ttu-id="03f0b-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="03f0b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="03f0b-104">ID</span><span class="sxs-lookup"><span data-stu-id="03f0b-104">ID</span></span>|<span data-ttu-id="03f0b-105">4802</span><span class="sxs-lookup"><span data-stu-id="03f0b-105">4802</span></span>|  
|<span data-ttu-id="03f0b-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="03f0b-106">Keywords</span></span>|<span data-ttu-id="03f0b-107">探索</span><span class="sxs-lookup"><span data-stu-id="03f0b-107">Discovery</span></span>|  
|<span data-ttu-id="03f0b-108">Level</span><span class="sxs-lookup"><span data-stu-id="03f0b-108">Level</span></span>|<span data-ttu-id="03f0b-109">情報</span><span class="sxs-lookup"><span data-stu-id="03f0b-109">Information</span></span>|  
|<span data-ttu-id="03f0b-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="03f0b-110">Channel</span></span>|<span data-ttu-id="03f0b-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="03f0b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="03f0b-112">Description</span><span class="sxs-lookup"><span data-stu-id="03f0b-112">Description</span></span>  

 <span data-ttu-id="03f0b-113">このイベントは DiscoveryClient の終了中に ProtocolException が抑制されたときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="03f0b-113">This event is emitted when the a ProtocolException was suppressed while closing the DiscoveryClient.</span></span>  
  
## <a name="message"></a><span data-ttu-id="03f0b-114">Message</span><span class="sxs-lookup"><span data-stu-id="03f0b-114">Message</span></span>  

 <span data-ttu-id="03f0b-115">DiscoveryClient を閉じているときに ProtocolException が抑制されました。</span><span class="sxs-lookup"><span data-stu-id="03f0b-115">A ProtocolException was suppressed while closing the DiscoveryClient.</span></span> <span data-ttu-id="03f0b-116">その理由として、DiscoveryService がまだ DiscoveryClient に応答を送信しようとしていることが考えられます。</span><span class="sxs-lookup"><span data-stu-id="03f0b-116">This could be because a DiscoveryService is still trying to send response to the DiscoveryClient.</span></span>  
  
## <a name="details"></a><span data-ttu-id="03f0b-117">詳細</span><span class="sxs-lookup"><span data-stu-id="03f0b-117">Details</span></span>
