---
title: フィールドのデザイン
ms.date: 10/22/2008
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
ms.openlocfilehash: 6e58274f32ea129d3271c11e321bdbd454d2406a
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821113"
---
# <a name="field-design"></a><span data-ttu-id="50e59-102">フィールドのデザイン</span><span class="sxs-lookup"><span data-stu-id="50e59-102">Field Design</span></span>
<span data-ttu-id="50e59-103">カプセル化の原則は、オブジェクト指向設計で最も重要な概念の1つです。</span><span class="sxs-lookup"><span data-stu-id="50e59-103">The principle of encapsulation is one of the most important notions in object-oriented design.</span></span> <span data-ttu-id="50e59-104">この原則は、オブジェクト内に格納されているデータが、そのオブジェクトに対してのみアクセスできる必要があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="50e59-104">This principle states that data stored inside an object should be accessible only to that object.</span></span>

 <span data-ttu-id="50e59-105">原則を解釈するには、型のメンバーに対して以外のコードを中断することなく、その型のフィールドに対する変更 (名前または型の変更) を行うことができるように、型を設計する必要があるという方法があります。</span><span class="sxs-lookup"><span data-stu-id="50e59-105">A useful way to interpret the principle is to say that a type should be designed so that changes to fields of that type (name or type changes) can be made without breaking code other than for members of the type.</span></span> <span data-ttu-id="50e59-106">この解釈は、すべてのフィールドをプライベートにする必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="50e59-106">This interpretation immediately implies that all fields must be private.</span></span>

 <span data-ttu-id="50e59-107">この厳格な制限から、定数および静的な読み取り専用フィールドを除外します。このようなフィールドは、ほとんどの場合定義によって変更する必要がないためです。</span><span class="sxs-lookup"><span data-stu-id="50e59-107">We exclude constant and static read-only fields from this strict restriction, because such fields, almost by definition, are never required to change.</span></span>

 <span data-ttu-id="50e59-108">❌ パブリックまたは保護されているインスタンスフィールドは指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="50e59-108">❌ DO NOT provide instance fields that are public or protected.</span></span>

 <span data-ttu-id="50e59-109">フィールドにアクセスするためのプロパティは、パブリックまたは保護するのではなく、指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="50e59-109">You should provide properties for accessing fields instead of making them public or protected.</span></span>

 <span data-ttu-id="50e59-110">変化しない定数には定数フィールドを使用✔️ます。</span><span class="sxs-lookup"><span data-stu-id="50e59-110">✔️ DO use constant fields for constants that will never change.</span></span>

 <span data-ttu-id="50e59-111">コンパイラは、const フィールドの値を直接呼び出しコードに焼きます。</span><span class="sxs-lookup"><span data-stu-id="50e59-111">The compiler burns the values of const fields directly into calling code.</span></span> <span data-ttu-id="50e59-112">そのため、互換性を損なうことなく const 値を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="50e59-112">Therefore, const values can never be changed without the risk of breaking compatibility.</span></span>

 <span data-ttu-id="50e59-113">`readonly`定義済みのオブジェクトインスタンスには、パブリック静的フィールドを使用✔️ます。</span><span class="sxs-lookup"><span data-stu-id="50e59-113">✔️ DO use public static `readonly` fields for predefined object instances.</span></span>

 <span data-ttu-id="50e59-114">型の定義済みのインスタンスがある場合は、型自体のパブリック読み取り専用の静的フィールドとして宣言します。</span><span class="sxs-lookup"><span data-stu-id="50e59-114">If there are predefined instances of the type, declare them as public read-only static fields of the type itself.</span></span>

 <span data-ttu-id="50e59-115">❌ 変更可能な型のインスタンスをフィールドに割り当てないでください `readonly` 。</span><span class="sxs-lookup"><span data-stu-id="50e59-115">❌ DO NOT assign instances of mutable types to `readonly` fields.</span></span>

 <span data-ttu-id="50e59-116">変更可能な型は、インスタンス化された後に変更できるインスタンスを持つ型です。</span><span class="sxs-lookup"><span data-stu-id="50e59-116">A mutable type is a type with instances that can be modified after they are instantiated.</span></span> <span data-ttu-id="50e59-117">たとえば、配列、ほとんどのコレクション、およびストリームは変更可能な型ですが、、、 <xref:System.Int32?displayProperty=nameWithType> <xref:System.Uri?displayProperty=nameWithType> および <xref:System.String?displayProperty=nameWithType> はすべて変更できません。</span><span class="sxs-lookup"><span data-stu-id="50e59-117">For example, arrays, most collections, and streams are mutable types, but <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, and <xref:System.String?displayProperty=nameWithType> are all immutable.</span></span> <span data-ttu-id="50e59-118">参照型フィールドの読み取り専用修飾子は、フィールドに格納されているインスタンスを置換しないようにします。ただし、インスタンスを変更する呼び出し元のメンバーによって、フィールドのインスタンスデータが変更されるのを防ぐことはできません。</span><span class="sxs-lookup"><span data-stu-id="50e59-118">The read-only modifier on a reference type field prevents the instance stored in the field from being replaced, but it does not prevent the field’s instance data from being modified by calling members changing the instance.</span></span>

 <span data-ttu-id="50e59-119">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="50e59-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="50e59-120">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="50e59-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="50e59-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="50e59-121">See also</span></span>

- [<span data-ttu-id="50e59-122">メンバーデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="50e59-122">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="50e59-123">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="50e59-123">Framework Design Guidelines</span></span>](index.md)
