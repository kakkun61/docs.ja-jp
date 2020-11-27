---
title: プロパティ条件に基づく UI オートメーション要素の検索
description: プロパティ条件に基づいて UI オートメーション要素を検索します。 特定のプロパティまたはプロパティに基づいて、UI オートメーションツリー内の要素を検索します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
ms.openlocfilehash: 603ecf5375af919a558168e14792035a16fb20f2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276491"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a><span data-ttu-id="d2754-104">プロパティ条件に基づく UI オートメーション要素の検索</span><span class="sxs-lookup"><span data-stu-id="d2754-104">Find a UI Automation Element Based on a Property Condition</span></span>

> [!NOTE]
> <span data-ttu-id="d2754-105">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="d2754-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d2754-106">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d2754-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="d2754-107">このトピックに [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] は、特定のプロパティまたはプロパティに基づいてツリー内の要素を検索する方法を示すコード例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d2754-107">This topic contains example code that shows how to locate an element within the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree based on a specific property or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2754-108">例</span><span class="sxs-lookup"><span data-stu-id="d2754-108">Example</span></span>  

 <span data-ttu-id="d2754-109">次の例では、ツリー内の関心のある要素 (または要素) を識別する一連のプロパティ条件を指定してい <xref:System.Windows.Automation.AutomationElement> ます。</span><span class="sxs-lookup"><span data-stu-id="d2754-109">In the following example, a set of property conditions are specified that identify a certain element (or elements) of interest in the <xref:System.Windows.Automation.AutomationElement> tree.</span></span> <span data-ttu-id="d2754-110">次に、一致するすべての要素の検索が、 <xref:System.Windows.Automation.AutomationElement.FindAll%2A> <xref:System.Windows.Automation.AndCondition> 一致する要素の数を制限する一連のブール演算を組み込むメソッドを使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="d2754-110">A search for all matching elements is then performed with the <xref:System.Windows.Automation.AutomationElement.FindAll%2A> method that incorporates a series of <xref:System.Windows.Automation.AndCondition> boolean operations to limit the number of matching elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d2754-111">から検索する場合 <xref:System.Windows.Automation.AutomationElement.RootElement%2A> は、直接の子のみを取得するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="d2754-111">When searching from the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, you should try to obtain only direct children.</span></span> <span data-ttu-id="d2754-112">子孫の検索では、数百または数千の要素を反復処理することがあります。その結果、スタックオーバーフローが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d2754-112">A search for descendants might iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="d2754-113">下位レベルの特定の要素を取得しようとする場合、アプリケーション ウィンドウから、または下位レベルのコンテナーから検索を開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2754-113">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a><span data-ttu-id="d2754-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2754-114">See also</span></span>

- <span data-ttu-id="d2754-115">[InvokePattern と ExpandCollapsePattern のメニュー項目のサンプル](/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d2754-115">[InvokePattern and ExpandCollapsePattern Menu Item Sample](/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span></span>
- [<span data-ttu-id="d2754-116">UI オートメーション要素の取得</span><span class="sxs-lookup"><span data-stu-id="d2754-116">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
- [<span data-ttu-id="d2754-117">AutomationID プロパティの使用</span><span class="sxs-lookup"><span data-stu-id="d2754-117">Use the AutomationID Property</span></span>](use-the-automationid-property.md)
