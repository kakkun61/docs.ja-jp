---
title: 省略可能な引数には、既定値を指定する必要があります。
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: 3718fe5c42c8af0948f3b5cb0d120c6876c6f98f
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162454"
---
# <a name="bc30812-optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="51b9e-102">BC30812:省略可能な引数には、既定値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="51b9e-102">BC30812: Optional parameters must specify a default value</span></span>

<span data-ttu-id="51b9e-103">省略可能なパラメーターには、呼び出し元のプロシージャによってパラメーターが指定されていない場合に使用できる既定値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="51b9e-103">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>

<span data-ttu-id="51b9e-104">**エラー ID:** BC30812</span><span class="sxs-lookup"><span data-stu-id="51b9e-104">**Error ID:** BC30812</span></span>

## <a name="example"></a><span data-ttu-id="51b9e-105">例</span><span class="sxs-lookup"><span data-stu-id="51b9e-105">Example</span></span>

<span data-ttu-id="51b9e-106">次の例では BC30812 が生成されます。</span><span class="sxs-lookup"><span data-stu-id="51b9e-106">The following example generates BC30812:</span></span>

```vb
Sub Proc1(x As Integer, Optional y As String)
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="to-correct-this-error"></a><span data-ttu-id="51b9e-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="51b9e-107">To correct this error</span></span>

<span data-ttu-id="51b9e-108">省略可能なパラメーターの既定値を指定します。</span><span class="sxs-lookup"><span data-stu-id="51b9e-108">Specify default values for optional parameters:</span></span>

```vb
Sub Proc1(x As Integer, Optional y As String = "Default Value")
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="see-also"></a><span data-ttu-id="51b9e-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="51b9e-109">See also</span></span>

- [<span data-ttu-id="51b9e-110">Optional</span><span class="sxs-lookup"><span data-stu-id="51b9e-110">Optional</span></span>](../modifiers/optional.md)
