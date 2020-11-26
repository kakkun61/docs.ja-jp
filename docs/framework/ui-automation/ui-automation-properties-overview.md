---
title: UI オートメーション プロパティの概要
description: Microsoft UI オートメーションプロパティの概要については、「」を参照してください。 プロパティ識別子、カテゴリ別のプロパティ、ローカライズ、およびプロパティとイベントについて説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, properties
- properties, UI Automation
ms.assetid: a6c31d7b-b33e-49b3-b5c1-31a345f9b7c8
ms.openlocfilehash: 95729c1d26a9ae7fdec4fa4215f9478251612242
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96240395"
---
# <a name="ui-automation-properties-overview"></a><span data-ttu-id="6bacc-104">UI オートメーション プロパティの概要</span><span class="sxs-lookup"><span data-stu-id="6bacc-104">UI Automation Properties Overview</span></span>

> [!NOTE]
> <span data-ttu-id="6bacc-105">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="6bacc-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="6bacc-106">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6bacc-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="6bacc-107">UI オートメーション プロバイダーは、 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 要素のプロパティを公開します。</span><span class="sxs-lookup"><span data-stu-id="6bacc-107">UI Automation providers expose properties on [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements.</span></span> <span data-ttu-id="6bacc-108">これらのプロパティにより、UI オートメーション クライアント アプリケーションは、静的データと動的データを含め、 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]の構成部分 (特にコントロール) に関する情報を探索できます。</span><span class="sxs-lookup"><span data-stu-id="6bacc-108">These properties enable UI Automation client applications to discover information about pieces of the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], especially controls, including both static and dynamic data.</span></span>  
  
 <span data-ttu-id="6bacc-109">このセクションでは、 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] プロパティの概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="6bacc-109">This section gives a broad overview of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] properties.</span></span> <span data-ttu-id="6bacc-110">詳細については、以下のトピックで説明しています。</span><span class="sxs-lookup"><span data-stu-id="6bacc-110">More specific information is given in the following topics:</span></span>  
  
- [<span data-ttu-id="6bacc-111">クライアントの UI オートメーション プロパティ</span><span class="sxs-lookup"><span data-stu-id="6bacc-111">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)  
  
- [<span data-ttu-id="6bacc-112">サーバー側 UI オートメーション プロバイダーの実装</span><span class="sxs-lookup"><span data-stu-id="6bacc-112">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)  
  
<a name="Property_Identifiers"></a>

## <a name="property-identifiers"></a><span data-ttu-id="6bacc-113">プロパティ識別子</span><span class="sxs-lookup"><span data-stu-id="6bacc-113">Property Identifiers</span></span>  

 <span data-ttu-id="6bacc-114">すべてのプロパティは、番号と名前によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="6bacc-114">Every property is identified by a number and a name.</span></span> <span data-ttu-id="6bacc-115">プロパティの名前を使用するのは、デバッグおよび診断を行う場合のみです。</span><span class="sxs-lookup"><span data-stu-id="6bacc-115">The names of properties are used only for debugging and diagnosis.</span></span> <span data-ttu-id="6bacc-116">プロバイダーは、数値 Id を使用して、受信プロパティ要求を識別します。</span><span class="sxs-lookup"><span data-stu-id="6bacc-116">Providers use the numeric IDs to identify incoming property requests.</span></span> <span data-ttu-id="6bacc-117">ただし、クライアント アプリケーションは、番号と名前をカプセル化した <xref:System.Windows.Automation.AutomationProperty>だけを使用して、取得したいプロパティを識別します。</span><span class="sxs-lookup"><span data-stu-id="6bacc-117">Client applications, however, only use <xref:System.Windows.Automation.AutomationProperty>, which encapsulates the number and name, to identify properties they wish to retrieve.</span></span>  
  
 <span data-ttu-id="6bacc-118">特定のプロパティを表す<xref:System.Windows.Automation.AutomationProperty> オブジェクトは、さまざまなクラスでフィールドとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="6bacc-118"><xref:System.Windows.Automation.AutomationProperty> objects representing particular properties are available as fields in various classes.</span></span> <span data-ttu-id="6bacc-119">セキュリティ上の理由から、UI オートメーション プロバイダーは、Uiautomationtypes.dll に含まれている別のクラスのセットから、これらのオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="6bacc-119">For security reasons, UI Automation providers obtain these objects from a separate set of classes that are contained in Uiautomationtypes.dll.</span></span>  
  
 <span data-ttu-id="6bacc-120">次の表は、id を含むクラスによってプロパティを分類して <xref:System.Windows.Automation.AutomationProperty> います。</span><span class="sxs-lookup"><span data-stu-id="6bacc-120">The following table categorizes properties by the classes that contain the <xref:System.Windows.Automation.AutomationProperty>IDs.</span></span>  
  
