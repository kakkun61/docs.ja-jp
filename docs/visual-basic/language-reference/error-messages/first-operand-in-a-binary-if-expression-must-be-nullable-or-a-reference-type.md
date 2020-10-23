---
title: バイナリ 'If' 式の最初のオペランドは Null 許容または参照型である必要があります
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: bca9b74a68815b4e5a3bb2dc114b9031cdf24099
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162740"
---
# <a name="bc33107-first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a><span data-ttu-id="a4f96-102">BC33107:バイナリ 'If' 式の最初のオペランドは Null 許容または参照型である必要があります</span><span class="sxs-lookup"><span data-stu-id="a4f96-102">BC33107: First operand in a binary 'If' expression must be nullable or a reference type</span></span>

<span data-ttu-id="a4f96-103">`If` 式は、2 つまたは 3 つの引数を取ることができます。</span><span class="sxs-lookup"><span data-stu-id="a4f96-103">An `If` expression can take either two or three arguments.</span></span> <span data-ttu-id="a4f96-104">2 つの引数のみを送信する場合、最初の引数は参照型または Null 許容値型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4f96-104">When you send only two arguments, the first argument must be a reference type or a nullable value type.</span></span> <span data-ttu-id="a4f96-105">最初の引数が `Nothing` 以外に評価される場合は、その値が返されます。</span><span class="sxs-lookup"><span data-stu-id="a4f96-105">If the first argument evaluates to anything other than `Nothing`, its value is returned.</span></span> <span data-ttu-id="a4f96-106">最初の引数が `Nothing` に評価される場合は、2 番目の引数が評価されて返されます。</span><span class="sxs-lookup"><span data-stu-id="a4f96-106">If the first argument evaluates to `Nothing`, the second argument is evaluated and returned.</span></span>

 <span data-ttu-id="a4f96-107">たとえば、次のコードには、3 つの引数を含むものと 2 つの引数を含むものの、2 つの `If` 式が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a4f96-107">For example, the following code contains two `If` expressions, one with three arguments and one with two arguments.</span></span> <span data-ttu-id="a4f96-108">これらの式は、同じ値を計算して返します。</span><span class="sxs-lookup"><span data-stu-id="a4f96-108">The expressions calculate and return the same value.</span></span>

```vb
' firstChoice is a nullable value type.
Dim firstChoice? As Integer = Nothing
Dim secondChoice As Integer = 1128
' If expression with three arguments.
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))
' If expression with two arguments.
Console.WriteLine(If(firstChoice, secondChoice))
```

 <span data-ttu-id="a4f96-109">次の式では、このエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="a4f96-109">The following expressions cause this error:</span></span>

```vb
Dim choice1 = 4
Dim choice2 = 5
Dim booleanVar = True

' Not valid.
'Console.WriteLine(If(choice1 < choice2, 1))
' Not valid.
'Console.WriteLine(If(booleanVar, "Test returns True."))
```

 <span data-ttu-id="a4f96-110">**エラー ID:** BC33107</span><span class="sxs-lookup"><span data-stu-id="a4f96-110">**Error ID:** BC33107</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="a4f96-111">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="a4f96-111">To correct this error</span></span>

- <span data-ttu-id="a4f96-112">最初の引数が Null 許容値型または参照型になるようにコードを変更できない場合は、3 つの引数の `If` 式、または `If...Then...Else` ステートメントに変換することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="a4f96-112">If you cannot change the code so that the first argument is a nullable value type or reference type, consider converting to a three-argument `If` expression, or to an `If...Then...Else` statement.</span></span>

```vb
Console.WriteLine(If(choice1 < choice2, 1, 2))
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))
```

## <a name="see-also"></a><span data-ttu-id="a4f96-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="a4f96-113">See also</span></span>

- [<span data-ttu-id="a4f96-114">If 演算子</span><span class="sxs-lookup"><span data-stu-id="a4f96-114">If Operator</span></span>](../operators/if-operator.md)
- [<span data-ttu-id="a4f96-115">If...Then...Else ステートメント</span><span class="sxs-lookup"><span data-stu-id="a4f96-115">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
- [<span data-ttu-id="a4f96-116">null 許容値型</span><span class="sxs-lookup"><span data-stu-id="a4f96-116">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
