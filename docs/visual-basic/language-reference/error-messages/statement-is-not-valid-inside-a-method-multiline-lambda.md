---
title: メソッドや複数行のラムダの内部では有効でないステートメントです。
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: cef992c3eaa2b82bbf5e8993f9fccd64ae388c95
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159678"
---
# <a name="bc30024-statement-is-not-valid-inside-a-methodmultiline-lambda"></a><span data-ttu-id="10e2b-102">BC30024:メソッドや複数行のラムダの内部では有効でないステートメントです。</span><span class="sxs-lookup"><span data-stu-id="10e2b-102">BC30024: Statement is not valid inside a method/multiline lambda</span></span>

<span data-ttu-id="10e2b-103">ステートメントは、`Sub`、`Function`、プロパティ `Get`、またはプロパティ `Set` プロシージャ内で無効です。</span><span class="sxs-lookup"><span data-stu-id="10e2b-103">The statement is not valid within a `Sub`, `Function`, property `Get`, or property `Set` procedure.</span></span> <span data-ttu-id="10e2b-104">一部のステートメントは、モジュール レベルまたはクラス レベルで配置できます。</span><span class="sxs-lookup"><span data-stu-id="10e2b-104">Some statements can be placed at the module or class level.</span></span> <span data-ttu-id="10e2b-105">`Option Strict` などの他のものは、名前空間レベルで、他のすべての宣言の前に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="10e2b-105">Others, such as `Option Strict`, must be at namespace level and precede all other declarations.</span></span>

 <span data-ttu-id="10e2b-106">**エラー ID:** BC30024</span><span class="sxs-lookup"><span data-stu-id="10e2b-106">**Error ID:** BC30024</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="10e2b-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="10e2b-107">To correct this error</span></span>

- <span data-ttu-id="10e2b-108">プロシージャからステートメントを削除します。</span><span class="sxs-lookup"><span data-stu-id="10e2b-108">Remove the statement from the procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="10e2b-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="10e2b-109">See also</span></span>

- [<span data-ttu-id="10e2b-110">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="10e2b-110">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="10e2b-111">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="10e2b-111">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="10e2b-112">Get ステートメント</span><span class="sxs-lookup"><span data-stu-id="10e2b-112">Get Statement</span></span>](../statements/get-statement.md)
- [<span data-ttu-id="10e2b-113">Set ステートメント</span><span class="sxs-lookup"><span data-stu-id="10e2b-113">Set Statement</span></span>](../statements/set-statement.md)
