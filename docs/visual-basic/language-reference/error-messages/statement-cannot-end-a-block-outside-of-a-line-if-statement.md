---
title: If ステートメント行の外側でステートメント ブロックを終了することはできません。
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 4fd7577accd0b312ee1e3d2d990d256514d5f5f6
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161336"
---
# <a name="bc32005-statement-cannot-end-a-block-outside-of-a-line-if-statement"></a><span data-ttu-id="fb766-102">BC32005:If ステートメント行の外側でステートメント ブロックを終了することはできません。</span><span class="sxs-lookup"><span data-stu-id="fb766-102">BC32005: Statement cannot end a block outside of a line 'If' statement</span></span>

<span data-ttu-id="fb766-103">単一行の `If` ステートメントにコロン (:) で区切られた複数のステートメントが含まれていて、そのうちの 1 つが、単一行の `If` の外側にある制御ブロックの `End` ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="fb766-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="fb766-104">単一行の `If` ステートメントで、`End If` ステートメントが使用されません。</span><span class="sxs-lookup"><span data-stu-id="fb766-104">Single-line `If` statements do not use the `End If` statement.</span></span>

 <span data-ttu-id="fb766-105">**エラー ID:** BC32005</span><span class="sxs-lookup"><span data-stu-id="fb766-105">**Error ID:** BC32005</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="fb766-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="fb766-106">To correct this error</span></span>

- <span data-ttu-id="fb766-107">単一行の `If` ステートメントを、`End If` ステートメントが含まれている制御ブロックの外側に移動します。</span><span class="sxs-lookup"><span data-stu-id="fb766-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="fb766-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="fb766-108">See also</span></span>

- [<span data-ttu-id="fb766-109">If...Then...Else ステートメント</span><span class="sxs-lookup"><span data-stu-id="fb766-109">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
