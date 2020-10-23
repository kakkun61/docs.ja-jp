---
title: "'Module' ステートメントは、ファイルまたは名前空間レベルでのみ発生します。"
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: b946a527d3de3a030ac03691c77afcf440f518ee
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160315"
---
# <a name="bc30617-module-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="29e09-102">BC30617:'Module' ステートメントは、ファイルまたは名前空間レベルでのみ発生します。</span><span class="sxs-lookup"><span data-stu-id="29e09-102">BC30617: 'Module' statements can occur only at file or namespace level</span></span>

<span data-ttu-id="29e09-103">`Module` ステートメントは、ソース ファイルの先頭の、`Option` および `Imports` ステートメント、グローバル属性、および名前空間宣言の直後、ただし他のすべての宣言の前に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="29e09-103">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>

 <span data-ttu-id="29e09-104">**エラー ID:** BC30617</span><span class="sxs-lookup"><span data-stu-id="29e09-104">**Error ID:** BC30617</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="29e09-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="29e09-105">To correct this error</span></span>

- <span data-ttu-id="29e09-106">`Module` ステートメントを名前空間の宣言またはソース ファイルの先頭に移動します。</span><span class="sxs-lookup"><span data-stu-id="29e09-106">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>

## <a name="see-also"></a><span data-ttu-id="29e09-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="29e09-107">See also</span></span>

- [<span data-ttu-id="29e09-108">Module ステートメント</span><span class="sxs-lookup"><span data-stu-id="29e09-108">Module Statement</span></span>](../statements/module-statement.md)
