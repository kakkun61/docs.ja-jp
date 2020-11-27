---
title: リスト項目の UI オートメーション要素の検索
description: 項目のインデックスがわかっている場合に、リスト項目の UI オートメーション要素を検索する方法を示す例を参照してください。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items, finding elements for
- elements, finding for list items
- UI Automation, finding elements for List items
ms.assetid: c326ad2b-2144-4f64-ae4c-d850c74f95c5
ms.openlocfilehash: 95f6b558cc53b00701232f247f8de7f8c603e3ac
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276478"
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a><span data-ttu-id="e7255-103">リスト項目の UI オートメーション要素の検索</span><span class="sxs-lookup"><span data-stu-id="e7255-103">Find a UI Automation Element for a List Item</span></span>

> [!NOTE]
> <span data-ttu-id="e7255-104">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="e7255-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e7255-105">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e7255-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="e7255-106">このトピックで <xref:System.Windows.Automation.AutomationElement> は、項目のインデックスがわかっている場合に、リスト内の項目のを取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e7255-106">This topic shows how to retrieve an <xref:System.Windows.Automation.AutomationElement> for an item within a list when the index of the item is known.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7255-107">例</span><span class="sxs-lookup"><span data-stu-id="e7255-107">Example</span></span>  

 <span data-ttu-id="e7255-108">次の例では、指定した項目をリストから取得する2つの方法を示します。1つはを使用し、もう1つ <xref:System.Windows.Automation.TreeWalker> はを使用し <xref:System.Windows.Automation.AutomationElement.FindAll%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="e7255-108">The following example shows two ways of retrieving a specified item from a list, one using <xref:System.Windows.Automation.TreeWalker> and the other using <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.</span></span>  
  
 <span data-ttu-id="e7255-109">最初の手法は Win32 コントロールではより高速になる傾向がありますが、2番目の方法は Windows Presentation Foundation (WPF) コントロールではより高速です。</span><span class="sxs-lookup"><span data-stu-id="e7255-109">The first technique tends to be faster for Win32 controls, but the second is faster for Windows Presentation Foundation (WPF) controls.</span></span>  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a><span data-ttu-id="e7255-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="e7255-110">See also</span></span>

- [<span data-ttu-id="e7255-111">UI オートメーション要素の取得</span><span class="sxs-lookup"><span data-stu-id="e7255-111">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
