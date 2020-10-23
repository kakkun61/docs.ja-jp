---
title: 共有 WithEvents 変数のイベントを、非共有メソッドで処理できません。
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: 02039b81251e59a951a0fe37ec2c9534b458b6a5
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161921"
---
# <a name="bc30594-events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a><span data-ttu-id="12263-102">BC30594:共有 WithEvents 変数のイベントを、非共有メソッドで処理できません。</span><span class="sxs-lookup"><span data-stu-id="12263-102">BC30594: Events of shared WithEvents variables cannot be handled by non-shared methods</span></span>

<span data-ttu-id="12263-103">`Shared` 修飾子で宣言される変数は共有変数です。</span><span class="sxs-lookup"><span data-stu-id="12263-103">A variable declared with the `Shared` modifier is a shared variable.</span></span> <span data-ttu-id="12263-104">共有変数は、格納場所を 1 つだけ識別します。</span><span class="sxs-lookup"><span data-stu-id="12263-104">A shared variable identifies exactly one storage location.</span></span> <span data-ttu-id="12263-105">`WithEvents` 修飾子で宣言される変数は、変数が属する型によって、変数で起動するイベントのセットが処理されることをアサートします。</span><span class="sxs-lookup"><span data-stu-id="12263-105">A variable declared with the `WithEvents` modifier asserts that the type to which the variable belongs handles the set of events the variable raises.</span></span> <span data-ttu-id="12263-106">変数に値が代入されると、`WithEvents` 宣言によって作成されるプロパティは、既存のイベント ハンドラーをアンフックし、`Add` メソッドを使用して新しいイベント ハンドラーをフックします。</span><span class="sxs-lookup"><span data-stu-id="12263-106">When a value is assigned to the variable, the property created by the `WithEvents` declaration unhooks any existing event handler and hooks up the new event handler via the `Add` method.</span></span>

 <span data-ttu-id="12263-107">**エラー ID:** BC30594</span><span class="sxs-lookup"><span data-stu-id="12263-107">**Error ID:** BC30594</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="12263-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="12263-108">To correct this error</span></span>

- <span data-ttu-id="12263-109">イベント ハンドラー `Shared` を宣言します。</span><span class="sxs-lookup"><span data-stu-id="12263-109">Declare your event handler `Shared`.</span></span>

## <a name="see-also"></a><span data-ttu-id="12263-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="12263-110">See also</span></span>

- [<span data-ttu-id="12263-111">Shared</span><span class="sxs-lookup"><span data-stu-id="12263-111">Shared</span></span>](../modifiers/shared.md)
- [<span data-ttu-id="12263-112">WithEvents</span><span class="sxs-lookup"><span data-stu-id="12263-112">WithEvents</span></span>](../modifiers/withevents.md)
