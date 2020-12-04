---
title: 移植性と相互運用性の規則 (コード分析)
description: コード分析規則の移植性と相互運用性の規則について
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis rules, interoperability rules, portability rules
- portability rules
- warnings, portability
- interoperability rules
- warnings, interoperability
author: gewarren
ms.author: gewarren
ms.openlocfilehash: a20cd77e13c4a8b95633d129990667f0a8de3ee8
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2020
ms.locfileid: "96591195"
---
# <a name="portability-and-interoperability-rules"></a><span data-ttu-id="4b064-103">移植性と相互運用性の規則</span><span class="sxs-lookup"><span data-stu-id="4b064-103">Portability and interoperability rules</span></span>

<span data-ttu-id="4b064-104">移植性ルールは、異なるプラットフォーム間での移植性をサポートします。</span><span class="sxs-lookup"><span data-stu-id="4b064-104">Portability rules support portability across different platforms.</span></span> <span data-ttu-id="4b064-105">相互運用性規則は、COM クライアントとの対話をサポートします。</span><span class="sxs-lookup"><span data-stu-id="4b064-105">Interoperability rules support interaction with COM clients.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="4b064-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="4b064-106">In this section</span></span>

| <span data-ttu-id="4b064-107">ルール</span><span class="sxs-lookup"><span data-stu-id="4b064-107">Rule</span></span> | <span data-ttu-id="4b064-108">説明</span><span class="sxs-lookup"><span data-stu-id="4b064-108">Description</span></span> |
| - | - |
| [<span data-ttu-id="4b064-109">CA1401: P/Invoke を表示できません</span><span class="sxs-lookup"><span data-stu-id="4b064-109">CA1401: P/Invokes should not be visible</span></span>](ca1401.md) | <span data-ttu-id="4b064-110">パブリック型のパブリックメソッドまたはプロテクトメソッドには System.Runtime.InteropServices.DllImportAttribute 属性があります (Visual Basic で Declare キーワードによっても実装されています)。</span><span class="sxs-lookup"><span data-stu-id="4b064-110">A public or protected method in a public type has the System.Runtime.InteropServices.DllImportAttribute attribute (also implemented by the Declare keyword in Visual Basic).</span></span> <span data-ttu-id="4b064-111">このようなメソッドは公開しないでください。</span><span class="sxs-lookup"><span data-stu-id="4b064-111">Such methods should not be exposed.</span></span> |
| [<span data-ttu-id="4b064-112">CA1416:プラットフォームの互換性を検証する</span><span class="sxs-lookup"><span data-stu-id="4b064-112">CA1416: Validate platform compatibility</span></span>](ca1416.md) | <span data-ttu-id="4b064-113">コンポーネントでプラットフォームに依存する Api を使用すると、コードがすべてのプラットフォームで動作しなくなります。</span><span class="sxs-lookup"><span data-stu-id="4b064-113">Using platform-dependent APIs on a component makes the code no longer work across all platforms.</span></span> |
| [<span data-ttu-id="4b064-114">CA1417: `OutAttribute` P/invoke に文字列パラメーターを使用しません</span><span class="sxs-lookup"><span data-stu-id="4b064-114">CA1417: Do not use `OutAttribute` on string parameters for P/Invokes</span></span>](ca1417.md) | <span data-ttu-id="4b064-115">で値によって渡される文字列パラメーター `OutAttribute` は、文字列がインターン文字列である場合、ランタイムを不安定にする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4b064-115">String parameters passed by value with the `OutAttribute` can destabilize the runtime if the string is an interned string.</span></span> |
