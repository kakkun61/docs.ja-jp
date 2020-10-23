---
title: "'<eventname>' はイベントであるため、直接呼び出すことはできません。"
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: 246cb92daa2c838c95f695542f33cf02af42764d
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161986"
---
# <a name="bc32022-eventname-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="7ee09-102">BC32022: '\<eventname>' はイベントであるため、直接呼び出すことはできません</span><span class="sxs-lookup"><span data-stu-id="7ee09-102">BC32022: '\<eventname>' is an event, and cannot be called directly</span></span>

<span data-ttu-id="7ee09-103">'<`eventname`>' はイベントであるため、直接呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="7ee09-103">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="7ee09-104">`RaiseEvent` ステートメントを使用して、イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="7ee09-104">Use a `RaiseEvent` statement to raise an event.</span></span>

 <span data-ttu-id="7ee09-105">プロシージャ呼び出しは、プロシージャ名のイベントを指定します。</span><span class="sxs-lookup"><span data-stu-id="7ee09-105">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="7ee09-106">イベント ハンドラーはプロシージャですが、イベント自体はシグナル通知デバイスであり、これを発生させて処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ee09-106">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>

 <span data-ttu-id="7ee09-107">**エラー ID:** BC32022</span><span class="sxs-lookup"><span data-stu-id="7ee09-107">**Error ID:** BC32022</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="7ee09-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="7ee09-108">To correct this error</span></span>

- <span data-ttu-id="7ee09-109">`RaiseEvent` ステートメントを使用して、イベントを通知し、それを処理するプロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7ee09-109">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ee09-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="7ee09-110">See also</span></span>

- [<span data-ttu-id="7ee09-111">RaiseEvent ステートメント</span><span class="sxs-lookup"><span data-stu-id="7ee09-111">RaiseEvent Statement</span></span>](../statements/raiseevent-statement.md)
