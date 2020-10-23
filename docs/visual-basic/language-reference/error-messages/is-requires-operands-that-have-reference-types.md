---
title: "'Is' には参照型を持つオペランドが必要ですが、このオペランドの値型は '<typename>' です。"
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: 5c9f156272cd0c3cbaeadbc0e162129f41619cc6
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163351"
---
# <a name="bc30020-is-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-typename"></a><span data-ttu-id="674b7-102">BC30020:'Is' には参照型を持つオペランドが必要ですが、このオペランドの値型は '\<typename>' です。</span><span class="sxs-lookup"><span data-stu-id="674b7-102">BC30020: 'Is' requires operands that have reference types, but this operand has the value type '\<typename>'</span></span>

<span data-ttu-id="674b7-103">`Is` 比較演算子は、2 つのオブジェクト変数が同じインスタンスを参照しているかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="674b7-103">The `Is` comparison operator determines whether two object variables refer to the same instance.</span></span> <span data-ttu-id="674b7-104">この比較は、値型に対して定義されていません。</span><span class="sxs-lookup"><span data-stu-id="674b7-104">This comparison is not defined for value types.</span></span>

 <span data-ttu-id="674b7-105">**エラー ID:** BC30020</span><span class="sxs-lookup"><span data-stu-id="674b7-105">**Error ID:** BC30020</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="674b7-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="674b7-106">To correct this error</span></span>

- <span data-ttu-id="674b7-107">適切な算術比較演算子または `Like` 演算子を使用して、2 つの値の型を比較します。</span><span class="sxs-lookup"><span data-stu-id="674b7-107">Use the appropriate arithmetic comparison operator or the `Like` operator to compare two value types.</span></span>

## <a name="see-also"></a><span data-ttu-id="674b7-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="674b7-108">See also</span></span>

- [<span data-ttu-id="674b7-109">Is 演算子</span><span class="sxs-lookup"><span data-stu-id="674b7-109">Is Operator</span></span>](../operators/is-operator.md)
- [<span data-ttu-id="674b7-110">Like 演算子</span><span class="sxs-lookup"><span data-stu-id="674b7-110">Like Operator</span></span>](../operators/like-operator.md)
- [<span data-ttu-id="674b7-111">比較演算子</span><span class="sxs-lookup"><span data-stu-id="674b7-111">Comparison Operators</span></span>](../operators/comparison-operators.md)
