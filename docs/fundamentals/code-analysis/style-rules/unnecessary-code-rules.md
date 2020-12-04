---
title: 不要なコード規則
description: コード分析の不要なコード規則について
ms.date: 09/30/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 16c4ba0e4bee2388736bf9813a3e8290d8d4da32
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2020
ms.locfileid: "96593857"
---
# <a name="unnecessary-code-rules"></a><span data-ttu-id="b1c1b-103">不要なコード規則</span><span class="sxs-lookup"><span data-stu-id="b1c1b-103">Unnecessary code rules</span></span>

<span data-ttu-id="b1c1b-104">不要なコード規則は、コードベースのさまざまな部分を特定する必要がなく、リファクタリングまたは削除することができます。</span><span class="sxs-lookup"><span data-stu-id="b1c1b-104">Unnecessary code rules identify different parts of the code base that are unnecessary and can be refactored or removed.</span></span> <span data-ttu-id="b1c1b-105">不要なコードが存在する場合は、次の問題の1つを示します。</span><span class="sxs-lookup"><span data-stu-id="b1c1b-105">The presence of unnecessary code indicates one of more of the following problems:</span></span>

- <span data-ttu-id="b1c1b-106">読みやすさ: 読みやすさを不必要に低下させるコード。</span><span class="sxs-lookup"><span data-stu-id="b1c1b-106">Readability: Code that is unnecessarily degrading readability.</span></span> <span data-ttu-id="b1c1b-107">たとえば、 [IDE0001](ide0001.md) は不要な型名の修飾にフラグを指定します。</span><span class="sxs-lookup"><span data-stu-id="b1c1b-107">For example, [IDE0001](ide0001.md) flags unnecessary type-name qualifications.</span></span>
- <span data-ttu-id="b1c1b-108">保守容易性: リファクタリング後に使用されなくなり、不必要に管理されます。</span><span class="sxs-lookup"><span data-stu-id="b1c1b-108">Maintainability: Code that is no longer used after refactoring and is unnecessarily being maintained.</span></span> <span data-ttu-id="b1c1b-109">たとえば、 [IDE0051](ide0051.md) は、使用されていないプライベートフィールド、プロパティ、イベント、およびメソッドにフラグを使用します。</span><span class="sxs-lookup"><span data-stu-id="b1c1b-109">For example, [IDE0051](ide0051.md) flags unused private fields, properties, events, and methods.</span></span>
- <span data-ttu-id="b1c1b-110">パフォーマンス: 副作用のない不要な計算によって、不要なパフォーマンスのオーバーヘッドが発生します。</span><span class="sxs-lookup"><span data-stu-id="b1c1b-110">Performance: Unnecessary computation that has no side effects and leads to unnecessary performance overhead.</span></span> <span data-ttu-id="b1c1b-111">たとえば、 [IDE0059](ide0059.md) は未使用の値の割り当てにフラグを指定し、値を計算する式には副作用がありません。</span><span class="sxs-lookup"><span data-stu-id="b1c1b-111">For example, [IDE0059](ide0059.md) flags unused value assignments where the expression to compute a value has no side effects.</span></span>
- <span data-ttu-id="b1c1b-112">機能: コードの機能の問題。必要なコードを冗長にレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="b1c1b-112">Functionality: Functional issue in code leading to required code being rendered redundant.</span></span> <span data-ttu-id="b1c1b-113">たとえば、 [IDE0060](ide0060.md) は、メソッドが誤って入力パラメーターを無視した場合に、未使用のパラメーターにフラグを指定します。</span><span class="sxs-lookup"><span data-stu-id="b1c1b-113">For example, [IDE0060](ide0060.md) flags unused parameters where the method accidentally ignores an input parameter.</span></span>

<span data-ttu-id="b1c1b-114">このセクションの規則では、次の不要なコード規則について考慮します。</span><span class="sxs-lookup"><span data-stu-id="b1c1b-114">The rules in this section concern the following unnecessary code rules:</span></span>

