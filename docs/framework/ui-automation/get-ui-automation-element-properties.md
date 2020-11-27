---
title: UI オートメーション要素のプロパティの取得
description: UI オートメーション要素の現在またはキャッシュされているプロパティを取得する方法については、「」および「例」を参照してください。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
ms.openlocfilehash: 34a42355acce0beafbb9658baf6032e4e7e19fcb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276426"
---
# <a name="get-ui-automation-element-properties"></a><span data-ttu-id="67847-103">UI オートメーション要素のプロパティの取得</span><span class="sxs-lookup"><span data-stu-id="67847-103">Get UI Automation Element Properties</span></span>

> [!NOTE]
> <span data-ttu-id="67847-104">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="67847-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="67847-105">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="67847-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="67847-106">このトピックでは、要素のプロパティを取得する方法について説明 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="67847-106">This topic shows how to retrieve properties of a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element.</span></span>  
  
### <a name="get-a-current-property-value"></a><span data-ttu-id="67847-107">現在のプロパティ値を取得します。</span><span class="sxs-lookup"><span data-stu-id="67847-107">Get a Current Property Value</span></span>  
  
1. <span data-ttu-id="67847-108">取得するプロパティが含まれているを取得 <xref:System.Windows.Automation.AutomationElement> します。</span><span class="sxs-lookup"><span data-stu-id="67847-108">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span>  
  
2. <span data-ttu-id="67847-109">を呼び出す <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> か、 <xref:System.Windows.Automation.AutomationElement.Current%2A> プロパティ構造体を取得して、そのメンバーの1つから値を取得します。</span><span class="sxs-lookup"><span data-stu-id="67847-109">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Current%2A> property structure and get the value from one of its members.</span></span>  
  
### <a name="get-a-cached-property-value"></a><span data-ttu-id="67847-110">キャッシュされたプロパティ値を取得する</span><span class="sxs-lookup"><span data-stu-id="67847-110">Get a Cached Property Value</span></span>  
  
1. <span data-ttu-id="67847-111">取得するプロパティが含まれているを取得 <xref:System.Windows.Automation.AutomationElement> します。</span><span class="sxs-lookup"><span data-stu-id="67847-111">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span> <span data-ttu-id="67847-112">プロパティは、で指定されている必要があり <xref:System.Windows.Automation.CacheRequest> ます。</span><span class="sxs-lookup"><span data-stu-id="67847-112">The property must have been specified in the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="67847-113">を呼び出す <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> か、 <xref:System.Windows.Automation.AutomationElement.Cached%2A> プロパティ構造体を取得して、そのメンバーの1つから値を取得します。</span><span class="sxs-lookup"><span data-stu-id="67847-113">Call <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property structure and get the value from one of its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67847-114">例</span><span class="sxs-lookup"><span data-stu-id="67847-114">Example</span></span>  

 <span data-ttu-id="67847-115">次の例は、の現在のプロパティを取得するさまざまな方法を示して <xref:System.Windows.Automation.AutomationElement> います。</span><span class="sxs-lookup"><span data-stu-id="67847-115">The following example shows various ways to retrieve current properties of an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a><span data-ttu-id="67847-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="67847-116">See also</span></span>

- [<span data-ttu-id="67847-117">クライアントの UI オートメーション プロパティ</span><span class="sxs-lookup"><span data-stu-id="67847-117">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)
- [<span data-ttu-id="67847-118">UI オートメーションにおけるキャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="67847-118">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
- [<span data-ttu-id="67847-119">UI オートメーション クライアントにおけるキャッシュ</span><span class="sxs-lookup"><span data-stu-id="67847-119">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