|<span data-ttu-id="6bacc-121">プロパティの種類</span><span class="sxs-lookup"><span data-stu-id="6bacc-121">Kinds of properties</span></span>|<span data-ttu-id="6bacc-122">クライアントが ID を取得する場所</span><span class="sxs-lookup"><span data-stu-id="6bacc-122">Clients get IDs from</span></span>|<span data-ttu-id="6bacc-123">プロバイダーが ID を取得する場所</span><span class="sxs-lookup"><span data-stu-id="6bacc-123">Providers get IDs from</span></span>|  
|-------------------------|--------------------------|----------------------------|  
|<span data-ttu-id="6bacc-124">すべての要素に共通のプロパティ (下記の表を参照)</span><span class="sxs-lookup"><span data-stu-id="6bacc-124">Properties common to all elements (see following tables)</span></span>|<xref:System.Windows.Automation.AutomationElement>|<xref:System.Windows.Automation.AutomationElementIdentifiers>|  
|<span data-ttu-id="6bacc-125">ドッキング ウィンドウの位置</span><span class="sxs-lookup"><span data-stu-id="6bacc-125">Position of a docking window</span></span>|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.DockPatternIdentifiers>|  
|<span data-ttu-id="6bacc-126">展開または折りたたみが可能な要素の状態</span><span class="sxs-lookup"><span data-stu-id="6bacc-126">State of an element that can expand and collapse</span></span>|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers>|  
|<span data-ttu-id="6bacc-127">グリッド内の項目のプロパティ</span><span class="sxs-lookup"><span data-stu-id="6bacc-127">Properties of an item in a grid</span></span>|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.GridItemPatternIdentifiers>|  
|<span data-ttu-id="6bacc-128">グリッドのプロパティ</span><span class="sxs-lookup"><span data-stu-id="6bacc-128">Properties of a grid</span></span>|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.GridPatternIdentifiers>|  
|<span data-ttu-id="6bacc-129">複数のビューを持つ要素の現在のサポートされているビュー</span><span class="sxs-lookup"><span data-stu-id="6bacc-129">Current and supported view of an element that has multiple views</span></span>|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers>|  
|<span data-ttu-id="6bacc-130">一定の値の範囲を移動する要素 (スライダーなど) のプロパティ</span><span class="sxs-lookup"><span data-stu-id="6bacc-130">Properties of an element that moves over a range of values, such as a slider</span></span>|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.RangeValuePatternIdentifiers>|  
|<span data-ttu-id="6bacc-131">スクロール ウィンドウのプロパティ</span><span class="sxs-lookup"><span data-stu-id="6bacc-131">Properties of a scrolling window</span></span>|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.ScrollPatternIdentifiers>|  
|<span data-ttu-id="6bacc-132">選択できる項目 (リスト内の項目など) の状態およびコンテナー</span><span class="sxs-lookup"><span data-stu-id="6bacc-132">Status and container of an item that can be selected, as in a list</span></span>|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers>|  
|<span data-ttu-id="6bacc-133">選択項目を含むコントロールのプロパティ</span><span class="sxs-lookup"><span data-stu-id="6bacc-133">Properties of a control that contains selection items</span></span>|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.SelectionPatternIdentifiers>|  
|<span data-ttu-id="6bacc-134">テーブル内の項目の列と行のヘッダー</span><span class="sxs-lookup"><span data-stu-id="6bacc-134">Column and row headers of an item in a table</span></span>|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.TableItemPatternIdentifiers>|  
|<span data-ttu-id="6bacc-135">テーブルの列と行のヘッダーおよびテーブルの向き</span><span class="sxs-lookup"><span data-stu-id="6bacc-135">Column and row headers, and orientation, of a table</span></span>|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.TablePatternIdentifiers>|  
|<span data-ttu-id="6bacc-136">切り替えコントロールの状態</span><span class="sxs-lookup"><span data-stu-id="6bacc-136">State of a toggle control</span></span>|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.TogglePatternIdentifiers>|  
|<span data-ttu-id="6bacc-137">移動、回転、またはサイズ変更できる要素の機能</span><span class="sxs-lookup"><span data-stu-id="6bacc-137">Capabilities of an element that can be moved, rotated, or resized</span></span>|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.TransformPatternIdentifiers>|  
|<span data-ttu-id="6bacc-138">値を持つ要素の値および読み取り/書き込み機能</span><span class="sxs-lookup"><span data-stu-id="6bacc-138">Value and read/write capabilities of an element that has a value</span></span>|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.ValuePatternIdentifiers>|  
|<span data-ttu-id="6bacc-139">ウィンドウの機能および状態</span><span class="sxs-lookup"><span data-stu-id="6bacc-139">Capabilities and state of a window</span></span>|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.WindowPatternIdentifiers>|  
  
