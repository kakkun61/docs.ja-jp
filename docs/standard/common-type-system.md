---
title: 共通型システムと共通言語仕様
description: 共通型システム (CTS) と共通言語仕様 (CLS) を使用して .NET で複数の言語をサポートする方法について説明します。
ms.date: 06/20/2016
ms.assetid: 3b1f5725-ac94-4f17-8e5f-244442438a4d
ms.openlocfilehash: e60205450e2f156407deb7be6b9c497d090b6f7b
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94822881"
---
# <a name="common-type-system--common-language-specification"></a><span data-ttu-id="37b7c-103">共通型システムと共通言語仕様</span><span class="sxs-lookup"><span data-stu-id="37b7c-103">Common Type System & Common Language Specification</span></span>

<span data-ttu-id="37b7c-104">これらの 2 つの用語は、.NET の世界で自由に使用されます。これらは実際には、.NET 実装で多言語開発を可能にし、そのしくみを理解するために重要です。</span><span class="sxs-lookup"><span data-stu-id="37b7c-104">Again, two terms that are freely used in the .NET world, they actually are crucial to understand how a .NET implementation enables multi-language development and to understand how it works.</span></span>

## <a name="common-type-system"></a><span data-ttu-id="37b7c-105">共通型システム</span><span class="sxs-lookup"><span data-stu-id="37b7c-105">Common Type System</span></span>

<span data-ttu-id="37b7c-106">最初に、.NET 実装は _言語に依存しない_ 点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="37b7c-106">To start from the beginning, remember that a .NET implementation is _language agnostic_.</span></span> <span data-ttu-id="37b7c-107">これはプログラマーが IL にコンパイルできる任意の言語でコードを記述できることを意味するだけではありません。</span><span class="sxs-lookup"><span data-stu-id="37b7c-107">This doesn't just mean that a programmer can write their code in any language that can be compiled to IL.</span></span> <span data-ttu-id="37b7c-108">また、.NET 実装で使用可能な他の言語で記述されたコードをプログラマーが操作できる必要があることも意味します。</span><span class="sxs-lookup"><span data-stu-id="37b7c-108">It also means that they need to be able to interact with code written in other languages that are able to be used on a .NET implementation.</span></span>

<span data-ttu-id="37b7c-109">これを透過的に行うには、すべてのサポートされる種類を記述するための共通の方法が存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="37b7c-109">In order to do this transparently, there has to be a common way to describe all supported types.</span></span> <span data-ttu-id="37b7c-110">これは、共通型システム (CTS) の役割です。</span><span class="sxs-lookup"><span data-stu-id="37b7c-110">This is what the Common Type System (CTS) is in charge of doing.</span></span> <span data-ttu-id="37b7c-111">CTS には、次のようないくつかの目的があります。</span><span class="sxs-lookup"><span data-stu-id="37b7c-111">It was made to do several things:</span></span>

* <span data-ttu-id="37b7c-112">多言語での実行のためのフレームワークを確立する。</span><span class="sxs-lookup"><span data-stu-id="37b7c-112">Establish a framework for cross-language execution.</span></span>
* <span data-ttu-id="37b7c-113">.NET 実装でさまざまな言語の実装をサポートするためのオブジェクト指向モデルを提供する。</span><span class="sxs-lookup"><span data-stu-id="37b7c-113">Provide an object-oriented model to support implementing various languages on a .NET implementation.</span></span>
* <span data-ttu-id="37b7c-114">型を扱うときにすべての言語が従う必要がある規則のセットを定義する。</span><span class="sxs-lookup"><span data-stu-id="37b7c-114">Define a set of rules that all languages must follow when it comes to working with types.</span></span>
* <span data-ttu-id="37b7c-115">アプリケーション開発に使用される基本的なプリミティブ データ型 (`Boolean`、`Byte`、`Char` など) を含んだライブラリを提供します。</span><span class="sxs-lookup"><span data-stu-id="37b7c-115">Provide a library that contains the basic primitive types that are used in application development (such as, `Boolean`, `Byte`, `Char` etc.)</span></span>

<span data-ttu-id="37b7c-116">CTS が定義する、参照型と値型という 2 つの主要な型をサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="37b7c-116">CTS defines two main kinds of types that should be supported: reference and value types.</span></span> <span data-ttu-id="37b7c-117">それらの名前が空の定義を示します。</span><span class="sxs-lookup"><span data-stu-id="37b7c-117">Their names point to their definitions.</span></span>

<span data-ttu-id="37b7c-118">参照型のオブジェクトは、オブジェクトの実際の値を指す参照によって表されます。ここでの参照は、C/C++ のポインターに似ています。</span><span class="sxs-lookup"><span data-stu-id="37b7c-118">Reference types' objects are represented by a reference to the object's actual value; a reference here is similar to a pointer in C/C++.</span></span> <span data-ttu-id="37b7c-119">これは、単純にオブジェクトの値が存在しているメモリの場所を参照します。</span><span class="sxs-lookup"><span data-stu-id="37b7c-119">It simply refers to a memory location where the objects' values are.</span></span> <span data-ttu-id="37b7c-120">このことはこれらの型の使用方法に深く影響します。</span><span class="sxs-lookup"><span data-stu-id="37b7c-120">This has a profound impact on how these types are used.</span></span> <span data-ttu-id="37b7c-121">変数に参照型割り当ててその変数をメソッドに渡す場合、たとえば、オブジェクトの変更はメイン オブジェクトに反映されます。コピーはありません。</span><span class="sxs-lookup"><span data-stu-id="37b7c-121">If you assign a reference type to a variable and then pass that variable into a method, for instance, any changes to the object will be reflected on the main object; there is no copying.</span></span>

