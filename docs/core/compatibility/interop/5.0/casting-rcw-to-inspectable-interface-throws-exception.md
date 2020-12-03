---
title: 破壊的変更:RCW を `InterfaceIsIInspectable` にキャストすると例外がスローされる
description: .NET 5.0 での相互運用に関する破壊的変更について学習します。RCW を `InterfaceIsIInspectable` インターフェイスにキャストすると、PlatformNotSupportedException がスローされます。
ms.date: 09/13/2020
ms.openlocfilehash: 7c0f37057aebcc41d0c00d949b921ec3a4bdf012
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759818"
---
# <a name="casting-rcw-to-an-interfaceisiinspectable-interface-throws-platformnotsupportedexception"></a><span data-ttu-id="54a43-103">RCW を `InterfaceIsIInspectable` インターフェイスにキャストすると、PlatformNotSupportedException がスローされる</span><span class="sxs-lookup"><span data-stu-id="54a43-103">Casting RCW to an `InterfaceIsIInspectable` interface throws PlatformNotSupportedException</span></span>

<span data-ttu-id="54a43-104">ランタイム呼び出し可能ラッパー (RCW) を <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> とマークされたインターフェイスにキャストすると、<xref:System.PlatformNotSupportedException> がスローされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="54a43-104">Casting a runtime callable wrapper (RCW) to an interface marked as <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> now throws a <xref:System.PlatformNotSupportedException>.</span></span> <span data-ttu-id="54a43-105">この変更は、[WinRT のサポートが .NET から削除された](built-in-support-for-winrt-removed.md)ことのフォローアップです。</span><span class="sxs-lookup"><span data-stu-id="54a43-105">This change is a follow up to the [removal of WinRT support from .NET](built-in-support-for-winrt-removed.md).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="54a43-106">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="54a43-106">Version introduced</span></span>

<span data-ttu-id="54a43-107">5.0 RC2</span><span class="sxs-lookup"><span data-stu-id="54a43-107">5.0 RC2</span></span>

## <a name="change-description"></a><span data-ttu-id="54a43-108">変更内容</span><span class="sxs-lookup"><span data-stu-id="54a43-108">Change description</span></span>

<span data-ttu-id="54a43-109">.NET 5.0 Preview 6 以前の .NET バージョンでは、RCW を <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> とマークされたインターフェイスにキャストすると想定どおりに動作します。</span><span class="sxs-lookup"><span data-stu-id="54a43-109">In .NET versions prior to .NET 5.0 preview 6, casting an RCW to an interface marked as <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> works as expected.</span></span> <span data-ttu-id="54a43-110">.NET 5.0 Preview 6-8 および RC1 では、RCW を <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> インターフェイスに正常にキャストできます。</span><span class="sxs-lookup"><span data-stu-id="54a43-110">In .NET 5.0 previews 6-8 and RC1, you can successfully cast an RCW to an <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> interface.</span></span> <span data-ttu-id="54a43-111">ただし、ランタイムの基になるサポートが [.NET 5.0 Preview 6 で削除された](built-in-support-for-winrt-removed.md)ため、インターフェイスでメソッドを実行するとアクセス違反が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="54a43-111">However, you might get access violations when you execute methods on the interface, because the underlying support in the runtime [was removed in .NET 5.0 preview 6](built-in-support-for-winrt-removed.md).</span></span>

<span data-ttu-id="54a43-112">.NET 5.0 RC2 以降のバージョンでは、RCW を <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> とマークされたインターフェイスにキャストすると、キャスト時に <xref:System.PlatformNotSupportedException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="54a43-112">In .NET 5.0 RC2 and later versions, casting an RCW to an interface marked as <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> throws a <xref:System.PlatformNotSupportedException> at cast time.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="54a43-113">変更理由</span><span class="sxs-lookup"><span data-stu-id="54a43-113">Reason for change</span></span>

<span data-ttu-id="54a43-114"><xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> のサポートが、[前の .NET 5.0 Preview で削除されました](built-in-support-for-winrt-removed.md)。</span><span class="sxs-lookup"><span data-stu-id="54a43-114">The support for <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> was [removed in a previous .NET 5.0 preview](built-in-support-for-winrt-removed.md).</span></span> <span data-ttu-id="54a43-115">しかし、<xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> インターフェイスへのキャストが誤って見落とされました。</span><span class="sxs-lookup"><span data-stu-id="54a43-115">However, casting to an <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> interface was accidentally overlooked.</span></span> <span data-ttu-id="54a43-116">ランタイムの基になるサポートが存在しなくなったため、<xref:System.PlatformNotSupportedException> をスローすると、正常なエラー パスが有効になります。</span><span class="sxs-lookup"><span data-stu-id="54a43-116">Since the underlying support in the runtime no longer exists, throwing a <xref:System.PlatformNotSupportedException> enables a graceful failure path.</span></span> <span data-ttu-id="54a43-117">また、例外をスローすることで、この機能がサポートされなくなったことが見つけやすくなります。</span><span class="sxs-lookup"><span data-stu-id="54a43-117">Throwing an exception also makes it more discoverable that this feature is no longer supported.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="54a43-118">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="54a43-118">Recommended action</span></span>

- <span data-ttu-id="54a43-119">Windows ランタイムメタデータ (WinMD) ファイルでインターフェイスを定義できる場合は、代わりに C#/WinRT ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="54a43-119">If you can define the interface in a Windows runtime metadata (WinMD) file, use the C#/WinRT tool instead.</span></span>

- <span data-ttu-id="54a43-120">それ以外の場合は、<xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> ではなく <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIUnknown> としてインターフェイスをマークし、<xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> メソッドのインターフェイスの先頭に 3 つのダミー エントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="54a43-120">Otherwise, mark the interface as <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIUnknown> instead of <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable>, and add three dummy entries to the start of the interface for the <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> methods.</span></span> <span data-ttu-id="54a43-121">次のコード スニペットに例を示します。</span><span class="sxs-lookup"><span data-stu-id="54a43-121">The following code snippet shows an example.</span></span>

  ```csharp
  [InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
  interface IMine
  {
      // Do not call these three methods.
      // They're exclusively to fill in the slots in the vtable.
      void GetIIdsSlot();
      void GetRuntimeClassNameSlot();
      void GetTrustLevelSlot();

      // The original members of the IMine interface go here.
      ...
  }
  ```

## <a name="affected-apis"></a><span data-ttu-id="54a43-122">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="54a43-122">Affected APIs</span></span>

- <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable?displayProperty=fullName>

<!--

### Affected APIs

- `F:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable`

### Category

Interop

-->
