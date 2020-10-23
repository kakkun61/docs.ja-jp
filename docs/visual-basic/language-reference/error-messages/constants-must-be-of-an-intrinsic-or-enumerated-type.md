---
title: 定数は、class、structure、または array 型ではなく、組み込み型または列挙型でなければなりません。
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: e820287f0ddf462b30867d90501f7d730c9c6739
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163156"
---
# <a name="bc30424-constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a><span data-ttu-id="90375-102">BC30424:定数は、class、structure、または array 型ではなく、組み込み型または列挙型でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="90375-102">BC30424: Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type</span></span>

<span data-ttu-id="90375-103">定数をクラス、構造体、または配列型として宣言しようとしたか、格納先のジェネリック型によって定義された型パラメーターとして宣言しようとしました。</span><span class="sxs-lookup"><span data-stu-id="90375-103">You have attempted to declare a constant as a class, structure, or array type, or as a type parameter defined by a containing generic type.</span></span>

 <span data-ttu-id="90375-104">定数は、組み込み型 (`Boolean`、`Byte`、`Date`、`Decimal`、`Double`、`Integer`、`Long`、`Object`、`SByte`、`Short`、`Single`、`String`、`UInteger`、`ULong`、または `UShort`)、または整数型のいずれかに基づいた `Enum` 型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="90375-104">Constants must be of an intrinsic type (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, or `UShort`), or an `Enum` type based on one of the integral types.</span></span>

 <span data-ttu-id="90375-105">**エラー ID:** BC30424</span><span class="sxs-lookup"><span data-stu-id="90375-105">**Error ID:** BC30424</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="90375-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="90375-106">To correct this error</span></span>

1. <span data-ttu-id="90375-107">定数を組み込み型または `Enum` 型として宣言します。</span><span class="sxs-lookup"><span data-stu-id="90375-107">Declare the constant as an intrinsic or `Enum` type.</span></span>

2. <span data-ttu-id="90375-108">定数は、`True`、`False`、`Nothing` などの特別な値でもかまいません。</span><span class="sxs-lookup"><span data-stu-id="90375-108">A constant can also be a special value such as `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="90375-109">コンパイラは、これらの定義済みの値を適切な組み込み型と見なします。</span><span class="sxs-lookup"><span data-stu-id="90375-109">The compiler considers these predefined values to be of the appropriate intrinsic type.</span></span>

## <a name="see-also"></a><span data-ttu-id="90375-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="90375-110">See also</span></span>

- [<span data-ttu-id="90375-111">定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="90375-111">Constants and Enumerations</span></span>](../constants-and-enumerations.md)
- [<span data-ttu-id="90375-112">データの種類</span><span class="sxs-lookup"><span data-stu-id="90375-112">Data Types</span></span>](../../programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="90375-113">データの種類</span><span class="sxs-lookup"><span data-stu-id="90375-113">Data Types</span></span>](../data-types/index.md)
