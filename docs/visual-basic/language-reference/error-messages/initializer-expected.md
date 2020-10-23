---
title: 初期化子が必要です
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: cbe77bab3e4f8bf2094c70c1c16d95ee897c729e
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163013"
---
# <a name="bc30996-initializer-expected"></a><span data-ttu-id="c6e69-102">BC30996:初期化子が必要です</span><span class="sxs-lookup"><span data-stu-id="c6e69-102">BC30996: Initializer expected</span></span>

<span data-ttu-id="c6e69-103">次の例に示すように、初期化リストが空のオブジェクト初期化子を使用して、クラスのインスタンスを宣言しようとしました。</span><span class="sxs-lookup"><span data-stu-id="c6e69-103">You have tried to declare an instance of a class by using an object initializer in which the initialization list is empty, as shown in the following example.</span></span>

 `' Not valid.`

 `' Dim aStudent As New Student With {}`

 <span data-ttu-id="c6e69-104">次の例に示すように、初期化子リストの少なくとも 1 つのフィールドまたはプロパティを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6e69-104">At least one field or property must be initialized in the initializer list, as shown in the following example.</span></span>

 `Dim aStudent As New Student With {.year = "Senior"}`

 <span data-ttu-id="c6e69-105">**エラー ID:** BC30996</span><span class="sxs-lookup"><span data-stu-id="c6e69-105">**Error ID:** BC30996</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="c6e69-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="c6e69-106">To correct this error</span></span>

- <span data-ttu-id="c6e69-107">初期化子の少なくとも 1 つのフィールドまたはプロパティを初期化するか、オブジェクト初期化子を使用しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="c6e69-107">Initialize at least one field or property in the initializer, or do not use an object initializer.</span></span>

## <a name="see-also"></a><span data-ttu-id="c6e69-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="c6e69-108">See also</span></span>

- [<span data-ttu-id="c6e69-109">オブジェクト初期化子: 名前付きの型と匿名型</span><span class="sxs-lookup"><span data-stu-id="c6e69-109">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="c6e69-110">方法: オブジェクト初期化子を使用してオブジェクトを宣言する</span><span class="sxs-lookup"><span data-stu-id="c6e69-110">How to: Declare an Object by Using an Object Initializer</span></span>](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
