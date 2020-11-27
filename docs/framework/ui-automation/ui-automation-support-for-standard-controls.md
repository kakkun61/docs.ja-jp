---
title: UI オートメーションによる標準コントロールのサポート
description: Windows Presentation Foundation (WPF)、Win32、Windows フォーム用に開発されたアプリケーションの標準コントロールに対する UI オートメーションのサポートに関する情報を入手します。
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 0a5a0b61a6492d9efb62799fa610859b247cf26e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261073"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="faac1-103">UI オートメーションによる標準コントロールのサポート</span><span class="sxs-lookup"><span data-stu-id="faac1-103">UI Automation Support for Standard Controls</span></span>

> [!NOTE]
> <span data-ttu-id="faac1-104">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="faac1-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="faac1-105">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="faac1-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="faac1-106">このトピックで [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] は [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 、、Win32、および Windows フォームフレームワーク用に開発されたアプリケーションの標準コントロールのサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="faac1-106">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32, and Windows Forms frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>

## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="faac1-107">Windows Presentation Foundation コントロール</span><span class="sxs-lookup"><span data-stu-id="faac1-107">Windows Presentation Foundation Controls</span></span>  

 <span data-ttu-id="faac1-108">ユーザー操作に関する情報やサポートを提供するすべての [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] コントロール要素は、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を全面的にネイティブ サポートしています。</span><span class="sxs-lookup"><span data-stu-id="faac1-108">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="faac1-109">パネルなどのその他の要素は、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]からは認識できません。</span><span class="sxs-lookup"><span data-stu-id="faac1-109">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>

## <a name="win32-controls"></a><span data-ttu-id="faac1-110">Win32 コントロール</span><span class="sxs-lookup"><span data-stu-id="faac1-110">Win32 Controls</span></span>  

 <span data-ttu-id="faac1-111">ほとんどの Win32 コントロールは、 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] UIAutomationClientsideProviders.dll のクライアント側プロバイダーを介してに公開されます。</span><span class="sxs-lookup"><span data-stu-id="faac1-111">Most Win32 controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="faac1-112">このアセンブリは、UI オートメーション クライアント アプリケーションで使用するために、自動的に登録されます。</span><span class="sxs-lookup"><span data-stu-id="faac1-112">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="faac1-113">完全サポートは、バージョン6の *ComCtrl32.dll* のコントロールに対してのみ提供されます。</span><span class="sxs-lookup"><span data-stu-id="faac1-113">Full support is provided only for controls from version 6 of *ComCtrl32.dll*.</span></span>  
  
 <span data-ttu-id="faac1-114">次のコントロールがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="faac1-114">The following controls are supported.</span></span>  
  
