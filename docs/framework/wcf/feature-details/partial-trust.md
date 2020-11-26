---
title: 部分信頼
ms.date: 03/30/2017
ms.assetid: 489b1587-9909-4d0e-8c1a-5e83c8f8292b
ms.openlocfilehash: 844fa65bbb2858fc961091614ba581265bc08be5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247968"
---
# <a name="partial-trust"></a><span data-ttu-id="5afd7-102">部分信頼</span><span class="sxs-lookup"><span data-stu-id="5afd7-102">Partial Trust</span></span>

<span data-ttu-id="5afd7-103">.NET Framework 3.5 以降、部分的に信頼された呼び出し元は、、、およびで実装されているパブリック型とメソッドにアクセスでき <xref:System.ServiceModel> <xref:System.Runtime.Serialization> <xref:System.ServiceModel.Web> ます。</span><span class="sxs-lookup"><span data-stu-id="5afd7-103">Starting with the .NET Framework 3.5, partially trusted callers can access public types and methods implemented in <xref:System.ServiceModel>, <xref:System.Runtime.Serialization>, and <xref:System.ServiceModel.Web>.</span></span> <span data-ttu-id="5afd7-104">このセクションでは、部分的に信頼されたアプリケーション内で Windows Communication Foundation (WCF) を使用するためのサポートされるシナリオと、コードアクセスセキュリティ (CAS) のアクセス許可が低下して実行されるアプリケーションで使用できる WCF 機能の限られたサブセットについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5afd7-104">This section describes supported scenarios for using Windows Communication Foundation (WCF) within a partially trusted application as well as the limited subset of WCF functionality available to applications running with reduced code access security (CAS) permissions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5afd7-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="5afd7-105">In This Section</span></span>  

 [<span data-ttu-id="5afd7-106">サポートされている配置シナリオ</span><span class="sxs-lookup"><span data-stu-id="5afd7-106">Supported Deployment Scenarios</span></span>](supported-deployment-scenarios.md)  
 <span data-ttu-id="5afd7-107">WCF を実行するための主な部分信頼のシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5afd7-107">Describes the main partial trust scenarios for running WCF.</span></span>  
  
 [<span data-ttu-id="5afd7-108">部分信頼機能の互換性</span><span class="sxs-lookup"><span data-stu-id="5afd7-108">Partial Trust Feature Compatibility</span></span>](partial-trust-feature-compatibility.md)  
 <span data-ttu-id="5afd7-109">部分信頼で使用できない WCF 機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="5afd7-109">Describes the WCF features that cannot be used with partial trust.</span></span>  
  
 [<span data-ttu-id="5afd7-110">部分信頼のベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="5afd7-110">Partial Trust Best Practices</span></span>](partial-trust-best-practices.md)  
 <span data-ttu-id="5afd7-111">部分的に信頼されたアプリケーションで WCF を使用するためのベストプラクティスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5afd7-111">Contains best practices for using WCF in partially trusted applications.</span></span>
