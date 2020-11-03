---
title: アセンブリ読み込みを解決する
description: この記事では、.NET AppDomain.AssemblyResolve イベントについて説明します。 このイベントは、アセンブリの読み込みを制御する必要があるアプリケーションに使用します。
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET], resolving loads
- application domains, loading assemblies
- resolving assembly loads
- assemblies [.NET], loading
- application domains, resolving assembly loads
ms.assetid: 5099e549-f4fd-49fb-a290-549edd456c6a
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 16f2f61a2a36e4189e98c85b3d3ce706a52e2938
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687276"
---
# <a name="resolve-assembly-loads"></a><span data-ttu-id="e8249-104">アセンブリ読み込みを解決する</span><span class="sxs-lookup"><span data-stu-id="e8249-104">Resolve assembly loads</span></span>

<span data-ttu-id="e8249-105">.NET では、アセンブリの読み込みをより細かく制御する必要があるアプリケーションのために、<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> イベントが用意されています。</span><span class="sxs-lookup"><span data-stu-id="e8249-105">.NET provides the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event for applications that require greater control over assembly loading.</span></span> <span data-ttu-id="e8249-106">アプリケーションでこのイベントを処理することにより、通常のプローブ パスの外部から読み込みコンテキストにアセンブリを読み込んだり、アセンブリの複数のバージョンから読み込むものを選んだり、動的アセンブリを生成してそれを返したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="e8249-106">By handling this event, your application can load an assembly into the load context from outside the normal probing paths, select which of several assembly versions to load, emit a dynamic assembly and return it, and so on.</span></span> <span data-ttu-id="e8249-107">ここでは、<xref:System.AppDomain.AssemblyResolve> イベントの処理について説明します。</span><span class="sxs-lookup"><span data-stu-id="e8249-107">This topic provides guidance for handling the <xref:System.AppDomain.AssemblyResolve> event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8249-108">リフレクションのみのコンテキストでアセンブリの読み込みを解決する場合は、代わりに <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> イベントを使います。</span><span class="sxs-lookup"><span data-stu-id="e8249-108">For resolving assembly loads in the reflection-only context, use the <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> event instead.</span></span>  
  
## <a name="how-the-assemblyresolve-event-works"></a><span data-ttu-id="e8249-109">AssemblyResolve イベントのしくみ</span><span class="sxs-lookup"><span data-stu-id="e8249-109">How the AssemblyResolve event works</span></span>  
 <span data-ttu-id="e8249-110"><xref:System.AppDomain.AssemblyResolve> イベント用のハンドラーを登録すると、ランタイムが名前によるアセンブリへのバインドに失敗すると、常にハンドラーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="e8249-110">When you register a handler for the <xref:System.AppDomain.AssemblyResolve> event, the handler is invoked whenever the runtime fails to bind to an assembly by name.</span></span> <span data-ttu-id="e8249-111">たとえば、ユーザー コードから次のメソッドを呼び出すと、<xref:System.AppDomain.AssemblyResolve> イベントが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e8249-111">For example, calling the following methods from user code can cause the <xref:System.AppDomain.AssemblyResolve> event to be raised:</span></span>  
  
- <span data-ttu-id="e8249-112">1 番目の引数が読み込むアセンブリの表示名を表す文字列 (つまり、<xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> プロパティによって返される文字列) である、<xref:System.AppDomain.Load%2A?displayProperty=nameWithType> メソッドまたは <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> メソッドのオーバーロード。</span><span class="sxs-lookup"><span data-stu-id="e8249-112">An <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> method overload or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overload whose first argument is a string that represents the display name of the assembly to load (that is, the string returned by the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property).</span></span>  
  
- <span data-ttu-id="e8249-113">1 番目の引数が読み込むアセンブリを示す <xref:System.Reflection.AssemblyName> オブジェクトである、<xref:System.AppDomain.Load%2A?displayProperty=nameWithType> メソッドまたは <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> メソッドのオーバーロード。</span><span class="sxs-lookup"><span data-stu-id="e8249-113">An <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> method overload or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overload whose first argument is an <xref:System.Reflection.AssemblyName> object that identifies the assembly to load.</span></span>  
  
- <span data-ttu-id="e8249-114"><xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> メソッドのオーバーロード。</span><span class="sxs-lookup"><span data-stu-id="e8249-114">An <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> method overload.</span></span>  
  
- <span data-ttu-id="e8249-115">別のアプリケーション ドメインでオブジェクトをインスタンス化する、<xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> メソッドまたは <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> メソッドのオーバーロード。</span><span class="sxs-lookup"><span data-stu-id="e8249-115">An <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> method overload that instantiates an object in another application domain.</span></span>  
  
