---
title: Windows フォームに関する破壊的変更
description: .NET Core 3.0 および 3.1 における Windows フォームでの破壊的変更の一覧を示します。
ms.date: 09/08/2020
ms.openlocfilehash: b944f7eea89b61f41feb8eef99e949c2d6017960
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726432"
---
# <a name="breaking-changes-in-windows-forms-for-net-core-30-and-31"></a><span data-ttu-id="5a737-103">.NET Core 3.0 および 3.1 における Windows フォームでの破壊的変更</span><span class="sxs-lookup"><span data-stu-id="5a737-103">Breaking changes in Windows Forms for .NET Core 3.0 and 3.1</span></span>

<span data-ttu-id="5a737-104">Windows フォームのサポートは、.NET Core にバージョン 3.0 で追加されました。</span><span class="sxs-lookup"><span data-stu-id="5a737-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="5a737-105">この記事では、Windows フォームの破壊的変更を、導入された .NET のバージョン別に説明します。</span><span class="sxs-lookup"><span data-stu-id="5a737-105">This article lists breaking changes for Windows Forms by the .NET version in which they were introduced.</span></span> <span data-ttu-id="5a737-106">この記事は、.NET Framework または以前のバージョンの .NET Core (3.0 以降) から Windows フォーム アプリをアップグレードするユーザーを対象としています。</span><span class="sxs-lookup"><span data-stu-id="5a737-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article applies to you.</span></span>

<span data-ttu-id="5a737-107">このページでは、次の破壊的変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="5a737-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="5a737-108">互換性に影響する変更点</span><span class="sxs-lookup"><span data-stu-id="5a737-108">Breaking change</span></span> | <span data-ttu-id="5a737-109">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="5a737-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="5a737-110">削除されたコントロール</span><span class="sxs-lookup"><span data-stu-id="5a737-110">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="5a737-111">3.1</span><span class="sxs-lookup"><span data-stu-id="5a737-111">3.1</span></span> |
| [<span data-ttu-id="5a737-112">ヒントが表示されていると CellFormatting が発生しない</span><span class="sxs-lookup"><span data-stu-id="5a737-112">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="5a737-113">3.1</span><span class="sxs-lookup"><span data-stu-id="5a737-113">3.1</span></span> |
| [<span data-ttu-id="5a737-114">Control.DefaultFont を Segoe UI 9 pt に変更</span><span class="sxs-lookup"><span data-stu-id="5a737-114">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="5a737-115">3.0</span><span class="sxs-lookup"><span data-stu-id="5a737-115">3.0</span></span> |
| [<span data-ttu-id="5a737-116">FolderBrowserDialog の最新化</span><span class="sxs-lookup"><span data-stu-id="5a737-116">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="5a737-117">3.0</span><span class="sxs-lookup"><span data-stu-id="5a737-117">3.0</span></span> |
| [<span data-ttu-id="5a737-118">一部の Windows フォーム型から SerializableAttribute を削除</span><span class="sxs-lookup"><span data-stu-id="5a737-118">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="5a737-119">3.0</span><span class="sxs-lookup"><span data-stu-id="5a737-119">3.0</span></span> |
| [<span data-ttu-id="5a737-120">AllowUpdateChildControlIndexForTabControls 互換性スイッチがサポートされない</span><span class="sxs-lookup"><span data-stu-id="5a737-120">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="5a737-121">3.0</span><span class="sxs-lookup"><span data-stu-id="5a737-121">3.0</span></span> |
| [<span data-ttu-id="5a737-122">DomainUpDown.UseLegacyScrolling 互換性スイッチがサポートされない</span><span class="sxs-lookup"><span data-stu-id="5a737-122">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="5a737-123">3.0</span><span class="sxs-lookup"><span data-stu-id="5a737-123">3.0</span></span> |
| [<span data-ttu-id="5a737-124">DoNotLoadLatestRichEditControl 互換性スイッチがサポートされない</span><span class="sxs-lookup"><span data-stu-id="5a737-124">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="5a737-125">3.0</span><span class="sxs-lookup"><span data-stu-id="5a737-125">3.0</span></span> |
| [<span data-ttu-id="5a737-126">DoNotSupportSelectAllShortcutInMultilineTextBox 互換性スイッチがサポートされない</span><span class="sxs-lookup"><span data-stu-id="5a737-126">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="5a737-127">3.0</span><span class="sxs-lookup"><span data-stu-id="5a737-127">3.0</span></span> |
| [<span data-ttu-id="5a737-128">DontSupportReentrantFilterMessage 互換性スイッチがサポートされない</span><span class="sxs-lookup"><span data-stu-id="5a737-128">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="5a737-129">3.0</span><span class="sxs-lookup"><span data-stu-id="5a737-129">3.0</span></span> |
| [<span data-ttu-id="5a737-130">EnableVisualStyleValidation 互換性スイッチがサポートされない</span><span class="sxs-lookup"><span data-stu-id="5a737-130">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="5a737-131">3.0</span><span class="sxs-lookup"><span data-stu-id="5a737-131">3.0</span></span> |
| [<span data-ttu-id="5a737-132">UseLegacyContextMenuStripSourceControlValue 互換性スイッチがサポートされない</span><span class="sxs-lookup"><span data-stu-id="5a737-132">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="5a737-133">3.0</span><span class="sxs-lookup"><span data-stu-id="5a737-133">3.0</span></span> |
| [<span data-ttu-id="5a737-134">UseLegacyImages 互換性スイッチがサポートされない</span><span class="sxs-lookup"><span data-stu-id="5a737-134">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="5a737-135">3.0</span><span class="sxs-lookup"><span data-stu-id="5a737-135">3.0</span></span> |

## <a name="net-core-31"></a><span data-ttu-id="5a737-136">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="5a737-136">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

<span data-ttu-id="5a737-137">\*\*_</span><span class="sxs-lookup"><span data-stu-id="5a737-137">\*\*_</span></span>

## <a name="net-core-30"></a><span data-ttu-id="5a737-138">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5a737-138">.NET Core 3.0</span></span>

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

<span data-ttu-id="5a737-139">_\*\*</span><span class="sxs-lookup"><span data-stu-id="5a737-139">_\*\*</span></span>

## <a name="see-also"></a><span data-ttu-id="5a737-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="5a737-140">See also</span></span>

- [<span data-ttu-id="5a737-141">Windows フォーム アプリを .NET Core に移植する</span><span class="sxs-lookup"><span data-stu-id="5a737-141">Port a Windows Forms app to .NET Core</span></span>](/dotnet/desktop/winforms/migration/?view=netdesktop-5.0&preserve-view=true)