|<span data-ttu-id="faac1-115">クラス名</span><span class="sxs-lookup"><span data-stu-id="faac1-115">Class name</span></span>|<span data-ttu-id="faac1-116">コントロール型</span><span class="sxs-lookup"><span data-stu-id="faac1-116">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="faac1-117">Button</span><span class="sxs-lookup"><span data-stu-id="faac1-117">Button</span></span>|<span data-ttu-id="faac1-118">Button</span><span class="sxs-lookup"><span data-stu-id="faac1-118">Button</span></span>|  
|<span data-ttu-id="faac1-119">Button</span><span class="sxs-lookup"><span data-stu-id="faac1-119">Button</span></span>|<span data-ttu-id="faac1-120">RadioButton</span><span class="sxs-lookup"><span data-stu-id="faac1-120">RadioButton</span></span>|  
|<span data-ttu-id="faac1-121">ボタン</span><span class="sxs-lookup"><span data-stu-id="faac1-121">Button</span></span>|<span data-ttu-id="faac1-122">グループ</span><span class="sxs-lookup"><span data-stu-id="faac1-122">Group</span></span>|  
|<span data-ttu-id="faac1-123">ボタン</span><span class="sxs-lookup"><span data-stu-id="faac1-123">Button</span></span>|<span data-ttu-id="faac1-124">CheckBox</span><span class="sxs-lookup"><span data-stu-id="faac1-124">CheckBox</span></span>|  
|<span data-ttu-id="faac1-125">ボタン</span><span class="sxs-lookup"><span data-stu-id="faac1-125">Button</span></span>|<span data-ttu-id="faac1-126">ハイパーリンク</span><span class="sxs-lookup"><span data-stu-id="faac1-126">Hyperlink</span></span>|  
|<span data-ttu-id="faac1-127">ボタン</span><span class="sxs-lookup"><span data-stu-id="faac1-127">Button</span></span>|<span data-ttu-id="faac1-128">SplitButton</span><span class="sxs-lookup"><span data-stu-id="faac1-128">SplitButton</span></span>|  
|<span data-ttu-id="faac1-129">ボタン</span><span class="sxs-lookup"><span data-stu-id="faac1-129">Button</span></span>|<span data-ttu-id="faac1-130">CheckBox</span><span class="sxs-lookup"><span data-stu-id="faac1-130">CheckBox</span></span>|  
|<span data-ttu-id="faac1-131">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="faac1-131">ComboBoxEx32</span></span>|<span data-ttu-id="faac1-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="faac1-132">ComboBox</span></span>|  
|<span data-ttu-id="faac1-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="faac1-133">ComboBox</span></span>|<span data-ttu-id="faac1-134">ComboBox</span><span class="sxs-lookup"><span data-stu-id="faac1-134">ComboBox</span></span>|  
|<span data-ttu-id="faac1-135">編集</span><span class="sxs-lookup"><span data-stu-id="faac1-135">Edit</span></span>|<span data-ttu-id="faac1-136">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="faac1-136">Document</span></span>|  
|<span data-ttu-id="faac1-137">編集</span><span class="sxs-lookup"><span data-stu-id="faac1-137">Edit</span></span>|<span data-ttu-id="faac1-138">編集</span><span class="sxs-lookup"><span data-stu-id="faac1-138">Edit</span></span>|  
|<span data-ttu-id="faac1-139">SysLink</span><span class="sxs-lookup"><span data-stu-id="faac1-139">SysLink</span></span>|<span data-ttu-id="faac1-140">ハイパーリンク</span><span class="sxs-lookup"><span data-stu-id="faac1-140">Hyperlink</span></span>|  
|<span data-ttu-id="faac1-141">静的</span><span class="sxs-lookup"><span data-stu-id="faac1-141">Static</span></span>|<span data-ttu-id="faac1-142">テキスト</span><span class="sxs-lookup"><span data-stu-id="faac1-142">Text</span></span>|  
|<span data-ttu-id="faac1-143">静的</span><span class="sxs-lookup"><span data-stu-id="faac1-143">Static</span></span>|<span data-ttu-id="faac1-144">Image</span><span class="sxs-lookup"><span data-stu-id="faac1-144">Image</span></span>|  
|<span data-ttu-id="faac1-145">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="faac1-145">SysIPAddress32</span></span>|<span data-ttu-id="faac1-146">カスタム</span><span class="sxs-lookup"><span data-stu-id="faac1-146">Custom</span></span>|  
|<span data-ttu-id="faac1-147">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="faac1-147">SysHeader32</span></span>|<span data-ttu-id="faac1-148">Header/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="faac1-148">Header/HeaderItem</span></span>|  
|<span data-ttu-id="faac1-149">SysListView32</span><span class="sxs-lookup"><span data-stu-id="faac1-149">SysListView32</span></span>|<span data-ttu-id="faac1-150">DataGrid</span><span class="sxs-lookup"><span data-stu-id="faac1-150">DataGrid</span></span>|  
|<span data-ttu-id="faac1-151">SysListView32</span><span class="sxs-lookup"><span data-stu-id="faac1-151">SysListView32</span></span>|<span data-ttu-id="faac1-152">List</span><span class="sxs-lookup"><span data-stu-id="faac1-152">List</span></span>|  
|<span data-ttu-id="faac1-153">ListBox</span><span class="sxs-lookup"><span data-stu-id="faac1-153">ListBox</span></span>|<span data-ttu-id="faac1-154">List</span><span class="sxs-lookup"><span data-stu-id="faac1-154">List</span></span>|  
|<span data-ttu-id="faac1-155">ListBox</span><span class="sxs-lookup"><span data-stu-id="faac1-155">ListBox</span></span>|<span data-ttu-id="faac1-156">ListItem</span><span class="sxs-lookup"><span data-stu-id="faac1-156">ListItem</span></span>|  
|<span data-ttu-id="faac1-157">#32768</span><span class="sxs-lookup"><span data-stu-id="faac1-157">#32768</span></span>|<span data-ttu-id="faac1-158">メニュー</span><span class="sxs-lookup"><span data-stu-id="faac1-158">Menu</span></span>|  
|<span data-ttu-id="faac1-159">#32768</span><span class="sxs-lookup"><span data-stu-id="faac1-159">#32768</span></span>|<span data-ttu-id="faac1-160">MenuItem</span><span class="sxs-lookup"><span data-stu-id="faac1-160">MenuItem</span></span>|  
|<span data-ttu-id="faac1-161">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="faac1-161">msctls_progress32</span></span>|<span data-ttu-id="faac1-162">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="faac1-162">ProgressBar</span></span>|  
|<span data-ttu-id="faac1-163">RichEdit</span><span class="sxs-lookup"><span data-stu-id="faac1-163">RichEdit</span></span>|<span data-ttu-id="faac1-164">ドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="faac1-164">Document.</span></span> <span data-ttu-id="faac1-165">「注」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="faac1-165">See note.</span></span>|  
|<span data-ttu-id="faac1-166">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="faac1-166">RichEdit20A</span></span>|<span data-ttu-id="faac1-167">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="faac1-167">Document</span></span>|  
|<span data-ttu-id="faac1-168">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="faac1-168">RichEdit20W</span></span>|<span data-ttu-id="faac1-169">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="faac1-169">Document</span></span>|  
|<span data-ttu-id="faac1-170">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="faac1-170">RichEdit50W</span></span>|<span data-ttu-id="faac1-171">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="faac1-171">Document</span></span>|  
|<span data-ttu-id="faac1-172">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="faac1-172">ScrollBar</span></span>|<span data-ttu-id="faac1-173">スライダー</span><span class="sxs-lookup"><span data-stu-id="faac1-173">Slider</span></span>|  
|<span data-ttu-id="faac1-174">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="faac1-174">msctls_trackbar32</span></span>|<span data-ttu-id="faac1-175">スライダー</span><span class="sxs-lookup"><span data-stu-id="faac1-175">Slider</span></span>|  
|<span data-ttu-id="faac1-176">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="faac1-176">msctls_updown32</span></span>|<span data-ttu-id="faac1-177">Spinner</span><span class="sxs-lookup"><span data-stu-id="faac1-177">Spinner</span></span>|  
|<span data-ttu-id="faac1-178">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="faac1-178">msctls_statusbar32</span></span>|<span data-ttu-id="faac1-179">StatusBar</span><span class="sxs-lookup"><span data-stu-id="faac1-179">StatusBar</span></span>|  
|<span data-ttu-id="faac1-180">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="faac1-180">SysTabControl32</span></span>|<span data-ttu-id="faac1-181">タブ</span><span class="sxs-lookup"><span data-stu-id="faac1-181">Tab</span></span>|  
|<span data-ttu-id="faac1-182">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="faac1-182">SysTabControl32</span></span>|<span data-ttu-id="faac1-183">TabItem</span><span class="sxs-lookup"><span data-stu-id="faac1-183">TabItem</span></span>|  
|<span data-ttu-id="faac1-184">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="faac1-184">ToolbarWindow32</span></span>|<span data-ttu-id="faac1-185">ToolBar</span><span class="sxs-lookup"><span data-stu-id="faac1-185">ToolBar</span></span>|  
|<span data-ttu-id="faac1-186">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="faac1-186">ToolbarWindow32</span></span>|<span data-ttu-id="faac1-187">MenuItem</span><span class="sxs-lookup"><span data-stu-id="faac1-187">MenuItem</span></span>|  
|<span data-ttu-id="faac1-188">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="faac1-188">ToolbarWindow32</span></span>|<span data-ttu-id="faac1-189">ボタン</span><span class="sxs-lookup"><span data-stu-id="faac1-189">Button</span></span>|  
|<span data-ttu-id="faac1-190">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="faac1-190">ToolbarWindow32</span></span>|<span data-ttu-id="faac1-191">CheckBox</span><span class="sxs-lookup"><span data-stu-id="faac1-191">CheckBox</span></span>|  
|<span data-ttu-id="faac1-192">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="faac1-192">ToolbarWindow32</span></span>|<span data-ttu-id="faac1-193">RadioButton</span><span class="sxs-lookup"><span data-stu-id="faac1-193">RadioButton</span></span>|  
|<span data-ttu-id="faac1-194">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="faac1-194">ToolbarWindow32</span></span>|<span data-ttu-id="faac1-195">区切り記号</span><span class="sxs-lookup"><span data-stu-id="faac1-195">Separator</span></span>|  
|<span data-ttu-id="faac1-196">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="faac1-196">tooltips_class32</span></span>|<span data-ttu-id="faac1-197">ToolTip</span><span class="sxs-lookup"><span data-stu-id="faac1-197">ToolTip</span></span>|  
|<span data-ttu-id="faac1-198">#32774</span><span class="sxs-lookup"><span data-stu-id="faac1-198">#32774</span></span>|<span data-ttu-id="faac1-199">ToolTip</span><span class="sxs-lookup"><span data-stu-id="faac1-199">ToolTip</span></span>|  
|<span data-ttu-id="faac1-200">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="faac1-200">ReBarWindow32</span></span>|<span data-ttu-id="faac1-201">ツール バー</span><span class="sxs-lookup"><span data-stu-id="faac1-201">Toolbar</span></span>|  
|<span data-ttu-id="faac1-202">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="faac1-202">SysTreeView32</span></span>|<span data-ttu-id="faac1-203">ツリー</span><span class="sxs-lookup"><span data-stu-id="faac1-203">Tree</span></span>|  
|<span data-ttu-id="faac1-204">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="faac1-204">SysTreeView32</span></span>|<span data-ttu-id="faac1-205">TreeItem</span><span class="sxs-lookup"><span data-stu-id="faac1-205">TreeItem</span></span>|  
  
 <span data-ttu-id="faac1-206">**メモ** RichEdit コントロールは、Windows Vista に付属しているバージョン (RichEd20.dll バージョン3.1 以降では MsftEdit.dll バージョン4.1 以降) でのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="faac1-206">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="faac1-207">次のコントロールはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="faac1-207">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="faac1-208">クラス名</span><span class="sxs-lookup"><span data-stu-id="faac1-208">Class name</span></span>|<span data-ttu-id="faac1-209">コントロール型</span><span class="sxs-lookup"><span data-stu-id="faac1-209">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="faac1-210">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="faac1-210">SysAnimate32</span></span>|<span data-ttu-id="faac1-211">Image</span><span class="sxs-lookup"><span data-stu-id="faac1-211">Image</span></span>|  
