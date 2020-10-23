---
title: ループの境界とステップの句が同じ型に変換されないため、'<variablename>' の型を推論できません
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: 1330cbd6567b69df9bd811ced49c6df2e120a0b2
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161210"
---
# <a name="bc30982-type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a><span data-ttu-id="8183f-102">BC30982:ループの境界とステップの句が同じ型に変換されないため、'\<variablename>' の型を推論できません</span><span class="sxs-lookup"><span data-stu-id="8183f-102">BC30982: Type of '\<variablename>' cannot be inferred because the loop bounds and the step variable do not widen to the same type</span></span>

<span data-ttu-id="8183f-103">`For...Next` ループを記述していますが、次の条件が当てはまるため、コンパイラがそのループの中でループ制御変数のデータ型を推論できません。</span><span class="sxs-lookup"><span data-stu-id="8183f-103">You have written a `For...Next` loop in which the compiler cannot infer a data type for the loop control variable because the following conditions are true:</span></span>

- <span data-ttu-id="8183f-104">ループ コントロール変数のデータ型が `As` 句で指定されていません。</span><span class="sxs-lookup"><span data-stu-id="8183f-104">The data type of the loop control variable is not specified with an `As` clause.</span></span>

- <span data-ttu-id="8183f-105">ループ境界とステップ変数に少なくとも 2 つのデータ型が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8183f-105">The loop bounds and step variable contain at least two data types.</span></span>

- <span data-ttu-id="8183f-106">データ型の間に標準変換が存在しません。</span><span class="sxs-lookup"><span data-stu-id="8183f-106">No standard conversions exist between the data types.</span></span>

 <span data-ttu-id="8183f-107">そのため、コンパイラが、ループの制御変数のデータ型を推論できません。</span><span class="sxs-lookup"><span data-stu-id="8183f-107">Therefore, the compiler cannot infer the data type of a loop's control variable.</span></span>

 <span data-ttu-id="8183f-108">次の例で、ステップ変数は文字で、ループの境界はどちらも整数です。</span><span class="sxs-lookup"><span data-stu-id="8183f-108">In the following example, the step variable is a character and the loop bounds are both integers.</span></span> <span data-ttu-id="8183f-109">文字と整数の間に標準変換がないため、このエラーが報告されます。</span><span class="sxs-lookup"><span data-stu-id="8183f-109">Because there is no standard conversion between characters and integers, this error is reported.</span></span>

```vb
Dim stepVar = "1"c
Dim m = 0
Dim n = 20

' Not valid.
' For i = 1 To 10 Step stepVar
    ' Loop processing
' Next
```

<span data-ttu-id="8183f-110">**エラー ID:** BC30982</span><span class="sxs-lookup"><span data-stu-id="8183f-110">**Error ID:** BC30982</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="8183f-111">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="8183f-111">To correct this error</span></span>

- <span data-ttu-id="8183f-112">必要に応じて、ループの境界とステップ変数の型を変更して、それらのうち少なくとも 1 つが、他の型の拡大変換先の型になるようにします。</span><span class="sxs-lookup"><span data-stu-id="8183f-112">Change the types of the loop bounds and step variable as necessary so that at least one of them is a type that the others widen to.</span></span> <span data-ttu-id="8183f-113">前の例では、`stepVar` の型を `Integer` に変更します。</span><span class="sxs-lookup"><span data-stu-id="8183f-113">In the preceding example, change the type of `stepVar` to `Integer`.</span></span>

  ```vb
  Dim stepVar = 1
  ```

  <span data-ttu-id="8183f-114">\- または -</span><span class="sxs-lookup"><span data-stu-id="8183f-114">-or-</span></span>

  ```vb
  Dim stepVar As Integer = 1
  ```

- <span data-ttu-id="8183f-115">明示的な変換関数を使用して、ループの境界とステップ変数を適切な型に変換します。</span><span class="sxs-lookup"><span data-stu-id="8183f-115">Use explicit conversion functions to convert the loop bounds and step variable to the appropriate types.</span></span> <span data-ttu-id="8183f-116">前の例では、`Val` 関数を `stepVar` に適用します。</span><span class="sxs-lookup"><span data-stu-id="8183f-116">In the preceding example, apply the `Val` function to `stepVar`.</span></span>

  ```vb
  For i = 1 To 10 Step Val(stepVar)
      ' Loop processing
  Next
  ```

## <a name="see-also"></a><span data-ttu-id="8183f-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="8183f-117">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [<span data-ttu-id="8183f-118">For...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="8183f-118">For...Next Statement</span></span>](../statements/for-next-statement.md)
- [<span data-ttu-id="8183f-119">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="8183f-119">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="8183f-120">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="8183f-120">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="8183f-121">Option Infer ステートメント</span><span class="sxs-lookup"><span data-stu-id="8183f-121">Option Infer Statement</span></span>](../statements/option-infer-statement.md)
- [<span data-ttu-id="8183f-122">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="8183f-122">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="8183f-123">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="8183f-123">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