- [<span data-ttu-id="b1c1b-115">簡易名 (IDE0001)</span><span class="sxs-lookup"><span data-stu-id="b1c1b-115">Simplify name (IDE0001)</span></span>](ide0001.md)
- [<span data-ttu-id="b1c1b-116">メンバーアクセスの簡略化 (IDE0002)</span><span class="sxs-lookup"><span data-stu-id="b1c1b-116">Simplify member access (IDE0002)</span></span>](ide0002.md)
- [<span data-ttu-id="b1c1b-117">不要なキャストの削除 (IDE0004)</span><span class="sxs-lookup"><span data-stu-id="b1c1b-117">Remove unnecessary cast (IDE0004)</span></span>](ide0004.md)
- [<span data-ttu-id="b1c1b-118">不要なインポートの削除 (IDE0005)</span><span class="sxs-lookup"><span data-stu-id="b1c1b-118">Remove unnecessary import (IDE0005)</span></span>](ide0005.md)
- [<span data-ttu-id="b1c1b-119">到達できないコードの削除 (IDE0035)</span><span class="sxs-lookup"><span data-stu-id="b1c1b-119">Remove unreachable code (IDE0035)</span></span>](ide0035.md)
- [<span data-ttu-id="b1c1b-120">未使用のプライベートメンバーの削除 (IDE0051)</span><span class="sxs-lookup"><span data-stu-id="b1c1b-120">Remove unused private member (IDE0051)</span></span>](ide0051.md)
- [<span data-ttu-id="b1c1b-121">未読のプライベートメンバーの削除 (IDE0052)</span><span class="sxs-lookup"><span data-stu-id="b1c1b-121">Remove unread private member (IDE0052)</span></span>](ide0052.md)
- [<span data-ttu-id="b1c1b-122">未使用の式の値 (IDE0058) の削除</span><span class="sxs-lookup"><span data-stu-id="b1c1b-122">Remove unused expression value (IDE0058)</span></span>](ide0058.md)
- [<span data-ttu-id="b1c1b-123">不要な値の割り当てを削除する (IDE0059)</span><span class="sxs-lookup"><span data-stu-id="b1c1b-123">Remove unnecessary value assignment (IDE0059)</span></span>](ide0059.md)
- [<span data-ttu-id="b1c1b-124">使用されていないパラメーター (IDE0060) を削除します。</span><span class="sxs-lookup"><span data-stu-id="b1c1b-124">Remove unused parameter (IDE0060)</span></span>](ide0060.md)
- [<span data-ttu-id="b1c1b-125">不要な抑制の削除 (IDE0079)</span><span class="sxs-lookup"><span data-stu-id="b1c1b-125">Remove unnecessary suppression (IDE0079)</span></span>](ide0079.md)
- <span data-ttu-id="b1c1b-126">[不要な抑制演算子 (IDE0080)](ide0080.md) -C# のみを削除します。</span><span class="sxs-lookup"><span data-stu-id="b1c1b-126">[Remove unnecessary suppression operator (IDE0080)](ide0080.md) - C# only.</span></span>
- <span data-ttu-id="b1c1b-127">[' ByVal ' (IDE0081)](ide0081.md) のみを削除します。 Visual Basic のみです。</span><span class="sxs-lookup"><span data-stu-id="b1c1b-127">[Remove 'ByVal' (IDE0081)](ide0081.md) - Visual Basic only.</span></span>
- [<span data-ttu-id="b1c1b-128">不要な等値演算子 (IDE0100) の削除</span><span class="sxs-lookup"><span data-stu-id="b1c1b-128">Remove unnecessary equality operator (IDE0100)</span></span>](ide0100.md)
- <span data-ttu-id="b1c1b-129">[不要な破棄 (IDE0110)](ide0110.md) -C# のみを削除します。</span><span class="sxs-lookup"><span data-stu-id="b1c1b-129">[Remove unnecessary discard (IDE0110)](ide0110.md) - C# only.</span></span>

<span data-ttu-id="b1c1b-130">これらのルールには、ルールの動作を構成するためのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="b1c1b-130">Some of these rules have options to configure the rule behavior:</span></span>

- [<span data-ttu-id="b1c1b-131">csharp_style_unused_value_expression_statement_preference (IDE0058)</span><span class="sxs-lookup"><span data-stu-id="b1c1b-131">csharp_style_unused_value_expression_statement_preference (IDE0058)</span></span>](ide0058.md#csharp_style_unused_value_expression_statement_preference)
- [<span data-ttu-id="b1c1b-132">visual_basic_style_unused_value_expression_statement_preference (IDE0058)</span><span class="sxs-lookup"><span data-stu-id="b1c1b-132">visual_basic_style_unused_value_expression_statement_preference (IDE0058)</span></span>](ide0058.md#visual_basic_style_unused_value_expression_statement_preference)
- [<span data-ttu-id="b1c1b-133">csharp_style_unused_value_assignment_preference (IDE0059)</span><span class="sxs-lookup"><span data-stu-id="b1c1b-133">csharp_style_unused_value_assignment_preference (IDE0059)</span></span>](ide0059.md#csharp_style_unused_value_assignment_preference)
- [<span data-ttu-id="b1c1b-134">visual_basic_style_unused_value_assignment_preference (IDE0059)</span><span class="sxs-lookup"><span data-stu-id="b1c1b-134">visual_basic_style_unused_value_assignment_preference (IDE0059)</span></span>](ide0059.md#visual_basic_style_unused_value_assignment_preference)
- [<span data-ttu-id="b1c1b-135">dotnet_code_quality_unused_parameters (IDE0060)</span><span class="sxs-lookup"><span data-stu-id="b1c1b-135">dotnet_code_quality_unused_parameters (IDE0060)</span></span>](ide0060.md#dotnet_code_quality_unused_parameters)
- [<span data-ttu-id="b1c1b-136">dotnet_remove_unnecessary_suppression_exclusions (IDE0079)</span><span class="sxs-lookup"><span data-stu-id="b1c1b-136">dotnet_remove_unnecessary_suppression_exclusions (IDE0079)</span></span>](ide0079.md#dotnet_remove_unnecessary_suppression_exclusions)

## <a name="see-also"></a><span data-ttu-id="b1c1b-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="b1c1b-137">See also</span></span>

- [<span data-ttu-id="b1c1b-138">コードスタイルの言語規則</span><span class="sxs-lookup"><span data-stu-id="b1c1b-138">Code style language rules</span></span>](language-rules.md)
- [<span data-ttu-id="b1c1b-139">コードスタイル規則のリファレンス</span><span class="sxs-lookup"><span data-stu-id="b1c1b-139">Code style rules reference</span></span>](index.md)
