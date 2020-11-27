---
title: UI オートメーション イベントのサブスクライブ
description: 「UI オートメーションプロバイダーによって発生するイベントをサブスクライブする方法」を参照してください。 このコード例では、コントロールが呼び出されたときに発生するイベントのイベントハンドラーを登録します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, subscribing to events
- subscribing to UI Automation events
- events, subscribing to
- listening for events
ms.assetid: b688effa-b3e8-4b05-944d-05ed89a245aa
ms.openlocfilehash: 9005139be69621e83efc592721a238c28ea1f6e9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96252319"
---
# <a name="subscribe-to-ui-automation-events"></a><span data-ttu-id="88526-104">UI オートメーション イベントのサブスクライブ</span><span class="sxs-lookup"><span data-stu-id="88526-104">Subscribe to UI Automation Events</span></span>

> [!NOTE]
> <span data-ttu-id="88526-105">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="88526-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="88526-106">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="88526-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="88526-107">このトピックでは、UI オートメーション プロバイダーによって生成されるイベントをサブスクライブする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="88526-107">This topic shows how to subscribe to events raised by UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88526-108">例</span><span class="sxs-lookup"><span data-stu-id="88526-108">Example</span></span>  

 <span data-ttu-id="88526-109">次のコード例では、ボタンなどのコントロールが呼び出された場合に生成されるイベントに対してイベント ハンドラーを登録し、アプリケーション フォームが閉じられた時にそのイベント ハンドラーを削除します。</span><span class="sxs-lookup"><span data-stu-id="88526-109">The following example code registers an event handler for the event that is raised when a control such as a button is invoked, and removes it when the application form closes.</span></span> <span data-ttu-id="88526-110">イベントは、パラメーターとして <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A> に渡される <xref:System.Windows.Automation.AutomationEvent> によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="88526-110">The event is identified by an <xref:System.Windows.Automation.AutomationEvent> passed as a parameter to <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#101)]
 [!code-vb[UIAClient_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#101)]  
  
## <a name="example"></a><span data-ttu-id="88526-111">例</span><span class="sxs-lookup"><span data-stu-id="88526-111">Example</span></span>  

 <span data-ttu-id="88526-112">次の例は、[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] を使用して、フォーカスが変更された場合に生成されるイベントをサブスクライブする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="88526-112">The following example shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to subscribe to an event that is raised when the focus changes.</span></span> <span data-ttu-id="88526-113">イベント ハンドラーの登録は、アプリケーションのシャットダウン時に呼び出されるメソッドで解除されるか、UI イベントの通知が必要なくなった時に解除されます。</span><span class="sxs-lookup"><span data-stu-id="88526-113">The event handler is unregistered in a method that could be called on application shutdown, or when notification of UI events is no longer required.</span></span>  
  
 [!code-csharp[UIAClient_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#102)]
 [!code-vb[UIAClient_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="88526-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="88526-114">See also</span></span>

- <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>
- <xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>
- <xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>
- [<span data-ttu-id="88526-115">UI オートメーション イベントの概要</span><span class="sxs-lookup"><span data-stu-id="88526-115">UI Automation Events Overview</span></span>](ui-automation-events-overview.md)
