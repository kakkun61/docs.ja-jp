---
title: '軽減策: 新しい 64 ビット JIT コンパイラ'
description: .NET Framework 4.6 に付属する新しい 64 ビット JIT コンパイラと、コンパイル中に発生することがある想定外の動作または例外について説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
ms.openlocfilehash: 228c286f6c5620dc838df5002edc60863a0fe4e2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256600"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a><span data-ttu-id="7b3fa-103">軽減策:新しい 64 ビット JIT コンパイラ</span><span class="sxs-lookup"><span data-stu-id="7b3fa-103">Mitigation: New 64-bit JIT Compiler</span></span>

<span data-ttu-id="7b3fa-104">.NET Framework 4.6 以降では、ランタイムに Just-In-Time コンパイル用の新しい 64 ビット JIT コンパイラが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-104">Starting with .NET Framework 4.6, the runtime includes a new 64-bit JIT compiler for just-in-time compilation.</span></span> <span data-ttu-id="7b3fa-105">この変更は、32 ビット JIT コンパイラでのコンパイルには影響しません。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-105">This change does not affect compilation with the 32-bit JIT compiler.</span></span>  
  
## <a name="unexpected-behavior-or-exceptions"></a><span data-ttu-id="7b3fa-106">予期しない動作または例外</span><span class="sxs-lookup"><span data-stu-id="7b3fa-106">Unexpected behavior or exceptions</span></span>  

 <span data-ttu-id="7b3fa-107">場合によっては、新しい 64 ビット JIT コンパイラでのコンパイルの結果、古い 64 ビット JIT コンパイラでコンパイルされたコードの実行時に監視されない動作が発生したり、ランタイム例外が発生したりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-107">In some cases, compilation with the new 64-bit JIT compiler results in a runtime exception or in behavior that is not observed when executing code compiled by the older 64-bit JIT compiler.</span></span> <span data-ttu-id="7b3fa-108">既知の相違には次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-108">The known differences include the following:</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7b3fa-109">これらの既知の問題はすべて、.NET Framework 4.6.2 と共にリリースされた新しい 64 ビット コンパイラで対処済みです。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-109">All of these known issues have been addressed in the new 64-bit compiler released with the .NET Framework 4.6.2.</span></span> <span data-ttu-id="7b3fa-110">また、Windows 更新プログラムに含まれる .NET Framework 4.6 および 4.6.1 のサービス リリースでも大部分に対処済みです。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-110">Most have also been addressed in service releases of the .NET Framework 4.6 and 4.6.1 that are included with Windows Update.</span></span> <span data-ttu-id="7b3fa-111">使用している Windows のバージョンが最新のものであることを確認するか、.NET Framework 4.6.2 にアップグレードすることで、これらの問題を解消できます。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-111">You can eliminate these issues by ensuring that your version of Windows is up to date, or by upgrading to the .NET Framework 4.6.2.</span></span>  
  
- <span data-ttu-id="7b3fa-112">特定の条件下では、最適化が有効なリリース ビルドの <xref:System.NullReferenceException> がボックス化解除操作でスローされる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-112">Under certain conditions, an unboxing operation may throw a <xref:System.NullReferenceException> in Release builds with optimization turned on.</span></span>  
  
- <span data-ttu-id="7b3fa-113">場合によっては、大きなメソッド本文の実働コードの実行時に <xref:System.StackOverflowException> がスローされることがあります。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-113">In some cases, execution of production code in a large method body may throw a <xref:System.StackOverflowException>.</span></span>  
  
- <span data-ttu-id="7b3fa-114">特定の条件下では、メソッドに渡された構造体が、リリース ビルドの値の型ではなく、参照型として扱われます。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-114">Under certain conditions, structures passed to a method are treated as reference types rather than value types in Release builds.</span></span> <span data-ttu-id="7b3fa-115">この問題の兆候の 1 つは、コレクション内の個々の項目が予期しない順序で表示されることです。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-115">One of the manifestations of this issue is that the individual items in a collection appear in an unexpected order.</span></span>  
  
- <span data-ttu-id="7b3fa-116">特定の条件下では、最適化が有効な場合、高ビットが設定された <xref:System.UInt16> 値が正しく比較されません。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-116">Under certain conditions, the comparison of <xref:System.UInt16> values with their high bit set is incorrect if optimization is enabled.</span></span>  
  
- <span data-ttu-id="7b3fa-117">特定の条件下では、特に、配列値の初期化中に、<xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL 命令でのメモリ初期化により、正しくない値でメモリが初期化される場合があります。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-117">Under certain conditions, particularly when initializing array values, memory initialization by the <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL instruction may initialize memory with an incorrect value.</span></span> <span data-ttu-id="7b3fa-118">その結果、ハンドルされない例外または正しくない出力が発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-118">This can result either in an unhandled exception or incorrect output.</span></span>  
  
- <span data-ttu-id="7b3fa-119">特定のまれな条件下では、コンパイラの最適化が有効な場合に、条件付きのビット テストで正しくない <xref:System.Boolean> 値が返されたり、例外がスローされたりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-119">Under certain rare conditions, a conditional bit test can return the incorrect <xref:System.Boolean> value or throw an exception if compiler optimizations are enabled.</span></span>  
  
- <span data-ttu-id="7b3fa-120">特定の条件下では、`if` ステートメントを使用して、`try` ブロックの開始前と `try` ブロックの終了時の条件をテストし、同じ条件を `catch` または `finally` ブロックで評価する場合、新しい 64 ビット JIT コンパイラが、コードの最適化の際に `catch` または `finally` ブロックから `if` 条件を削除します。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-120">Under certain conditions, if an `if` statement is used to test for a condition before entering  a `try` block and in the exit from the `try` block, and the same condition is evaluated in the `catch` or `finally` block, the new 64-bit JIT compiler removes the `if` condition from the `catch` or `finally` block when it optimizes code.</span></span> <span data-ttu-id="7b3fa-121">その結果、`catch` または `finally` ブロックの `if` ステートメント内のコードは無条件で実行されます。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-121">As a result, code inside the `if` statement in the `catch` or `finally` block is executed unconditionally.</span></span>  
  
