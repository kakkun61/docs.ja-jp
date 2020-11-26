---
title: クライアントの UI オートメーション コントロール パターン
description: UI オートメーションクライアントのコントロールパターンの概要について説明します。 ユーザーインターフェイス (UI) に関する情報にアクセスするには、コントロールパターンを使用します。
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
ms.openlocfilehash: 3f58e9909b18681b3a0acf9332cc0c7c604e2002
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241968"
---
# <a name="ui-automation-control-patterns-for-clients"></a><span data-ttu-id="2f91d-104">クライアントの UI オートメーション コントロール パターン</span><span class="sxs-lookup"><span data-stu-id="2f91d-104">UI Automation Control Patterns for Clients</span></span>

> [!NOTE]
> <span data-ttu-id="2f91d-105">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="2f91d-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="2f91d-106">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2f91d-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="2f91d-107">この概要では、UI オートメーション クライアントのコントロール パターンについて説明します。</span><span class="sxs-lookup"><span data-stu-id="2f91d-107">This overview introduces control patterns for UI Automation clients.</span></span> <span data-ttu-id="2f91d-108">また、UI オートメーション クライアントがコントロール パターンを使用して、 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]の情報にアクセスするしくみについても説明します。</span><span class="sxs-lookup"><span data-stu-id="2f91d-108">It includes information on how a UI Automation client can use control patterns to access information about the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="2f91d-109">コントロール パターンは、コントロール型や外観に関係なく、コントロールの機能を分類したり公開したりするための手段です。</span><span class="sxs-lookup"><span data-stu-id="2f91d-109">Control patterns provide a way to categorize and expose a control's functionality independent of the control type or the appearance of the control.</span></span> <span data-ttu-id="2f91d-110">UI オートメーション クライアントは、 <xref:System.Windows.Automation.AutomationElement> を調べてどのコントロール パターンがサポートされているかを特定し、そのコントロールの動作を確実に実行することができます。</span><span class="sxs-lookup"><span data-stu-id="2f91d-110">UI Automation clients can examine an <xref:System.Windows.Automation.AutomationElement> to determine which control patterns are supported and be assured of the behavior of the control.</span></span>  
  
 <span data-ttu-id="2f91d-111">コントロール パターンの完全なリストについては、「 [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2f91d-111">For a complete list of control patterns, see [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md).</span></span>  
  
<a name="uiautomation_getting_control_patterns"></a>

## <a name="getting-control-patterns"></a><span data-ttu-id="2f91d-112">コントロール パターンの取得</span><span class="sxs-lookup"><span data-stu-id="2f91d-112">Getting Control Patterns</span></span>  

 <span data-ttu-id="2f91d-113">クライアントは、 <xref:System.Windows.Automation.AutomationElement> または <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> を呼び出して、 <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>からコントロール パターンを取得します。</span><span class="sxs-lookup"><span data-stu-id="2f91d-113">Clients retrieve a control pattern from an <xref:System.Windows.Automation.AutomationElement> by calling either <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> or <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="2f91d-114">クライアントは、 <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> メソッドまたは個別の `IsPatternAvailable` プロパティ ( <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>など) を使用して、パターンまたはパターンのグループが <xref:System.Windows.Automation.AutomationElement>でサポートされているかどうかを特定できます。</span><span class="sxs-lookup"><span data-stu-id="2f91d-114">Clients can use the <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> method or an individual `IsPatternAvailable` property (for example, <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>) to determine if a pattern or group of patterns is supported on the <xref:System.Windows.Automation.AutomationElement>.</span></span> <span data-ttu-id="2f91d-115">ただし、サポートされているプロパティを確認してコントロール パターンを取得するよりも、コントロール パターンを取得して `null` 参照に対するテストを試行する方が、プロセス間呼び出しが少なくなるため効率的です。</span><span class="sxs-lookup"><span data-stu-id="2f91d-115">However, it is more efficient to attempt to get the control pattern and test for a `null` reference than to check the supported properties and retrieve the control pattern since it results in fewer cross-process calls.</span></span>  
  
 <span data-ttu-id="2f91d-116"><xref:System.Windows.Automation.TextPattern> から <xref:System.Windows.Automation.AutomationElement>コントロール パターンを取得する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="2f91d-116">The following example demonstrates how to get a <xref:System.Windows.Automation.TextPattern> control pattern from an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>

## <a name="retrieving-properties-on-control-patterns"></a><span data-ttu-id="2f91d-117">コントロール パターンのプロパティの取得</span><span class="sxs-lookup"><span data-stu-id="2f91d-117">Retrieving Properties on Control Patterns</span></span>  

 <span data-ttu-id="2f91d-118">クライアントは、 <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> または <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> を呼び出し、返されたオブジェクトを適切な型にキャストすることで、コントロール パターンのプロパティ値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="2f91d-118">Clients can retrieve the property values on control patterns by calling either <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> or <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> and casting the object returned to an appropriate type.</span></span> <span data-ttu-id="2f91d-119">プロパティの詳細につい [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ては、「 [クライアントの UI オートメーションのプロパティ](ui-automation-properties-for-clients.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f91d-119">For more information on [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] properties, see [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).</span></span>  
  
 <span data-ttu-id="2f91d-120">メソッドだけで `GetPropertyValue` なく、共通言語ランタイム (CLR) アクセサーを使用してプロパティ値を取得し、パターンのプロパティにアクセスすることもでき [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="2f91d-120">In addition to the `GetPropertyValue` methods, property values can be retrieved through the common language runtime (CLR) accessors to access the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] properties on a pattern.</span></span>  
  
<a name="uiautomation_with_variable_patterns"></a>

## <a name="controls-with-variable-patterns"></a><span data-ttu-id="2f91d-121">変数パターンを持つコントロール</span><span class="sxs-lookup"><span data-stu-id="2f91d-121">Controls with Variable Patterns</span></span>  

 <span data-ttu-id="2f91d-122">一部のコントロール型は、状態やコントロールの使用方法に応じた複数のパターンをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="2f91d-122">Some control types support different patterns depending on their state or the manner in which the control is being used.</span></span> <span data-ttu-id="2f91d-123">変数パターンを持つコントロールの例としては、リストビュー (サムネイル、タイル、アイコン、リスト、詳細)、Microsoft Excel グラフ (円、線、横棒、数式を使用したセル値)、Microsoft Word のドキュメント領域 (標準、Web レイアウト、アウトライン、印刷レイアウト、印刷プレビュー)、および Microsoft Windows Media Player スキンなどがあります。</span><span class="sxs-lookup"><span data-stu-id="2f91d-123">Examples of controls that can have variable patterns are list views (thumbnails, tiles, icons, list, details), Microsoft Excel Charts (Pie, Line, Bar, Cell Value with a formula), Microsoft Word's document area (Normal, Web Layout, Outline, Print Layout, Print Preview), and Microsoft Windows Media Player skins.</span></span>  
  
 <span data-ttu-id="2f91d-124">カスタム コントロール型を実装するコントロールは、機能を表すために必要なコントロール パターンの任意のセットを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="2f91d-124">Controls implementing custom control types can have any set of control patterns that are needed to represent their functionality.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f91d-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f91d-125">See also</span></span>

- [<span data-ttu-id="2f91d-126">UI オートメーション コントロール パターン</span><span class="sxs-lookup"><span data-stu-id="2f91d-126">UI Automation Control Patterns</span></span>](ui-automation-control-patterns.md)
- [<span data-ttu-id="2f91d-127">UI オートメーション テキスト パターン</span><span class="sxs-lookup"><span data-stu-id="2f91d-127">UI Automation Text Pattern</span></span>](ui-automation-text-pattern.md)
- [<span data-ttu-id="2f91d-128">UI オートメーションを使用したコントロールの呼び出し</span><span class="sxs-lookup"><span data-stu-id="2f91d-128">Invoke a Control Using UI Automation</span></span>](invoke-a-control-using-ui-automation.md)
- [<span data-ttu-id="2f91d-129">UI オートメーションを使用した、チェック ボックスのトグル状態の取得</span><span class="sxs-lookup"><span data-stu-id="2f91d-129">Get the Toggle State of a Check Box Using UI Automation</span></span>](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [<span data-ttu-id="2f91d-130">UI オートメーション クライアントのコントロール パターン マッピング</span><span class="sxs-lookup"><span data-stu-id="2f91d-130">Control Pattern Mapping for UI Automation Clients</span></span>](control-pattern-mapping-for-ui-automation-clients.md)
- [<span data-ttu-id="2f91d-131">TextPattern の挿入テキストのサンプル</span><span class="sxs-lookup"><span data-stu-id="2f91d-131">TextPattern Insert Text Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [<span data-ttu-id="2f91d-132">TextPattern の検索と選択のサンプル</span><span class="sxs-lookup"><span data-stu-id="2f91d-132">TextPattern Search and Selection Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
- [<span data-ttu-id="2f91d-133">InvokePattern、ExpandCollapsePattern、および TogglePattern サンプル</span><span class="sxs-lookup"><span data-stu-id="2f91d-133">InvokePattern, ExpandCollapsePattern, and TogglePattern Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
