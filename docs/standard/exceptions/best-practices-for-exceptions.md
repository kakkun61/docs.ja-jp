---
title: 例外の推奨事項 - .NET
description: try/catch/finally の使用、例外のない一般的な条件の処理、事前定義済みの .NET の例外の種類の使用など、例外に対するベスト プラクティスについて説明します。
ms.date: 12/05/2018
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
ms.openlocfilehash: 815dcc81cf41465bffd1515d366a66ff558304fa
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828232"
---
# <a name="best-practices-for-exceptions"></a><span data-ttu-id="99b3d-103">例外の推奨事項</span><span class="sxs-lookup"><span data-stu-id="99b3d-103">Best practices for exceptions</span></span>

<span data-ttu-id="99b3d-104">適切にデザインされたアプリケーションは、アプリケーションのクラッシュを防ぐために、例外やエラーを処理します。</span><span class="sxs-lookup"><span data-stu-id="99b3d-104">A well-designed app handles exceptions and errors to prevent app crashes.</span></span> <span data-ttu-id="99b3d-105">このセクションでは、例外の処理と作成のためのベスト プラクティスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="99b3d-105">This section describes best practices for handling and creating exceptions.</span></span>

## <a name="use-trycatchfinally-blocks-to-recover-from-errors-or-release-resources"></a><span data-ttu-id="99b3d-106">try/catch/finally ブロックを使用し、エラーから回復させるか、リソースを解放する</span><span class="sxs-lookup"><span data-stu-id="99b3d-106">Use try/catch/finally blocks to recover from errors or release resources</span></span>

<span data-ttu-id="99b3d-107">例外が発生する可能性があるコードの前後に `try`/`catch` を使用します。***すると***、その例外からコードは回復できます。</span><span class="sxs-lookup"><span data-stu-id="99b3d-107">Use `try`/`catch` blocks around code that can potentially generate an exception ***and*** your code can recover from that exception.</span></span> <span data-ttu-id="99b3d-108">`catch` ブロックでは、例外を常に最も強い派生型から最も弱い派生型の順序で並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="99b3d-108">In `catch` blocks, always order exceptions from the most derived to the least derived.</span></span> <span data-ttu-id="99b3d-109">すべての例外は <xref:System.Exception> から派生します。</span><span class="sxs-lookup"><span data-stu-id="99b3d-109">All exceptions derive from <xref:System.Exception>.</span></span> <span data-ttu-id="99b3d-110">最も強い派生型の例外は、基礎例外クラスの catch 句に続く catch 句では処理されません。</span><span class="sxs-lookup"><span data-stu-id="99b3d-110">More derived exceptions are not handled by a catch clause that is preceded by a catch clause for a base exception class.</span></span> <span data-ttu-id="99b3d-111">コードが例外から回復できないとき、その例外はキャッチしないでください。</span><span class="sxs-lookup"><span data-stu-id="99b3d-111">When your code cannot recover from an exception, don't catch that exception.</span></span> <span data-ttu-id="99b3d-112">可能であれば、回復させる呼び出し履歴のずっと上でメソッドを有効にします。</span><span class="sxs-lookup"><span data-stu-id="99b3d-112">Enable methods further up the call stack to recover if possible.</span></span>

<span data-ttu-id="99b3d-113">`using` ステートメントか `finally` ブロックで割り当てられているリソースをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="99b3d-113">Clean up resources allocated with either `using` statements, or `finally` blocks.</span></span> <span data-ttu-id="99b3d-114">例外がスローされたとき、リソースを自動クリーンアップするには `using` ステートメントを選択します。</span><span class="sxs-lookup"><span data-stu-id="99b3d-114">Prefer `using` statements to automatically clean up resources when exceptions are thrown.</span></span> <span data-ttu-id="99b3d-115"><xref:System.IDisposable> を実装しないリソースをクリーンアップするには `finally` ブロックを使用します。</span><span class="sxs-lookup"><span data-stu-id="99b3d-115">Use `finally` blocks to clean up resources that don't implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="99b3d-116">`finally` 句のコードは常に、例外がスローされるときでも実行されます。</span><span class="sxs-lookup"><span data-stu-id="99b3d-116">Code in a `finally` clause is almost always executed even when exceptions are thrown.</span></span>

