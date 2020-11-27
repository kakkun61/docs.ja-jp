---
title: UI オートメーションを使用した、チェック ボックスのトグル状態の取得
description: Microsoft UI オートメーションを使用して、コントロール (チェックボックスなど) のトグル状態を取得する方法を示すコード例を参照してください。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, getting toggle states of check boxes
- check boxes, getting toggle states of
- getting, toggle states of check boxes
ms.assetid: 84fc31a3-175f-4e93-90a0-dd29d89b77ce
ms.openlocfilehash: 2ec0cc996461b13d0ddc3453188eeb3287a56be7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276439"
---
# <a name="get-the-toggle-state-of-a-check-box-using-ui-automation"></a><span data-ttu-id="5aed6-103">UI オートメーションを使用した、チェック ボックスのトグル状態の取得</span><span class="sxs-lookup"><span data-stu-id="5aed6-103">Get the Toggle State of a Check Box Using UI Automation</span></span>

> [!NOTE]
> <span data-ttu-id="5aed6-104">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="5aed6-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="5aed6-105">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5aed6-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="5aed6-106">このトピックでは、を使用し [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] て、コントロールのトグル状態を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5aed6-106">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to get the toggle state of a control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5aed6-107">例</span><span class="sxs-lookup"><span data-stu-id="5aed6-107">Example</span></span>  

 <span data-ttu-id="5aed6-108">この例では、 <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> クラスのメソッドを使用し <xref:System.Windows.Automation.AutomationElement> て、 <xref:System.Windows.Automation.TogglePattern> コントロールからオブジェクトを取得し、そのプロパティを返し <xref:System.Windows.Automation.ToggleState> ます。</span><span class="sxs-lookup"><span data-stu-id="5aed6-108">This example uses the <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> method of the <xref:System.Windows.Automation.AutomationElement> class to obtain a <xref:System.Windows.Automation.TogglePattern> object from a control and return its <xref:System.Windows.Automation.ToggleState> property.</span></span>  
  
 [!code-csharp[NavigatingWithTreeWalker#1200](../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigatingWithTreeWalker/CSharp/ClientClass.cs#1200)]
 [!code-vb[NavigatingWithTreeWalker#1200](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigatingWithTreeWalker/visualbasic/clientclass.vb#1200)]
