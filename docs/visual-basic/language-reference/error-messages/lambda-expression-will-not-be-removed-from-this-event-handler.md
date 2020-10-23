---
title: ラムダ式はこのイベント ハンドラーから削除されません
ms.date: 07/20/2015
f1_keywords:
- bc42326
- vbc42326
helpviewer_keywords:
- BC42326
ms.assetid: 63214dc6-0112-4245-8ebf-7c9e8f5a5782
ms.openlocfilehash: 5a30e63044b51f8176dfeebdcc9eb8fd517739ae
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163117"
---
# <a name="bc42326-lambda-expression-will-not-be-removed-from-this-event-handler"></a><span data-ttu-id="1202d-102">BC42326:ラムダ式はこのイベント ハンドラーから削除されません</span><span class="sxs-lookup"><span data-stu-id="1202d-102">BC42326: Lambda expression will not be removed from this event handler</span></span>

<span data-ttu-id="1202d-103">ラムダ式はこのイベント ハンドラーから削除されません。</span><span class="sxs-lookup"><span data-stu-id="1202d-103">Lambda expression will not be removed from this event handler.</span></span> <span data-ttu-id="1202d-104">ラムダ式に変数を割り当て、その変数を使用してイベントを追加または削除します。</span><span class="sxs-lookup"><span data-stu-id="1202d-104">Assign the lambda expression to a variable and use the variable to add and remove the event.</span></span>

<span data-ttu-id="1202d-105">ラムダ式をイベント ハンドラーと共に使用すると、期待どおりの動作が見られない場合があります。</span><span class="sxs-lookup"><span data-stu-id="1202d-105">When lambda expressions are used with event handlers, you may not see the behavior you expect.</span></span> <span data-ttu-id="1202d-106">コンパイラは、定義が同一であっても、ラムダ式ごとに新しいメソッドを生成します。</span><span class="sxs-lookup"><span data-stu-id="1202d-106">The compiler generates a new method for each lambda expression definition, even if they are identical.</span></span> <span data-ttu-id="1202d-107">そのため、次のコードは `False` を表示します。</span><span class="sxs-lookup"><span data-stu-id="1202d-107">Therefore, the following code displays `False`.</span></span>

```vb
Module Module1

    Sub Main()
        Dim fun1 As ChangeInteger = Function(p As Integer) p + 1
        Dim fun2 As ChangeInteger = Function(p As Integer) p + 1
        Console.WriteLine(fun1 = fun2)
    End Sub

    Delegate Function ChangeInteger(ByVal x As Integer) As Integer

End Module
```

<span data-ttu-id="1202d-108">ラムダ式をイベント ハンドラーと共に使用すると、予期しない結果が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1202d-108">When lambda expressions are used with event handlers, this may cause unexpected results.</span></span> <span data-ttu-id="1202d-109">次の例では、`AddHandler` によって追加されたラムダ式は、`RemoveHandler` ステートメントによって削除されません。</span><span class="sxs-lookup"><span data-stu-id="1202d-109">In the following example, the lambda expression added by `AddHandler` is not removed by the `RemoveHandler` statement.</span></span>

```vb
Module Module1

    Event ProcessInteger(ByVal x As Integer)

    Sub Main()

        ' The following line adds one listener to the event.
        AddHandler ProcessInteger, Function(m As Integer) m

        ' The following statement searches the current listeners
        ' for a match to remove. However, this lambda is not the same
        ' as the previous one, so nothing is removed.
        RemoveHandler ProcessInteger, Function(m As Integer) m

    End Sub
End Module
```

<span data-ttu-id="1202d-110">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="1202d-110">By default, this message is a warning.</span></span> <span data-ttu-id="1202d-111">警告を表示しない方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1202d-111">For more information about how to hide warnings or treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

<span data-ttu-id="1202d-112">**エラー ID:** BC42326</span><span class="sxs-lookup"><span data-stu-id="1202d-112">**Error ID:** BC42326</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="1202d-113">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="1202d-113">To correct this error</span></span>

<span data-ttu-id="1202d-114">この警告を回避し、ラムダ式を削除するには、次の例に示すように、ラムダ式を変数に割り当て、`AddHandler` と `RemoveHandler` の両方のステートメントで変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="1202d-114">To avoid the warning and remove the lambda expression, assign the lambda expression to a variable and use the variable in both the `AddHandler` and `RemoveHandler` statements, as shown in the following example.</span></span>

```vb
Module Module1

    Event ProcessInteger(ByVal x As Integer)

    Dim PrintHandler As ProcessIntegerEventHandler

    Sub Main()

        ' Assign the lambda expression to a variable.
        PrintHandler = Function(m As Integer) m

        ' Use the variable to add the listener.
        AddHandler ProcessInteger, PrintHandler

        ' Use the variable again when you want to remove the listener.
        RemoveHandler ProcessInteger, PrintHandler

    End Sub
End Module
```

## <a name="see-also"></a><span data-ttu-id="1202d-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="1202d-115">See also</span></span>

- [<span data-ttu-id="1202d-116">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="1202d-116">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="1202d-117">厳密でないデリゲート変換</span><span class="sxs-lookup"><span data-stu-id="1202d-117">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="1202d-118">イベント</span><span class="sxs-lookup"><span data-stu-id="1202d-118">Events</span></span>](../../programming-guide/language-features/events/index.md)
