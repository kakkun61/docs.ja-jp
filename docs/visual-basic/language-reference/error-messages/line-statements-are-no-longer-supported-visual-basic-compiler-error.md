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
# <a name="bc30830-line-statements-are-no-longer-supported"></a>BC30830:'Line' ステートメントは現在サポートされていません

Line ステートメントは現在サポートされていません。 ファイル I/O 機能は `Microsoft.VisualBasic.FileSystem.LineInput` として使用でき、グラフィックス機能は `System.Drawing.Graphics.DrawLine` として使用できます。

 **エラー ID:** BC30830

## <a name="to-correct-this-error"></a>このエラーを解決するには

- ファイル アクセスを実行する場合は、`Microsoft.VisualBasic.FileSystem.LineInput` を使用します。

- グラフィックス処理を行っている場合は、 `System.Drawing.Graphics.Drawline`を使用します。

## <a name="see-also"></a>関連項目

- <xref:System.IO>
- <xref:System.Drawing>
- [Visual Basic におけるファイル アクセス](../../developing-apps/programming/drives-directories-files/file-access.md)