<a name="Properties_by_Category"></a>

## <a name="properties-by-category"></a><span data-ttu-id="6bacc-140">カテゴリ別プロパティ</span><span class="sxs-lookup"><span data-stu-id="6bacc-140">Properties by Category</span></span>  

 <span data-ttu-id="6bacc-141">次の表は、とで Id が見つかったプロパティを分類したもの <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.AutomationElementIdentifiers> です。</span><span class="sxs-lookup"><span data-stu-id="6bacc-141">The following tables categorize the properties whose IDs are found in <xref:System.Windows.Automation.AutomationElement> and <xref:System.Windows.Automation.AutomationElementIdentifiers>.</span></span> <span data-ttu-id="6bacc-142">これらのプロパティは、すべてのコントロールに共通です。</span><span class="sxs-lookup"><span data-stu-id="6bacc-142">These properties are common to all controls.</span></span> <span data-ttu-id="6bacc-143">一部の例外を除き、ほとんどのプロパティがプロバイダー アプリケーションの有効期間にわたって静的です。動的プロパティのほとんどは、コントロール パターンに関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="6bacc-143">All but a few of them are likely to be static over the lifetime of the provider application; most dynamic properties are associated with control patterns.</span></span>  
  
 <span data-ttu-id="6bacc-144">**「プロパティ アクセス」** 列には、 <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> と <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>だけでなく、各プロパティのすべてのアクセサーを示しています。</span><span class="sxs-lookup"><span data-stu-id="6bacc-144">The **Property Access** column lists any other accessors for each property, in addition to <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> and <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>.</span></span> <span data-ttu-id="6bacc-145">クライアント アプリケーションでプロパティを取得する方法の詳細については、「 [UI Automation Properties for Clients](ui-automation-properties-for-clients.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bacc-145">For more information on getting properties in a client application, see [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6bacc-146">各プロパティの詳細については、 **「プロパティ アクセス」** 列のリンク先を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bacc-146">For specific information about each property, follow the link in the **Property Access** column.</span></span>  
  
### <a name="display-characteristics"></a><span data-ttu-id="6bacc-147">表示特性</span><span class="sxs-lookup"><span data-stu-id="6bacc-147">Display Characteristics</span></span>  
  
|<span data-ttu-id="6bacc-148">プロパティの識別子</span><span class="sxs-lookup"><span data-stu-id="6bacc-148">Property identifier</span></span>|<span data-ttu-id="6bacc-149">「プロパティ アクセス」</span><span class="sxs-lookup"><span data-stu-id="6bacc-149">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>|  
|<xref:System.Windows.Automation.AutomationElement.CultureProperty>|<span data-ttu-id="6bacc-150">該当なし</span><span class="sxs-lookup"><span data-stu-id="6bacc-150">n/a</span></span>|  
|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsOffscreen%2A>|  
|<xref:System.Windows.Automation.AutomationElement.OrientationProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Orientation%2A>|  
  
### <a name="element-type"></a><span data-ttu-id="6bacc-151">要素型</span><span class="sxs-lookup"><span data-stu-id="6bacc-151">Element Type</span></span>  
  
|<span data-ttu-id="6bacc-152">プロパティの識別子</span><span class="sxs-lookup"><span data-stu-id="6bacc-152">Property identifier</span></span>|<span data-ttu-id="6bacc-153">「プロパティ アクセス」</span><span class="sxs-lookup"><span data-stu-id="6bacc-153">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsContentElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsControlElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LocalizedControlType%2A>|  
  
### <a name="identification"></a><span data-ttu-id="6bacc-154">識別</span><span class="sxs-lookup"><span data-stu-id="6bacc-154">Identification</span></span>  
  
|<span data-ttu-id="6bacc-155">プロパティの識別子</span><span class="sxs-lookup"><span data-stu-id="6bacc-155">Property identifier</span></span>|<span data-ttu-id="6bacc-156">「プロパティ アクセス」</span><span class="sxs-lookup"><span data-stu-id="6bacc-156">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClassNameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ClassName%2A>|  
|<xref:System.Windows.Automation.AutomationElement.FrameworkIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.FrameworkId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LabeledByProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LabeledBy%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ProcessIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ProcessId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.RuntimeIdProperty>|<xref:System.Windows.Automation.AutomationElement.GetRuntimeId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NativeWindowHandleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.NativeWindowHandle%2A>|  
  
### <a name="interaction"></a><span data-ttu-id="6bacc-157">相互作用</span><span class="sxs-lookup"><span data-stu-id="6bacc-157">Interaction</span></span>  
  
|<span data-ttu-id="6bacc-158">プロパティの識別子</span><span class="sxs-lookup"><span data-stu-id="6bacc-158">Property identifier</span></span>|<span data-ttu-id="6bacc-159">「プロパティ アクセス」</span><span class="sxs-lookup"><span data-stu-id="6bacc-159">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AcceleratorKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AccessKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>|<xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>|  
|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HasKeyboardFocus%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsEnabled%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsKeyboardFocusable%2A>|  
  
### <a name="support-for-patterns"></a><span data-ttu-id="6bacc-160">パターンのサポート</span><span class="sxs-lookup"><span data-stu-id="6bacc-160">Support for Patterns</span></span>  
  
|<span data-ttu-id="6bacc-161">プロパティの識別子</span><span class="sxs-lookup"><span data-stu-id="6bacc-161">Property identifier</span></span>|<span data-ttu-id="6bacc-162">「プロパティ アクセス」</span><span class="sxs-lookup"><span data-stu-id="6bacc-162">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsDockPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsExpandCollapsePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsGridItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsGridPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsInvokePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsMultipleViewPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsRangeValuePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsScrollItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsScrollPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsSelectionItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsSelectionPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTableItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTablePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTogglePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTransformPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsValuePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsWindowPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
  
### <a name="miscellaneous"></a><span data-ttu-id="6bacc-163">その他</span><span class="sxs-lookup"><span data-stu-id="6bacc-163">Miscellaneous</span></span>  
  
|<span data-ttu-id="6bacc-164">プロパティの識別子</span><span class="sxs-lookup"><span data-stu-id="6bacc-164">Property identifier</span></span>|<span data-ttu-id="6bacc-165">「プロパティ アクセス」</span><span class="sxs-lookup"><span data-stu-id="6bacc-165">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsRequiredForFormProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsRequiredForForm%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsPassword%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemStatusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemStatus%2A>|  
  
<a name="Localization"></a>

## <a name="localization"></a><span data-ttu-id="6bacc-166">ローカリゼーション</span><span class="sxs-lookup"><span data-stu-id="6bacc-166">Localization</span></span>  

 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <span data-ttu-id="6bacc-167">プロバイダーは、以下のプロパティをオペレーティング システムの言語で提示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bacc-167">providers should present the following properties in the language of the operating system:</span></span>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
<a name="Properties_and_Events"></a>

## <a name="properties-and-events"></a><span data-ttu-id="6bacc-168">プロパティおよびイベント</span><span class="sxs-lookup"><span data-stu-id="6bacc-168">Properties and Events</span></span>  

 <span data-ttu-id="6bacc-169">プロパティ変更イベントの概念は、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] のプロパティと密接に関連しています。</span><span class="sxs-lookup"><span data-stu-id="6bacc-169">Closely tied in with the properties in [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is the concept of property-changed events.</span></span> <span data-ttu-id="6bacc-170">動的プロパティの場合は、プロパティの値が変更されたときにキャッシュの情報を更新したり新しい情報に何らかの形で対応したりできるように、クライアント アプリケーションは、プロパティの値が変更されたことを認識できなければなりません。</span><span class="sxs-lookup"><span data-stu-id="6bacc-170">For dynamic properties, the client application needs a way to know that a property value has changed, so that it can update its cache of information or react to the new information in some other way.</span></span>  
  
 <span data-ttu-id="6bacc-171">[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] で何らかの変更が発生すると、プロバイダーはイベントを生成します。</span><span class="sxs-lookup"><span data-stu-id="6bacc-171">Providers raise events when something in the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] changes.</span></span> <span data-ttu-id="6bacc-172">たとえば、チェック ボックスのオン/オフが切り替えられると、プロバイダーの Toggle パターンの実装によって、プロパティ変更イベントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="6bacc-172">For example, if a check box is selected or cleared, a property-changed event is raised by the provider's implementation of the Toggle pattern.</span></span> <span data-ttu-id="6bacc-173">プロバイダーは、クライアントがイベントをリッスンしているのか、特定のイベントをリッスンしているのかに応じて、イベントを選択的に生成できます。</span><span class="sxs-lookup"><span data-stu-id="6bacc-173">Providers can raise events selectively, depending on whether any clients are listening for events, or listening for specific events.</span></span>  
  
 <span data-ttu-id="6bacc-174">すべてのプロパティ変更がイベントを生成するわけではありません。これは完全に、該当する要素の UI オートメーション プロバイダーの実装に依存します。</span><span class="sxs-lookup"><span data-stu-id="6bacc-174">Not all property changes raise events; that is entirely up to the implementation of the UI Automation provider for the element.</span></span> <span data-ttu-id="6bacc-175">たとえば、リスト ボックスの標準プロキシ プロバイダーは、 <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> が変更されてもイベントを生成しません。</span><span class="sxs-lookup"><span data-stu-id="6bacc-175">For example, the standard proxy providers for list boxes do not raise an event when the <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> changes.</span></span> <span data-ttu-id="6bacc-176">この場合、アプリケーションが <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>をリッスンする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bacc-176">In this case, the application instead must listen for an <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>.</span></span>  
  
 <span data-ttu-id="6bacc-177">クライアントは、イベントをサブスクライブすることでイベントをリッスンします。</span><span class="sxs-lookup"><span data-stu-id="6bacc-177">Clients listen for events by subscribing to them.</span></span> <span data-ttu-id="6bacc-178">イベントをサブスクライブすることは、イベントを処理できるデリゲート メソッドを作成し、それらのメソッドで処理する特定のイベントと共に、それらのメソッドを [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] に渡すことを意味します。</span><span class="sxs-lookup"><span data-stu-id="6bacc-178">Subscribing to events means creating delegate methods that can handle the events, and then passing the methods to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] along with the specific events that will be dealt with in those methods.</span></span> <span data-ttu-id="6bacc-179">特にプロパティ変更イベントについては、クライアントが <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bacc-179">For property-changed events in particular, clients must implement <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bacc-180">関連項目</span><span class="sxs-lookup"><span data-stu-id="6bacc-180">See also</span></span>

