---
title: "'<membername>' は、継承インターフェイス '<interfacename1>' および '<interfacename2>' 間ではあいまいです。"
ms.date: 07/20/2015
f1_keywords:
- vbc30685
- bc30685
helpviewer_keywords:
- BC30685
ms.assetid: 756add7a-23d5-4b4f-a48d-8297d6459c73
ms.openlocfilehash: f666bf380f8b94c50c2bc5fd865b37d96e92991f
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162441"
---
# <a name="bc30685-membername-is-ambiguous-across-the-inherited-interfaces-interfacename1-and-interfacename2"></a><span data-ttu-id="4d5f5-102">BC30685: '\<membername>' は、継承インターフェイス '\<interfacename1>' および '\<interfacename2>' 間ではあいまいです</span><span class="sxs-lookup"><span data-stu-id="4d5f5-102">BC30685: '\<membername>' is ambiguous across the inherited interfaces '\<interfacename1>' and '\<interfacename2>'</span></span>

<span data-ttu-id="4d5f5-103">このインターフェイスは、複数のインターフェイスからの同じ名前を持つ複数のメンバーを継承しています。</span><span class="sxs-lookup"><span data-stu-id="4d5f5-103">The interface inherits two or more members with the same name from multiple interfaces.</span></span>

 <span data-ttu-id="4d5f5-104">**エラー ID:** BC30685</span><span class="sxs-lookup"><span data-stu-id="4d5f5-104">**Error ID:** BC30685</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="4d5f5-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="4d5f5-105">To correct this error</span></span>

- <span data-ttu-id="4d5f5-106">使用する基底インターフェイスに値をキャストします。たとえば、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="4d5f5-106">Cast the value to the base interface that you want to use; for example:</span></span>

    ```vb
    Interface Left
        Sub MySub()
    End Interface

    Interface Right
        Sub MySub()
    End Interface

    Interface LeftRight
        Inherits Left, Right
    End Interface

    Module test
        Sub Main()
            Dim x As LeftRight
            ' x.MySub()  'x is ambiguous.
            CType(x, Left).MySub() ' Cast to base type.
            CType(x, Right).MySub() ' Call the other base type.
        End Sub
    End Module
    ```

## <a name="see-also"></a><span data-ttu-id="4d5f5-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="4d5f5-107">See also</span></span>

- [<span data-ttu-id="4d5f5-108">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4d5f5-108">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
