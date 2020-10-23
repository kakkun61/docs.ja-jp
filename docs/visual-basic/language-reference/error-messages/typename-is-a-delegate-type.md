---
title: "'<typename>' はデリゲート型です。"
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: dcb52188c53b38ac14de0002b5212bb33c9f7203
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161778"
---
# <a name="bc32008-typename-is-a-delegate-type"></a><span data-ttu-id="9cc67-102">BC32008: '\<typename>' はデリゲート型です</span><span class="sxs-lookup"><span data-stu-id="9cc67-102">BC32008: '\<typename>' is a delegate type</span></span>

<span data-ttu-id="9cc67-103">'\<typename>' はデリゲート型です。</span><span class="sxs-lookup"><span data-stu-id="9cc67-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="9cc67-104">デリゲート コンストラクションでは、引数リストとして 1 つの AddressOf 式のみが許可されます。</span><span class="sxs-lookup"><span data-stu-id="9cc67-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="9cc67-105">多くの場合、デリゲート コンストラクションの代わりに AddressOf 式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="9cc67-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>

 <span data-ttu-id="9cc67-106">デリゲート クラスのインスタンスを作成する `New` 句は、デリゲート コンストラクターに無効な引数リストを指定します。</span><span class="sxs-lookup"><span data-stu-id="9cc67-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>

 <span data-ttu-id="9cc67-107">新しいデリゲート インスタンスを作成するときは、1 つの `AddressOf` 式のみを指定できます。</span><span class="sxs-lookup"><span data-stu-id="9cc67-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>

 <span data-ttu-id="9cc67-108">このエラーは、デリゲート コンストラクターに引数を渡さない場合、複数の引数を渡した場合、または有効な `AddressOf` 式ではない 1 つの引数を渡した場合に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9cc67-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>

 <span data-ttu-id="9cc67-109">**エラー ID:** BC32008</span><span class="sxs-lookup"><span data-stu-id="9cc67-109">**Error ID:** BC32008</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="9cc67-110">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="9cc67-110">To correct this error</span></span>

- <span data-ttu-id="9cc67-111">`New` 句で、デリゲート クラスの引数リストに含まれる 1 つの `AddressOf` 式を使用します。</span><span class="sxs-lookup"><span data-stu-id="9cc67-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>

## <a name="see-also"></a><span data-ttu-id="9cc67-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="9cc67-112">See also</span></span>

- [<span data-ttu-id="9cc67-113">New 演算子</span><span class="sxs-lookup"><span data-stu-id="9cc67-113">New Operator</span></span>](../operators/new-operator.md)
- [<span data-ttu-id="9cc67-114">AddressOf 演算子</span><span class="sxs-lookup"><span data-stu-id="9cc67-114">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="9cc67-115">デリゲート</span><span class="sxs-lookup"><span data-stu-id="9cc67-115">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="9cc67-116">方法: デリゲート メソッドを呼び出す</span><span class="sxs-lookup"><span data-stu-id="9cc67-116">How to: Invoke a Delegate Method</span></span>](../../programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
