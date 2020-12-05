---
title: 呼び出し元情報
description: 呼び出し元情報の引数属性を使用して、メソッドから呼び出し元情報を取得する方法について説明します。
ms.date: 11/04/2019
ms.openlocfilehash: 700cde26fbe4e6c48155f88bfc63af59af86cfe2
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739777"
---
# <a name="caller-information"></a><span data-ttu-id="ab261-103">呼び出し元情報</span><span class="sxs-lookup"><span data-stu-id="ab261-103">Caller information</span></span>

<span data-ttu-id="ab261-104">呼び出し元情報の属性を使用すると、メソッドへの呼び出し元に関する情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="ab261-104">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="ab261-105">ソース コードのファイル パス、ソース コードの行番号、および呼び出し元のメンバー名を取得できます。</span><span class="sxs-lookup"><span data-stu-id="ab261-105">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="ab261-106">この情報は、トレース、デバッグ、および診断ツールの作成に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ab261-106">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>

<span data-ttu-id="ab261-107">この情報を取得するには、省略可能なパラメーターに適用される属性を使用します。各パラメーターには既定値があります。</span><span class="sxs-lookup"><span data-stu-id="ab261-107">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="ab261-108">次の表に、 [system.runtime.compilerservices](/dotnet/api/system.runtime.compilerservices) 名前空間で定義されている呼び出し元情報の属性を示します。</span><span class="sxs-lookup"><span data-stu-id="ab261-108">The following table lists the Caller Info attributes that are defined in the [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) namespace:</span></span>

