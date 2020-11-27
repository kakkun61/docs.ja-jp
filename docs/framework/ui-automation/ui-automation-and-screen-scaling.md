---
title: UI オートメーションおよび画面の拡大縮小
description: Windows と UI オートメーションが画面のスケーリングを処理する方法について説明します。 DWM は、UI オートメーションクライアントアプリが考慮する必要があるすべてのアプリケーションの既定のスケーリングを実行します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scaling, screens
- screens, scaling
- UI (user interface), automation
- UI Automation
ms.assetid: 4380cad7-e509-448f-b9a5-6de042605fd4
ms.openlocfilehash: cf8069f26b85318994aeeb47d42ad28a3a33834a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262529"
---
# <a name="ui-automation-and-screen-scaling"></a><span data-ttu-id="a9054-104">UI オートメーションおよび画面の拡大縮小</span><span class="sxs-lookup"><span data-stu-id="a9054-104">UI Automation and Screen Scaling</span></span>

> [!NOTE]
> <span data-ttu-id="a9054-105">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="a9054-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a9054-106">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a9054-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
<span data-ttu-id="a9054-107">Windows Vista 以降では、ユーザーはドット/インチ (dpi) の設定を変更して、画面上のほとんどのユーザーインターフェイス (UI) 要素のサイズを大きくすることができます。</span><span class="sxs-lookup"><span data-stu-id="a9054-107">Starting with Windows Vista, Windows enables users to change the dots per inch (dpi) setting so that most user interface (UI) elements on the screen appear larger.</span></span> <span data-ttu-id="a9054-108">この機能は Windows では長時間使用できましたが、以前のバージョンでは、アプリケーションによってスケーリングを実装する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="a9054-108">Although this feature has long been available in Windows, in previous versions the scaling had to be implemented by applications.</span></span> <span data-ttu-id="a9054-109">Windows Vista 以降では、デスクトップウィンドウマネージャーによって、独自のスケーリングを処理しないすべてのアプリケーションに対して既定のスケーリングが実行されます。</span><span class="sxs-lookup"><span data-stu-id="a9054-109">Starting with Windows Vista, the Desktop Window Manager performs default scaling for all applications that do not handle their own scaling.</span></span> <span data-ttu-id="a9054-110">UI オートメーション クライアント アプリケーションでは、この機能を考慮に入れる必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9054-110">UI Automation client applications must take this feature into account.</span></span>  
  
<a name="Scaling_in_Windows_Vista"></a>