### <a name="what-the-event-handler-does"></a><span data-ttu-id="e8249-116">イベント ハンドラーでの処理</span><span class="sxs-lookup"><span data-stu-id="e8249-116">What the event handler does</span></span>  
 <span data-ttu-id="e8249-117"><xref:System.AppDomain.AssemblyResolve> イベントのハンドラーは、読み込まれるアセンブリの表示名を、<xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> プロパティで受け取ります。</span><span class="sxs-lookup"><span data-stu-id="e8249-117">The handler for the <xref:System.AppDomain.AssemblyResolve> event receives the display name of the assembly to be loaded, in the <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="e8249-118">ハンドラーは、アセンブリ名を認識できない場合は `null` (C#)、`Nothing` (Visual Basic)、または `nullptr` (Visual C++) を返します。</span><span class="sxs-lookup"><span data-stu-id="e8249-118">If the handler does not recognize the assembly name, it returns `null` (C#), `Nothing` (Visual Basic), or `nullptr` (Visual C++).</span></span>  
  
 <span data-ttu-id="e8249-119">ハンドラーは、アセンブリ名を認識すると、要求を満たすアセンブリを読み込んで返すことができます。</span><span class="sxs-lookup"><span data-stu-id="e8249-119">If the handler recognizes the assembly name, it can load and return an assembly that satisfies the request.</span></span> <span data-ttu-id="e8249-120">シナリオの例をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="e8249-120">The following list describes some sample scenarios.</span></span>  
  
- <span data-ttu-id="e8249-121">ハンドラーは、アセンブリのバージョンの場所がわかっている場合は、<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> メソッドまたは <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> メソッドを使ってアセンブリを読み込むことができ、正常に読み込んだ場合はアセンブリを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="e8249-121">If the handler knows the location of a version of the assembly, it can load the assembly by using the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> method, and can return the loaded assembly if successful.</span></span>  
  
- <span data-ttu-id="e8249-122">ハンドラーは、バイト配列として格納されているアセンブリのデータベースにアクセスできる場合は、<xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> メソッドのバイト配列を受け取るオーバーロードのいずれかを使って、バイト配列を読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="e8249-122">If the handler has access to a database of assemblies stored as byte arrays, it can load a byte array by using one of the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overloads that take a byte array.</span></span>  
  
- <span data-ttu-id="e8249-123">ハンドラーは、動的アセンブリを生成して返すことができます。</span><span class="sxs-lookup"><span data-stu-id="e8249-123">The handler can generate a dynamic assembly and return it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8249-124">ハンドラーは、アセンブリを読み込み元コンテキストまたは読み込みコンテキストに読み込むか、コンテキストなしで読み込む必要があります。ハンドラーが <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> メソッドまたは <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> メソッドを使ってリフレクションのみのコンテキストにアセンブリを読み込むと、<xref:System.AppDomain.AssemblyResolve> イベントを生成した読み込みの試みは失敗します。</span><span class="sxs-lookup"><span data-stu-id="e8249-124">The handler must load the assembly into the load-from context, into the load context, or without context.If the handler loads the assembly into the reflection-only context by using the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> or the <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> method, the load attempt that raised the <xref:System.AppDomain.AssemblyResolve> event fails.</span></span>  
  
 <span data-ttu-id="e8249-125">適切なアセンブリを返すのはイベント ハンドラーの役目です。</span><span class="sxs-lookup"><span data-stu-id="e8249-125">It is the responsibility of the event handler to return a suitable assembly.</span></span> <span data-ttu-id="e8249-126">ハンドラーは、<xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> プロパティの値を <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> コンストラクターに渡すことによって、要求されたアセンブリの表示名を解析できます。</span><span class="sxs-lookup"><span data-stu-id="e8249-126">The handler can parse the display name of the requested assembly by passing the <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> property value to the <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> constructor.</span></span> <span data-ttu-id="e8249-127">.NET Framework 4 以降では、ハンドラーは <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> プロパティを使って、現在の要求が別のアセンブリの依存関係であるかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="e8249-127">Beginning with the .NET Framework 4, the handler can use the <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property to determine whether the current request is a dependency of another assembly.</span></span> <span data-ttu-id="e8249-128">この情報は、依存関係を満たすアセンブリを特定するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e8249-128">This information can help identify an assembly that will satisfy the dependency.</span></span>  
  
 <span data-ttu-id="e8249-129">イベント ハンドラーは、要求されたバージョンとは異なるバージョンのアセンブリを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="e8249-129">The event handler can return a different version of the assembly than the version that was requested.</span></span>  
  
 <span data-ttu-id="e8249-130">ほとんどの場合、ハンドラーによって返されたアセンブリは、ハンドラーがそれを読み込んだコンテキストに関係なく、読み込みコンテキストで表示されます。</span><span class="sxs-lookup"><span data-stu-id="e8249-130">In most cases, the assembly that is returned by the handler appears in the load context, regardless of the context the handler loads it into.</span></span> <span data-ttu-id="e8249-131">たとえば、ハンドラーが <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> メソッドを使って読み込み元コンテキストにアセンブリを読み込んだ場合でも、ハンドラーによって返されたアセンブリは、読み込みコンテキストに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e8249-131">For example, if the handler uses the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method to load an assembly into the load-from context, the assembly appears in the load context when the handler returns it.</span></span> <span data-ttu-id="e8249-132">ただし、次の場合は、ハンドラーによって返されたアセンブリはコンテキストなしで表示されます。</span><span class="sxs-lookup"><span data-stu-id="e8249-132">However, in the following case the assembly appears without context when the handler returns it:</span></span>  
  
- <span data-ttu-id="e8249-133">ハンドラーがコンテキストなしでアセンブリを読み込んだ場合。</span><span class="sxs-lookup"><span data-stu-id="e8249-133">The handler loads an assembly without context.</span></span>  
  
- <span data-ttu-id="e8249-134"><xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> プロパティが null ではない場合。</span><span class="sxs-lookup"><span data-stu-id="e8249-134">The <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property is not null.</span></span>  
  
- <span data-ttu-id="e8249-135">要求元のアセンブリ (つまり、<xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> プロパティによって返されるアセンブリ) がコンテキストなしで読み込まれた場合。</span><span class="sxs-lookup"><span data-stu-id="e8249-135">The requesting assembly (that is, the assembly that is returned by the <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property) was loaded without context.</span></span>  
  
 <span data-ttu-id="e8249-136">コンテキストについて詳しくは、<xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> メソッドのオーバーロードをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e8249-136">For information about contexts, see the <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> method overload.</span></span>  
  
 <span data-ttu-id="e8249-137">同じアセンブリの複数のバージョンを、同じアプリケーション ドメインに読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="e8249-137">Multiple versions of the same assembly can be loaded into the same application domain.</span></span> <span data-ttu-id="e8249-138">ただし、型の割り当ての問題が発生する可能性があるため、この方法は推奨されません。</span><span class="sxs-lookup"><span data-stu-id="e8249-138">This practice is not recommended, because it can lead to type assignment problems.</span></span> <span data-ttu-id="e8249-139">「[アセンブリの読み込みのベスト プラクティス](../../framework/deployment/best-practices-for-assembly-loading.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e8249-139">See [Best practices for assembly loading](../../framework/deployment/best-practices-for-assembly-loading.md).</span></span>  
  
### <a name="what-the-event-handler-should-not-do"></a><span data-ttu-id="e8249-140">イベント ハンドラーで行ってはいけないこと</span><span class="sxs-lookup"><span data-stu-id="e8249-140">What the event handler should not do</span></span>  
<span data-ttu-id="e8249-141"><xref:System.AppDomain.AssemblyResolve> イベントの処理に関する基本原則は、認識できないアセンブリを返そうとしてはならない、ということです。</span><span class="sxs-lookup"><span data-stu-id="e8249-141">The primary rule for handling the <xref:System.AppDomain.AssemblyResolve> event is that you should not try to return an assembly you do not recognize.</span></span> <span data-ttu-id="e8249-142">ハンドラーを記述するときは、イベントを発生させる可能性があるアセンブリを知っておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8249-142">When you write the handler, you should know which assemblies might cause the event to be raised.</span></span> <span data-ttu-id="e8249-143">それ以外のアセンブリに対して、ハンドラーは null を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8249-143">Your handler should return null for other assemblies.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="e8249-144">.NET Framework 4 以降では、<xref:System.AppDomain.AssemblyResolve> イベントはサテライト アセンブリに対して発生します。</span><span class="sxs-lookup"><span data-stu-id="e8249-144">Beginning with the .NET Framework 4, the <xref:System.AppDomain.AssemblyResolve> event is raised for satellite assemblies.</span></span> <span data-ttu-id="e8249-145">以前のバージョンの .NET Framework で作成されたイベント ハンドラーが、すべてのアセンブリ読み込み要求を解決しようとしている場合、この変更によって影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="e8249-145">This change affects an event handler that was written for an earlier version of the .NET Framework, if the handler tries to resolve all assembly load requests.</span></span> <span data-ttu-id="e8249-146">認識しないアセンブリを無視するイベント ハンドラーはこの変更の影響を受けません。null を返し、通常のフォールバック メカニズムがそれに続きます。</span><span class="sxs-lookup"><span data-stu-id="e8249-146">Event handlers that ignore assemblies they do not recognize are not affected by this change: They return null, and normal fallback mechanisms are followed.</span></span>  

<span data-ttu-id="e8249-147">アセンブリを読み込むとき、イベント ハンドラーは、<xref:System.AppDomain.AssemblyResolve> イベントを再帰的に生成する可能性がある <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> メソッドまたは <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> メソッドのオーバー ロードを、使わないようにする必要があります。使った場合、スタック オーバーフローが発生することがあります</span><span class="sxs-lookup"><span data-stu-id="e8249-147">When loading an assembly, the event handler must not use any of the <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overloads that can cause the <xref:System.AppDomain.AssemblyResolve> event to be raised recursively, because this can lead to a stack overflow.</span></span> <span data-ttu-id="e8249-148">(このトピックで先に示したリストを参照)。すべてのイベント ハンドラーから返るまで例外はスローされないため、読み込み要求に対して例外処理を提供した場合でも、この問題は発生します。</span><span class="sxs-lookup"><span data-stu-id="e8249-148">(See the list provided earlier in this topic.) This happens even if you provide exception handling for the load request, because no exception is thrown until all event handlers have returned.</span></span> <span data-ttu-id="e8249-149">したがって、次のようなコードでは、`MyAssembly` が見つからないとスタック オーバーフローが発生します。</span><span class="sxs-lookup"><span data-stu-id="e8249-149">Thus, the following code results in a stack overflow if `MyAssembly` is not found:</span></span>  

```cpp
using namespace System;
using namespace System::Reflection;

ref class Example
{
internal:
    static Assembly^ MyHandler(Object^ source, ResolveEventArgs^ e)
    {
        Console::WriteLine("Resolving {0}", e->Name);
        return Assembly::Load(e->Name);
    }
};

void main()
{
    AppDomain^ ad = AppDomain::CreateDomain("Test");
    ad->AssemblyResolve += gcnew ResolveEventHandler(&Example::MyHandler);

    try
    {
        Object^ obj = ad->CreateInstanceAndUnwrap(
            "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
            "MyType");
    }
    catch (Exception^ ex)
    {
        Console::WriteLine(ex->Message);
    }
}

/* This example produces output similar to the following:

Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
...
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null

Process is terminated due to StackOverflowException.
 */
```

```csharp
using System;
using System.Reflection;

class BadExample
{
    static void Main()
    {
        AppDomain ad = AppDomain.CreateDomain("Test");
        ad.AssemblyResolve += MyHandler;

        try
        {
            object obj = ad.CreateInstanceAndUnwrap(
                "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
                "MyType");
        }
        catch (Exception ex)
        {
            Console.WriteLine(ex.Message);
        }
    }

    static Assembly MyHandler(object source, ResolveEventArgs e)
    {
        Console.WriteLine("Resolving {0}", e.Name);
        return Assembly.Load(e.Name);
    }
}

/* This example produces output similar to the following:

Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
...
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null

Process is terminated due to StackOverflowException.
 */
```

```vb
Imports System.Reflection

Class BadExample

    Shared Sub Main()

        Dim ad As AppDomain = AppDomain.CreateDomain("Test")
        AddHandler ad.AssemblyResolve, AddressOf MyHandler

        Try
            Dim obj As object = ad.CreateInstanceAndUnwrap(
                "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
                "MyType")
        Catch ex As Exception
            Console.WriteLine(ex.Message)
        End Try
    End Sub

    Shared Function MyHandler(ByVal source As Object, _
                              ByVal e As ResolveEventArgs) As Assembly
        Console.WriteLine("Resolving {0}", e.Name)
        Return Assembly.Load(e.Name)
    End Function
End Class

' This example produces output similar to the following:
'
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'...
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'
'Process is terminated due to StackOverflowException.
```

## <a name="see-also"></a><span data-ttu-id="e8249-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="e8249-150">See also</span></span>

- [<span data-ttu-id="e8249-151">アセンブリの読み込みのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="e8249-151">Best practices for assembly loading</span></span>](../../framework/deployment/best-practices-for-assembly-loading.md)
- [<span data-ttu-id="e8249-152">アプリケーション ドメインを使用する</span><span class="sxs-lookup"><span data-stu-id="e8249-152">Use application domains</span></span>](../../framework/app-domains/use.md)