|<span data-ttu-id="ab261-109">属性</span><span class="sxs-lookup"><span data-stu-id="ab261-109">Attribute</span></span>|<span data-ttu-id="ab261-110">説明</span><span class="sxs-lookup"><span data-stu-id="ab261-110">Description</span></span>|<span data-ttu-id="ab261-111">Type</span><span class="sxs-lookup"><span data-stu-id="ab261-111">Type</span></span>|
|---------|-----------|----|
|[<span data-ttu-id="ab261-112">CallerFilePath</span><span class="sxs-lookup"><span data-stu-id="ab261-112">CallerFilePath</span></span>](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|<span data-ttu-id="ab261-113">呼び出し元を含むソース ファイルのフル パスです。</span><span class="sxs-lookup"><span data-stu-id="ab261-113">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="ab261-114">これは、コンパイル時のファイル パスです。</span><span class="sxs-lookup"><span data-stu-id="ab261-114">This is the file path at compile time.</span></span>|`String`
|[<span data-ttu-id="ab261-115">CallerLineNumber</span><span class="sxs-lookup"><span data-stu-id="ab261-115">CallerLineNumber</span></span>](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|<span data-ttu-id="ab261-116">メソッドが呼び出されたソース ファイルの行番号。</span><span class="sxs-lookup"><span data-stu-id="ab261-116">Line number in the source file at which the method is called.</span></span>|`Integer`|
|[<span data-ttu-id="ab261-117">CallerMemberName</span><span class="sxs-lookup"><span data-stu-id="ab261-117">CallerMemberName</span></span>](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|<span data-ttu-id="ab261-118">呼び出し元のメソッド名またはプロパティ名。</span><span class="sxs-lookup"><span data-stu-id="ab261-118">Method or property name of the caller.</span></span> <span data-ttu-id="ab261-119">このトピックで後述する「メンバー名」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab261-119">See the Member Names section later in this topic.</span></span>|`String`|

## <a name="example"></a><span data-ttu-id="ab261-120">例</span><span class="sxs-lookup"><span data-stu-id="ab261-120">Example</span></span>

<span data-ttu-id="ab261-121">次の例は、これらの属性を使用して呼び出し元をトレースする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="ab261-121">The following example shows how you might use these attributes to trace a caller.</span></span>

```fsharp
open System.Diagnostics
open System.Runtime.CompilerServices
open System.Runtime.InteropServices

type Tracer() =
    member _.DoTrace(message: string,
                      [<CallerMemberName; Optional; DefaultParameterValue("")>] memberName: string,
                      [<CallerFilePath; Optional; DefaultParameterValue("")>] path: string,
                      [<CallerLineNumber; Optional; DefaultParameterValue(0)>] line: int) =
        Trace.WriteLine(sprintf $"Message: {message}")
        Trace.WriteLine(sprintf $"Member name: {memberName}")
        Trace.WriteLine(sprintf $"Source file path: {path}")
        Trace.WriteLine(sprintf $"Source line number: {line}")
```

## <a name="remarks"></a><span data-ttu-id="ab261-122">注釈</span><span class="sxs-lookup"><span data-stu-id="ab261-122">Remarks</span></span>

<span data-ttu-id="ab261-123">呼び出し元情報の属性は、省略可能なパラメーターにのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="ab261-123">Caller Info attributes can only be applied to optional parameters.</span></span> <span data-ttu-id="ab261-124">呼び出し元情報属性により、コンパイラは、呼び出し元情報属性で修飾された省略可能な各パラメーターに対して適切な値を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="ab261-124">The Caller Info attributes cause the compiler to write the proper value for each optional parameter decorated with a Caller Info attribute.</span></span>

<span data-ttu-id="ab261-125">呼び出し元情報の値は、コンパイル時に中間言語 (IL) 内にリテラルとして出力されます。</span><span class="sxs-lookup"><span data-stu-id="ab261-125">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="ab261-126">例外の [StackTrace](/dotnet/api/system.diagnostics.stacktrace) プロパティの結果とは異なり、結果は難読化の影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="ab261-126">Unlike the results of the [StackTrace](/dotnet/api/system.diagnostics.stacktrace) property for exceptions, the results aren't affected by obfuscation.</span></span>

<span data-ttu-id="ab261-127">省略可能な引数を明示的に指定して、呼び出し元情報を制御したり、非表示にしたりできます。</span><span class="sxs-lookup"><span data-stu-id="ab261-127">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

## <a name="member-names"></a><span data-ttu-id="ab261-128">メンバー名</span><span class="sxs-lookup"><span data-stu-id="ab261-128">Member names</span></span>

<span data-ttu-id="ab261-129">属性を使用し [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) て、 `String` 呼び出されたメソッドの引数としてメンバー名を指定しないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="ab261-129">You can use the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="ab261-130">この方法を使用すると、リファクタリングの名前の変更で `String` 値が変更されないという問題が発生しなくなります。</span><span class="sxs-lookup"><span data-stu-id="ab261-130">By using this technique, you avoid the problem that Rename Refactoring doesn't change the `String` values.</span></span> <span data-ttu-id="ab261-131">この利点は、次のタスクで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ab261-131">This benefit is especially useful for the following tasks:</span></span>

- <span data-ttu-id="ab261-132">トレース ルーチンと診断ルーチンの使用。</span><span class="sxs-lookup"><span data-stu-id="ab261-132">Using tracing and diagnostic routines.</span></span>
- <span data-ttu-id="ab261-133">データをバインドするときに [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="ab261-133">Implementing the [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) interface when binding data.</span></span> <span data-ttu-id="ab261-134">このインターフェイスを使用すると、オブジェクトのプロパティが、プロパティが変更されたことをデータ バインド コントロールに通知できます。これによって、このコントロールは、更新された情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="ab261-134">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="ab261-135">属性を指定しない場合は、 [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) プロパティ名をリテラルとして指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab261-135">Without the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="ab261-136">次のグラフは、CallerMemberName 属性を使用したときに返されるメンバー名を示しています。</span><span class="sxs-lookup"><span data-stu-id="ab261-136">The following chart shows the member names that are returned when you use the CallerMemberName attribute.</span></span>

|<span data-ttu-id="ab261-137">呼び出しは、次のものの中で発生します。</span><span class="sxs-lookup"><span data-stu-id="ab261-137">Calls occurs within</span></span>|<span data-ttu-id="ab261-138">メンバー名の結果</span><span class="sxs-lookup"><span data-stu-id="ab261-138">Member name result</span></span>|
|-------------------|------------------|
|<span data-ttu-id="ab261-139">メソッド、プロパティ、またはイベント</span><span class="sxs-lookup"><span data-stu-id="ab261-139">Method, property, or event</span></span>|<span data-ttu-id="ab261-140">呼び出しが発生したメソッド、プロパティ、またはイベントの名前。</span><span class="sxs-lookup"><span data-stu-id="ab261-140">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="ab261-141">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="ab261-141">Constructor</span></span>|<span data-ttu-id="ab261-142">文字列「.ctor」</span><span class="sxs-lookup"><span data-stu-id="ab261-142">The string ".ctor"</span></span>|
|<span data-ttu-id="ab261-143">静的コンストラクター</span><span class="sxs-lookup"><span data-stu-id="ab261-143">Static constructor</span></span>|<span data-ttu-id="ab261-144">文字列「.cctor」</span><span class="sxs-lookup"><span data-stu-id="ab261-144">The string ".cctor"</span></span>|
|<span data-ttu-id="ab261-145">デストラクターです。</span><span class="sxs-lookup"><span data-stu-id="ab261-145">Destructor</span></span>|<span data-ttu-id="ab261-146">文字列「Finalize」</span><span class="sxs-lookup"><span data-stu-id="ab261-146">The string "Finalize"</span></span>|
|<span data-ttu-id="ab261-147">ユーザー定義の演算子または変換</span><span class="sxs-lookup"><span data-stu-id="ab261-147">User-defined operators or conversions</span></span>|<span data-ttu-id="ab261-148">生成されたメンバー名 (「op_Addition」など)。</span><span class="sxs-lookup"><span data-stu-id="ab261-148">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="ab261-149">Attribute コンストラクター</span><span class="sxs-lookup"><span data-stu-id="ab261-149">Attribute constructor</span></span>|<span data-ttu-id="ab261-150">属性が適用されるメンバーの名前。</span><span class="sxs-lookup"><span data-stu-id="ab261-150">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="ab261-151">属性がメンバー内の要素 (パラメーター、戻り値、ジェネリック型パラメーターなど) である場合、この結果は、その要素に関連付けられているメンバーの名前になります。</span><span class="sxs-lookup"><span data-stu-id="ab261-151">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="ab261-152">含んでいないメンバー (型に適用されているアセンブリ レベルや属性など)</span><span class="sxs-lookup"><span data-stu-id="ab261-152">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="ab261-153">省略可能なパラメーターの既定値。</span><span class="sxs-lookup"><span data-stu-id="ab261-153">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="ab261-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab261-154">See also</span></span>

- [<span data-ttu-id="ab261-155">属性</span><span class="sxs-lookup"><span data-stu-id="ab261-155">Attributes</span></span>](attributes.md)
- [<span data-ttu-id="ab261-156">名前付き引数</span><span class="sxs-lookup"><span data-stu-id="ab261-156">Named arguments</span></span>](parameters-and-arguments.md#named-arguments)
- [<span data-ttu-id="ab261-157">省略可能なパラメーター</span><span class="sxs-lookup"><span data-stu-id="ab261-157">Optional parameters</span></span>](parameters-and-arguments.md#optional-parameters)
