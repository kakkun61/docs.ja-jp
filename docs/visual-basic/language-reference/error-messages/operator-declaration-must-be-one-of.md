---
title: '演算子宣言は次のいずれかでなければなりません: +、-、*、\、/、^、&amp;、Like、Mod、And、Or、Xor、Not、<<、>>、=、<>、<、<=、>、>=、CType、IsTrue、または IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: a94e62e33427987a302a6244b2b8ce8d295e4f11
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159899"
---
# <a name="bc33000-operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not--"></a><span data-ttu-id="4400b-102">BC33000:演算子宣言は次のいずれかでなければなりません: +、-、\*、\,/、^、&amp;、Like、Mod、And、Or、Xor、Not、\<\<, >>...</span><span class="sxs-lookup"><span data-stu-id="4400b-102">BC33000: Operator declaration must be one of:  +,-,\*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, \<\<, >>...</span></span>

<span data-ttu-id="4400b-103">オーバーロードの対象となる演算子のみ宣言できます。</span><span class="sxs-lookup"><span data-stu-id="4400b-103">You can declare only an operator that is eligible for overloading.</span></span> <span data-ttu-id="4400b-104">次の表に宣言可能な演算子を示します。</span><span class="sxs-lookup"><span data-stu-id="4400b-104">The following table lists the operators you can declare.</span></span>

|<span data-ttu-id="4400b-105">種類</span><span class="sxs-lookup"><span data-stu-id="4400b-105">Type</span></span>|<span data-ttu-id="4400b-106">演算子</span><span class="sxs-lookup"><span data-stu-id="4400b-106">Operators</span></span>|
|----------|---------------|
|<span data-ttu-id="4400b-107">単項</span><span class="sxs-lookup"><span data-stu-id="4400b-107">Unary</span></span>|<span data-ttu-id="4400b-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="4400b-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|
|<span data-ttu-id="4400b-109">2 項</span><span class="sxs-lookup"><span data-stu-id="4400b-109">Binary</span></span>|<span data-ttu-id="4400b-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="4400b-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|
|<span data-ttu-id="4400b-111">変換 (単項)</span><span class="sxs-lookup"><span data-stu-id="4400b-111">Conversion (unary)</span></span>|`CType`|

 <span data-ttu-id="4400b-112">2 項の一覧に示した `=` 演算子は比較演算子であり、代入演算子ではありません。</span><span class="sxs-lookup"><span data-stu-id="4400b-112">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>

 <span data-ttu-id="4400b-113">**エラー ID:** BC33000</span><span class="sxs-lookup"><span data-stu-id="4400b-113">**Error ID:** BC33000</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="4400b-114">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="4400b-114">To correct this error</span></span>

- <span data-ttu-id="4400b-115">演算子をオーバーロード可能な演算子の中から選択します。</span><span class="sxs-lookup"><span data-stu-id="4400b-115">Select an operator from the set of overloadable operators.</span></span>

- <span data-ttu-id="4400b-116">直接オーバーロードできない演算子をオーバーロードする機能が必要な場合は、適切なパラメーターを受け取り適切な値を返す `Function` プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="4400b-116">If you need the functionality of overloading an operator that you cannot overload directly, create a `Function` procedure that takes the appropriate parameters and returns the appropriate value.</span></span>

## <a name="see-also"></a><span data-ttu-id="4400b-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="4400b-117">See also</span></span>

- [<span data-ttu-id="4400b-118">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="4400b-118">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="4400b-119">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="4400b-119">Operator Procedures</span></span>](../../programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="4400b-120">方法: 演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="4400b-120">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="4400b-121">方法: 変換演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="4400b-121">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="4400b-122">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="4400b-122">Function Statement</span></span>](../statements/function-statement.md)
