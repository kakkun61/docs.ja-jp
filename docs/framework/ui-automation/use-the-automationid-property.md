---
title: AutomationID プロパティの使用
description: AutomationID プロパティを使用して UI オートメーションツリー内の要素を検索する方法とタイミングを示すシナリオとサンプルコードを確認します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutomationId property
- UI Automation, AutomationId property
- properties, AutomationId
ms.assetid: a24e807b-d7c3-4e93-ac48-80094c4e1c90
ms.openlocfilehash: 91254903b3481861f21d5e2f4e51f1e50726c46b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258596"
---
# <a name="use-the-automationid-property"></a><span data-ttu-id="23efb-103">AutomationID プロパティの使用</span><span class="sxs-lookup"><span data-stu-id="23efb-103">Use the AutomationID Property</span></span>

> [!NOTE]
> <span data-ttu-id="23efb-104">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="23efb-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="23efb-105">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="23efb-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="23efb-106">このトピックには、 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> を使用して [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー内の要素を配置する方法とタイミングを示すシナリオおよびサンプル コードが記載されています。</span><span class="sxs-lookup"><span data-stu-id="23efb-106">This topic contains scenarios and sample code that show how and when the <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> can be used to locate an element within the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree.</span></span>  
  
 <span data-ttu-id="23efb-107"><xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> は、UI オートメーション要素をその兄弟から一意に識別します。</span><span class="sxs-lookup"><span data-stu-id="23efb-107"><xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> uniquely identifies a UI Automation element from its siblings.</span></span> <span data-ttu-id="23efb-108">コントロール ID に関連するプロパティの識別子の詳細については、「 [UI Automation Properties Overview](ui-automation-properties-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23efb-108">For more information on property identifiers related to control identification, see [UI Automation Properties Overview](ui-automation-properties-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="23efb-109"><xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> では、ツリー全体で一意の ID は保証されません。これが役に立つには、通常、コンテナーとスコープ情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="23efb-109"><xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> does not guarantee a unique identity throughout the tree; it typically needs container and scope information to be useful.</span></span> <span data-ttu-id="23efb-110">たとえば、アプリケーションには複数のトップレベルのメニュー項目を持つメニュー コントロールが含まれ、さらに、それらのメニュー項目に複数の子メニュー項目が含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="23efb-110">For example, an application may contain a menu control with multiple top-level menu items that, in turn, have multiple child menu items.</span></span> <span data-ttu-id="23efb-111">これらの 2 次メニュー項目は、"Item1"、"Item 2" などの汎用スキームで識別され、トップレベルのメニュー項目間で子の識別子が重複することがあります。</span><span class="sxs-lookup"><span data-stu-id="23efb-111">These secondary menu items may be identified by a generic scheme such as "Item1", "Item 2", and so on, allowing duplicate identifiers for children across top-level menu items.</span></span>  
  
## <a name="scenarios"></a><span data-ttu-id="23efb-112">シナリオ</span><span class="sxs-lookup"><span data-stu-id="23efb-112">Scenarios</span></span>  

 <span data-ttu-id="23efb-113">要素を検索するときに、正確で一貫性のある結果を実現するために <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> の使用を必要とする 3 つの主な UI オートメーション クライアント アプリケーションのシナリオが識別されています。</span><span class="sxs-lookup"><span data-stu-id="23efb-113">Three primary UI Automation client application scenarios have been identified that require the use of <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> to achieve accurate and consistent results when searching for elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="23efb-114"><xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> は、最上位のアプリケーションウィンドウを除くコントロールビュー内のすべての UI オートメーション要素、 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] ID または x:Uid を持たないコントロールから派生した ui オートメーション要素、およびコントロール ID を持たない Win32 コントロールから派生した ui オートメーション要素によってサポートされます。</span><span class="sxs-lookup"><span data-stu-id="23efb-114"><xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> is supported by all UI Automation elements in the control view except top-level application windows, UI Automation elements derived from [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] controls that do not have an ID or x:Uid, and UI Automation elements derived from Win32 controls that do not have a control ID.</span></span>  
  
#### <a name="use-a-unique-and-discoverable-automationid-to-locate-a-specific-element-in-the-ui-automation-tree"></a><span data-ttu-id="23efb-115">一意で探索可能な AutomationID を使用して UI オートメーション ツリーで特定の要素を検索する</span><span class="sxs-lookup"><span data-stu-id="23efb-115">Use a unique and discoverable AutomationID to locate a specific element in the UI Automation tree</span></span>  
  
- <span data-ttu-id="23efb-116">UI Spy などのツールを使用して、 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> 目的の要素のを報告し [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="23efb-116">Use a tool such as UI Spy to report the <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> of a [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] element of interest.</span></span> <span data-ttu-id="23efb-117">この値をコピーし、その後の自動テストのテスト スクリプトなどのクライアント アプリケーションに貼り付けることができます。</span><span class="sxs-lookup"><span data-stu-id="23efb-117">This value can then be copied and pasted into a client application such as a test script for subsequent automated testing.</span></span> <span data-ttu-id="23efb-118">この方法により、実行時に要素を特定して検索するために必要なコードを削減して簡略化します。</span><span class="sxs-lookup"><span data-stu-id="23efb-118">This approach reduces and simplifies the code necessary to identify and locate an element at runtime.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="23efb-119">通常、 <xref:System.Windows.Automation.AutomationElement.RootElement%2A>の直接の子のみの取得を試行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="23efb-119">In general, you should try to obtain only direct children of the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>.</span></span> <span data-ttu-id="23efb-120">子孫の検索は、数百または数千もの要素を反復処理する場合があり、スタック オーバーフローを引き起こす可能性があります。</span><span class="sxs-lookup"><span data-stu-id="23efb-120">A search for descendants may iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="23efb-121">下位レベルの特定の要素を取得しようとする場合、アプリケーション ウィンドウから、または下位レベルのコンテナーから検索を開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="23efb-121">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
 [!code-csharp[UIAAutomationID_snip#100](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#100)]
 [!code-vb[UIAAutomationID_snip#100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#100)]  
  
#### <a name="use-a-persistent-path-to-return-to-a-previously-identified-automationelement"></a><span data-ttu-id="23efb-122">永続的なパスを使用して、既に特定されている AutomationElement に戻る</span><span class="sxs-lookup"><span data-stu-id="23efb-122">Use a persistent path to return to a previously identified AutomationElement</span></span>  
  
- <span data-ttu-id="23efb-123">クライアント アプリケーションは (単純なテスト スクリプトから、堅牢な記録と再生のためのユーティリティまで)、ファイルを開くダイアログやメニュー項目など、現在インスタンス化されていないために UI オートメーション ツリーに存在しない要素にアクセスしなければならないことがあります。</span><span class="sxs-lookup"><span data-stu-id="23efb-123">Client applications, from simple test scripts to robust record and playback utilities, may require access to elements that are not currently instantiated, such as a file open dialog or a menu item and therefore do not exist in the UI Automation tree.</span></span> <span data-ttu-id="23efb-124">これらの要素は、AutomationID、コントロールパターン、イベントリスナーなどの UI オートメーションプロパティを使用して、UI 操作の特定のシーケンスを再現または "再生" することによってのみインスタンス化できます。</span><span class="sxs-lookup"><span data-stu-id="23efb-124">These elements can only be instantiated by reproducing, or "playing back", a specific sequence of UI actions through the use of UI Automation properties such as AutomationID, control patterns, and event listeners.</span></span>
  
 [!code-csharp[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#uiaworkerthread)]
 [!code-vb[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#uiaworkerthread)]  
[!code-csharp[UIAAutomationID_snip#Playback](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#playback)]
[!code-vb[UIAAutomationID_snip#Playback](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#playback)]  
  
#### <a name="use-a-relative-path-to-return-to-a-previously-identified-automationelement"></a><span data-ttu-id="23efb-125">相対パスを使用して、既に特定されている AutomationElement に戻る</span><span class="sxs-lookup"><span data-stu-id="23efb-125">Use a relative path to return to a previously identified AutomationElement</span></span>  
  
- <span data-ttu-id="23efb-126">特定の状況では、AutomationID が兄弟間でのみ一意であることが保証されているので、UI オートメーション ツリー内の複数の要素が同一の AutomationID プロパティの値を持っていることがあります。</span><span class="sxs-lookup"><span data-stu-id="23efb-126">In certain circumstances, since AutomationID is only guaranteed to be unique amongst siblings, multiple elements in the UI Automation tree may have identical AutomationID property values.</span></span> <span data-ttu-id="23efb-127">このような場合、親 (または必要に応じて親の親) に基づいて、要素を一意に識別できます。</span><span class="sxs-lookup"><span data-stu-id="23efb-127">In these situations the elements can be uniquely identified based on a parent and, if necessary, a grandparent.</span></span> <span data-ttu-id="23efb-128">たとえば、開発者が複数のメニュー項目を持ち、それぞれに複数の子メニュー項目があるメニュー バーを提供するとします。ここで、子は "Item1"、"Item2" など、シーケンシャルの AutomationID で識別されます。</span><span class="sxs-lookup"><span data-stu-id="23efb-128">For example, a developer may provide a menu bar with multiple menu items each with multiple child menu items where the children are identified with sequential AutomationID's such as "Item1", "Item2", and so on.</span></span> <span data-ttu-id="23efb-129">各メニュー項目は、それ自体の AutomationID と、その親の AutomationID (必要に応じて親の親の AutomationID も) によって一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="23efb-129">Each menu item could then be uniquely identified by its AutomationID along with the AutomationID of its parent and, if necessary, its grandparent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23efb-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="23efb-130">See also</span></span>

- <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>
- [<span data-ttu-id="23efb-131">UI オートメーション ツリーの概要</span><span class="sxs-lookup"><span data-stu-id="23efb-131">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="23efb-132">プロパティ条件に基づく UI オートメーション要素の検索</span><span class="sxs-lookup"><span data-stu-id="23efb-132">Find a UI Automation Element Based on a Property Condition</span></span>](find-a-ui-automation-element-based-on-a-property-condition.md)
