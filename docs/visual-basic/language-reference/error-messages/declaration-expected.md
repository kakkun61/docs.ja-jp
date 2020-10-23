---
title: 宣言が必要です。
ms.date: 07/20/2015
f1_keywords:
- vbc30188
- bc30188
helpviewer_keywords:
- BC30188
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
ms.openlocfilehash: 2755f5afcb96ca7a6c4d140908649390dd66d571
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162701"
---
# <a name="bc30188-declaration-expected"></a><span data-ttu-id="314a6-102">BC30188:宣言が必要です。</span><span class="sxs-lookup"><span data-stu-id="314a6-102">BC30188: Declaration expected</span></span>

<span data-ttu-id="314a6-103">代入ステートメントやループ ステートメントなどの非宣言ステートメントが、プロシージャの外側に記述されています。</span><span class="sxs-lookup"><span data-stu-id="314a6-103">A nondeclarative statement, such as an assignment or loop statement, occurs outside any procedure.</span></span> <span data-ttu-id="314a6-104">プロシージャの外側で許可されるのは宣言のみです。</span><span class="sxs-lookup"><span data-stu-id="314a6-104">Only declarations are allowed outside procedures.</span></span>

 <span data-ttu-id="314a6-105">または、プログラミング要素が、`Dim` や `Const` などの宣言キーワードを使用せずに宣言されています。</span><span class="sxs-lookup"><span data-stu-id="314a6-105">Alternatively, a programming element is declared without a declaration keyword such as `Dim` or `Const`.</span></span>

 <span data-ttu-id="314a6-106">**エラー ID:** BC30188</span><span class="sxs-lookup"><span data-stu-id="314a6-106">**Error ID:** BC30188</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="314a6-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="314a6-107">To correct this error</span></span>

- <span data-ttu-id="314a6-108">非宣言ステートメントをプロシージャの本体に移動します。</span><span class="sxs-lookup"><span data-stu-id="314a6-108">Move the nondeclarative statement to the body of a procedure.</span></span>

- <span data-ttu-id="314a6-109">適切な宣言キーワードを使用して、宣言を開始します。</span><span class="sxs-lookup"><span data-stu-id="314a6-109">Begin the declaration with an appropriate declaration keyword.</span></span>

- <span data-ttu-id="314a6-110">宣言キーワードのスペルが間違っていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="314a6-110">Ensure that a declaration keyword is not misspelled.</span></span>

## <a name="see-also"></a><span data-ttu-id="314a6-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="314a6-111">See also</span></span>

- [<span data-ttu-id="314a6-112">手順</span><span class="sxs-lookup"><span data-stu-id="314a6-112">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="314a6-113">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="314a6-113">Dim Statement</span></span>](../statements/dim-statement.md)
