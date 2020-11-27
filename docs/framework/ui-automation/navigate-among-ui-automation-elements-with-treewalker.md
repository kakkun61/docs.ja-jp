---
title: TreeWalker を使用した UI オートメーション要素間の移動
description: TreeWalker クラスを使用して UI オートメーション要素間を移動する方法を示すコード例を参照してください。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes, TreeWalker
- TreeWalker class
- elements, navigating among
- UI Automation, navigating among elements
ms.assetid: afcd21dc-2ffa-48c9-9332-51269f44b7e9
ms.openlocfilehash: e102e6ce258bef06d1fb44decfa1a3a27384e0bc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261216"
---
# <a name="navigate-among-ui-automation-elements-with-treewalker"></a><span data-ttu-id="74d55-103">TreeWalker を使用した UI オートメーション要素間の移動</span><span class="sxs-lookup"><span data-stu-id="74d55-103">Navigate Among UI Automation Elements with TreeWalker</span></span>

> [!NOTE]
> <span data-ttu-id="74d55-104">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="74d55-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="74d55-105">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="74d55-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="74d55-106">このトピックには、クラスを使用して要素間を移動する方法を示すコード例が含まれてい [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] <xref:System.Windows.Automation.TreeWalker> ます。</span><span class="sxs-lookup"><span data-stu-id="74d55-106">This topic contains example code that shows how to navigate among [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements by using the <xref:System.Windows.Automation.TreeWalker> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74d55-107">例</span><span class="sxs-lookup"><span data-stu-id="74d55-107">Example</span></span>  

 <span data-ttu-id="74d55-108">次の例では、を使用し <xref:System.Windows.Automation.TreeWalker.GetParent%2A> [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] て、ルート要素 (desktop) が見つかるまでツリーをウォークします。</span><span class="sxs-lookup"><span data-stu-id="74d55-108">The following example uses <xref:System.Windows.Automation.TreeWalker.GetParent%2A> to walk up the [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tree until it finds the root element, or desktop.</span></span> <span data-ttu-id="74d55-109">指定された要素の親ウィンドウである、そのすぐ下にある要素。</span><span class="sxs-lookup"><span data-stu-id="74d55-109">The element just below that is the parent window of the specified element.</span></span>  
  
 [!code-csharp[UIAFocusTracker_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFocusTracker_snip/CSharp/FocusTracker.cs#102)]
 [!code-vb[UIAFocusTracker_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFocusTracker_snip/VisualBasic/FocusTracker.vb#102)]  
  
## <a name="example"></a><span data-ttu-id="74d55-110">例</span><span class="sxs-lookup"><span data-stu-id="74d55-110">Example</span></span>  

 <span data-ttu-id="74d55-111">次の例では、およびを使用して <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> 、 <xref:System.Windows.Forms.TreeView> [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] コントロールビュー内にあり、有効になっている要素のサブツリー全体を表示するを作成します。</span><span class="sxs-lookup"><span data-stu-id="74d55-111">The following example uses <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> and <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> to create a <xref:System.Windows.Forms.TreeView> that shows an entire subtree of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements that are in the control view and that are enabled.</span></span>  
  
 [!code-csharp[UIAClient_snip#174](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#174)]
 [!code-vb[UIAClient_snip#174](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#174)]  
  
## <a name="see-also"></a><span data-ttu-id="74d55-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="74d55-112">See also</span></span>

- [<span data-ttu-id="74d55-113">UI オートメーション要素の取得</span><span class="sxs-lookup"><span data-stu-id="74d55-113">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
