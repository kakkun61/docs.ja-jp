---
title: 名前空間の名前
description: .NET ライブラリを拡張および操作するライブラリを設計するためのガイドラインの一部として名前空間の名前を付けるには、次のガイドラインに従います。
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
ms.openlocfilehash: 561a6e4ed1abf82fc1412123a4558a63e7176b2f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706490"
---
# <a name="names-of-namespaces"></a><span data-ttu-id="ca45d-103">名前空間の名前</span><span class="sxs-lookup"><span data-stu-id="ca45d-103">Names of Namespaces</span></span>

<span data-ttu-id="ca45d-104">他の命名ガイドラインと同様に、名前空間に名前を付ける際の目的は、名前空間の内容がどのようなものである可能性があるかをすぐに把握するために、フレームワークを使用するプログラマにとって十分なわかりやすいものにすることです。</span><span class="sxs-lookup"><span data-stu-id="ca45d-104">As with other naming guidelines, the goal when naming namespaces is creating sufficient clarity for the programmer using the framework to immediately know what the content of the namespace is likely to be.</span></span> <span data-ttu-id="ca45d-105">次のテンプレートは、名前空間の名前付けに関する一般的な規則を指定します。</span><span class="sxs-lookup"><span data-stu-id="ca45d-105">The following template specifies the general rule for naming namespaces:</span></span>

 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`

 <span data-ttu-id="ca45d-106">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ca45d-106">The following are examples:</span></span>

 <span data-ttu-id="ca45d-107">`Fabrikam.Math` `Litware.Security`</span><span class="sxs-lookup"><span data-stu-id="ca45d-107">`Fabrikam.Math` `Litware.Security`</span></span>

 <span data-ttu-id="ca45d-108">異なる企業の名前空間が同じ名前にならないように、会社名を使用して名前空間名にプレフィックスを付ける✔️ます。</span><span class="sxs-lookup"><span data-stu-id="ca45d-108">✔️ DO prefix namespace names with a company name to prevent namespaces from different companies from having the same name.</span></span>

 <span data-ttu-id="ca45d-109">名前空間名の2番目のレベルでは、バージョンに依存しない安定した製品名を使用✔️ます。</span><span class="sxs-lookup"><span data-stu-id="ca45d-109">✔️ DO use a stable, version-independent product name at the second level of a namespace name.</span></span>

 <span data-ttu-id="ca45d-110">❌ 企業内のグループ名は有効期間が短くなる傾向があるため、名前空間階層内の名前の基準として組織階層を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="ca45d-110">❌ DO NOT use organizational hierarchies as the basis for names in namespace hierarchies, because group names within corporations tend to be short-lived.</span></span> <span data-ttu-id="ca45d-111">関連するテクノロジのグループを中心に、名前空間の階層を整理します。</span><span class="sxs-lookup"><span data-stu-id="ca45d-111">Organize the hierarchy of namespaces around groups of related technologies.</span></span>

 <span data-ttu-id="ca45d-112">✔️は、文字の大文字と小文字の区別を使用し、ピリオドを使用して名前空間コンポーネントを分離します (例: `Microsoft.Office.PowerPoint` )。</span><span class="sxs-lookup"><span data-stu-id="ca45d-112">✔️ DO use PascalCasing, and separate namespace components with periods (e.g., `Microsoft.Office.PowerPoint`).</span></span> <span data-ttu-id="ca45d-113">ブランドで nontraditional の大文字と小文字の区別が使用されている場合は、通常の名前空間の大文字と小文字が異なる場合でも、ブランドで定義されている大文字と小文字を</span><span class="sxs-lookup"><span data-stu-id="ca45d-113">If your brand employs nontraditional casing, you should follow the casing defined by your brand, even if it deviates from normal namespace casing.</span></span>

 <span data-ttu-id="ca45d-114">✔️、必要に応じて複数形の名前空間を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="ca45d-114">✔️ CONSIDER using plural namespace names where appropriate.</span></span>

 <span data-ttu-id="ca45d-115">たとえば、`System.Collection` の代わりに `System.Collections` を使用します。</span><span class="sxs-lookup"><span data-stu-id="ca45d-115">For example, use `System.Collections` instead of `System.Collection`.</span></span> <span data-ttu-id="ca45d-116">ただし、ブランド名と頭字語は、このルールの例外です。</span><span class="sxs-lookup"><span data-stu-id="ca45d-116">Brand names and acronyms are exceptions to this rule, however.</span></span> <span data-ttu-id="ca45d-117">たとえば、`System.IOs` の代わりに `System.IO` を使用します。</span><span class="sxs-lookup"><span data-stu-id="ca45d-117">For example, use `System.IO` instead of `System.IOs`.</span></span>

 <span data-ttu-id="ca45d-118">❌ 名前空間とその名前空間の型に同じ名前を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="ca45d-118">❌ DO NOT use the same name for a namespace and a type in that namespace.</span></span>

 <span data-ttu-id="ca45d-119">たとえば、名前空間名としてを使用せずに、 `Debug` `Debug` 同じ名前空間内にという名前のクラスを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="ca45d-119">For example, do not use `Debug` as a namespace name and then also provide a class named `Debug` in the same namespace.</span></span> <span data-ttu-id="ca45d-120">いくつかのコンパイラでは、このような型を完全に修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca45d-120">Several compilers require such types to be fully qualified.</span></span>

### <a name="namespaces-and-type-name-conflicts"></a><span data-ttu-id="ca45d-121">名前空間と型名の競合</span><span class="sxs-lookup"><span data-stu-id="ca45d-121">Namespaces and Type Name Conflicts</span></span>

 <span data-ttu-id="ca45d-122">❌ 、、、などのジェネリック型の名前は導入しないでください `Element` `Node` `Log` `Message` 。</span><span class="sxs-lookup"><span data-stu-id="ca45d-122">❌ DO NOT introduce generic type names such as `Element`, `Node`, `Log`, and `Message`.</span></span>

 <span data-ttu-id="ca45d-123">これを行うと、一般的なシナリオでの型名の競合が発生する可能性が非常に高くなります。</span><span class="sxs-lookup"><span data-stu-id="ca45d-123">There is a very high probability that doing so will lead to type name conflicts in common scenarios.</span></span> <span data-ttu-id="ca45d-124">ジェネリック型名を修飾する必要があり `FormElement` ます (、、 `XmlNode` `EventLog` 、 `SoapMessage` )。</span><span class="sxs-lookup"><span data-stu-id="ca45d-124">You should qualify the generic type names (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span></span>

 <span data-ttu-id="ca45d-125">名前空間のカテゴリごとに型名の競合を回避するための特定のガイドラインがあります。</span><span class="sxs-lookup"><span data-stu-id="ca45d-125">There are specific guidelines for avoiding type name conflicts for different categories of namespaces.</span></span>

- <span data-ttu-id="ca45d-126">**アプリケーションモデルの名前空間**</span><span class="sxs-lookup"><span data-stu-id="ca45d-126">**Application model namespaces**</span></span>

     <span data-ttu-id="ca45d-127">1つのアプリケーションモデルに属する名前空間は、一緒に使用されることがよくありますが、他のアプリケーションモデルの名前空間で使用されることはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="ca45d-127">Namespaces belonging to a single application model are very often used together, but they are almost never used with namespaces of other application models.</span></span> <span data-ttu-id="ca45d-128">たとえば、名前空間は、 <xref:System.Windows.Forms?displayProperty=nameWithType> 名前空間と共に使用することはほとんど <xref:System.Web.UI?displayProperty=nameWithType> ありません。</span><span class="sxs-lookup"><span data-stu-id="ca45d-128">For example, the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace is very rarely used together with the <xref:System.Web.UI?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="ca45d-129">既知のアプリケーションモデル名前空間グループの一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ca45d-129">The following is a list of well-known application model namespace groups:</span></span>

     <span data-ttu-id="ca45d-130">`System.Windows*` `System.Web.UI*`</span><span class="sxs-lookup"><span data-stu-id="ca45d-130">`System.Windows*` `System.Web.UI*`</span></span>

     <span data-ttu-id="ca45d-131">❌ 単一のアプリケーションモデル内の名前空間の型に同じ名前を付けないでください。</span><span class="sxs-lookup"><span data-stu-id="ca45d-131">❌ DO NOT give the same name to types in namespaces within a single application model.</span></span>

     <span data-ttu-id="ca45d-132">たとえば、という名前の型を名前空間に追加しないでください。名前空間には、 `Page` <xref:System.Web.UI.Adapters?displayProperty=nameWithType> という名前の型が <xref:System.Web.UI?displayProperty=nameWithType> 既に含まれてい `Page` ます。</span><span class="sxs-lookup"><span data-stu-id="ca45d-132">For example, do not add a type named `Page` to the <xref:System.Web.UI.Adapters?displayProperty=nameWithType> namespace, because the <xref:System.Web.UI?displayProperty=nameWithType> namespace already contains a type named `Page`.</span></span>

- <span data-ttu-id="ca45d-133">**インフラストラクチャの名前空間**</span><span class="sxs-lookup"><span data-stu-id="ca45d-133">**Infrastructure namespaces**</span></span>

     <span data-ttu-id="ca45d-134">このグループには、一般的なアプリケーションの開発時にインポートされることがほとんどない名前空間が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ca45d-134">This group contains namespaces that are rarely imported during development of common applications.</span></span> <span data-ttu-id="ca45d-135">たとえば、 `.Design` 名前空間は主にプログラミングツールを開発するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="ca45d-135">For example, `.Design` namespaces are mainly used when developing programming tools.</span></span> <span data-ttu-id="ca45d-136">これらの名前空間の型との競合を回避することは、重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="ca45d-136">Avoiding conflicts with types in these namespaces is not critical.</span></span>

- <span data-ttu-id="ca45d-137">**コア名前空間**</span><span class="sxs-lookup"><span data-stu-id="ca45d-137">**Core namespaces**</span></span>

     <span data-ttu-id="ca45d-138">コア名前空間には `System` 、アプリケーションモデルの名前空間とインフラストラクチャの名前空間を除く、すべての名前空間が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ca45d-138">Core namespaces include all `System` namespaces, excluding namespaces of the application models and the Infrastructure namespaces.</span></span> <span data-ttu-id="ca45d-139">コア名前空間には、他の、、、、およびが含ま `System` `System.IO` `System.Xml` `System.Net` れます。</span><span class="sxs-lookup"><span data-stu-id="ca45d-139">Core namespaces include, among others, `System`, `System.IO`, `System.Xml`, and `System.Net`.</span></span>

     <span data-ttu-id="ca45d-140">❌ コア名前空間の型と競合する型名を指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="ca45d-140">❌ DO NOT give types names that would conflict with any type in the Core namespaces.</span></span>

     <span data-ttu-id="ca45d-141">たとえば、 `Stream` 型名としてを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="ca45d-141">For example, never use `Stream` as a type name.</span></span> <span data-ttu-id="ca45d-142">これは <xref:System.IO.Stream?displayProperty=nameWithType> 、よく使用される型と競合します。</span><span class="sxs-lookup"><span data-stu-id="ca45d-142">It would conflict with <xref:System.IO.Stream?displayProperty=nameWithType>, a very commonly used type.</span></span>

- <span data-ttu-id="ca45d-143">**テクノロジ名前空間グループ**</span><span class="sxs-lookup"><span data-stu-id="ca45d-143">**Technology namespace groups**</span></span>

     <span data-ttu-id="ca45d-144">このカテゴリには、やなど、同じ最初の2つの名前空間ノードを持つすべての名前空間が含まれ `(<Company>.<Technology>*` `Microsoft.Build.Utilities` `Microsoft.Build.Tasks` ます。</span><span class="sxs-lookup"><span data-stu-id="ca45d-144">This category includes all namespaces with the same first two namespace nodes `(<Company>.<Technology>*`), such as `Microsoft.Build.Utilities` and `Microsoft.Build.Tasks`.</span></span> <span data-ttu-id="ca45d-145">1つのテクノロジに属する型が互いに競合しないことが重要です。</span><span class="sxs-lookup"><span data-stu-id="ca45d-145">It is important that types belonging to a single technology do not conflict with each other.</span></span>

     <span data-ttu-id="ca45d-146">❌ 1つのテクノロジ内の他の型と競合する型名を割り当てないでください。</span><span class="sxs-lookup"><span data-stu-id="ca45d-146">❌ DO NOT assign type names that would conflict with other types within a single technology.</span></span>

     <span data-ttu-id="ca45d-147">❌ テクノロジ名前空間の型とアプリケーションモデルの名前空間の間で型名の競合を発生させないでください (テクノロジがアプリケーションモデルで使用されることを想定していない場合)。</span><span class="sxs-lookup"><span data-stu-id="ca45d-147">❌ DO NOT introduce type name conflicts between types in technology namespaces and an application model namespace (unless the technology is not intended to be used with the application model).</span></span>

 <span data-ttu-id="ca45d-148">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="ca45d-148">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="ca45d-149">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="ca45d-149">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="ca45d-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="ca45d-150">See also</span></span>

- [<span data-ttu-id="ca45d-151">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="ca45d-151">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="ca45d-152">名前付けのガイドライン</span><span class="sxs-lookup"><span data-stu-id="ca45d-152">Naming Guidelines</span></span>](naming-guidelines.md)
