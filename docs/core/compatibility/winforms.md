---
title: Windows フォームに関する破壊的変更
description: .NET Core および .NET 5 の Windows フォームにおける破壊的変更の一覧を示します。
ms.date: 09/08/2020
ms.openlocfilehash: c79fd28b5c3b81ae7ddf1ef3f470601108b87705
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440791"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="46f4d-103">Windows フォームでの破壊的変更</span><span class="sxs-lookup"><span data-stu-id="46f4d-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="46f4d-104">Windows フォームのサポートは、.NET Core にバージョン 3.0 で追加されました。</span><span class="sxs-lookup"><span data-stu-id="46f4d-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="46f4d-105">この記事では、Windows フォームの破壊的変更を、導入された .NET のバージョン別に説明します。</span><span class="sxs-lookup"><span data-stu-id="46f4d-105">This article lists breaking changes for Windows Forms by the .NET version in which they were introduced.</span></span> <span data-ttu-id="46f4d-106">この記事は、.NET Framework または以前のバージョンの .NET Core (3.0 以降) から Windows フォーム アプリをアップグレードするユーザーを対象としています。</span><span class="sxs-lookup"><span data-stu-id="46f4d-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article applies to you.</span></span>

<span data-ttu-id="46f4d-107">このページでは、次の破壊的変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="46f4d-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="46f4d-108">互換性に影響する変更点</span><span class="sxs-lookup"><span data-stu-id="46f4d-108">Breaking change</span></span> | <span data-ttu-id="46f4d-109">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="46f4d-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="46f4d-110">TextFormatFlags.ModifyString は古くなっています</span><span class="sxs-lookup"><span data-stu-id="46f4d-110">TextFormatFlags.ModifyString is obsolete</span></span>](#textformatflagsmodifystring-is-obsolete) | <span data-ttu-id="46f4d-111">5.0</span><span class="sxs-lookup"><span data-stu-id="46f4d-111">5.0</span></span> |
| [<span data-ttu-id="46f4d-112">カスタマイズされたセル スタイルのフォントが DataGridView によってリセットされなくなった</span><span class="sxs-lookup"><span data-stu-id="46f4d-112">DataGridView no longer resets fonts for customized cell styles</span></span>](#datagridview-no-longer-resets-fonts-for-customized-cell-styles) | <span data-ttu-id="46f4d-113">5.0</span><span class="sxs-lookup"><span data-stu-id="46f4d-113">5.0</span></span> |
| [<span data-ttu-id="46f4d-114">WPF アプリと WinForms アプリで OutputType が WinExe に設定されている</span><span class="sxs-lookup"><span data-stu-id="46f4d-114">OutputType set to WinExe for WPF and WinForms apps</span></span>](#outputtype-set-to-winexe-for-wpf-and-winforms-apps) | <span data-ttu-id="46f4d-115">5.0</span><span class="sxs-lookup"><span data-stu-id="46f4d-115">5.0</span></span> |
| [<span data-ttu-id="46f4d-116">DataGridView 関連の API が InvalidOperationException をスローするようになった</span><span class="sxs-lookup"><span data-stu-id="46f4d-116">DataGridView-related APIs now throw InvalidOperationException</span></span>](#datagridview-related-apis-now-throw-invalidoperationexception) | <span data-ttu-id="46f4d-117">5.0</span><span class="sxs-lookup"><span data-stu-id="46f4d-117">5.0</span></span> |
| [<span data-ttu-id="46f4d-118">WinForms と WPF アプリで Microsoft.NET.Sdk が使用される</span><span class="sxs-lookup"><span data-stu-id="46f4d-118">WinForms and WPF apps use Microsoft.NET.Sdk</span></span>](#winforms-and-wpf-apps-use-microsoftnetsdk) | <span data-ttu-id="46f4d-119">5.0</span><span class="sxs-lookup"><span data-stu-id="46f4d-119">5.0</span></span> |
| [<span data-ttu-id="46f4d-120">削除されたステータス バー コントロール</span><span class="sxs-lookup"><span data-stu-id="46f4d-120">Removed status bar controls</span></span>](#removed-status-bar-controls) | <span data-ttu-id="46f4d-121">5.0</span><span class="sxs-lookup"><span data-stu-id="46f4d-121">5.0</span></span> |
| [<span data-ttu-id="46f4d-122">WinForms メソッドで ArgumentException がスローされるようになった</span><span class="sxs-lookup"><span data-stu-id="46f4d-122">WinForms methods now throw ArgumentException</span></span>](#winforms-methods-now-throw-argumentexception) | <span data-ttu-id="46f4d-123">5.0</span><span class="sxs-lookup"><span data-stu-id="46f4d-123">5.0</span></span> |
| [<span data-ttu-id="46f4d-124">WinForms メソッドで ArgumentNullException がスローされるようになった</span><span class="sxs-lookup"><span data-stu-id="46f4d-124">WinForms methods now throw ArgumentNullException</span></span>](#winforms-methods-now-throw-argumentnullexception) | <span data-ttu-id="46f4d-125">5.0</span><span class="sxs-lookup"><span data-stu-id="46f4d-125">5.0</span></span> |
| [<span data-ttu-id="46f4d-126">WinForms プロパティによる ArgumentOutOfRangeException のスロー</span><span class="sxs-lookup"><span data-stu-id="46f4d-126">WinForms properties now throw ArgumentOutOfRangeException</span></span>](#winforms-properties-now-throw-argumentoutofrangeexception) | <span data-ttu-id="46f4d-127">5.0</span><span class="sxs-lookup"><span data-stu-id="46f4d-127">5.0</span></span> |
| [<span data-ttu-id="46f4d-128">削除されたコントロール</span><span class="sxs-lookup"><span data-stu-id="46f4d-128">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="46f4d-129">3.1</span><span class="sxs-lookup"><span data-stu-id="46f4d-129">3.1</span></span> |
| [<span data-ttu-id="46f4d-130">ヒントが表示されていると CellFormatting が発生しない</span><span class="sxs-lookup"><span data-stu-id="46f4d-130">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="46f4d-131">3.1</span><span class="sxs-lookup"><span data-stu-id="46f4d-131">3.1</span></span> |
| [<span data-ttu-id="46f4d-132">Control.DefaultFont を Segoe UI 9 pt に変更</span><span class="sxs-lookup"><span data-stu-id="46f4d-132">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="46f4d-133">3.0</span><span class="sxs-lookup"><span data-stu-id="46f4d-133">3.0</span></span> |
| [<span data-ttu-id="46f4d-134">FolderBrowserDialog の最新化</span><span class="sxs-lookup"><span data-stu-id="46f4d-134">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="46f4d-135">3.0</span><span class="sxs-lookup"><span data-stu-id="46f4d-135">3.0</span></span> |
| [<span data-ttu-id="46f4d-136">一部の Windows フォーム型から SerializableAttribute を削除</span><span class="sxs-lookup"><span data-stu-id="46f4d-136">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="46f4d-137">3.0</span><span class="sxs-lookup"><span data-stu-id="46f4d-137">3.0</span></span> |
| [<span data-ttu-id="46f4d-138">AllowUpdateChildControlIndexForTabControls 互換性スイッチがサポートされない</span><span class="sxs-lookup"><span data-stu-id="46f4d-138">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="46f4d-139">3.0</span><span class="sxs-lookup"><span data-stu-id="46f4d-139">3.0</span></span> |
| [<span data-ttu-id="46f4d-140">DomainUpDown.UseLegacyScrolling 互換性スイッチがサポートされない</span><span class="sxs-lookup"><span data-stu-id="46f4d-140">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="46f4d-141">3.0</span><span class="sxs-lookup"><span data-stu-id="46f4d-141">3.0</span></span> |
| [<span data-ttu-id="46f4d-142">DoNotLoadLatestRichEditControl 互換性スイッチがサポートされない</span><span class="sxs-lookup"><span data-stu-id="46f4d-142">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="46f4d-143">3.0</span><span class="sxs-lookup"><span data-stu-id="46f4d-143">3.0</span></span> |
| [<span data-ttu-id="46f4d-144">DoNotSupportSelectAllShortcutInMultilineTextBox 互換性スイッチがサポートされない</span><span class="sxs-lookup"><span data-stu-id="46f4d-144">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="46f4d-145">3.0</span><span class="sxs-lookup"><span data-stu-id="46f4d-145">3.0</span></span> |
| [<span data-ttu-id="46f4d-146">DontSupportReentrantFilterMessage 互換性スイッチがサポートされない</span><span class="sxs-lookup"><span data-stu-id="46f4d-146">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="46f4d-147">3.0</span><span class="sxs-lookup"><span data-stu-id="46f4d-147">3.0</span></span> |
| [<span data-ttu-id="46f4d-148">EnableVisualStyleValidation 互換性スイッチがサポートされない</span><span class="sxs-lookup"><span data-stu-id="46f4d-148">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="46f4d-149">3.0</span><span class="sxs-lookup"><span data-stu-id="46f4d-149">3.0</span></span> |
| [<span data-ttu-id="46f4d-150">UseLegacyContextMenuStripSourceControlValue 互換性スイッチがサポートされない</span><span class="sxs-lookup"><span data-stu-id="46f4d-150">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="46f4d-151">3.0</span><span class="sxs-lookup"><span data-stu-id="46f4d-151">3.0</span></span> |
| [<span data-ttu-id="46f4d-152">UseLegacyImages 互換性スイッチがサポートされない</span><span class="sxs-lookup"><span data-stu-id="46f4d-152">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="46f4d-153">3.0</span><span class="sxs-lookup"><span data-stu-id="46f4d-153">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="46f4d-154">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="46f4d-154">.NET 5.0</span></span>

[!INCLUDE [modifystring-field-of-textformatflags-obsolete](../../../includes/core-changes/windowsforms/5.0/modifystring-field-of-textformatflags-obsolete.md)]

***

[!INCLUDE [datagridview-doesnt-reset-custom-font-settings](../../../includes/core-changes/windowsforms/5.0/datagridview-doesnt-reset-custom-font-settings.md)]

<span data-ttu-id="46f4d-155">\*\*_</span><span class="sxs-lookup"><span data-stu-id="46f4d-155">\*\*_</span></span>

[!INCLUDE [automatically-infer-winexe-output-type](../../../includes/core-changes/windowsforms/5.0/automatically-infer-winexe-output-type.md)]

_*_

[!INCLUDE [null-owner-causes-invalidoperationexception](../../../includes/core-changes/windowsforms/5.0/null-owner-causes-invalidoperationexception.md)]

_*_

[!INCLUDE [sdk-and-target-framework-change](../../../includes/core-changes/windowsforms/5.0/sdk-and-target-framework-change.md)]

_*_

[!INCLUDE [winforms-deprecated-controls](../../../includes/core-changes/windowsforms/5.0/winforms-deprecated-controls.md)]

_*_

[!INCLUDE [invalid-args-cause-argumentexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentexception.md)]

_*_

[!INCLUDE [null-args-cause-argumentnullexception](../../../includes/core-changes/windowsforms/5.0/null-args-cause-argumentnullexception.md)]

_*_

[!INCLUDE [invalid-args-cause-argumentoutofrangeexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentoutofrangeexception.md)]

_*_

## <a name="net-core-31"></a><span data-ttu-id="46f4d-156">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="46f4d-156">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

_*_

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

_*_

## <a name="net-core-30"></a><span data-ttu-id="46f4d-157">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="46f4d-157">.NET Core 3.0</span></span>

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9pt](~/includes/core-changes/windowsforms/3.0/control-defaultfont-changed.md)]

_*_

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/3.0/modernized-folderbrowserdialog.md)]

_*_

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/3.0/remove-serializationattribute.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyscrolling.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotloadlatestricheditcontrol.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-dontsupportreentrantfiltermessage.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-enablevisualstylevalidation.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyimages.md)]

<span data-ttu-id="46f4d-158">_\*\*</span><span class="sxs-lookup"><span data-stu-id="46f4d-158">_\*\*</span></span>

## <a name="see-also"></a><span data-ttu-id="46f4d-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="46f4d-159">See also</span></span>

- [<span data-ttu-id="46f4d-160">Windows フォーム アプリを .NET Core に移植する</span><span class="sxs-lookup"><span data-stu-id="46f4d-160">Port a Windows Forms app to .NET Core</span></span>](/dotnet/desktop/winforms/migration/?view=netdesktop-5.0&preserve-view=true)