## <a name="handle-common-conditions-without-throwing-exceptions"></a><span data-ttu-id="99b3d-117">例外をスローせずに一般的な状態を処理する</span><span class="sxs-lookup"><span data-stu-id="99b3d-117">Handle common conditions without throwing exceptions</span></span>

<span data-ttu-id="99b3d-118">発生する可能性があり、例外をトリガーする可能性がある状態に対し、例外を回避する方法で処理することを検討します。</span><span class="sxs-lookup"><span data-stu-id="99b3d-118">For conditions that are likely to occur but might trigger an exception, consider handling them in a way that will avoid the exception.</span></span> <span data-ttu-id="99b3d-119">たとえば、既に終了している接続を終了しようとすると、`InvalidOperationException` を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="99b3d-119">For example, if you try to close a connection that is already closed, you'll get an `InvalidOperationException`.</span></span> <span data-ttu-id="99b3d-120">`if` ステートメントを使用して、終了しようとする前に接続状態を確認することで、これを回避することができます。</span><span class="sxs-lookup"><span data-stu-id="99b3d-120">You can avoid that by using an `if` statement to check the connection state before trying to close it.</span></span>

[!code-cpp[Conceptual.Exception.Handling#2](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]

<span data-ttu-id="99b3d-121">終了する前に接続状態を確認しない場合は、`InvalidOperationException` 例外をキャッチする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="99b3d-121">If you don't check connection state before closing, you can catch the `InvalidOperationException` exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#3](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]

<span data-ttu-id="99b3d-122">選択するメソッドは、予期されるイベント発生頻度によって決まります。</span><span class="sxs-lookup"><span data-stu-id="99b3d-122">The method to choose depends on how often you expect the event to occur.</span></span>

- <span data-ttu-id="99b3d-123">イベントが頻繁には発生しない場合、つまり、イベントが本当に例外的であり、エラー (予期しないファイルの終端の検出など) を示す場合に、例外処理を使用します。</span><span class="sxs-lookup"><span data-stu-id="99b3d-123">Use exception handling if the event doesn't occur very often, that is, if the event is truly exceptional and indicates an error (such as an unexpected end-of-file).</span></span> <span data-ttu-id="99b3d-124">例外処理を使用すると、通常の状況では、実行されるコードが少なくなります。</span><span class="sxs-lookup"><span data-stu-id="99b3d-124">When you use exception handling, less code is executed in normal conditions.</span></span>

- <span data-ttu-id="99b3d-125">イベントが定期的に発生し、通常の実行の一部であると見なせる場合は、コード内でエラー条件をチェックします。</span><span class="sxs-lookup"><span data-stu-id="99b3d-125">Check for error conditions in code if the event happens routinely and could be considered part of normal execution.</span></span> <span data-ttu-id="99b3d-126">一般的なエラー条件をチェックするときに、例外を回避するためにより少ないコードが実行されます。</span><span class="sxs-lookup"><span data-stu-id="99b3d-126">When you check for common error conditions, less code is executed because you avoid exceptions.</span></span>

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a><span data-ttu-id="99b3d-127">例外を回避するようにクラスを設計する</span><span class="sxs-lookup"><span data-stu-id="99b3d-127">Design classes so that exceptions can be avoided</span></span>

<span data-ttu-id="99b3d-128">クラスは、例外をトリガーする呼び出しを行うことを回避できるようにするメソッドとプロパティを提供できます。</span><span class="sxs-lookup"><span data-stu-id="99b3d-128">A class can provide methods or properties that enable you to avoid making a call that would trigger an exception.</span></span> <span data-ttu-id="99b3d-129">たとえば、<xref:System.IO.FileStream> クラスには、ファイルの終端に到達したかどうかを判別するために役立つメソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="99b3d-129">For example, a <xref:System.IO.FileStream> class provides methods that help determine whether the end of the file has been reached.</span></span> <span data-ttu-id="99b3d-130">これらは、ファイルの終端を越えて読み取りを実行しようとした場合にも例外がスローされないようにするために使用できます。</span><span class="sxs-lookup"><span data-stu-id="99b3d-130">These can be used to avoid the exception that is thrown if you read past the end of the file.</span></span> <span data-ttu-id="99b3d-131">次の例では、例外をトリガーすることなく、ファイルの末尾まで読み取る方法を示します。</span><span class="sxs-lookup"><span data-stu-id="99b3d-131">The following example shows how to read to the end of a file without triggering an exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#5](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]

<span data-ttu-id="99b3d-132">例外が返されるのを回避するもう 1 つの方法は、非常に一般的なエラーの場合に、例外をスローする代わりに null (または既定値) を返すことです。</span><span class="sxs-lookup"><span data-stu-id="99b3d-132">Another way to avoid exceptions is to return null (or default) for extremely common error cases instead of throwing an exception.</span></span> <span data-ttu-id="99b3d-133">非常に一般的なエラーは、通常の制御の流れと見なすことができます。</span><span class="sxs-lookup"><span data-stu-id="99b3d-133">An extremely common error case can be considered normal flow of control.</span></span> <span data-ttu-id="99b3d-134">このような場合は、null (または既定値) を返すことによって、アプリケーションのパフォーマンスへの影響を最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="99b3d-134">By returning null (or default) in these cases, you minimize the performance impact to an app.</span></span>

<span data-ttu-id="99b3d-135">値の型の場合、`Nullable<T>` または既定値をエラー インジケーターとして使用するかどうかを特定のアプリに関して検討します。</span><span class="sxs-lookup"><span data-stu-id="99b3d-135">For value types, whether to use `Nullable<T>` or default as your error indicator is something to consider for your particular app.</span></span> <span data-ttu-id="99b3d-136">`Nullable<Guid>` を使用すると、`default` は `Guid.Empty` ではなく `null` になります。</span><span class="sxs-lookup"><span data-stu-id="99b3d-136">By using `Nullable<Guid>`, `default` becomes `null` instead of `Guid.Empty`.</span></span> <span data-ttu-id="99b3d-137">`Nullable<T>` を追加すると、値があるときとないときがはっきりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="99b3d-137">Some times, adding `Nullable<T>` can make it clearer when a value is present or absent.</span></span> <span data-ttu-id="99b3d-138">`Nullable<T>` を追加すると、不要な確認事項が増え、潜在的なエラーの原因にしかならないこともあります。</span><span class="sxs-lookup"><span data-stu-id="99b3d-138">Other times, adding `Nullable<T>` can create extra cases to check that aren't necessary, and only serve to create potential sources of errors.</span></span>

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a><span data-ttu-id="99b3d-139">エラー コードを返す代わりに、例外をスローする</span><span class="sxs-lookup"><span data-stu-id="99b3d-139">Throw exceptions instead of returning an error code</span></span>

<span data-ttu-id="99b3d-140">呼び出しのコードはリターン コードを確認しないので、例外によって、エラーを見過ごさないようにします。</span><span class="sxs-lookup"><span data-stu-id="99b3d-140">Exceptions ensure that failures do not go unnoticed because calling code didn't check a return code.</span></span>

## <a name="use-the-predefined-net-exception-types"></a><span data-ttu-id="99b3d-141">事前定義済みの .NET の例外の種類を使用する</span><span class="sxs-lookup"><span data-stu-id="99b3d-141">Use the predefined .NET exception types</span></span>

<span data-ttu-id="99b3d-142">事前定義の例外クラスが適用されない場合に限り、新しい例外クラスを導入します。</span><span class="sxs-lookup"><span data-stu-id="99b3d-142">Introduce a new exception class only when a predefined one doesn't apply.</span></span> <span data-ttu-id="99b3d-143">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="99b3d-143">For example:</span></span>

- <span data-ttu-id="99b3d-144">オブジェクトの現在の状態に対して、プロパティの設定またはメソッドの呼び出しが適切でない場合は、<xref:System.InvalidOperationException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="99b3d-144">Throw an <xref:System.InvalidOperationException> exception if a property set or method call is not appropriate given the object's current state.</span></span>

- <span data-ttu-id="99b3d-145"><xref:System.ArgumentException> 例外または <xref:System.ArgumentException> から派生する定義済みのクラスの 1 つをスローします。</span><span class="sxs-lookup"><span data-stu-id="99b3d-145">Throw an <xref:System.ArgumentException> exception or one of the predefined classes that derive from <xref:System.ArgumentException> if invalid parameters are passed.</span></span>

## <a name="end-exception-class-names-with-the-word-exception"></a><span data-ttu-id="99b3d-146">例外クラス名の末尾に `Exception` という単語を付加する</span><span class="sxs-lookup"><span data-stu-id="99b3d-146">End exception class names with the word `Exception`</span></span>

<span data-ttu-id="99b3d-147">カスタム例外が必要な場合は、適切に名前を付け、<xref:System.Exception> クラスから派生させます。</span><span class="sxs-lookup"><span data-stu-id="99b3d-147">When a custom exception is necessary, name it appropriately and derive it from the <xref:System.Exception> class.</span></span> <span data-ttu-id="99b3d-148">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="99b3d-148">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#4](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]

## <a name="include-three-constructors-in-custom-exception-classes"></a><span data-ttu-id="99b3d-149">カスタム例外クラスに 3 つのコンストラクターを含める</span><span class="sxs-lookup"><span data-stu-id="99b3d-149">Include three constructors in custom exception classes</span></span>

<span data-ttu-id="99b3d-150">独自の例外クラスを作成するときに、少なくとも 3 つの共通コンストラクターを使用します。それらは、パラメーターなしのコンストラクター、文字列メッセージを受け取るコンストラクター、および文字列メッセージと内部例外を受け取るコンストラクターです。</span><span class="sxs-lookup"><span data-stu-id="99b3d-150">Use at least the three common constructors when creating your own exception classes: the parameterless constructor, a constructor that takes a string message, and a constructor that takes a string message and an inner exception.</span></span>

- <span data-ttu-id="99b3d-151">既定の値を使用する <xref:System.Exception.%23ctor>。</span><span class="sxs-lookup"><span data-stu-id="99b3d-151"><xref:System.Exception.%23ctor>, which uses default values.</span></span>

- <span data-ttu-id="99b3d-152">文字列メッセージを受け取る <xref:System.Exception.%23ctor%28System.String%29>。</span><span class="sxs-lookup"><span data-stu-id="99b3d-152"><xref:System.Exception.%23ctor%28System.String%29>, which accepts a string message.</span></span>

- <span data-ttu-id="99b3d-153">文字列メッセージと内部例外を受け取る <xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>。</span><span class="sxs-lookup"><span data-stu-id="99b3d-153"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, which accepts a string message and an inner exception.</span></span>

<span data-ttu-id="99b3d-154">例については、「[方法: ユーザー定義の例外を作成する](how-to-create-user-defined-exceptions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="99b3d-154">For an example, see [How to: Create User-Defined Exceptions](how-to-create-user-defined-exceptions.md).</span></span>

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a><span data-ttu-id="99b3d-155">コードがリモートで実行されるときに、例外データが利用できるようにする</span><span class="sxs-lookup"><span data-stu-id="99b3d-155">Ensure that exception data is available when code executes remotely</span></span>

<span data-ttu-id="99b3d-156">ユーザー定義例外を作成するときには、リモートで実行されるコードで例外のメタデータを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="99b3d-156">When you create user-defined exceptions, ensure that the metadata for the exceptions is available to code that is executing remotely.</span></span>

<span data-ttu-id="99b3d-157">たとえば、アプリ ドメインをサポートする .NET 実装では、アプリ ドメイン間で例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="99b3d-157">For example, on .NET implementations that support App Domains, exceptions may occur across App domains.</span></span> <span data-ttu-id="99b3d-158">アプリ ドメイン A が、例外をスローするコードを実行するアプリ ドメイン B を作成するとします。</span><span class="sxs-lookup"><span data-stu-id="99b3d-158">Suppose App Domain A creates App Domain B, which executes code that throws an exception.</span></span> <span data-ttu-id="99b3d-159">アプリ ドメイン A が例外を適切にキャッチして処理するには、アプリ ドメイン B によりスローされた例外が含まれているアセンブリを検出できる必要があります。アプリ ドメイン B が、アプリ ドメイン A のアプリケーション ベースではなく、自身のアプリケーション ベースの下のアセンブリに含まれている例外をスローする場合、アプリ ドメイン A は、例外を検出できなくなり、共通言語ランタイムが <xref:System.IO.FileNotFoundException> 例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="99b3d-159">For App Domain A to properly catch and handle the exception, it must be able to find the assembly that contains the exception thrown by App Domain B. If App Domain B throws an exception that is contained in an assembly under its application base, but not under App Domain A's application base, App Domain A will not be able to find the exception, and the common language runtime will throw a <xref:System.IO.FileNotFoundException> exception.</span></span> <span data-ttu-id="99b3d-160">このような状況を回避するには、例外情報が格納されているアセンブリを次のいずれかの方法で配置します。</span><span class="sxs-lookup"><span data-stu-id="99b3d-160">To avoid this situation, you can deploy the assembly that contains the exception information in two ways:</span></span>

- <span data-ttu-id="99b3d-161">2 つのアプリ ドメインが共有する共通アプリケーション ベースにアセンブリを配置する。</span><span class="sxs-lookup"><span data-stu-id="99b3d-161">Put the assembly into a common application base shared by both app domains.</span></span>

    <span data-ttu-id="99b3d-162">\- または</span><span class="sxs-lookup"><span data-stu-id="99b3d-162">\- or -</span></span>

- <span data-ttu-id="99b3d-163">ドメインが共通アプリケーション ベースを共有していない場合には、例外情報が格納されているアセンブリに厳密な名前で署名し、グローバル アセンブリ キャッシュにこのアセンブリを配置する。</span><span class="sxs-lookup"><span data-stu-id="99b3d-163">If the domains do not share a common application base, sign the assembly that contains the exception information with a strong name and deploy the assembly into the global assembly cache.</span></span>

## <a name="use-grammatically-correct-error-messages"></a><span data-ttu-id="99b3d-164">文法的に正しいエラー メッセージを使用する</span><span class="sxs-lookup"><span data-stu-id="99b3d-164">Use grammatically correct error messages</span></span>

<span data-ttu-id="99b3d-165">明確な文を記述し、末尾に句点を含めます。</span><span class="sxs-lookup"><span data-stu-id="99b3d-165">Write clear sentences and include ending punctuation.</span></span> <span data-ttu-id="99b3d-166"><xref:System.Exception.Message?displayProperty=nameWithType>プロパティに割り当てられた文字列のそれぞれの文がピリオドで終わる必要があります。</span><span class="sxs-lookup"><span data-stu-id="99b3d-166">Each sentence in the string assigned to the <xref:System.Exception.Message?displayProperty=nameWithType> property should end in a period.</span></span> <span data-ttu-id="99b3d-167">たとえば、"ログ テーブルがオーバーフローしました。" は、</span><span class="sxs-lookup"><span data-stu-id="99b3d-167">For example, "The log table has overflowed."</span></span> <span data-ttu-id="99b3d-168">適切なメッセージ文字列です。</span><span class="sxs-lookup"><span data-stu-id="99b3d-168">would be an appropriate message string.</span></span>

## <a name="include-a-localized-string-message-in-every-exception"></a><span data-ttu-id="99b3d-169">すべての例外に、ローカライズした文字列メッセージを含める</span><span class="sxs-lookup"><span data-stu-id="99b3d-169">Include a localized string message in every exception</span></span>

<span data-ttu-id="99b3d-170">ユーザーに対して表示されるエラー メッセージは、例外クラスの名前ではなく、スローされた例外の <xref:System.Exception.Message?displayProperty=nameWithType> プロパティから派生されます。</span><span class="sxs-lookup"><span data-stu-id="99b3d-170">The error message that the user sees is derived from the <xref:System.Exception.Message?displayProperty=nameWithType> property of the exception that was thrown, and not from the name of the exception class.</span></span> <span data-ttu-id="99b3d-171">通常は、メッセージ文字列を[例外コンストラクター](xref:System.Exception.%23ctor%2A)の `message` 引数に渡すことで、<xref:System.Exception.Message?displayProperty=nameWithType> プロパティに値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="99b3d-171">Typically, you assign a value to the <xref:System.Exception.Message?displayProperty=nameWithType>  property by passing the message string to the `message` argument of an [Exception constructor](xref:System.Exception.%23ctor%2A).</span></span>

<span data-ttu-id="99b3d-172">ローカライズされたアプリケーションの場合は、アプリケーションがスローできるすべての例外に、ローカライズされたメッセージ文字列を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99b3d-172">For localized applications, you should provide a localized message string for every exception that your application can throw.</span></span> <span data-ttu-id="99b3d-173">ローカライズされたエラー メッセージを指定するには、リソース ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="99b3d-173">You use resource files to provide localized error messages.</span></span> <span data-ttu-id="99b3d-174">アプリケーションのローカライズとローカライズされた文字列の取得の詳細については、次の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99b3d-174">For information on localizing applications and retrieving localized strings, see the following articles:</span></span>

- [<span data-ttu-id="99b3d-175">方法: ローカライズされた例外メッセージを使用するユーザー定義の例外を作成する</span><span class="sxs-lookup"><span data-stu-id="99b3d-175">How to: create user-defined exceptions with localized exception messages</span></span>](how-to-create-localized-exception-messages.md)
- [<span data-ttu-id="99b3d-176">デスクトップ アプリケーションのリソース</span><span class="sxs-lookup"><span data-stu-id="99b3d-176">Resources in Desktop Apps</span></span>](../../framework/resources/index.md)
- <xref:System.Resources.ResourceManager?displayProperty=nameWithType>

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a><span data-ttu-id="99b3d-177">カスタム例外で、必要に応じて追加のプロパティを提供する</span><span class="sxs-lookup"><span data-stu-id="99b3d-177">In custom exceptions, provide additional properties as needed</span></span>

<span data-ttu-id="99b3d-178">プログラミングの点で追加情報が役立つ場合にだけ、(カスタム メッセージ文字列以外の) 例外の追加プロパティを含めてください。</span><span class="sxs-lookup"><span data-stu-id="99b3d-178">Provide additional properties for an exception (in addition to the custom message string) only when there's a programmatic scenario where the additional information is useful.</span></span> <span data-ttu-id="99b3d-179">たとえば、<xref:System.IO.FileNotFoundException> には <xref:System.IO.FileNotFoundException.FileName> プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="99b3d-179">For example, the <xref:System.IO.FileNotFoundException> provides the <xref:System.IO.FileNotFoundException.FileName> property.</span></span>

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a><span data-ttu-id="99b3d-180">スタック トレースが役に立つように throw ステートメントを配置する</span><span class="sxs-lookup"><span data-stu-id="99b3d-180">Place throw statements so that the stack trace will be helpful</span></span>

<span data-ttu-id="99b3d-181">例外がスローされたステートメントからスタック トレースが開始され、例外をキャッチした `catch` ステートメントでトレースが終了します。</span><span class="sxs-lookup"><span data-stu-id="99b3d-181">The stack trace begins at the statement where the exception is thrown and ends at the `catch` statement that catches the exception.</span></span>

## <a name="use-exception-builder-methods"></a><span data-ttu-id="99b3d-182">例外ビルダー メソッドを使用する</span><span class="sxs-lookup"><span data-stu-id="99b3d-182">Use exception builder methods</span></span>

<span data-ttu-id="99b3d-183">一般に、クラスはクラス実装内の複数の位置で同一の例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="99b3d-183">It is common for a class to throw the same exception from different places in its implementation.</span></span> <span data-ttu-id="99b3d-184">コードが長くなることを防ぐため、例外を作成して返すヘルパー メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="99b3d-184">To avoid excessive code, use helper methods that create the exception and return it.</span></span> <span data-ttu-id="99b3d-185">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="99b3d-185">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#6](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]

<span data-ttu-id="99b3d-186">場合によっては、例外のコンストラクターを使用して例外を作成する方が適切な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="99b3d-186">In some cases, it's more appropriate to use the exception's constructor to build the exception.</span></span> <span data-ttu-id="99b3d-187"><xref:System.ArgumentException> などのグローバル例外クラスはその一例です。</span><span class="sxs-lookup"><span data-stu-id="99b3d-187">An example is a global exception class such as <xref:System.ArgumentException>.</span></span>

## <a name="restore-state-when-methods-dont-complete-due-to-exceptions"></a><span data-ttu-id="99b3d-188">例外に起因してメソッドが完了しないとき、状態を復元する</span><span class="sxs-lookup"><span data-stu-id="99b3d-188">Restore state when methods don't complete due to exceptions</span></span>

<span data-ttu-id="99b3d-189">呼び出し元が、メソッドから例外がスローされるときに副作用が発生しないと仮定できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="99b3d-189">Callers should be able to assume that there are no side effects when an exception is thrown from a method.</span></span> <span data-ttu-id="99b3d-190">たとえば、ある口座から現金を引き出して別の口座に預金することで送金を行うコードがあって、預金の実行中に例外がスローされた場合、引き出しが有効のままにしておきたくはないはずです。</span><span class="sxs-lookup"><span data-stu-id="99b3d-190">For example, if you have code that transfers money by withdrawing from one account and depositing in another account, and an exception is thrown while executing the deposit, you don't want the withdrawal to remain in effect.</span></span>

```csharp
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect.
    to.Deposit(amount);
}
```

```vb
Public Sub TransferFunds(from As Account, [to] As Account, amount As Decimal)
    from.Withdrawal(amount)
    ' If the deposit fails, the withdrawal shouldn't remain in effect.
    [to].Deposit(amount)
End Sub
```

<span data-ttu-id="99b3d-191">上記のメソッドでは例外は直接スローされませんが、預金操作が失敗した場合、引き出しが取り消されるよう、安全性を優先して記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99b3d-191">The method above does not directly throw any exceptions, but must be written defensively so that if the deposit operation fails, the withdrawal is reversed.</span></span>

<span data-ttu-id="99b3d-192">この状況に対処する方法の 1 つは、預金トランザクションによってスローされた例外をキャッチし、引き出しをロールバックすることです。</span><span class="sxs-lookup"><span data-stu-id="99b3d-192">One way to handle this situation is to catch any exceptions thrown by the deposit transaction and roll back the withdrawal.</span></span>

```csharp
private static void TransferFunds(Account from, Account to, decimal amount)
{
    string withdrawalTrxID = from.Withdrawal(amount);
    try
    {
        to.Deposit(amount);
    }
    catch
    {
        from.RollbackTransaction(withdrawalTrxID);
        throw;
    }
}
```

```vb
Private Shared Sub TransferFunds(from As Account, [to] As Account, amount As Decimal)
    Dim withdrawalTrxID As String = from.Withdrawal(amount)
    Try
        [to].Deposit(amount)
    Catch
        from.RollbackTransaction(withdrawalTrxID)
        Throw
    End Try
End Sub
```

<span data-ttu-id="99b3d-193">この例では、`throw` を使用して、元の例外を再スローすることを示しています。これにより、呼び出し元が <xref:System.Exception.InnerException> プロパティを確認することなく、問題の本当の原因を容易に確認できるようになります。</span><span class="sxs-lookup"><span data-stu-id="99b3d-193">This example illustrates the use of `throw` to re-throw the original exception, which can make it easier for callers to see the real cause of the problem without having to examine the <xref:System.Exception.InnerException> property.</span></span> <span data-ttu-id="99b3d-194">別の方法は、新しい例外をスローして元の例外を内部例外として含めることです。</span><span class="sxs-lookup"><span data-stu-id="99b3d-194">An alternative is to throw a new exception and include the original exception as the inner exception:</span></span>

```csharp
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new TransferFundsException("Withdrawal failed.", innerException: ex)
    {
        From = from,
        To = to,
        Amount = amount
    };
}
```

```vb
Catch ex As Exception
    from.RollbackTransaction(withdrawalTrxID)
    Throw New TransferFundsException("Withdrawal failed.", innerException:=ex) With
    {
        .From = from,
        .[To] = [to],
        .Amount = amount
    }
End Try
```

## <a name="see-also"></a><span data-ttu-id="99b3d-195">関連項目</span><span class="sxs-lookup"><span data-stu-id="99b3d-195">See also</span></span>

- [<span data-ttu-id="99b3d-196">例外</span><span class="sxs-lookup"><span data-stu-id="99b3d-196">Exceptions</span></span>](index.md)