<span data-ttu-id="37b7c-122">値型は、反対にオブジェクトがそれらの値によって表されます。</span><span class="sxs-lookup"><span data-stu-id="37b7c-122">Value types are the opposite, where the objects are represented by their values.</span></span> <span data-ttu-id="37b7c-123">変数に値型を割り当てた場合、基本的にオブジェクトの値をコピーすることになります。</span><span class="sxs-lookup"><span data-stu-id="37b7c-123">If you assign a value type to a variable, you are essentially copying a value of the object.</span></span>

<span data-ttu-id="37b7c-124">CTS では、いくつかの型のカテゴリが定義され、それぞれに固有のセマンティックスと使用方法があります。</span><span class="sxs-lookup"><span data-stu-id="37b7c-124">CTS defines several categories of types, each with their specific semantics and usage:</span></span>

* <span data-ttu-id="37b7c-125">クラス</span><span class="sxs-lookup"><span data-stu-id="37b7c-125">Classes</span></span>
* <span data-ttu-id="37b7c-126">構造体</span><span class="sxs-lookup"><span data-stu-id="37b7c-126">Structures</span></span>
* <span data-ttu-id="37b7c-127">列挙型</span><span class="sxs-lookup"><span data-stu-id="37b7c-127">Enums</span></span>
* <span data-ttu-id="37b7c-128">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="37b7c-128">Interfaces</span></span>
* <span data-ttu-id="37b7c-129">デリゲート</span><span class="sxs-lookup"><span data-stu-id="37b7c-129">Delegates</span></span>

<span data-ttu-id="37b7c-130">CTS では、アクセス修飾子、有効な型のメンバー、継承とオーバーロードの動作など、型の他のすべてのプロパティも定義されます。</span><span class="sxs-lookup"><span data-stu-id="37b7c-130">CTS also defines all other properties of the types, such as access modifiers, what are valid type members, how inheritance and overloading works and so on.</span></span> <span data-ttu-id="37b7c-131">残念ながら、これらのプロパティについての詳しい説明は概要の記事の範囲外ですが、これらのトピックの詳細情報については、最後の「[その他のリソース](#more-resources)」のリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="37b7c-131">Unfortunately, going deep into any of those is beyond the scope of an introductory article such as this, but you can consult [More resources](#more-resources) section at the end for links to more in-depth content that covers these topics.</span></span>

## <a name="common-language-specification"></a><span data-ttu-id="37b7c-132">共通言語仕様</span><span class="sxs-lookup"><span data-stu-id="37b7c-132">Common Language Specification</span></span>

<span data-ttu-id="37b7c-133">完全な相互運用シナリオを有効にするには、コードで作成されるすべてのオブジェクトがそれらを使用している言語 (_呼び出し元_) で何らかの共通点に依存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37b7c-133">To enable full interoperability scenarios, all objects that are created in code must rely on some commonality in the languages that are consuming them (are their _callers_).</span></span> <span data-ttu-id="37b7c-134">多くの異なる言語があるので、.NET では、**共通言語仕様** (CLS) という共通性を規定しています。</span><span class="sxs-lookup"><span data-stu-id="37b7c-134">Since there are numerous different languages, .NET has specified those commonalities in something called the **Common Language Specification** (CLS).</span></span> <span data-ttu-id="37b7c-135">CLS は、多くの一般的なアプリケーションに必要な機能のセットを定義しています。</span><span class="sxs-lookup"><span data-stu-id="37b7c-135">CLS defines a set of features that are needed by many common applications.</span></span> <span data-ttu-id="37b7c-136">さらに、サポートする必要がある .NET 上に実装される言語用のある種のレシピも提供しています。</span><span class="sxs-lookup"><span data-stu-id="37b7c-136">It also provides a sort of recipe for any language that is implemented on top of .NET on what it needs to support.</span></span>

<span data-ttu-id="37b7c-137">CLS は CTS のサブセットです。</span><span class="sxs-lookup"><span data-stu-id="37b7c-137">CLS is a subset of the CTS.</span></span> <span data-ttu-id="37b7c-138">つまり、CLS により厳しい規則がない限り、CTS のすべての規則は CLS にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="37b7c-138">This means that all of the rules in the CTS also apply to the CLS, unless the CLS rules are more strict.</span></span> <span data-ttu-id="37b7c-139">CLS の規則のみを使用してコンポーネントがビルドされている場合、つまり API で CLS の機能のみが公開されている場合、**CLS 準拠** であると言われます。</span><span class="sxs-lookup"><span data-stu-id="37b7c-139">If a component is built using only the rules in the CLS, that is, it exposes only the CLS features in its API, it is said to be **CLS-compliant**.</span></span> <span data-ttu-id="37b7c-140">たとえば、`<framework-librares>` は、.NET がサポートされているすべての言語で機能する必要があるため、まさに CLS 準拠です。</span><span class="sxs-lookup"><span data-stu-id="37b7c-140">For instance, the `<framework-librares>` are CLS-compliant precisely because they need to work across all of the languages that are supported on .NET.</span></span>

<span data-ttu-id="37b7c-141">CMS のすべての機能の概要については、下の「[その他のリソース](#more-resources)」セクションのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="37b7c-141">You can consult the documents in the [More Resources](#more-resources) section below to get an overview of all the features in the CLS.</span></span>

## <a name="more-resources"></a><span data-ttu-id="37b7c-142">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="37b7c-142">More resources</span></span>

* [<span data-ttu-id="37b7c-143">共通型システム</span><span class="sxs-lookup"><span data-stu-id="37b7c-143">Common Type System</span></span>](./base-types/common-type-system.md)
* [<span data-ttu-id="37b7c-144">共通言語仕様</span><span class="sxs-lookup"><span data-stu-id="37b7c-144">Common Language Specification</span></span>](language-independence-and-language-independent-components.md)
