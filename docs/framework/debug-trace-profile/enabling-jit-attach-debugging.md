---
title: JIT アタッチ デバッグの有効化
description: エラーが発生したときにデバッガーをプロセスにアタッチするには、just-in-time (JIT) アタッチデバッグを有効にします。 特定のメソッドまたは関数によってトリガーされる場合があります。
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
ms.openlocfilehash: dc1c8608b0d16e618b5ad6144d492db3302532dc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273504"
---
# <a name="enabling-jit-attach-debugging"></a><span data-ttu-id="25f5f-104">JIT アタッチ デバッグの有効化</span><span class="sxs-lookup"><span data-stu-id="25f5f-104">Enabling JIT-Attach Debugging</span></span>

<span data-ttu-id="25f5f-105">JIT アタッチ デバッグとは、エラーが発生したとき、または特定のメソッドまたは関数によってトリガーすることで、プロセスにデバッガーをアタッチすることを表すために使用される語句です。</span><span class="sxs-lookup"><span data-stu-id="25f5f-105">JIT-attach debugging is the phrase used to describe attaching a debugger to a process when you encounter errors, or it can be triggered by specific methods or functions.</span></span>  
  
 <span data-ttu-id="25f5f-106">JIT アタッチ デバッグは、次のエラー状態で使用されます。</span><span class="sxs-lookup"><span data-stu-id="25f5f-106">JIT-attach debugging is used under the following fault conditions:</span></span>  
  
- <span data-ttu-id="25f5f-107">未処理の例外 (ネイティブ コードとマネージド コードの両方)。</span><span class="sxs-lookup"><span data-stu-id="25f5f-107">Unhandled exceptions (in both native and managed code).</span></span>  
  
- <span data-ttu-id="25f5f-108"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> メソッドまたは [RaiseFailFastException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raisefailfastexception) 関数 (Windows 7 ファミリ)。</span><span class="sxs-lookup"><span data-stu-id="25f5f-108"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> method or [RaiseFailFastException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raisefailfastexception) function (Windows 7 family).</span></span>  
  
- <span data-ttu-id="25f5f-109">実行時の致命的なエラー。</span><span class="sxs-lookup"><span data-stu-id="25f5f-109">Runtime fatal errors.</span></span>  
  
 <span data-ttu-id="25f5f-110">JIT アタッチ デバッグは、次のメソッドや関数への呼び出しによってもトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="25f5f-110">JIT-attach debugging is also triggered by calls to the following methods and functions:</span></span>  
  
- <span data-ttu-id="25f5f-111"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> メソッド</span><span class="sxs-lookup"><span data-stu-id="25f5f-111"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="25f5f-112"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> メソッド</span><span class="sxs-lookup"><span data-stu-id="25f5f-112"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="25f5f-113">[DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) 関数 (Win32)。</span><span class="sxs-lookup"><span data-stu-id="25f5f-113">[DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) function (Win32).</span></span>  
  
 <span data-ttu-id="25f5f-114">.NET Framework 4 より前の .NET Framework では、ネイティブデバッガーとマネージデバッガーの動作を制御するために個別のレジストリキーが提供されていました。</span><span class="sxs-lookup"><span data-stu-id="25f5f-114">Before the .NET Framework 4, the .NET Framework provided separate registry keys to control the behavior of native and managed debuggers.</span></span> <span data-ttu-id="25f5f-115">.NET Framework 4 以降では、コントロールは単一のレジストリキー (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug) の下に統合されます。</span><span class="sxs-lookup"><span data-stu-id="25f5f-115">Starting with the .NET Framework 4, control is consolidated under a single registry key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span></span> <span data-ttu-id="25f5f-116">このキーに設定できる値により、デバッガーを呼び出すかどうか、呼び出す場合は、ユーザーの操作を必要とするダイアログ ボックスによって呼び出すかどうかが決まります。</span><span class="sxs-lookup"><span data-stu-id="25f5f-116">The values you can set for that key determine whether a debugger is invoked, and, if so, whether it is invoked with a dialog box that requires user interaction.</span></span> <span data-ttu-id="25f5f-117">このレジストリキーの設定の詳細については、「 [自動デバッグの構成](/windows/win32/debug/configuring-automatic-debugging)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="25f5f-117">For information about setting this registry key, see [Configuring Automatic Debugging](/windows/win32/debug/configuring-automatic-debugging).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25f5f-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="25f5f-118">See also</span></span>

- [<span data-ttu-id="25f5f-119">デバッグ、トレース、およびプロファイリング</span><span class="sxs-lookup"><span data-stu-id="25f5f-119">Debugging, Tracing, and Profiling</span></span>](index.md)
- [<span data-ttu-id="25f5f-120">イメージのデバッグの簡略化</span><span class="sxs-lookup"><span data-stu-id="25f5f-120">Making an Image Easier to Debug</span></span>](making-an-image-easier-to-debug.md)
