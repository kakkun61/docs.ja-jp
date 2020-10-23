---
title: "'typename' は Null 許容型であるため、'typename' 型の 'IsNot' オペランドは 'Nothing' とのみ比較できます"
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: 084978c1e047eebd60149af63c0ec9a1135225be
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163338"
---
# <a name="bc32128-isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a><span data-ttu-id="c41a9-102">BC32128:'typename' は Null 許容型であるため、'typename' 型の 'IsNot' オペランドは 'Nothing' とのみ比較できます</span><span class="sxs-lookup"><span data-stu-id="c41a9-102">BC32128: 'IsNot' operand of type 'typename' can only be compared to 'Nothing', because 'typename' is a nullable type</span></span>

<span data-ttu-id="c41a9-103">Null 許容値型として宣言された変数が、`Nothing` 演算子を使用して、`IsNot` 以外の式と比較されました。</span><span class="sxs-lookup"><span data-stu-id="c41a9-103">A variable declared as a nullable value type has been compared to an expression other than `Nothing` using the `IsNot` operator.</span></span>

<span data-ttu-id="c41a9-104">**エラー ID:** BC32128</span><span class="sxs-lookup"><span data-stu-id="c41a9-104">**Error ID:** BC32128</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="c41a9-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="c41a9-105">To correct this error</span></span>

<span data-ttu-id="c41a9-106">`Nothing` 演算子を使用して、Null 許容型を `IsNot` 以外の式と比較するには、次の例に示すように、Null 許容型に対して `GetType` メソッドを呼び出し、その結果を式と比較します。</span><span class="sxs-lookup"><span data-stu-id="c41a9-106">To compare a nullable type to an expression other than `Nothing` by using the `IsNot` operator, call the `GetType` method on the nullable type and compare the result to the expression, as shown in the following example.</span></span>

```vb
Dim number? As Integer = 5

If number IsNot Nothing Then
  If number.GetType() IsNot Type.GetType("System.Int32") Then

  End If
End If
```

## <a name="see-also"></a><span data-ttu-id="c41a9-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="c41a9-107">See also</span></span>

- [<span data-ttu-id="c41a9-108">null 許容値型</span><span class="sxs-lookup"><span data-stu-id="c41a9-108">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="c41a9-109">IsNot 演算子</span><span class="sxs-lookup"><span data-stu-id="c41a9-109">IsNot Operator</span></span>](../operators/isnot-operator.md)
