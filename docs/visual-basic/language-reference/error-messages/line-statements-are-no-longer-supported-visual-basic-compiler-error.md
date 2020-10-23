---
title: "'Line' ステートメントはサポートされていません (Visual Basic コンパイラ エラー)"
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: f34095becf321c6cb4b316b6378a2da0107577ba
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162480"
---
# <a name="bc30830-line-statements-are-no-longer-supported"></a><span data-ttu-id="88f74-102">BC30830:'Line' ステートメントは現在サポートされていません</span><span class="sxs-lookup"><span data-stu-id="88f74-102">BC30830: 'Line' statements are no longer supported</span></span>

<span data-ttu-id="88f74-103">Line ステートメントは現在サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="88f74-103">Line statements are no longer supported.</span></span> <span data-ttu-id="88f74-104">ファイル I/O 機能は `Microsoft.VisualBasic.FileSystem.LineInput` として使用でき、グラフィックス機能は `System.Drawing.Graphics.DrawLine` として使用できます。</span><span class="sxs-lookup"><span data-stu-id="88f74-104">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>

 <span data-ttu-id="88f74-105">**エラー ID:** BC30830</span><span class="sxs-lookup"><span data-stu-id="88f74-105">**Error ID:** BC30830</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="88f74-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="88f74-106">To correct this error</span></span>

- <span data-ttu-id="88f74-107">ファイル アクセスを実行する場合は、`Microsoft.VisualBasic.FileSystem.LineInput` を使用します。</span><span class="sxs-lookup"><span data-stu-id="88f74-107">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>

- <span data-ttu-id="88f74-108">グラフィックス処理を行っている場合は、 `System.Drawing.Graphics.Drawline`を使用します。</span><span class="sxs-lookup"><span data-stu-id="88f74-108">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>

## <a name="see-also"></a><span data-ttu-id="88f74-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="88f74-109">See also</span></span>

- <xref:System.IO>
- <xref:System.Drawing>
- [<span data-ttu-id="88f74-110">Visual Basic におけるファイル アクセス</span><span class="sxs-lookup"><span data-stu-id="88f74-110">File Access with Visual Basic</span></span>](../../developing-apps/programming/drives-directories-files/file-access.md)
