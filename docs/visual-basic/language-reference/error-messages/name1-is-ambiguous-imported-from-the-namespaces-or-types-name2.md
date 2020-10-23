---
title: "'<name1>' 名前空間または型からインポートされた '<name2>' があいまいです。"
ms.date: 07/20/2015
f1_keywords:
- vbc30561
- bc30561
helpviewer_keywords:
- BC30561
ms.assetid: 761091f7-1018-4299-b481-3966a4a2c126
ms.openlocfilehash: 73cc604f1e3a06687ca93779a01e698512be198b
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160185"
---
# <a name="bc30561-name1-is-ambiguous-imported-from-the-namespaces-or-types-name2"></a><span data-ttu-id="09bf2-102">BC30561: "\<name1>" 名前空間または型からインポートされた "\<name2>" があいまいです。</span><span class="sxs-lookup"><span data-stu-id="09bf2-102">BC30561: '\<name1>' is ambiguous, imported from the namespaces or types '\<name2>'</span></span>

<span data-ttu-id="09bf2-103">あいまいな名前を指定したため、別の名前と競合しています。</span><span class="sxs-lookup"><span data-stu-id="09bf2-103">You have provided a name that is ambiguous and therefore conflicts with another name.</span></span> <span data-ttu-id="09bf2-104">Visual Basic コンパイラには、競合解決規則がありません。ユーザー自身が名前のあいまいさを解消する必要があります。</span><span class="sxs-lookup"><span data-stu-id="09bf2-104">The Visual Basic compiler does not have any conflict resolution rules; you must disambiguate names yourself.</span></span>

 <span data-ttu-id="09bf2-105">**エラー ID:** BC30561</span><span class="sxs-lookup"><span data-stu-id="09bf2-105">**Error ID:** BC30561</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="09bf2-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="09bf2-106">To correct this error</span></span>

- <span data-ttu-id="09bf2-107">名前空間のインポートを削除して、名前のあいまいさをなくします。</span><span class="sxs-lookup"><span data-stu-id="09bf2-107">Disambiguate the name by removing namespace imports.</span></span>

- <span data-ttu-id="09bf2-108">名前を完全修飾します。</span><span class="sxs-lookup"><span data-stu-id="09bf2-108">Fully qualify the name.</span></span>

## <a name="see-also"></a><span data-ttu-id="09bf2-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="09bf2-109">See also</span></span>

- [<span data-ttu-id="09bf2-110">Imports ステートメント (.NET 名前空間および型)</span><span class="sxs-lookup"><span data-stu-id="09bf2-110">Imports Statement (.NET Namespace and Type)</span></span>](../statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="09bf2-111">Visual Basic における名前空間</span><span class="sxs-lookup"><span data-stu-id="09bf2-111">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="09bf2-112">Namespace ステートメント</span><span class="sxs-lookup"><span data-stu-id="09bf2-112">Namespace Statement</span></span>](../statements/namespace-statement.md)
