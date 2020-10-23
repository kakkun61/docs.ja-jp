---
title: 遅延バインドの解決です。ランタイム エラーが発生する可能性があります。
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: ef0fa295cadaaa0550be4809ec97c6da13b5e2db
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160432"
---
# <a name="bc42017-late-bound-resolution-runtime-errors-could-occur"></a><span data-ttu-id="e0a06-102">BC42017:遅延バインドの解決です。ランタイム エラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e0a06-102">BC42017: Late bound resolution; runtime errors could occur</span></span>

<span data-ttu-id="e0a06-103">オブジェクトは、[Object データ型](../data-types/object-data-type.md)として宣言された変数に代入されます。</span><span class="sxs-lookup"><span data-stu-id="e0a06-103">An object is assigned to a variable declared to be of the [Object Data Type](../data-types/object-data-type.md).</span></span>

 <span data-ttu-id="e0a06-104">変数を `Object` として宣言した場合、コンパイラでは*遅延バインディング*を実行する必要があり、これによって実行時に余分な処理が発生します。</span><span class="sxs-lookup"><span data-stu-id="e0a06-104">When you declare a variable as `Object`, the compiler must perform *late binding*, which causes extra operations at run time.</span></span> <span data-ttu-id="e0a06-105">また、アプリケーションで実行時エラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e0a06-105">It also exposes your application to potential run-time errors.</span></span> <span data-ttu-id="e0a06-106">たとえば、`Object` 変数に <xref:System.Windows.Forms.Form> を代入し、<xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> プロパティにアクセスしようとすると、<xref:System.Windows.Forms.Form> クラスが `NameTable` プロパティを公開しないため、ランタイムで <xref:System.MemberAccessException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="e0a06-106">For example, if you assign a <xref:System.Windows.Forms.Form> to the `Object` variable and then try to access the <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> property, the runtime throws a <xref:System.MemberAccessException> because the <xref:System.Windows.Forms.Form> class does not expose a `NameTable` property.</span></span>

 <span data-ttu-id="e0a06-107">変数を特定の型として宣言する場合、コンパイラではコンパイル時に*事前バインディング*を実行できます。</span><span class="sxs-lookup"><span data-stu-id="e0a06-107">If you declare the variable to be of a specific type, the compiler can perform *early binding* at compile time.</span></span> <span data-ttu-id="e0a06-108">これにより、パフォーマンスが向上し、特定の型のメンバーへのアクセスが制御され、コードが読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="e0a06-108">This results in improved performance, controlled access to the members of the specific type, and better readability of your code.</span></span>

 <span data-ttu-id="e0a06-109">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="e0a06-109">By default, this message is a warning.</span></span> <span data-ttu-id="e0a06-110">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e0a06-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="e0a06-111">**エラー ID:** BC42017</span><span class="sxs-lookup"><span data-stu-id="e0a06-111">**Error ID:** BC42017</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="e0a06-112">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="e0a06-112">To correct this error</span></span>

- <span data-ttu-id="e0a06-113">可能であれば、変数を特定の型として宣言します。</span><span class="sxs-lookup"><span data-stu-id="e0a06-113">If possible, declare the variable to be of a specific type.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0a06-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="e0a06-114">See also</span></span>

- [<span data-ttu-id="e0a06-115">事前バインディングと遅延バインディング</span><span class="sxs-lookup"><span data-stu-id="e0a06-115">Early and Late Binding</span></span>](../../programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="e0a06-116">オブジェクト変数の宣言</span><span class="sxs-lookup"><span data-stu-id="e0a06-116">Object Variable Declaration</span></span>](../../programming-guide/language-features/variables/object-variable-declaration.md)
