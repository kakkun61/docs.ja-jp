---
title: 定数式は、型 '<typename>' では表現できません。
ms.date: 07/20/2015
f1_keywords:
- bc30439
- vbc30439
helpviewer_keywords:
- BC30439
ms.assetid: 0a842906-3bc5-4946-8a37-3e3da883ef63
ms.openlocfilehash: e18f05c0d6a37ac4563b554d7ba943ba21131f85
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163169"
---
# <a name="bc30439-constant-expression-not-representable-in-type-typename"></a><span data-ttu-id="5c25b-102">BC30439:定数式は、型 '\<typename>' では表現できません。</span><span class="sxs-lookup"><span data-stu-id="5c25b-102">BC30439: Constant expression not representable in type '\<typename>'</span></span>

<span data-ttu-id="5c25b-103">通常は範囲をオーバーフローしているため、ターゲットの型に収まらない定数を評価しようとしています。</span><span class="sxs-lookup"><span data-stu-id="5c25b-103">You are trying to evaluate a constant that will not fit into the target type, usually because it is overflowing the range.</span></span>

 <span data-ttu-id="5c25b-104">**エラー ID:** BC30439</span><span class="sxs-lookup"><span data-stu-id="5c25b-104">**Error ID:** BC30439</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="5c25b-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="5c25b-105">To correct this error</span></span>

1. <span data-ttu-id="5c25b-106">ターゲットの型を、定数を処理できるものに変更します。</span><span class="sxs-lookup"><span data-stu-id="5c25b-106">Change the target type to one that can handle the constant.</span></span>

## <a name="see-also"></a><span data-ttu-id="5c25b-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="5c25b-107">See also</span></span>

- [<span data-ttu-id="5c25b-108">定数の概要</span><span class="sxs-lookup"><span data-stu-id="5c25b-108">Constants Overview</span></span>](../../programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="5c25b-109">定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="5c25b-109">Constants and Enumerations</span></span>](../constants-and-enumerations.md)
