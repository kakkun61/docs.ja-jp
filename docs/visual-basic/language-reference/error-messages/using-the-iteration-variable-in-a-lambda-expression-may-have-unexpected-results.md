---
title: ラムダ式内で繰り返し変数を使用すると、予期しない結果が発生する可能性があります。
ms.date: 07/20/2015
f1_keywords:
- vbc42324
- bc42324
helpviewer_keywords:
- BC42324
ms.assetid: b5c2c4bd-3b2a-4a73-aaeb-55728eb03b68
ms.openlocfilehash: d0deea94084565ea91debe2b6db30def4cd9e00e
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161492"
---
# <a name="bc42324-using-the-iteration-variable-in-a-lambda-expression-may-have-unexpected-results"></a><span data-ttu-id="d789b-102">BC42324:ラムダ式内で繰り返し変数を使用すると、予期しない結果が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d789b-102">BC42324: Using the iteration variable in a lambda expression may have unexpected results</span></span>

<span data-ttu-id="d789b-103">ラムダ式内で反復変数を使用すると、予期しない結果が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d789b-103">Using the iteration variable in a lambda expression may have unexpected results.</span></span> <span data-ttu-id="d789b-104">代わりに、ループ内にローカル変数を作成して反復変数の値を割り当ててください。</span><span class="sxs-lookup"><span data-stu-id="d789b-104">Instead, create a local variable within the loop and assign it the value of the iteration variable.</span></span>

 <span data-ttu-id="d789b-105">この警告は、ループ内で宣言されているラムダ式でループの反復変数を使用すると表示されます。</span><span class="sxs-lookup"><span data-stu-id="d789b-105">This warning appears when you use a loop iteration variable in a lambda expression that is declared inside the loop.</span></span> <span data-ttu-id="d789b-106">たとえば、次のコード例では、警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d789b-106">For example, the following example causes the warning to appear.</span></span>

```vb
For i As Integer = 1 To 10
    ' The warning is given for the use of i.
    Dim exampleFunc As Func(Of Integer) = Function() i
Next
```

 <span data-ttu-id="d789b-107">次の例は、予期しない結果が発生する可能性があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="d789b-107">The following example shows the unexpected results that might occur.</span></span>

```vb
Module Module1
    Sub Main()
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}

        For i As Integer = 0 To 4
            array1(i) = Function() i
        Next

        For Each funcElement In array1
            System.Console.WriteLine(funcElement())
        Next

    End Sub
End Module
```

 <span data-ttu-id="d789b-108">`For` ループは、それぞれがループの反復変数 `i` の値を返す、ラムダ式の配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="d789b-108">The `For` loop creates an array of lambda expressions, each of which returns the value of the loop iteration variable `i`.</span></span> <span data-ttu-id="d789b-109">ラムダ式が `For Each` ループで評価されると、0、1、2、3、および 4 (`For` ループ内の `i` の連続する値) が表示されると予想される場合があります。</span><span class="sxs-lookup"><span data-stu-id="d789b-109">When the lambda expressions are evaluated in the `For Each` loop, you might expect to see 0, 1, 2, 3, and 4 displayed, the successive values of `i` in the `For` loop.</span></span> <span data-ttu-id="d789b-110">そうではなく、`i` の最終的な値が 5 回表示されます。</span><span class="sxs-lookup"><span data-stu-id="d789b-110">Instead, you see the final value of `i` displayed five times:</span></span>

 `5`

 `5`

 `5`

 `5`

 `5`

 <span data-ttu-id="d789b-111">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="d789b-111">By default, this message is a warning.</span></span> <span data-ttu-id="d789b-112">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d789b-112">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="d789b-113">**エラー ID:** BC42324</span><span class="sxs-lookup"><span data-stu-id="d789b-113">**Error ID:** BC42324</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="d789b-114">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="d789b-114">To correct this error</span></span>

- <span data-ttu-id="d789b-115">反復変数の値をローカル変数に代入し、そのローカル変数をラムダ式で使用します。</span><span class="sxs-lookup"><span data-stu-id="d789b-115">Assign the value of the iteration variable to a local variable, and use the local variable in the lambda expression.</span></span>

```vb
Module Module1
    Sub Main()
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}

        For i As Integer = 0 To 4
            Dim j = i
            array1(i) = Function() j
        Next

        For Each funcElement In array1
            System.Console.WriteLine(funcElement())
        Next

    End Sub
End Module
```

## <a name="see-also"></a><span data-ttu-id="d789b-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="d789b-116">See also</span></span>

- [<span data-ttu-id="d789b-117">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="d789b-117">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
