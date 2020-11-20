---
title: with 式 - C# リファレンス
description: C# レコードの非破壊的な変更を実行する with 式について説明します
ms.date: 11/12/2020
f1_keywords:
- with_CSharpKeyword
helpviewer_keywords:
- with expression [C#]
- with operator [C#]
ms.openlocfilehash: 8412dfe8663703d3b201fe98b5f4752da1b344cf
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2020
ms.locfileid: "94556713"
---
# <a name="with-expression-c-reference"></a><span data-ttu-id="d7cc7-103">with 式 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="d7cc7-103">with expression (C# reference)</span></span>

<span data-ttu-id="d7cc7-104">C# 9.0 以降で使用可能な `with` 式は、指定されたプロパティと変更されたフィールドにより、[レコード](../../whats-new/csharp-9.md#record-types) オペランドのコピーを生成します。</span><span class="sxs-lookup"><span data-stu-id="d7cc7-104">Available in C# 9.0 and later, a `with` expression produces a copy of its [record](../../whats-new/csharp-9.md#record-types) operand with the specified properties and fields modified:</span></span>

:::code language="csharp" source="snippets/with-expression/BasicExample.cs" :::

<span data-ttu-id="d7cc7-105">前の例で示したように、変更するメンバーとその新しい値は、[オブジェクト初期化子](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)構文を使用して指定します。</span><span class="sxs-lookup"><span data-stu-id="d7cc7-105">As the preceding example shows, you use [object initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) syntax to specify what members to modify and their new values.</span></span> <span data-ttu-id="d7cc7-106">`with` 式では、左側のオペランドがレコード型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7cc7-106">In a `with` expression, a left-hand operand must be of a record type.</span></span>

<span data-ttu-id="d7cc7-107">次の例に示すように、`with` 式の結果は、式のオペランドと同じランタイム型になります。</span><span class="sxs-lookup"><span data-stu-id="d7cc7-107">The result of a `with` expression has the same runtime type as the expression's operand, as the following example shows:</span></span>

:::code language="csharp" source="snippets/with-expression/InheritanceExample.cs" :::

<span data-ttu-id="d7cc7-108">参照型のメンバーの場合、レコードがコピーされるときに、インスタンスへの参照だけがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="d7cc7-108">In case of a reference-type member, only the reference to an instance is copied when a record is copied.</span></span> <span data-ttu-id="d7cc7-109">コピーと元のレコードの両方が、同じ参照型のインスタンスにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="d7cc7-109">Both the copy and original record have access to the same reference-type instance.</span></span> <span data-ttu-id="d7cc7-110">次の例は、その動作を示します。</span><span class="sxs-lookup"><span data-stu-id="d7cc7-110">The following example demonstrates that behavior:</span></span>

:::code language="csharp" source="snippets/with-expression/ExampleWithReferenceType.cs" :::

<span data-ttu-id="d7cc7-111">すべてのレコード型には、"*コピー コンストラクター*" があります。</span><span class="sxs-lookup"><span data-stu-id="d7cc7-111">Any record type has the *copy constructor*.</span></span> <span data-ttu-id="d7cc7-112">これは、含んでいるレコード型の 1 つのパラメーターを持つコンストラクターです。</span><span class="sxs-lookup"><span data-stu-id="d7cc7-112">That is a constructor with a single parameter of the containing record type.</span></span> <span data-ttu-id="d7cc7-113">その引数の状態が新しいレコード インスタンスにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="d7cc7-113">It copies the state of its argument to a new record instance.</span></span> <span data-ttu-id="d7cc7-114">`with` 式の評価では、コピー コンストラクターが呼び出され、元のレコードに基づいて新しいレコード インスタンスがインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="d7cc7-114">At evaluation of a `with` expression, the copy constructor gets called to instantiate a new record instance based on an original record.</span></span> <span data-ttu-id="d7cc7-115">その後、新しいインスタンスは、指定された変更に従って更新されます。</span><span class="sxs-lookup"><span data-stu-id="d7cc7-115">After that, the new instance gets updated according to the specified modifications.</span></span> <span data-ttu-id="d7cc7-116">既定では、コピー コンストラクターは暗黙的、つまり、コンパイラによって生成されます。</span><span class="sxs-lookup"><span data-stu-id="d7cc7-116">By default, the copy constructor is implicit, that is, compiler-generated.</span></span> <span data-ttu-id="d7cc7-117">レコード コピーのセマンティクスをカスタマイズする必要がある場合は、必要な動作が含まれるコピー コンストラクターを明示的に宣言します。</span><span class="sxs-lookup"><span data-stu-id="d7cc7-117">If you need to customize the record copy semantics, explicitly declare a copy constructor with the desired behavior.</span></span> <span data-ttu-id="d7cc7-118">次の例では、明示的なコピー コンストラクターを使用して前の例が更新されます。</span><span class="sxs-lookup"><span data-stu-id="d7cc7-118">The following example updates the preceding example with an explicit copy constructor.</span></span> <span data-ttu-id="d7cc7-119">新しいコピー動作では、レコードがコピーされるときにリスト参照ではなくリスト項目がコピーされます。</span><span class="sxs-lookup"><span data-stu-id="d7cc7-119">The new copy behavior is to copy list items instead of a list reference when a record is copied:</span></span>

:::code language="csharp" source="snippets/with-expression/UserDefinedCopyConstructor.cs" :::

## <a name="c-language-specification"></a><span data-ttu-id="d7cc7-120">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="d7cc7-120">C# language specification</span></span>

<span data-ttu-id="d7cc7-121">詳細については、[レコード機能提案メモ](~/_csharplang/proposals/csharp-9.0/records.md)の次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7cc7-121">For more information, see the following sections of the [records feature proposal note](~/_csharplang/proposals/csharp-9.0/records.md):</span></span>

- [<span data-ttu-id="d7cc7-122">`with` 式</span><span class="sxs-lookup"><span data-stu-id="d7cc7-122">`with` expression</span></span>](~/_csharplang/proposals/csharp-9.0/records.md#with-expression)
- [<span data-ttu-id="d7cc7-123">コピー メンバーとクローン メンバー</span><span class="sxs-lookup"><span data-stu-id="d7cc7-123">Copy and Clone members</span></span>](~/_csharplang/proposals/csharp-9.0/records.md#copy-and-clone-members)

## <a name="see-also"></a><span data-ttu-id="d7cc7-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="d7cc7-124">See also</span></span>

- [<span data-ttu-id="d7cc7-125">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="d7cc7-125">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d7cc7-126">C# の演算子と式</span><span class="sxs-lookup"><span data-stu-id="d7cc7-126">C# operators and expressions</span></span>](index.md)
