---
title: "'<functionname>' は宣言されていません (スマート デバイスおよび Visual Basic コンパイラ エラー)"
ms.date: 07/20/2015
f1_keywords:
- bc30766
- vbc30766
helpviewer_keywords:
- BC30766
ms.assetid: 13918600-6087-40d7-8134-32aa9d3bfda4
ms.openlocfilehash: 1c57e1aaea2eb52133d37b782f8fa0ddd96943a9
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163403"
---
# <a name="bc30766-functionname-is-not-declared-smart-devicevisual-basic-compiler-error"></a><span data-ttu-id="1dbb6-102">BC30766: '\<functionname>' は宣言されていません (スマート デバイスおよび Visual Basic コンパイラ エラー)</span><span class="sxs-lookup"><span data-stu-id="1dbb6-102">BC30766: '\<functionname>' is not declared (Smart Device/Visual Basic Compiler Error)</span></span>

<span data-ttu-id="1dbb6-103"><`functionname`> が宣言されていません。</span><span class="sxs-lookup"><span data-stu-id="1dbb6-103"><`functionname`> is not declared.</span></span> <span data-ttu-id="1dbb6-104">通常、ファイル I/O 機能は `Microsoft.VisualBasic` 名前空間で使用できますが、.NET Compact Framework のターゲット バージョンではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="1dbb6-104">File I/O functionality is normally available in the `Microsoft.VisualBasic` namespace, but the targeted version of the .NET Compact Framework does not support it.</span></span>

 <span data-ttu-id="1dbb6-105">**エラー ID:** BC30766</span><span class="sxs-lookup"><span data-stu-id="1dbb6-105">**Error ID:** BC30766</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="1dbb6-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="1dbb6-106">To correct this error</span></span>

- <span data-ttu-id="1dbb6-107">`System.IO` 名前空間で定義された関数を使用して、ファイル操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="1dbb6-107">Perform file operations with functions defined in the `System.IO` namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="1dbb6-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="1dbb6-108">See also</span></span>

- <xref:System.IO>
- [<span data-ttu-id="1dbb6-109">Visual Basic におけるファイル アクセス</span><span class="sxs-lookup"><span data-stu-id="1dbb6-109">File Access with Visual Basic</span></span>](../../developing-apps/programming/drives-directories-files/file-access.md)
