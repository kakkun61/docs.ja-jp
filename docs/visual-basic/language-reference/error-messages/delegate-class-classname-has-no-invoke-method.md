---
title: Delegate クラス '<classname>' には Invoke メソッドが含まれていないため、この型の式をメソッド呼び出しのターゲットに設定することはできません。
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: 4e0fc61c7356008755134f670fa1fab0165cfd48
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162792"
---
# <a name="bc30220-delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="76e97-102">BC30220:Delegate クラス '\<classname>' には Invoke メソッドが含まれていないため、この型の式をメソッド呼び出しのターゲットに設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="76e97-102">BC30220: Delegate class '\<classname>' has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>

<span data-ttu-id="76e97-103">デリゲート クラスに `Invoke` が実装されていないため、デリゲートを使用して `Invoke` を呼び出すことができませんでした。</span><span class="sxs-lookup"><span data-stu-id="76e97-103">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>

 <span data-ttu-id="76e97-104">**エラー ID:** BC30220</span><span class="sxs-lookup"><span data-stu-id="76e97-104">**Error ID:** BC30220</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="76e97-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="76e97-105">To correct this error</span></span>

1. <span data-ttu-id="76e97-106">デリゲート クラスのインスタンスが `Dim` ステートメントを使用して作成されていること、およびプロシージャが `AddressOf` 演算子を使用してデリゲート インスタンスに割り当てられていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="76e97-106">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>

2. <span data-ttu-id="76e97-107">デリゲート クラスを実装するコードを見つけ、それによって `Invoke` プロシージャが実装されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="76e97-107">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="76e97-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="76e97-108">See also</span></span>

- [<span data-ttu-id="76e97-109">デリゲート</span><span class="sxs-lookup"><span data-stu-id="76e97-109">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="76e97-110">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="76e97-110">Delegate Statement</span></span>](../statements/delegate-statement.md)
- [<span data-ttu-id="76e97-111">AddressOf 演算子</span><span class="sxs-lookup"><span data-stu-id="76e97-111">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="76e97-112">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="76e97-112">Dim Statement</span></span>](../statements/dim-statement.md)
