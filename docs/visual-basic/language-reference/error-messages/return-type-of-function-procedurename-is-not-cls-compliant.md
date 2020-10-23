---
title: 関数 '<procedurename>' の戻り値の型は CLS に準拠していません。
ms.date: 07/20/2015
f1_keywords:
- bc40027
- vbc40027
helpviewer_keywords:
- BC40027
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
ms.openlocfilehash: 9a877046a1b30e2e3773a41b8b44573e11ff1c96
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159704"
---
# <a name="bc40027-return-type-of-function-procedurename-is-not-cls-compliant"></a><span data-ttu-id="4eadb-102">BC40027:関数 '\<procedurename>' の戻り値の型は CLS に準拠していません。</span><span class="sxs-lookup"><span data-stu-id="4eadb-102">BC40027: Return type of function '\<procedurename>' is not CLS-compliant</span></span>

<span data-ttu-id="4eadb-103">`Function` プロシージャが `<CLSCompliant(True)>` としてマークされていますが、`<CLSCompliant(False)>` としてマークされている型、マークされていない型、または非準拠の型であるために修飾されていない型を返します。</span><span class="sxs-lookup"><span data-stu-id="4eadb-103">A `Function` procedure is marked as `<CLSCompliant(True)>` but returns a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>

 <span data-ttu-id="4eadb-104">プロシージャを[言語への非依存性および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md) (CLS) に準拠させるには、CLS 準拠型のみを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4eadb-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="4eadb-105">これは、パラメーターの型、戻り値の型、およびすべてのローカル変数の型に適用されます。</span><span class="sxs-lookup"><span data-stu-id="4eadb-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>

 <span data-ttu-id="4eadb-106">次の Visual Basic データ型は CLS に準拠していません。</span><span class="sxs-lookup"><span data-stu-id="4eadb-106">The following Visual Basic data types are not CLS-compliant:</span></span>

- [<span data-ttu-id="4eadb-107">SByte データ型</span><span class="sxs-lookup"><span data-stu-id="4eadb-107">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)

- [<span data-ttu-id="4eadb-108">UInteger データ型</span><span class="sxs-lookup"><span data-stu-id="4eadb-108">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)

- [<span data-ttu-id="4eadb-109">ULong データ型</span><span class="sxs-lookup"><span data-stu-id="4eadb-109">ULong Data Type</span></span>](../data-types/ulong-data-type.md)

- [<span data-ttu-id="4eadb-110">UShort データ型</span><span class="sxs-lookup"><span data-stu-id="4eadb-110">UShort Data Type</span></span>](../data-types/ushort-data-type.md)

 <span data-ttu-id="4eadb-111">プログラミング要素に <xref:System.CLSCompliantAttribute> を適用する場合は、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定して、準拠または非準拠を示します。</span><span class="sxs-lookup"><span data-stu-id="4eadb-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="4eadb-112">このパラメーターには既定値がありません。値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4eadb-112">There is no default for this parameter, and you must supply a value.</span></span>

 <span data-ttu-id="4eadb-113">要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。</span><span class="sxs-lookup"><span data-stu-id="4eadb-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>

 <span data-ttu-id="4eadb-114">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="4eadb-114">By default, this message is a warning.</span></span> <span data-ttu-id="4eadb-115">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4eadb-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="4eadb-116">**エラー ID:** BC40027</span><span class="sxs-lookup"><span data-stu-id="4eadb-116">**Error ID:** BC40027</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="4eadb-117">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="4eadb-117">To correct this error</span></span>

- <span data-ttu-id="4eadb-118">`Function` プロシージャがこの特定の型を返す必要がある場合は、<xref:System.CLSCompliantAttribute> を削除します。</span><span class="sxs-lookup"><span data-stu-id="4eadb-118">If the `Function` procedure must return this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="4eadb-119">プロシージャは CLS 準拠になりません。</span><span class="sxs-lookup"><span data-stu-id="4eadb-119">The procedure cannot be CLS-compliant.</span></span>

- <span data-ttu-id="4eadb-120">`Function` プロシージャを CLS 準拠にする必要がある場合は、戻り値の型を最も近い CLS 準拠型に変更します。</span><span class="sxs-lookup"><span data-stu-id="4eadb-120">If the `Function` procedure must be CLS-compliant, change the return type to the closest CLS-compliant type.</span></span> <span data-ttu-id="4eadb-121">たとえば、2,147,483,647 を超える値の範囲が不要な場合は、 `UInteger` の代わりに `Integer` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="4eadb-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="4eadb-122">拡張範囲が必要な場合は、 `UInteger` の代わりに `Long`を使用できます。</span><span class="sxs-lookup"><span data-stu-id="4eadb-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>

- <span data-ttu-id="4eadb-123">オートメーション オブジェクトや COM オブジェクトとやり取りする場合は、一部の型のデータ幅が .NET Framework とは異なることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4eadb-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="4eadb-124">たとえば、他の多くの環境では `int` は 16 ビットです。</span><span class="sxs-lookup"><span data-stu-id="4eadb-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="4eadb-125">このようなコンポーネントに 16 ビット整数を返す場合、Visual Basic のマネージド コードでは、`Integer` ではなく `Short` を宣言してください。</span><span class="sxs-lookup"><span data-stu-id="4eadb-125">If you are returning a 16-bit integer to such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>
