---
title: 式レベルの基本設定
description: 式レベルの設定のコード分析言語規則について説明します
ms.date: 09/30/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 9933111b1ed76166e5ae86e9bc1a2332c3c77c81
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2020
ms.locfileid: "96593791"
---
# <a name="expression-level-preferences"></a><span data-ttu-id="4dd9e-103">式レベルの基本設定</span><span class="sxs-lookup"><span data-stu-id="4dd9e-103">Expression-level preferences</span></span>

## <a name="net-expression-level-preferences"></a><span data-ttu-id="4dd9e-104">.NET 式レベルの基本設定</span><span class="sxs-lookup"><span data-stu-id="4dd9e-104">.NET expression-level preferences</span></span>

<span data-ttu-id="4dd9e-105">このセクションのスタイルルールでは、C# と Visual Basic に共通する次の式レベルの設定について考慮します。</span><span class="sxs-lookup"><span data-stu-id="4dd9e-105">The style rules in this section concern the following expression-level preferences that are common to C# and Visual Basic:</span></span>

- [<span data-ttu-id="4dd9e-106">不足しているケースを switch ステートメントに追加する (IDE0010)</span><span class="sxs-lookup"><span data-stu-id="4dd9e-106">Add missing cases to switch statement (IDE0010)</span></span>](ide0010.md)
- [<span data-ttu-id="4dd9e-107">オブジェクト初期化子の使用 (IDE0017)</span><span class="sxs-lookup"><span data-stu-id="4dd9e-107">Use object initializers (IDE0017)</span></span>](ide0017.md)
- [<span data-ttu-id="4dd9e-108">コレクション初期化子を使用する (IDE0028)</span><span class="sxs-lookup"><span data-stu-id="4dd9e-108">Use collection initializers (IDE0028)</span></span>](ide0028.md)
- [<span data-ttu-id="4dd9e-109">自動プロパティを使用する (IDE0032)</span><span class="sxs-lookup"><span data-stu-id="4dd9e-109">Use auto property (IDE0032)</span></span>](ide0032.md)
- [<span data-ttu-id="4dd9e-110">明示的に指定されたタプル名を使用する (IDE0033)</span><span class="sxs-lookup"><span data-stu-id="4dd9e-110">Use explicitly provided tuple name (IDE0033)</span></span>](ide0033.md)
- [<span data-ttu-id="4dd9e-111">推定メンバー名を使用する (IDE0037)</span><span class="sxs-lookup"><span data-stu-id="4dd9e-111">Use inferred member name (IDE0037)</span></span>](ide0037.md)
- [<span data-ttu-id="4dd9e-112">割り当てに条件式を使用する (IDE0045)</span><span class="sxs-lookup"><span data-stu-id="4dd9e-112">Use conditional expression for assignment (IDE0045)</span></span>](ide0045.md)
- [<span data-ttu-id="4dd9e-113">Return に条件式を使用する (IDE0046)</span><span class="sxs-lookup"><span data-stu-id="4dd9e-113">Use conditional expression for return (IDE0046)</span></span>](ide0046.md)
- [<span data-ttu-id="4dd9e-114">匿名型からタプルへの変換 (IDE0050)</span><span class="sxs-lookup"><span data-stu-id="4dd9e-114">Convert anonymous type to tuple (IDE0050)</span></span>](ide0050.md)
- [<span data-ttu-id="4dd9e-115">複合代入 (IDE0054 および IDE0074) を使用する</span><span class="sxs-lookup"><span data-stu-id="4dd9e-115">Use compound assignment (IDE0054 and IDE0074)</span></span>](ide0054-ide0074.md)
- [<span data-ttu-id="4dd9e-116">' ハッシュコード ' (IDE0070) を使用します</span><span class="sxs-lookup"><span data-stu-id="4dd9e-116">Use 'System.HashCode.Combine' (IDE0070)</span></span>](ide0070.md)
- [<span data-ttu-id="4dd9e-117">補間の単純化 (IDE0071)</span><span class="sxs-lookup"><span data-stu-id="4dd9e-117">Simplify interpolation (IDE0071)</span></span>](ide0071.md)
- [<span data-ttu-id="4dd9e-118">条件式を簡略化する (IDE0075)</span><span class="sxs-lookup"><span data-stu-id="4dd9e-118">Simplify conditional expression (IDE0075)</span></span>](ide0075.md)
- [<span data-ttu-id="4dd9e-119">' Typeof ' を ' IDE0082 ' に変換します</span><span class="sxs-lookup"><span data-stu-id="4dd9e-119">Convert 'typeof' to 'nameof' (IDE0082)</span></span>](ide0082.md)

## <a name="c-expression-level-preferences"></a><span data-ttu-id="4dd9e-120">C# の式レベルのユーザー設定</span><span class="sxs-lookup"><span data-stu-id="4dd9e-120">C# expression-level preferences</span></span>

<span data-ttu-id="4dd9e-121">このセクションのスタイルルールでは、C# に固有の次の式レベルの設定について考慮します。</span><span class="sxs-lookup"><span data-stu-id="4dd9e-121">The style rules in this section concern the following expression-level preferences that are specific to C#:</span></span>

- [<span data-ttu-id="4dd9e-122">インライン変数宣言 (IDE0018)</span><span class="sxs-lookup"><span data-stu-id="4dd9e-122">Inline variable declaration (IDE0018)</span></span>](ide0018.md)
- [<span data-ttu-id="4dd9e-123">' Default ' 式を単純化する (IDE0034)</span><span class="sxs-lookup"><span data-stu-id="4dd9e-123">Simplify 'default' expression (IDE0034)</span></span>](ide0034.md)
- [<span data-ttu-id="4dd9e-124">ラムダの代わりにローカル関数を使用する (IDE0039)</span><span class="sxs-lookup"><span data-stu-id="4dd9e-124">Use local function instead of lambda (IDE0039)</span></span>](ide0039.md)
- [<span data-ttu-id="4dd9e-125">分解 variable 宣言 (IDE0042)</span><span class="sxs-lookup"><span data-stu-id="4dd9e-125">Deconstruct variable declaration (IDE0042)</span></span>](ide0042.md)
- [<span data-ttu-id="4dd9e-126">Use index 演算子 (IDE0056)</span><span class="sxs-lookup"><span data-stu-id="4dd9e-126">Use index operator (IDE0056)</span></span>](ide0056.md)
- [<span data-ttu-id="4dd9e-127">Use range 演算子 (IDE0057)</span><span class="sxs-lookup"><span data-stu-id="4dd9e-127">Use range operator (IDE0057)</span></span>](ide0057.md)
- [<span data-ttu-id="4dd9e-128">欠損したケースを switch 式に追加する (IDE0072)</span><span class="sxs-lookup"><span data-stu-id="4dd9e-128">Add missing cases to switch expression (IDE0072)</span></span>](ide0072.md)
- [<span data-ttu-id="4dd9e-129">' New ' 式を単純化します (IDE0090)</span><span class="sxs-lookup"><span data-stu-id="4dd9e-129">Simplify 'new' expression (IDE0090)</span></span>](ide0090.md)

## <a name="see-also"></a><span data-ttu-id="4dd9e-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="4dd9e-130">See also</span></span>

- [<span data-ttu-id="4dd9e-131">コードスタイル規則のリファレンス</span><span class="sxs-lookup"><span data-stu-id="4dd9e-131">Code style rules reference</span></span>](index.md)
- [<span data-ttu-id="4dd9e-132">コードスタイルの言語規則</span><span class="sxs-lookup"><span data-stu-id="4dd9e-132">Code style language rules</span></span>](language-rules.md)
