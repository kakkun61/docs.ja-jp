---
title: "'#Region' および '#End Region' ステートメントは、メソッド本体や複数行ラムダの内部では有効ではありません。"
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: c792fa1a42bde22959ae21439cb2a0a1e4be343f
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162285"
---
# <a name="bc32025-region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="def2b-102">BC32025: '#Region' および '#End Region' ステートメントは、メソッド本体や複数行ラムダの内部では有効ではありません</span><span class="sxs-lookup"><span data-stu-id="def2b-102">BC32025: '#Region' and '#End Region' statements are not valid within method bodies/multiline lambdas</span></span>

<span data-ttu-id="def2b-103">`#Region` ブロックは、クラス、モジュール、または名前空間レベルで宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="def2b-103">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="def2b-104">折りたたみ可能な領域には 1 つ以上のプロシージャを含めることができますが、プロシージャの内部で開始または終了することはできません。</span><span class="sxs-lookup"><span data-stu-id="def2b-104">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>

 <span data-ttu-id="def2b-105">**エラー ID:** BC32025</span><span class="sxs-lookup"><span data-stu-id="def2b-105">**Error ID:** BC32025</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="def2b-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="def2b-106">To correct this error</span></span>

1. <span data-ttu-id="def2b-107">前の手順が `End Function` または `End Sub` ステートメントで適切に終了していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="def2b-107">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>

2. <span data-ttu-id="def2b-108">`#Region` ディレクティブと `#End Region` ディレクティブが同じコード ブロック内にあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="def2b-108">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>

## <a name="see-also"></a><span data-ttu-id="def2b-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="def2b-109">See also</span></span>

- [<span data-ttu-id="def2b-110">#Region ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="def2b-110">#Region Directive</span></span>](../directives/region-directive.md)