<a name="General"></a>

## <a name="mitigation-of-known-issues"></a><span data-ttu-id="7b3fa-122">既知の問題の軽減策</span><span class="sxs-lookup"><span data-stu-id="7b3fa-122">Mitigation of known issues</span></span>  

 <span data-ttu-id="7b3fa-123">上記の問題が発生する場合は、次のいずれかの方法で解決できます。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-123">If you encounter the issues listed above, you can address them by doing any of the following:</span></span>  
  
- <span data-ttu-id="7b3fa-124">.NET Framework 4.6.2 にアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-124">Upgrade to the .NET Framework 4.6.2.</span></span> <span data-ttu-id="7b3fa-125">.NET Framework 4.6.2 に含まれている新しい 64 ビット コンパイラは、これらの既知の問題のそれぞれに対処します。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-125">The new 64-bit compiler included with the .NET Framework 4.6.2 addresses each of these known issues.</span></span>  
  
- <span data-ttu-id="7b3fa-126">Windows Update を実行して、Windows のバージョンが最新のものであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-126">Ensure that your version of Windows is up to date by running Windows Update.</span></span> <span data-ttu-id="7b3fa-127">.NET Framework 4.6 および 4.6.1 へのサービス更新により、ボックス化解除操作での <xref:System.NullReferenceException> を除き、これらの問題のそれぞれに対処することができます。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-127">Service updates to the .NET Framework 4.6 and 4.6.1 address each of these issues except the <xref:System.NullReferenceException> in an unboxing operation.</span></span>  
  
- <span data-ttu-id="7b3fa-128">古い 64 ビット JIT コンパイラでコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-128">Compile with the older 64-bit JIT compiler.</span></span> <span data-ttu-id="7b3fa-129">この方法の詳細については、「[その他の問題の軽減策](#Other)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-129">See the [Mitigation of other issues](#Other) section for more information on how to do this.</span></span>  
  
<a name="Other"></a>

## <a name="mitigation-of-other-issues"></a><span data-ttu-id="7b3fa-130">その他の問題の軽減策</span><span class="sxs-lookup"><span data-stu-id="7b3fa-130">Mitigation of other issues</span></span>  

 <span data-ttu-id="7b3fa-131">古い 64 ビット コンパイラと新しい 64 ビット JIT コンパイラでコンパイルされたコードの動作、またはアプリのデバッグ バージョンとリリース バージョン (両方とも新しい 64 ビット JIT コンパイラでコンパイル) の動作に違いが見られる場合は、次のようにして、古い 64 ビット JIT コンパイラでアプリをコンパイルすることができます。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-131">If you encounter any other difference in behavior between code compiled with the older 64-bit compiler and the new 64-bit JIT compiler, or between the debug and release versions of your app that are both compiled with the new 64-bit JIT compiler, you can do the following to compile your app with the older 64-bit JIT compiler:</span></span>  
  
- <span data-ttu-id="7b3fa-132">アプリケーションごとに、アプリケーションの構成ファイルに [\<useLegacyJit>](../configure-apps/file-schema/runtime/uselegacyjit-element.md) 要素を追加できます。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-132">On a per-application basis, you can add the [\<useLegacyJit>](../configure-apps/file-schema/runtime/uselegacyjit-element.md) element to your application's configuration file.</span></span> <span data-ttu-id="7b3fa-133">次のように新しい 64 ビット JIT コンパイラでのコンパイルを無効にし、代わりに従来の 64 ビット JIT コンパイラを使用します。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-133">The following disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
- <span data-ttu-id="7b3fa-134">ユーザーごとに、`useLegacyJit` という `REG_DWORD` 値をレジストリの `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` キーに追加できます。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-134">On a per-user basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="7b3fa-135">値を 1 にすると、従来の 64 ビット JIT コンパイラが有効になり、値を 0 にすると、従来の 64 ビット JIT コンパイラが無効になり、新しい 64 ビット JIT コンパイラが有効になります。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-135">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
- <span data-ttu-id="7b3fa-136">コンピューターごとに、`useLegacyJit` という名前の `REG_DWORD` 値をレジストリの `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` キーに追加できます。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-136">On a per-machine basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="7b3fa-137">値を 1 にすると、従来の 64 ビット JIT コンパイラが有効になり、値を 0 にすると、従来の 64 ビット JIT コンパイラが無効になり、新しい 64 ビット JIT コンパイラが有効になります。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-137">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
 <span data-ttu-id="7b3fa-138">[Microsoft Connect](https://connect.microsoft.com/VisualStudio) でバグを報告し、問題を弊社に知らせることもできます。</span><span class="sxs-lookup"><span data-stu-id="7b3fa-138">You can also let us know about the problem by reporting a bug on [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b3fa-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b3fa-139">See also</span></span>

- [<span data-ttu-id="7b3fa-140">アプリケーションの互換性</span><span class="sxs-lookup"><span data-stu-id="7b3fa-140">Application compatibility</span></span>](application-compatibility.md)
- [<span data-ttu-id="7b3fa-141">\<useLegacyJit> 要素</span><span class="sxs-lookup"><span data-stu-id="7b3fa-141">\<useLegacyJit> Element</span></span>](../configure-apps/file-schema/runtime/uselegacyjit-element.md)