|<span data-ttu-id="faac1-212">SysPager</span><span class="sxs-lookup"><span data-stu-id="faac1-212">SysPager</span></span>|<span data-ttu-id="faac1-213">Spinner</span><span class="sxs-lookup"><span data-stu-id="faac1-213">Spinner</span></span>|  
|<span data-ttu-id="faac1-214">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="faac1-214">SysDateTimePick32</span></span>|<span data-ttu-id="faac1-215">カスタム</span><span class="sxs-lookup"><span data-stu-id="faac1-215">Custom</span></span>|  
|<span data-ttu-id="faac1-216">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="faac1-216">SysMonthCal32</span></span>|<span data-ttu-id="faac1-217">Calendar</span><span class="sxs-lookup"><span data-stu-id="faac1-217">Calendar</span></span>|  
|<span data-ttu-id="faac1-218">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="faac1-218">MS_WINNOTE</span></span>|<span data-ttu-id="faac1-219">ヒント</span><span class="sxs-lookup"><span data-stu-id="faac1-219">Tooltip</span></span>|  
|<span data-ttu-id="faac1-220">VBBubble</span><span class="sxs-lookup"><span data-stu-id="faac1-220">VBBubble</span></span>|<span data-ttu-id="faac1-221">ヒント</span><span class="sxs-lookup"><span data-stu-id="faac1-221">Tooltip</span></span>|  
|<span data-ttu-id="faac1-222">ScrollBar (スタンドアロン コントロールとして使用される場合)</span><span class="sxs-lookup"><span data-stu-id="faac1-222">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="faac1-223">スライダー</span><span class="sxs-lookup"><span data-stu-id="faac1-223">Slider</span></span>|  
|<span data-ttu-id="faac1-224">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="faac1-224">SuperGrid</span></span>|<span data-ttu-id="faac1-225">カスタム</span><span class="sxs-lookup"><span data-stu-id="faac1-225">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>

