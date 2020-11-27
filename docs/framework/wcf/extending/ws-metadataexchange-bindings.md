---
title: WS-MetadataExchange のバインディング
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 94f0ba602cd1f58f5491a44a64e24be8ea52895b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293989"
---
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="eee4d-102">WS-MetadataExchange のバインディング</span><span class="sxs-lookup"><span data-stu-id="eee4d-102">WS-MetadataExchange Bindings</span></span>

<span data-ttu-id="eee4d-103">ここでは、既定のメタデータ交換バインディングを各種のトランスポート用に構築する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="eee4d-103">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="eee4d-104">既定のバインディング</span><span class="sxs-lookup"><span data-stu-id="eee4d-104">The Default Bindings</span></span>  
  
|<span data-ttu-id="eee4d-105">既定のバインディング名</span><span class="sxs-lookup"><span data-stu-id="eee4d-105">Default Binding Name</span></span>|<span data-ttu-id="eee4d-106">バインディングを構築する方法</span><span class="sxs-lookup"><span data-stu-id="eee4d-106">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="eee4d-107">mexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="eee4d-107">mexHttpBinding</span></span>|<span data-ttu-id="eee4d-108">トランスポート レベルのセキュリティが無効な <xref:System.ServiceModel.WSHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="eee4d-108">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="eee4d-109">mexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="eee4d-109">mexHttpsBinding</span></span>|<span data-ttu-id="eee4d-110">トランスポート レベルのセキュリティをサポートする <xref:System.ServiceModel.WSHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="eee4d-110">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="eee4d-111">mexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="eee4d-111">mexNamedPipeBinding</span></span>|<span data-ttu-id="eee4d-112"><xref:System.ServiceModel.Channels.CustomBinding> で既定値を使用する <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="eee4d-112">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="eee4d-113">mexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="eee4d-113">mexTcpBinding</span></span>|<span data-ttu-id="eee4d-114"><xref:System.ServiceModel.Channels.CustomBinding> で既定値を使用する <xref:System.ServiceModel.Channels.TcpTransportBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="eee4d-114">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|
