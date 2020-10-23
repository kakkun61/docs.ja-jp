---
title: メソッド '<methodname>' には、同じシグネチャを持つ複数の定義が含まれています。
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: 663b22421d1a0e401cfb3c135c99bd097163a78b
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160367"
---
# <a name="bc30269-methodname-has-multiple-definitions-with-identical-signatures"></a><span data-ttu-id="69001-102">BC30269: メソッド "\<methodname>" には、同じシグネチャを持つ複数の定義が含まれています。</span><span class="sxs-lookup"><span data-stu-id="69001-102">BC30269: '\<methodname>' has multiple definitions with identical signatures</span></span>

<span data-ttu-id="69001-103">`Function` または `Sub` プロシージャ宣言で、前の宣言と同じプロシージャ名と引数リストを使用しています。</span><span class="sxs-lookup"><span data-stu-id="69001-103">A `Function` or `Sub` procedure declaration uses the identical procedure name and argument list as a previous declaration.</span></span> <span data-ttu-id="69001-104">考えられる原因の 1 つは、元のプロシージャをオーバーロードしようとしたことです。</span><span class="sxs-lookup"><span data-stu-id="69001-104">One possible cause is an attempt to overload the original procedure.</span></span> <span data-ttu-id="69001-105">オーバーロードされたプロシージャには、異なる引数リストが必要です。</span><span class="sxs-lookup"><span data-stu-id="69001-105">Overloaded procedures must have different argument lists.</span></span>

 <span data-ttu-id="69001-106">**エラー ID:** BC30269</span><span class="sxs-lookup"><span data-stu-id="69001-106">**Error ID:** BC30269</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="69001-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="69001-107">To correct this error</span></span>

- <span data-ttu-id="69001-108">プロシージャ名または引数リストを変更するか、または重複する宣言を削除します。</span><span class="sxs-lookup"><span data-stu-id="69001-108">Change the procedure name or the argument list, or remove the duplicate declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="69001-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="69001-109">See also</span></span>

- [<span data-ttu-id="69001-110">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="69001-110">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="69001-111">プロシージャのオーバーロードに関する注意事項</span><span class="sxs-lookup"><span data-stu-id="69001-111">Considerations in Overloading Procedures</span></span>](../../programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)
