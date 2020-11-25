---
title: 名前付けのガイドライン
description: この概要では、フレームワーク開発で使用する名前付け規則について説明します。 大文字と小文字の区別、一般的な名前付け、およびその他のガイドラインに関する記事にアクセスしてください。
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], about naming guidelines
- naming guidelines [.NET Framework]
- class library design guidelines [.NET Framework], names
- formatting [.NET Framework], names
- identifiers, class library element names
- names [.NET Framework]
- format naming guidelines [.NET Framework]
ms.assetid: fc076d66-9b5f-42d3-aa65-61d970c794a3
ms.openlocfilehash: de68eeb287b13bc9f55230243f23cd03508f2561
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706425"
---
# <a name="naming-guidelines"></a><span data-ttu-id="af72c-104">名前付けのガイドライン</span><span class="sxs-lookup"><span data-stu-id="af72c-104">Naming Guidelines</span></span>

<span data-ttu-id="af72c-105">フレームワークの開発における一貫した名前付け規則に従うことは、フレームワークのユーザビリティに大きな影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="af72c-105">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="af72c-106">これにより、多数の開発者が広範に分離されたプロジェクトでフレームワークを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="af72c-106">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="af72c-107">フォームの一貫性を超えて、フレームワーク要素の名前を簡単に理解し、各要素の機能を伝達する必要があります。</span><span class="sxs-lookup"><span data-stu-id="af72c-107">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="af72c-108">この章の目的は、一貫性のある名前付け規則を提供して、開発者にとってわかりやすい名前にすることです。</span><span class="sxs-lookup"><span data-stu-id="af72c-108">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="af72c-109">一般的なコード開発ガイドラインとしてこれらの名前付け規則を採用することにより、コード全体で一貫性のある名前付けを行うことができますが、公開されている Api (パブリックまたは保護された型とメンバー、および明示的に実装されたインターフェイス) に適用するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="af72c-109">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="af72c-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="af72c-110">In This Section</span></span>  

 [<span data-ttu-id="af72c-111">大文字の表記規則</span><span class="sxs-lookup"><span data-stu-id="af72c-111">Capitalization Conventions</span></span>](capitalization-conventions.md)  
 [<span data-ttu-id="af72c-112">一般的な名前付け規則</span><span class="sxs-lookup"><span data-stu-id="af72c-112">General Naming Conventions</span></span>](general-naming-conventions.md)  
 [<span data-ttu-id="af72c-113">アセンブリと Dll の名前</span><span class="sxs-lookup"><span data-stu-id="af72c-113">Names of Assemblies and DLLs</span></span>](names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="af72c-114">名前空間の名前</span><span class="sxs-lookup"><span data-stu-id="af72c-114">Names of Namespaces</span></span>](names-of-namespaces.md)  
 [<span data-ttu-id="af72c-115">クラス、構造体、およびインターフェイスの名前</span><span class="sxs-lookup"><span data-stu-id="af72c-115">Names of Classes, Structs, and Interfaces</span></span>](names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="af72c-116">型のメンバーの名前</span><span class="sxs-lookup"><span data-stu-id="af72c-116">Names of Type Members</span></span>](names-of-type-members.md)  
 [<span data-ttu-id="af72c-117">パラメーターの名前付け</span><span class="sxs-lookup"><span data-stu-id="af72c-117">Naming Parameters</span></span>](naming-parameters.md)  
 [<span data-ttu-id="af72c-118">リソースの名前付け</span><span class="sxs-lookup"><span data-stu-id="af72c-118">Naming Resources</span></span>](naming-resources.md)  
 <span data-ttu-id="af72c-119">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="af72c-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="af72c-120">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="af72c-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af72c-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="af72c-121">See also</span></span>

- [<span data-ttu-id="af72c-122">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="af72c-122">Framework Design Guidelines</span></span>](index.md)