## <a name="windows-forms-controls"></a><span data-ttu-id="faac1-226">Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="faac1-226">Windows Forms Controls</span></span>  

 <span data-ttu-id="faac1-227">Windows フォームコントロールは、 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] UIAutomationClientsideProviders.dll のクライアント側プロバイダーを介してに公開されます。</span><span class="sxs-lookup"><span data-stu-id="faac1-227">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="faac1-228">このアセンブリは、UI オートメーション クライアント アプリケーションで使用するために、自動的に登録されます。</span><span class="sxs-lookup"><span data-stu-id="faac1-228">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="faac1-229">通常、Win32 コモンコントロールのマネージラッパーである Windows フォームコントロールは、でサポートされてい [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="faac1-229">Typically, Windows Forms controls that are managed wrappers for Win32 common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="faac1-230">次のコントロールがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="faac1-230">The following controls are supported.</span></span>  
  
|<span data-ttu-id="faac1-231">Class Name (クラス名)</span><span class="sxs-lookup"><span data-stu-id="faac1-231">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="faac1-232">ボタン</span><span class="sxs-lookup"><span data-stu-id="faac1-232">Button</span></span>|  
|<span data-ttu-id="faac1-233">CheckBox</span><span class="sxs-lookup"><span data-stu-id="faac1-233">CheckBox</span></span>|  
|<span data-ttu-id="faac1-234">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="faac1-234">CheckedListBox</span></span>|  
|<span data-ttu-id="faac1-235">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="faac1-235">ColorDialog</span></span>|  
|<span data-ttu-id="faac1-236">ComboBox</span><span class="sxs-lookup"><span data-stu-id="faac1-236">ComboBox</span></span>|  
|<span data-ttu-id="faac1-237">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="faac1-237">FolderBrowser</span></span>|  
|<span data-ttu-id="faac1-238">FontDialog</span><span class="sxs-lookup"><span data-stu-id="faac1-238">FontDialog</span></span>|  
|<span data-ttu-id="faac1-239">GroupBox</span><span class="sxs-lookup"><span data-stu-id="faac1-239">GroupBox</span></span>|  
|<span data-ttu-id="faac1-240">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="faac1-240">HscrollBar</span></span>|  
|<span data-ttu-id="faac1-241">ImageList</span><span class="sxs-lookup"><span data-stu-id="faac1-241">ImageList</span></span>|  
|<span data-ttu-id="faac1-242">Label</span><span class="sxs-lookup"><span data-stu-id="faac1-242">Label</span></span>|  
|<span data-ttu-id="faac1-243">ListBox</span><span class="sxs-lookup"><span data-stu-id="faac1-243">ListBox</span></span>|  
|<span data-ttu-id="faac1-244">ListView</span><span class="sxs-lookup"><span data-stu-id="faac1-244">ListView</span></span>|  
|<span data-ttu-id="faac1-245">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="faac1-245">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="faac1-246">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="faac1-246">MonthCalendar</span></span>|  
|<span data-ttu-id="faac1-247">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="faac1-247">NotifyIcon</span></span>|  
|<span data-ttu-id="faac1-248">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="faac1-248">OpenFileDialog</span></span>|  
|<span data-ttu-id="faac1-249">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="faac1-249">PageSetupDialog</span></span>|  
|<span data-ttu-id="faac1-250">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="faac1-250">PrintDialog</span></span>|  
|<span data-ttu-id="faac1-251">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="faac1-251">ProgressBar</span></span>|  
|<span data-ttu-id="faac1-252">RadioButton</span><span class="sxs-lookup"><span data-stu-id="faac1-252">RadioButton</span></span>|  
|<span data-ttu-id="faac1-253">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="faac1-253">RichTextBox</span></span>|  
|<span data-ttu-id="faac1-254">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="faac1-254">SaveFileDialog</span></span>|  
|<span data-ttu-id="faac1-255">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="faac1-255">ScrollableControl</span></span>|  
|<span data-ttu-id="faac1-256">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="faac1-256">SoundPlayer</span></span>|  
|<span data-ttu-id="faac1-257">StatusBar</span><span class="sxs-lookup"><span data-stu-id="faac1-257">StatusBar</span></span>|  
|<span data-ttu-id="faac1-258">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="faac1-258">TabControl/TabPage</span></span>|  
|<span data-ttu-id="faac1-259">TextBox</span><span class="sxs-lookup"><span data-stu-id="faac1-259">TextBox</span></span>|  
|<span data-ttu-id="faac1-260">Timer</span><span class="sxs-lookup"><span data-stu-id="faac1-260">Timer</span></span>|  
|<span data-ttu-id="faac1-261">ツール バー</span><span class="sxs-lookup"><span data-stu-id="faac1-261">Toolbar</span></span>|  
|<span data-ttu-id="faac1-262">ToolTip</span><span class="sxs-lookup"><span data-stu-id="faac1-262">ToolTip</span></span>|  
|<span data-ttu-id="faac1-263">TrackBar</span><span class="sxs-lookup"><span data-stu-id="faac1-263">TrackBar</span></span>|  
|<span data-ttu-id="faac1-264">TreeView</span><span class="sxs-lookup"><span data-stu-id="faac1-264">TreeView</span></span>|  
|<span data-ttu-id="faac1-265">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="faac1-265">VscrollBar</span></span>|  
|<span data-ttu-id="faac1-266">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="faac1-266">WebBrowser</span></span>|  
  
 <span data-ttu-id="faac1-267">次のコントロールは、 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Microsoft Active Accessibility のサポートを通じてのみに公開されます。</span><span class="sxs-lookup"><span data-stu-id="faac1-267">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="faac1-268">一部の機能が使用できないことがあります。</span><span class="sxs-lookup"><span data-stu-id="faac1-268">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="faac1-269">コントロール名</span><span class="sxs-lookup"><span data-stu-id="faac1-269">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="faac1-270">BindingSource</span><span class="sxs-lookup"><span data-stu-id="faac1-270">BindingSource</span></span>|  
|<span data-ttu-id="faac1-271">DataGrid</span><span class="sxs-lookup"><span data-stu-id="faac1-271">DataGrid</span></span>|  
|<span data-ttu-id="faac1-272">DataGridView</span><span class="sxs-lookup"><span data-stu-id="faac1-272">DataGridView</span></span>|  
|<span data-ttu-id="faac1-273">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="faac1-273">DataNavigator</span></span>|  
|<span data-ttu-id="faac1-274">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="faac1-274">DomainUpDown</span></span>|  
|<span data-ttu-id="faac1-275">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="faac1-275">ErrorProvider</span></span>|  
|<span data-ttu-id="faac1-276">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="faac1-276">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="faac1-277">フォーム</span><span class="sxs-lookup"><span data-stu-id="faac1-277">Form</span></span>|  
|<span data-ttu-id="faac1-278">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="faac1-278">LinkLabel</span></span>|  
|<span data-ttu-id="faac1-279">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="faac1-279">HelpProvider</span></span>|  
|<span data-ttu-id="faac1-280">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="faac1-280">MaskedTextBox</span></span>|  
|<span data-ttu-id="faac1-281">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="faac1-281">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="faac1-282">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="faac1-282">NumericUpDown</span></span>|  
|<span data-ttu-id="faac1-283">パネル</span><span class="sxs-lookup"><span data-stu-id="faac1-283">Panel</span></span>|  
|<span data-ttu-id="faac1-284">PictureBox</span><span class="sxs-lookup"><span data-stu-id="faac1-284">PictureBox</span></span>|  
|<span data-ttu-id="faac1-285">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="faac1-285">PrintDocument</span></span>|  
|<span data-ttu-id="faac1-286">PrintPreview-Control</span><span class="sxs-lookup"><span data-stu-id="faac1-286">PrintPreview-Control</span></span>|  
|<span data-ttu-id="faac1-287">PrintPreview-Dialog</span><span class="sxs-lookup"><span data-stu-id="faac1-287">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="faac1-288">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="faac1-288">PropertyGrid</span></span>|  
|<span data-ttu-id="faac1-289">UserControl</span><span class="sxs-lookup"><span data-stu-id="faac1-289">UserControl</span></span>|  
|<span data-ttu-id="faac1-290">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="faac1-290">ToolStrip</span></span>|  
|<span data-ttu-id="faac1-291">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="faac1-291">TableLayoutPanel</span></span>|  
|<span data-ttu-id="faac1-292">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="faac1-292">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="faac1-293">スプリッター</span><span class="sxs-lookup"><span data-stu-id="faac1-293">Splitter</span></span>|  
|<span data-ttu-id="faac1-294">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="faac1-294">RaftingContainer</span></span>|  
|<span data-ttu-id="faac1-295">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="faac1-295">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="faac1-296">関連項目</span><span class="sxs-lookup"><span data-stu-id="faac1-296">See also</span></span>

- [<span data-ttu-id="faac1-297">UI オートメーション コントロール型</span><span class="sxs-lookup"><span data-stu-id="faac1-297">UI Automation Control Types</span></span>](ui-automation-control-types.md)