## <a name="scaling-in-windows-vista"></a><span data-ttu-id="a9054-111">Windows Vista での拡大縮小</span><span class="sxs-lookup"><span data-stu-id="a9054-111">Scaling in Windows Vista</span></span>  

 <span data-ttu-id="a9054-112">既定の dpi 設定は96です。これは、96ピクセルが1概念的なインチの幅または高さを占めていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="a9054-112">The default dpi setting is 96, which means that 96 pixels occupy a width or height of one notional inch.</span></span> <span data-ttu-id="a9054-113">「インチ」の正確な寸法は、モニターのサイズと物理的な解像度によって異なります。</span><span class="sxs-lookup"><span data-stu-id="a9054-113">The exact measure of an "inch" depends on the size and physical resolution of the monitor.</span></span> <span data-ttu-id="a9054-114">たとえば、幅 12 インチで水平方向の解像度 1280 ピクセルのモニターでは、96 ピクセルの水平線は 1 インチの約 9/10 の長さになります。</span><span class="sxs-lookup"><span data-stu-id="a9054-114">For example, on a monitor 12 inches wide, at a horizontal resolution of 1280 pixels, a horizontal line of 96 pixels extends about 9/10 of an inch.</span></span>  
  
 <span data-ttu-id="a9054-115">Dpi 設定の変更は、画面の解像度の変更と同じではありません。</span><span class="sxs-lookup"><span data-stu-id="a9054-115">Changing the dpi setting is not the same as changing the screen resolution.</span></span> <span data-ttu-id="a9054-116">Dpi スケーリングでは、画面上の物理ピクセルの数は変わりません。</span><span class="sxs-lookup"><span data-stu-id="a9054-116">With dpi scaling, the number of physical pixels on the screen remains the same.</span></span> <span data-ttu-id="a9054-117">拡大縮小が適用されるのは、 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 要素のサイズと位置です。</span><span class="sxs-lookup"><span data-stu-id="a9054-117">However, scaling is applied to the size and location of [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elements.</span></span> <span data-ttu-id="a9054-118">拡大縮小しないよう明示的に指定されていないデスクトップとアプリケーションに対し、デスクトップ ウィンドウ マネージャー (DWM) はこの拡大縮小を自動的に実行できます。</span><span class="sxs-lookup"><span data-stu-id="a9054-118">This scaling can be performed automatically by the Desktop Window Manager (DWM) for the desktop and for applications that do not explicitly ask not to be scaled.</span></span>  
  
 <span data-ttu-id="a9054-119">実際には、ユーザーがスケールファクターを 120 dpi に設定すると、画面上の垂直方向または水平方向のインチが25% 大きくなります。</span><span class="sxs-lookup"><span data-stu-id="a9054-119">In effect, when the user sets the scale factor to 120 dpi, a vertical or horizontal inch on the screen becomes bigger by 25 percent.</span></span> <span data-ttu-id="a9054-120">すべての寸法は、それに応じて拡大されます。</span><span class="sxs-lookup"><span data-stu-id="a9054-120">All dimensions are scaled accordingly.</span></span> <span data-ttu-id="a9054-121">画面の左上隅からのアプリケーション ウィンドウのオフセットは、25% 増加します。</span><span class="sxs-lookup"><span data-stu-id="a9054-121">The offset of an application window from the top and left edges of the screen increases by 25 percent.</span></span> <span data-ttu-id="a9054-122">アプリケーションのスケーリングが有効になっていて、アプリケーションが dpi 対応でない場合、ウィンドウのサイズは、含まれるすべての要素のオフセットとサイズと共に、同じ比率で増加し [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="a9054-122">If application scaling is enabled and the application is not dpi-aware, the size of the window increases in the same proportion, along with the offsets and sizes of all [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elements it contains.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a9054-123">既定では、DWM は dpi が120に設定されている場合は dpi 非対応アプリケーションのスケーリングを実行しませんが、dpi が144以上のカスタム値に設定されている場合は、この動作を実行します。</span><span class="sxs-lookup"><span data-stu-id="a9054-123">By default, the DWM does not perform scaling for non-dpi-aware applications when the user sets the dpi to 120, but does perform it when the dpi is set to a custom value of 144 or higher.</span></span> <span data-ttu-id="a9054-124">ただし、この既定の動作は、ユーザーがオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="a9054-124">However, the user can override the default behavior.</span></span>  
  
 <span data-ttu-id="a9054-125">画面の拡大縮小は、画面座標に何らかの関わりを持つアプリケーションに新しい課題をもたらします。</span><span class="sxs-lookup"><span data-stu-id="a9054-125">Screen scaling creates new challenges for applications that are concerned in any way with screen coordinates.</span></span> <span data-ttu-id="a9054-126">現在、画面には物理座標と論理座標という 2 つの座標系が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a9054-126">The screen now contains two coordinate systems: physical and logical.</span></span> <span data-ttu-id="a9054-127">あるポイントの物理座標は、原点の左上からの実際のオフセット (ピクセル数) です。</span><span class="sxs-lookup"><span data-stu-id="a9054-127">The physical coordinates of a point are the actual offset in pixels from the top left of the origin.</span></span> <span data-ttu-id="a9054-128">論理座標は、ピクセル自体が拡大縮小された場合のオフセットです。</span><span class="sxs-lookup"><span data-stu-id="a9054-128">The logical coordinates are the offsets as they would be if the pixels themselves were scaled.</span></span>  
  
 <span data-ttu-id="a9054-129">たとえば、ダイアログ ボックスを設計し、座標 (100, 48) にボタンを配置するとします。</span><span class="sxs-lookup"><span data-stu-id="a9054-129">Suppose you design a dialog box with a button at coordinates (100, 48).</span></span> <span data-ttu-id="a9054-130">このダイアログボックスが既定の 96 dpi で表示されている場合、ボタンはの物理座標 (100、48) にあります。</span><span class="sxs-lookup"><span data-stu-id="a9054-130">When this dialog box is displayed at the default 96 dpi, the button is located at physical coordinates of (100, 48).</span></span> <span data-ttu-id="a9054-131">120 dpi では、(125、60) の物理座標に配置されます。</span><span class="sxs-lookup"><span data-stu-id="a9054-131">At 120 dpi, it is located at physical coordinates of (125, 60).</span></span> <span data-ttu-id="a9054-132">ただし、論理座標は、すべての dpi 設定で同じです (100、48)。</span><span class="sxs-lookup"><span data-stu-id="a9054-132">But the logical coordinates are the same at any dpi setting: (100, 48).</span></span>  
  
 <span data-ttu-id="a9054-133">論理座標は、dpi 設定に関係なく、オペレーティングシステムとアプリケーションの動作が一貫しているため、重要です。</span><span class="sxs-lookup"><span data-stu-id="a9054-133">Logical coordinates are important, because they make the behavior of the operating system and applications consistent regardless of the dpi setting.</span></span> <span data-ttu-id="a9054-134">たとえば、 <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> は通常、論理座標を返します。</span><span class="sxs-lookup"><span data-stu-id="a9054-134">For example, <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> normally returns the logical coordinates.</span></span> <span data-ttu-id="a9054-135">ダイアログボックス内の要素の上にカーソルを移動すると、dpi 設定に関係なく同じ座標が返されます。</span><span class="sxs-lookup"><span data-stu-id="a9054-135">If you move the cursor over an element in a dialog box, the same coordinates are returned regardless of the dpi setting.</span></span> <span data-ttu-id="a9054-136">(100, 100) にコントロールを描画すると、それらの論理座標に描画され、すべての dpi 設定で同じ相対位置が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a9054-136">If you draw a control at (100, 100), it is drawn to those logical coordinates, and will occupy the same relative position at any dpi setting.</span></span>  
  
<a name="Scaling_in_UI_Automation_Clients"></a>

## <a name="scaling-in-ui-automation-clients"></a><span data-ttu-id="a9054-137">UI オートメーション クライアントにおける拡大縮小</span><span class="sxs-lookup"><span data-stu-id="a9054-137">Scaling in UI Automation Clients</span></span>  

 <span data-ttu-id="a9054-138">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]API は論理座標を使用しません。</span><span class="sxs-lookup"><span data-stu-id="a9054-138">The [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] API does not use logical coordinates.</span></span> <span data-ttu-id="a9054-139">次のメソッドとプロパティが返す、あるいはパラメーターとして受け取るのは、物理座標です。</span><span class="sxs-lookup"><span data-stu-id="a9054-139">The following methods and properties either return physical coordinates or take them as parameters.</span></span>  
  
- <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
- <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 <span data-ttu-id="a9054-140">既定では、96 dpi 以外の環境で実行されている UI オートメーションクライアントアプリケーションは、これらのメソッドとプロパティから正しい結果を得ることができません。</span><span class="sxs-lookup"><span data-stu-id="a9054-140">By default, a UI Automation client application running in a non-96- dpi environment will not be able to obtain correct results from these methods and properties.</span></span> <span data-ttu-id="a9054-141">たとえば、カーソルの位置は論理座標で表されるため、クライアントはそのカーソルの位置にある要素を取得するために、これらの座標をそのまま <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> に渡すことができません。</span><span class="sxs-lookup"><span data-stu-id="a9054-141">For example, because the cursor position is in logical coordinates, the client cannot simply pass these coordinates to <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> to obtain the element that is under the cursor.</span></span> <span data-ttu-id="a9054-142">さらに、アプリケーションはクライアント領域外にウィンドウを正しく配置することもできません。</span><span class="sxs-lookup"><span data-stu-id="a9054-142">In addition, the application will not be able to correctly place windows outside its client area.</span></span>  
  
 <span data-ttu-id="a9054-143">解決方法は 2 つの部分で構成されます。</span><span class="sxs-lookup"><span data-stu-id="a9054-143">The solution is in two parts.</span></span>  
  
1. <span data-ttu-id="a9054-144">まず、クライアントアプリケーションを dpi 対応にします。</span><span class="sxs-lookup"><span data-stu-id="a9054-144">First, make the client application dpi-aware.</span></span> <span data-ttu-id="a9054-145">これを行うには、起動時に Win32 関数を呼び出し `SetProcessDPIAware` ます。</span><span class="sxs-lookup"><span data-stu-id="a9054-145">To do this, call the Win32 function `SetProcessDPIAware` at startup.</span></span> <span data-ttu-id="a9054-146">マネージド コードで、次の宣言によりこの関数を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a9054-146">In managed code, the following declaration makes this function available.</span></span>  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     <span data-ttu-id="a9054-147">この関数は、プロセス全体を dpi 対応にします。つまり、プロセスに属するすべてのウィンドウはスケーリングされません。</span><span class="sxs-lookup"><span data-stu-id="a9054-147">This function makes the entire process dpi-aware, meaning that all windows that belong to the process are unscaled.</span></span> <span data-ttu-id="a9054-148">[蛍光ペンのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)では、強調表示の四角形を構成する4つのウィンドウは、論理座標ではなく、UI オートメーションから取得した物理座標に配置されます。</span><span class="sxs-lookup"><span data-stu-id="a9054-148">In the [Highlighter Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter), for instance, the four windows that make up the highlight rectangle are located at the physical coordinates obtained from UI Automation, not the logical coordinates.</span></span> <span data-ttu-id="a9054-149">サンプルが dpi に対応していない場合、強調表示はデスクトップ上の論理座標に描画されます。これにより、96 dpi 以外の環境での配置が不適切になります。</span><span class="sxs-lookup"><span data-stu-id="a9054-149">If the sample were not dpi-aware, the highlight would be drawn at the logical coordinates on the desktop, which would result in incorrect placement in a non-96- dpi environment.</span></span>  
  
2. <span data-ttu-id="a9054-150">カーソルの座標を取得するには、Win32 関数を呼び出し `GetPhysicalCursorPos` ます。</span><span class="sxs-lookup"><span data-stu-id="a9054-150">To get cursor coordinates, call the Win32 function `GetPhysicalCursorPos`.</span></span> <span data-ttu-id="a9054-151">次の例に、この関数を宣言して使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a9054-151">The following example shows how to declare and use this function.</span></span>  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
> <span data-ttu-id="a9054-152"><xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="a9054-152">Do not use <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a9054-153">拡大縮小される環境において、クライアント ウィンドウ外でのこのプロパティの動作は定義されていません。</span><span class="sxs-lookup"><span data-stu-id="a9054-153">The behavior of this property outside client windows in a scaled environment is undefined.</span></span>  
  
 <span data-ttu-id="a9054-154">アプリケーションが非 dpi 対応アプリケーションとの間で直接のプロセス間通信を実行する場合、Win32 関数とを使用して論理座標と物理座標を変換することができ `PhysicalToLogicalPoint` `LogicalToPhysicalPoint` ます。</span><span class="sxs-lookup"><span data-stu-id="a9054-154">If your application performs direct cross-process communication with non- dpi-aware applications, you may have convert between logical and physical coordinates by using the Win32 functions `PhysicalToLogicalPoint` and `LogicalToPhysicalPoint`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9054-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="a9054-155">See also</span></span>

- [<span data-ttu-id="a9054-156">Highlighter Sample</span><span class="sxs-lookup"><span data-stu-id="a9054-156">Highlighter Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)
