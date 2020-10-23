---
title: インポート '<qualifiedelementname>' で指定された名前空間または型が、パブリック メンバーを含んでいないか、または見つかりません。
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: 284a8c71fee8835f78ca5435932819fded1b1f30
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160133"
---
# <a name="bc40056-namespace-or-type-specified-in-the-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="a1c58-102">BC40056:インポート '\<qualifiedelementname>' で指定された名前空間または型が、パブリック メンバーを含んでいないか、または見つかりません。</span><span class="sxs-lookup"><span data-stu-id="a1c58-102">BC40056: Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found</span></span>

<span data-ttu-id="a1c58-103">インポート '\<qualifiedelementname>' で指定された名前空間または型が、パブリック メンバーを含んでいないか、または見つかりません。</span><span class="sxs-lookup"><span data-stu-id="a1c58-103">Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="a1c58-104">名前空間または型が定義されており、少なくとも 1 つのパブリック メンバーが含まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a1c58-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="a1c58-105">別名の名前に他の別名が含まれていないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a1c58-105">Make sure the alias name doesn't contain other aliases.</span></span>

<span data-ttu-id="a1c58-106">`Imports` ステートメントは、見つからないか、`Public` メンバーを定義しないコンテナー要素を指定しています。</span><span class="sxs-lookup"><span data-stu-id="a1c58-106">An `Imports` statement specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>

<span data-ttu-id="a1c58-107">*コンテナー要素*は、名前空間、クラス、構造体、モジュール、インターフェイス、または列挙型にすることができます。</span><span class="sxs-lookup"><span data-stu-id="a1c58-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="a1c58-108">コンテナー要素には、変数、プロシージャ、その他のコンテナー要素などのメンバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a1c58-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>

<span data-ttu-id="a1c58-109">インポートの目的は、コードによって名前空間または型のメンバーに、それらを修飾しなくてもアクセスできるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="a1c58-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="a1c58-110">また、プロジェクトで名前空間や型への参照を追加する必要がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="a1c58-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="a1c58-111">詳細については、「[宣言された要素の参照](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)」の "コンテナー要素のインポート" に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1c58-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

<span data-ttu-id="a1c58-112">コンパイラは、指定したコンテナー要素が見つからない場合、それを使用する参照を解決できません。</span><span class="sxs-lookup"><span data-stu-id="a1c58-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="a1c58-113">要素が見つかったが、要素が `Public` のメンバーを公開していない場合、参照を正常に実行できません。</span><span class="sxs-lookup"><span data-stu-id="a1c58-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="a1c58-114">どちらの場合も、要素をインポートしても意味がありません。</span><span class="sxs-lookup"><span data-stu-id="a1c58-114">In either case it is meaningless to import the element.</span></span>

<span data-ttu-id="a1c58-115">コンテナー要素をインポートし、それにインポートの別名を割り当てた場合は、その別名を使用して別の要素をインポートできないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a1c58-115">Keep in mind that if you import a containing element and assign an import alias to it, then you cannot use that import alias to import another element.</span></span> <span data-ttu-id="a1c58-116">次のコードはコンパイラ エラーになります。</span><span class="sxs-lookup"><span data-stu-id="a1c58-116">The following code generates a compiler error.</span></span>

```vb
Imports winfrm = System.Windows.Forms

' The following statement is INVALID  because it reuses an import alias.

Imports behave = winfrm.Design.Behavior`
```

<span data-ttu-id="a1c58-117">**エラー ID:** BC40056</span><span class="sxs-lookup"><span data-stu-id="a1c58-117">**Error ID:** BC40056</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="a1c58-118">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="a1c58-118">To correct this error</span></span>

1. <span data-ttu-id="a1c58-119">コンテナー要素がプロジェクトからアクセス可能であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a1c58-119">Verify that the containing element is accessible from your project.</span></span>

2. <span data-ttu-id="a1c58-120">コンテナー要素の指定に、別のインポートの別名が含まれていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="a1c58-120">Verify that the specification of the containing element does not include any import alias from another import.</span></span>

3. <span data-ttu-id="a1c58-121">コンテナー要素が少なくとも 1 つの `Public` メンバーを公開していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a1c58-121">Verify that the containing element exposes at least one `Public` member.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1c58-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1c58-122">See also</span></span>

- [<span data-ttu-id="a1c58-123">Imports ステートメント (.NET 名前空間および型)</span><span class="sxs-lookup"><span data-stu-id="a1c58-123">Imports Statement (.NET Namespace and Type)</span></span>](../statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="a1c58-124">Namespace ステートメント</span><span class="sxs-lookup"><span data-stu-id="a1c58-124">Namespace Statement</span></span>](../statements/namespace-statement.md)
- [<span data-ttu-id="a1c58-125">Public</span><span class="sxs-lookup"><span data-stu-id="a1c58-125">Public</span></span>](../modifiers/public.md)
- [<span data-ttu-id="a1c58-126">Visual Basic における名前空間</span><span class="sxs-lookup"><span data-stu-id="a1c58-126">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="a1c58-127">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="a1c58-127">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
