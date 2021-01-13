---
title: Debugging StackOverflow エラー
description: StackOverflow 例外の診断方法について説明します
ms.topic: tutorial
ms.date: 12/22/2020
ms.openlocfilehash: 92edf854ddcc2e778949d74eff1370cf27db25b4
ms.sourcegitcommit: c0b803bffaf101e12f071faf94ca21b46d04ff30
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/24/2020
ms.locfileid: "97764930"
---
# <a name="debugging-stackoverflow-errors"></a><span data-ttu-id="e030a-103">Debugging StackOverflow エラー</span><span class="sxs-lookup"><span data-stu-id="e030a-103">Debugging StackOverflow errors</span></span>

<span data-ttu-id="e030a-104"><xref:System.StackOverflowException> は、入れ子になったメソッド呼び出しが多くなりすぎ、実行スタックがオーバーフローした場合にスローされます。</span><span class="sxs-lookup"><span data-stu-id="e030a-104">A <xref:System.StackOverflowException> is thrown when when the execution stack overflows because it contains too many nested method calls.</span></span>  

<span data-ttu-id="e030a-105">たとえば、次のようなアプリがあるとします。</span><span class="sxs-lookup"><span data-stu-id="e030a-105">For example, suppose you have an app as follows:</span></span>

````
using System;

namespace temp
{
    class Program
    {
        static void Main(string[] args)
        {
            Main(args); // oops this recursion won't stop
        }
    }
}
````

<span data-ttu-id="e030a-106">スタック領域がなくなるまで、Main メソッドによって継続的にそれ自体が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="e030a-106">The Main method will continuously call itself until there is no more stack space.</span></span>  <span data-ttu-id="e030a-107">スタック領域がなくなると、実行を継続できず、<xref:System.StackOverflowException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="e030a-107">Once there is no more stack space, execution cannot continue and so it will throw a <xref:System.StackOverflowException>.</span></span>  

````
> dotnet run
Stack overflow.
````

> [!NOTE]
> <span data-ttu-id="e030a-108">.NET 5 以降では、呼び出し履歴がコンソールに出力されます。</span><span class="sxs-lookup"><span data-stu-id="e030a-108">On .NET 5 and later, the callstack is output to the console.</span></span>

> [!NOTE]
> <span data-ttu-id="e030a-109">この記事では、lldb でスタック オーバーフローをデバッグする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e030a-109">This article describes how to debug a stack overflow with lldb.</span></span> <span data-ttu-id="e030a-110">Windows で実行している場合、[Visual Studio](/visualstudio/debugger/what-is-debugging) または [Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging) でアプリをデバッグすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e030a-110">If you are running on Windows, we suggest debugging the app with [Visual Studio](/visualstudio/debugger/what-is-debugging) or [Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging).</span></span>  

## <a name="example"></a><span data-ttu-id="e030a-111">例</span><span class="sxs-lookup"><span data-stu-id="e030a-111">Example</span></span>

1. <span data-ttu-id="e030a-112">クラッシュ時にダンプを収集するようにそれを構成した状態でアプリを実行します</span><span class="sxs-lookup"><span data-stu-id="e030a-112">Run the app with it configured to collect a dump on crash</span></span>

    ````
    > export COMPlus_DbgEnableMiniDump=1
    > dotnet run
    Stack overflow.
    Writing minidump with heap to file /tmp/coredump.6412
    Written 58191872 bytes (14207 pages) to core file
    ````

2. <span data-ttu-id="e030a-113">[dotnet-sos](dotnet-sos.md) を使用して SOS 拡張機能をインストールします</span><span class="sxs-lookup"><span data-stu-id="e030a-113">Install the SOS extension using [dotnet-sos](dotnet-sos.md)</span></span>

    ````
    dotnet-sos install
    ````

