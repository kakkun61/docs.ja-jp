---
title: イベントとコールバック
ms.date: 10/22/2008
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
ms.openlocfilehash: c63a88cb4e500504f993352a03478f40cad58400
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734735"
---
# <a name="events-and-callbacks"></a><span data-ttu-id="39a48-102">イベントとコールバック</span><span class="sxs-lookup"><span data-stu-id="39a48-102">Events and Callbacks</span></span>

<span data-ttu-id="39a48-103">コールバックは、フレームワークがデリゲートを通じてユーザーコードにコールバックすることを可能にする拡張ポイントです。</span><span class="sxs-lookup"><span data-stu-id="39a48-103">Callbacks are extensibility points that allow a framework to call back into user code through a delegate.</span></span> <span data-ttu-id="39a48-104">これらのデリゲートは、通常、メソッドのパラメーターを使用してフレームワークに渡されます。</span><span class="sxs-lookup"><span data-stu-id="39a48-104">These delegates are usually passed to the framework through a parameter of a method.</span></span>

 <span data-ttu-id="39a48-105">イベントは、デリゲート (イベントハンドラー) を提供するための便利で一貫性のある構文をサポートする、特殊なコールバックのケースです。</span><span class="sxs-lookup"><span data-stu-id="39a48-105">Events are a special case of callbacks that supports convenient and consistent syntax for supplying the delegate (an event handler).</span></span> <span data-ttu-id="39a48-106">さらに、Visual Studio のステートメント入力候補とデザイナーは、イベントベースの Api の使用に関するヘルプを提供します。</span><span class="sxs-lookup"><span data-stu-id="39a48-106">In addition, Visual Studio's statement completion and designers provide help in using event-based APIs.</span></span> <span data-ttu-id="39a48-107">(「 [イベントの設計](event.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="39a48-107">(See [Event Design](event.md).)</span></span>

 <span data-ttu-id="39a48-108">✔️コールバックを使用して、ユーザーがフレームワークによって実行されるカスタムコードを提供できるようにすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="39a48-108">✔️ CONSIDER using callbacks to allow users to provide custom code to be executed by the framework.</span></span>

 <span data-ttu-id="39a48-109">✔️イベントを使用して、ユーザーがオブジェクト指向設計を理解しなくても、フレームワークの動作をカスタマイズできるようにすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="39a48-109">✔️ CONSIDER using events to allow users to customize the behavior of a framework without the need for understanding object-oriented design.</span></span>

 <span data-ttu-id="39a48-110">✔️は、より幅広い開発者を対象とし、Visual Studio のステートメント入力候補と統合されるため、プレーンコールバックでイベントを優先します。</span><span class="sxs-lookup"><span data-stu-id="39a48-110">✔️ DO prefer events over plain callbacks, because they are more familiar to a broader range of developers and are integrated with Visual Studio statement completion.</span></span>

 <span data-ttu-id="39a48-111">❌ パフォーマンスを重視する Api ではコールバックを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="39a48-111">❌ AVOID using callbacks in performance-sensitive APIs.</span></span>

 <span data-ttu-id="39a48-112">`Func<...>` `Action<...>` `Expression<...>` コールバックを使用して api を定義するときは、カスタムデリゲートではなく、新しい型、型、または型を使用✔️ます。</span><span class="sxs-lookup"><span data-stu-id="39a48-112">✔️ DO use the new `Func<...>`, `Action<...>`, or `Expression<...>` types instead of custom delegates, when defining APIs with callbacks.</span></span>

 <span data-ttu-id="39a48-113">`Func<...>` とは `Action<...>` 汎用デリゲートを表します。</span><span class="sxs-lookup"><span data-stu-id="39a48-113">`Func<...>` and `Action<...>` represent generic delegates.</span></span> <span data-ttu-id="39a48-114">`Expression<...>` コンパイル後に実行時に呼び出すことができる関数定義を表しますが、シリアル化してリモートプロセスに渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="39a48-114">`Expression<...>` represents function definitions that can be compiled and subsequently invoked at runtime but can also be serialized and passed to remote processes.</span></span>

 <span data-ttu-id="39a48-115">とデリゲートを使用する代わりに、を使用してパフォーマンスへの影響を測定し、理解する✔️ `Expression<...>` `Func<...>` `Action<...>` ます。</span><span class="sxs-lookup"><span data-stu-id="39a48-115">✔️ DO measure and understand performance implications of using `Expression<...>`, instead of using `Func<...>` and `Action<...>` delegates.</span></span>

 <span data-ttu-id="39a48-116">`Expression<...>` 型は、ほとんどの場合 `Func<...>` 、とデリゲートと論理的に等価です `Action<...>` 。</span><span class="sxs-lookup"><span data-stu-id="39a48-116">`Expression<...>` types are in most cases logically equivalent to `Func<...>` and `Action<...>` delegates.</span></span> <span data-ttu-id="39a48-117">これらの主な違いは、デリゲートはローカルプロセスシナリオで使用することを意図していることです。式は、リモートのプロセスまたはコンピューターで式を評価することが有益であるケースを対象としています。</span><span class="sxs-lookup"><span data-stu-id="39a48-117">The main difference between them is that the delegates are intended to be used in local process scenarios; expressions are intended for cases where it's beneficial and possible to evaluate the expression in a remote process or machine.</span></span>

 <span data-ttu-id="39a48-118">デリゲートを呼び出すことによって、任意のコードを実行し、セキュリティ、正確性、および互換性の影響を与える可能性があることを✔️理解することができます。</span><span class="sxs-lookup"><span data-stu-id="39a48-118">✔️ DO understand that by calling a delegate, you are executing arbitrary code and that could have security, correctness, and compatibility repercussions.</span></span>

 <span data-ttu-id="39a48-119">*部分 &copy; 2005、2009 Microsoft Corporation。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="39a48-119">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="39a48-120">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="39a48-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="39a48-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="39a48-121">See also</span></span>

- [<span data-ttu-id="39a48-122">機能拡張のデザイン</span><span class="sxs-lookup"><span data-stu-id="39a48-122">Designing for Extensibility</span></span>](designing-for-extensibility.md)
- [<span data-ttu-id="39a48-123">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="39a48-123">Framework Design Guidelines</span></span>](index.md)
