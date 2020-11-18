---
title: リソースに名前を付ける
description: .NET でのリソースの名前付けガイドラインを確認します。これは、プロパティの名前付けのガイドラインに似ています。
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
ms.openlocfilehash: c01e041edbf30813c477e579867abb9099ce0528
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820853"
---
# <a name="naming-resources"></a><span data-ttu-id="faace-103">リソースに名前を付ける</span><span class="sxs-lookup"><span data-stu-id="faace-103">Naming Resources</span></span>
<span data-ttu-id="faace-104">ローカライズ可能なリソースは、プロパティのように特定のオブジェクトを介して参照できるので、リソースの名前付けガイドラインはプロパティガイドラインに似ています。</span><span class="sxs-lookup"><span data-stu-id="faace-104">Because localizable resources can be referenced via certain objects as if they were properties, the naming guidelines for resources are similar to property guidelines.</span></span>

 <span data-ttu-id="faace-105">リソースキーでは、✔️の大文字と小文字の区別を使用します。</span><span class="sxs-lookup"><span data-stu-id="faace-105">✔️ DO use PascalCasing in resource keys.</span></span>

 <span data-ttu-id="faace-106">✔️は、短い識別子ではなく説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="faace-106">✔️ DO provide descriptive rather than short identifiers.</span></span>

 <span data-ttu-id="faace-107">❌ メインの CLR 言語の言語固有のキーワードは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="faace-107">❌ DO NOT use language-specific keywords of the main CLR languages.</span></span>

 <span data-ttu-id="faace-108">✔️リソースには英数字とアンダースコアのみを使用します。</span><span class="sxs-lookup"><span data-stu-id="faace-108">✔️ DO use only alphanumeric characters and underscores in naming resources.</span></span>

 <span data-ttu-id="faace-109">✔️例外メッセージリソースには、次の名前付け規則を使用します。</span><span class="sxs-lookup"><span data-stu-id="faace-109">✔️ DO use the following naming convention for exception message resources.</span></span>

 <span data-ttu-id="faace-110">リソース識別子は、例外の種類の名前に例外の短い識別子を加えたものにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="faace-110">The resource identifier should be the exception type name plus a short identifier of the exception:</span></span>

 <span data-ttu-id="faace-111">`ArgumentExceptionIllegalCharacters` `ArgumentExceptionInvalidName`</span><span class="sxs-lookup"><span data-stu-id="faace-111">`ArgumentExceptionIllegalCharacters` `ArgumentExceptionInvalidName`</span></span>
 `ArgumentExceptionFileNameIsMalformed`

 <span data-ttu-id="faace-112">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="faace-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="faace-113">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="faace-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="faace-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="faace-114">See also</span></span>

- [<span data-ttu-id="faace-115">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="faace-115">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="faace-116">名前付けのガイドライン</span><span class="sxs-lookup"><span data-stu-id="faace-116">Naming Guidelines</span></span>](naming-guidelines.md)
