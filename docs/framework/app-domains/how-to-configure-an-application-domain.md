---
title: '方法: アプリケーション ドメインを構成する'
description: .NET のアプリケーション ドメインを構成します。 AppDomainSetup クラスを利用し、新しいアプリケーション ドメインの構成情報を CLR に提供できます。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, configuring
- ApplicationBase property
ms.assetid: 07ea8438-7a34-49f0-a7e8-3d6ff7e4a482
ms.openlocfilehash: bbda1f75da6b994c54cd71c56f16615a3758859b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271513"
---
# <a name="how-to-configure-an-application-domain"></a><span data-ttu-id="617df-104">方法: アプリケーション ドメインを構成する</span><span class="sxs-lookup"><span data-stu-id="617df-104">How to: Configure an Application Domain</span></span>

<span data-ttu-id="617df-105"><xref:System.AppDomainSetup> クラスを利用し、新しいアプリケーション ドメインの構成情報を共通言語ランタイムに提供できます。</span><span class="sxs-lookup"><span data-stu-id="617df-105">You can provide the common language runtime with configuration information for a new application domain using the <xref:System.AppDomainSetup> class.</span></span> <span data-ttu-id="617df-106">独自のアプリケーション ドメインを作成するとき、最も重要なプロパティが <xref:System.AppDomainSetup.ApplicationBase%2A> です。</span><span class="sxs-lookup"><span data-stu-id="617df-106">When creating your own application domains, the most important property is <xref:System.AppDomainSetup.ApplicationBase%2A>.</span></span> <span data-ttu-id="617df-107">その他の **AppDomainSetup** プロパティは、特定のアプリケーション ドメインを構成する目的で主にランタイム ホストにより使用されます。</span><span class="sxs-lookup"><span data-stu-id="617df-107">The other **AppDomainSetup** properties are used mainly by runtime hosts to configure a particular application domain.</span></span>  
  
 <span data-ttu-id="617df-108">**ApplicationBase** プロパティにより、アプリケーションのルート ディレクトリが定義されます。</span><span class="sxs-lookup"><span data-stu-id="617df-108">The **ApplicationBase** property defines the root directory of the application.</span></span> <span data-ttu-id="617df-109">ランタイムで型要求を満たす必要があるとき、**ApplicationBase** プロパティで指定されたディレクトリでその型を含むアセンブリが検索されます。</span><span class="sxs-lookup"><span data-stu-id="617df-109">When the runtime needs to satisfy a type request, it probes for the assembly containing the type in the directory specified by the **ApplicationBase** property.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="617df-110">新しいアプリケーション ドメインは、作成者の **ApplicationBase** プロパティのみを継承します。</span><span class="sxs-lookup"><span data-stu-id="617df-110">A new application domain inherits only the **ApplicationBase** property of the creator.</span></span>  
  
 <span data-ttu-id="617df-111">次の例では、**AppDomainSetup** クラスのインスタンスが作成され、このクラスを利用して新しいアプリケーション ドメインが作成され、情報がコンソールに書き込まれ、アプリケーション ドメインがアンロードされます。</span><span class="sxs-lookup"><span data-stu-id="617df-111">The following example creates an instance of the **AppDomainSetup** class, uses this class to create a new application domain, writes the information to console, and then unloads the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="617df-112">例</span><span class="sxs-lookup"><span data-stu-id="617df-112">Example</span></span>  

 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="617df-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="617df-113">See also</span></span>

- [<span data-ttu-id="617df-114">アプリケーション ドメインを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="617df-114">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="617df-115">アプリケーション ドメインの使用</span><span class="sxs-lookup"><span data-stu-id="617df-115">Using Application Domains</span></span>](use.md)
