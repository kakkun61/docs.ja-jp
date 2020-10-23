---
title: デリゲート型 '<eventname1>' および '<eventname2>' が一致しないため、イベント '<interface>' はインターフェイス '<delegate1>' 上のイベント '<delegate2>' を実装できません。
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: d0b2b095ed355b420b28e87ed0b9d6a31f049ebf
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162025"
---
# <a name="bc31423-event-eventname1-cannot-implement-event-eventname2-on-interface-interface-because-their-delegate-types-delegate1-and-delegate2-do-not-match"></a><span data-ttu-id="54c58-102">BC31423:デリゲート型 '\<eventname1>' および '\<eventname2>' が一致しないため、イベント '\<interface>' はインターフェイス '\<delegate1>' 上のイベント '\<delegate2>' を実装できません。</span><span class="sxs-lookup"><span data-stu-id="54c58-102">BC31423: Event '\<eventname1>' cannot implement event '\<eventname2>' on interface '\<interface>' because their delegate types '\<delegate1>' and '\<delegate2>' do not match</span></span>

<span data-ttu-id="54c58-103">イベントのデリゲート型が、インターフェイスのイベントのデリゲート型と一致しないため、Visual Basic ではイベントを実装できません。</span><span class="sxs-lookup"><span data-stu-id="54c58-103">Visual Basic cannot implement an event because the delegate type of the event does not match the delegate type of the event in the interface.</span></span> <span data-ttu-id="54c58-104">このエラーは、インターフェイス内で複数のイベントを定義して、同じイベントと共にそれらを実装しようとする場合に、発生します。</span><span class="sxs-lookup"><span data-stu-id="54c58-104">This error can occur when you define multiple events in an interface and then attempt to implement them together with the same event.</span></span> <span data-ttu-id="54c58-105">実装されたすべてのイベントが `As` 構文を使用して宣言され、同じデリゲート型を指定する場合にのみ、イベントは 2 つ以上のイベントを実装することができます。</span><span class="sxs-lookup"><span data-stu-id="54c58-105">An event can implement two or more events only if all implemented events are declared using the `As` syntax and specify the same delegate type.</span></span>

 <span data-ttu-id="54c58-106">**エラー ID:** BC31423</span><span class="sxs-lookup"><span data-stu-id="54c58-106">**Error ID:** BC31423</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="54c58-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="54c58-107">To correct this error</span></span>

- <span data-ttu-id="54c58-108">イベントを個別に実装します。</span><span class="sxs-lookup"><span data-stu-id="54c58-108">Implement the events separately.</span></span>

     <span data-ttu-id="54c58-109">または</span><span class="sxs-lookup"><span data-stu-id="54c58-109">—or—</span></span>

- <span data-ttu-id="54c58-110">`As` 構文を使用してインターフェイスにイベントを定義し、同じデリゲート型を指定します。</span><span class="sxs-lookup"><span data-stu-id="54c58-110">Define the events in the interface using the `As` syntax and specify the same delegate type.</span></span>

## <a name="see-also"></a><span data-ttu-id="54c58-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="54c58-111">See also</span></span>

- [<span data-ttu-id="54c58-112">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="54c58-112">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="54c58-113">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="54c58-113">Delegate Statement</span></span>](../statements/delegate-statement.md)
- [<span data-ttu-id="54c58-114">イベント</span><span class="sxs-lookup"><span data-stu-id="54c58-114">Events</span></span>](../../programming-guide/language-features/events/index.md)