3. <span data-ttu-id="e030a-114">lldb でダンプをデバッグし、失敗したスタックを確認します</span><span class="sxs-lookup"><span data-stu-id="e030a-114">Debug the dump in lldb to see the failing stack</span></span>

    ````
    lldb --core /temp/coredump.6412
    (lldb) bt
    ...
        frame #261930: 0x00007f59b40900cc
        frame #261931: 0x00007f59b40900cc
        frame #261932: 0x00007f59b40900cc
        frame #261933: 0x00007f59b40900cc
        frame #261934: 0x00007f59b40900cc
        frame #261935: 0x00007f5a2d4a080f libcoreclr.so`CallDescrWorkerInternal at unixasmmacrosamd64.inc:867
        frame #261936: 0x00007f5a2d3cc4c3 libcoreclr.so`MethodDescCallSite::CallTargetWorker(unsigned long const*, unsigned long*, int) at callhelpers.cpp:70
        frame #261937: 0x00007f5a2d3cc468 libcoreclr.so`MethodDescCallSite::CallTargetWorker(this=<unavailable>, pArguments=0x00007ffe8222e7b0, pReturnValue=0x0000000000000000, cbReturnValue=0) at callhelpers.cpp:604
        frame #261938: 0x00007f5a2d4b6182 libcoreclr.so`RunMain(MethodDesc*, short, int*, PtrArray**) [inlined] MethodDescCallSite::Call(this=<unavailable>, pArguments=<unavailable>) at callhelpers.h:468
    ...
    ````

4. <span data-ttu-id="e030a-115">一番上のフレーム `0x00007f59b40900cc` が数回繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="e030a-115">The top frame `0x00007f59b40900cc` is repeated several times.</span></span> <span data-ttu-id="e030a-116">[SOS](sos-debugging-extension.md) `ip2md` コマンドを使用し、`0x00007f59b40900cc` アドレスに配置されているメソッドを判別します</span><span class="sxs-lookup"><span data-stu-id="e030a-116">Use the [SOS](sos-debugging-extension.md) `ip2md` command to figure out what method is located at the `0x00007f59b40900cc` address</span></span>

    ````
    (lldb) ip2md 0x00007f59b40900cc
    MethodDesc:   00007f59b413ffa8
    Method Name:          temp.Program.Main(System.String[])
    Class:                00007f59b4181d40
    MethodTable:          00007f59b4190020
    mdToken:              0000000006000001
    Module:               00007f59b413dbf8
    IsJitted:             yes
    Current CodeAddr:     00007f59b40900a0
    Version History:
      ILCodeVersion:      0000000000000000
      ReJIT ID:           0
      IL Addr:            0000000000000000
         CodeAddr:           00007f59b40900a0  (MinOptJitted)
         NativeCodeVersion:  0000000000000000
    Source file:  /temp/Program.cs @ 9
    ````

5. <span data-ttu-id="e030a-117">示されたメソッド temp.Program.Main(System.String[]) とソース "/temp/Program.cs @ 9" を参照し、問題を突き止められるか確認します。</span><span class="sxs-lookup"><span data-stu-id="e030a-117">Go look at the indicated method temp.Program.Main(System.String[]) and source "/temp/Program.cs @ 9" to see if you can figure out what you did wrong.</span></span> <span data-ttu-id="e030a-118">依然として不明の場合、コードのその領域でログ記録を追加できます。</span><span class="sxs-lookup"><span data-stu-id="e030a-118">If it still wasn't clear you could add logging in that area of the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="e030a-119">参照</span><span class="sxs-lookup"><span data-stu-id="e030a-119">See Also</span></span>

* [<span data-ttu-id="e030a-120">.NET でのダンプの概要</span><span class="sxs-lookup"><span data-stu-id="e030a-120">An introduction to dumps in .NET</span></span>](dumps.md)
* [<span data-ttu-id="e030a-121">Linux ダンプのデバッグ</span><span class="sxs-lookup"><span data-stu-id="e030a-121">Debug Linux dumps</span></span>](debug-linux-dumps.md)
* [<span data-ttu-id="e030a-122">.NET 用 SOS デバッガー拡張</span><span class="sxs-lookup"><span data-stu-id="e030a-122">SOS Debugging Extension for .NET</span></span>](sos-debugging-extension.md)
