---
title: ルート名前空間 <namespacename> にある名前 <fullnamespacename> は CLS に準拠していません。
ms.date: 07/20/2015
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
ms.openlocfilehash: 48e020cb74641279a4f402e47034514d78dfc4fc
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160211"
---
# <a name="bc40039-name-namespacename-in-the-root-namespace-fullnamespacename-is-not-cls-compliant"></a><span data-ttu-id="0bb00-102">BC40039:ルート名前空間 \<namespacename> にある名前 \<fullnamespacename> は CLS に準拠していません。</span><span class="sxs-lookup"><span data-stu-id="0bb00-102">BC40039: Name \<namespacename> in the root namespace \<fullnamespacename> is not CLS-compliant</span></span>

<span data-ttu-id="0bb00-103">アセンブリが `<CLSCompliant(True)>` としてマークされているのに、ルート名前空間の名前の要素がアンダースコア (`_`) で始まっています。</span><span class="sxs-lookup"><span data-stu-id="0bb00-103">An assembly is marked as `<CLSCompliant(True)>`, but an element of the root namespace name begins with an underscore (`_`).</span></span>

 <span data-ttu-id="0bb00-104">プログラミング要素には 1 つ以上のアンダースコアを含めることができますが、[言語への非依存性、および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md) (CLS) に準拠するためには、先頭をアンダースコアにしてはなりません。</span><span class="sxs-lookup"><span data-stu-id="0bb00-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="0bb00-105">「 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0bb00-105">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

 <span data-ttu-id="0bb00-106">プログラミング要素に <xref:System.CLSCompliantAttribute> を適用する場合は、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定して、準拠または非準拠を示します。</span><span class="sxs-lookup"><span data-stu-id="0bb00-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="0bb00-107">このパラメーターには既定値がありません。値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bb00-107">There is no default for this parameter, and you must supply a value.</span></span>

 <span data-ttu-id="0bb00-108">要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。</span><span class="sxs-lookup"><span data-stu-id="0bb00-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>

 <span data-ttu-id="0bb00-109">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="0bb00-109">By default, this message is a warning.</span></span> <span data-ttu-id="0bb00-110">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0bb00-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="0bb00-111">**エラー ID:** BC40039</span><span class="sxs-lookup"><span data-stu-id="0bb00-111">**Error ID:** BC40039</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="0bb00-112">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="0bb00-112">To correct this error</span></span>

- <span data-ttu-id="0bb00-113">CLS 準拠にする必要がある場合は、ルート名前空間の名前を変更し、その要素がアンダースコアで始まらないようにします。</span><span class="sxs-lookup"><span data-stu-id="0bb00-113">If you require CLS compliance, change the root namespace name so that none of its elements begins with an underscore.</span></span>

- <span data-ttu-id="0bb00-114">名前空間の名前が変更されないようにする必要がある場合は、アセンブリから <xref:System.CLSCompliantAttribute> を削除するか、アセンブリを `<CLSCompliant(False)>` としてマークします。</span><span class="sxs-lookup"><span data-stu-id="0bb00-114">If you require that the namespace name remain unchanged, then remove the <xref:System.CLSCompliantAttribute> from the assembly or mark it as `<CLSCompliant(False)>`.</span></span>

## <a name="see-also"></a><span data-ttu-id="0bb00-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="0bb00-115">See also</span></span>

- [<span data-ttu-id="0bb00-116">Namespace ステートメント</span><span class="sxs-lookup"><span data-stu-id="0bb00-116">Namespace Statement</span></span>](../statements/namespace-statement.md)
- [<span data-ttu-id="0bb00-117">Visual Basic における名前空間</span><span class="sxs-lookup"><span data-stu-id="0bb00-117">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="0bb00-118">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="0bb00-118">-rootnamespace</span></span>](../../reference/command-line-compiler/rootnamespace.md)
- <span data-ttu-id="0bb00-119">[[アプリケーション] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="0bb00-119">[Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)</span></span>
- [<span data-ttu-id="0bb00-120">宣言された要素の名前</span><span class="sxs-lookup"><span data-stu-id="0bb00-120">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="0bb00-121">Visual Basic の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="0bb00-121">Visual Basic Naming Conventions</span></span>](../../programming-guide/program-structure/naming-conventions.md)