- [<span data-ttu-id="6bacc-181">UI オートメーション クライアントにおけるキャッシュ</span><span class="sxs-lookup"><span data-stu-id="6bacc-181">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
- [<span data-ttu-id="6bacc-182">クライアントの UI オートメーション プロパティ</span><span class="sxs-lookup"><span data-stu-id="6bacc-182">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)
- [<span data-ttu-id="6bacc-183">サーバー側 UI オートメーション プロバイダーの実装</span><span class="sxs-lookup"><span data-stu-id="6bacc-183">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
- [<span data-ttu-id="6bacc-184">プロパティ条件に基づく UI オートメーション要素の検索</span><span class="sxs-lookup"><span data-stu-id="6bacc-184">Find a UI Automation Element Based on a Property Condition</span></span>](find-a-ui-automation-element-based-on-a-property-condition.md)
- [<span data-ttu-id="6bacc-185">UI オートメーション プロバイダーからのプロパティの返却</span><span class="sxs-lookup"><span data-stu-id="6bacc-185">Return Properties from a UI Automation Provider</span></span>](return-properties-from-a-ui-automation-provider.md)
- [<span data-ttu-id="6bacc-186">UI オートメーション プロバイダーからのイベントの発生</span><span class="sxs-lookup"><span data-stu-id="6bacc-186">Raise Events from a UI Automation Provider</span></span>](raise-events-from-a-ui-automation-provider.md)
