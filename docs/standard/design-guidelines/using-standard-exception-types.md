---
title: 標準例外型の使用
description: .NET での標準の例外の種類について説明します。 SystemException、ApplicationException、ArgumentException、ComException などについて説明します。
ms.date: 10/22/2008
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
ms.openlocfilehash: ef420d47e6204aef5e3d9bc12ace31fbf5521ee7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734362"
---
# <a name="using-standard-exception-types"></a><span data-ttu-id="4755e-104">標準例外型の使用</span><span class="sxs-lookup"><span data-stu-id="4755e-104">Using Standard Exception Types</span></span>

<span data-ttu-id="4755e-105">このセクションでは、フレームワークによって提供される標準の例外とその使用法の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="4755e-105">This section describes the standard exceptions provided by the Framework and the details of their usage.</span></span> <span data-ttu-id="4755e-106">リストは、完全な手段ではありません。</span><span class="sxs-lookup"><span data-stu-id="4755e-106">The list is by no means exhaustive.</span></span> <span data-ttu-id="4755e-107">他のフレームワークの例外の種類の使用方法については、.NET Framework リファレンスドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4755e-107">Please refer to the .NET Framework reference documentation for usage of other Framework exception types.</span></span>

## <a name="exception-and-systemexception"></a><span data-ttu-id="4755e-108">Exception および SystemException</span><span class="sxs-lookup"><span data-stu-id="4755e-108">Exception and SystemException</span></span>

 <span data-ttu-id="4755e-109">❌<xref:System.Exception?displayProperty=nameWithType>またはをスローしないで <xref:System.SystemException?displayProperty=nameWithType> ください。</span><span class="sxs-lookup"><span data-stu-id="4755e-109">❌ DO NOT throw <xref:System.Exception?displayProperty=nameWithType> or <xref:System.SystemException?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="4755e-110">❌ を再 `System.Exception` `System.SystemException` スローする場合を除き、フレームワークコードでまたはをキャッチしないでください。</span><span class="sxs-lookup"><span data-stu-id="4755e-110">❌ DO NOT catch `System.Exception` or `System.SystemException` in framework code, unless you intend to rethrow.</span></span>

 <span data-ttu-id="4755e-111">❌`System.Exception` `System.SystemException` 最上位レベルの例外ハンドラーを除き、またはをキャッチしないでください。</span><span class="sxs-lookup"><span data-stu-id="4755e-111">❌ AVOID catching `System.Exception` or `System.SystemException`, except in top-level exception handlers.</span></span>

## <a name="applicationexception"></a><span data-ttu-id="4755e-112">ApplicationException</span><span class="sxs-lookup"><span data-stu-id="4755e-112">ApplicationException</span></span>

 <span data-ttu-id="4755e-113">❌ をスローしたり、から派生させたりしないで <xref:System.ApplicationException> ください。</span><span class="sxs-lookup"><span data-stu-id="4755e-113">❌ DO NOT throw or derive from <xref:System.ApplicationException>.</span></span>

## <a name="invalidoperationexception"></a><span data-ttu-id="4755e-114">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="4755e-114">InvalidOperationException</span></span>

 <span data-ttu-id="4755e-115"><xref:System.InvalidOperationException>オブジェクトが不適切な状態にある場合は、✔️スローされます。</span><span class="sxs-lookup"><span data-stu-id="4755e-115">✔️ DO throw an <xref:System.InvalidOperationException> if the object is in an inappropriate state.</span></span>

## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a><span data-ttu-id="4755e-116">ArgumentException、System.argumentnullexception、ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="4755e-116">ArgumentException, ArgumentNullException, and ArgumentOutOfRangeException</span></span>

 <span data-ttu-id="4755e-117"><xref:System.ArgumentException>無効な引数がメンバーに渡された場合、✔️、またはそのサブタイプの1つをスローします。</span><span class="sxs-lookup"><span data-stu-id="4755e-117">✔️ DO throw <xref:System.ArgumentException> or one of its subtypes if bad arguments are passed to a member.</span></span> <span data-ttu-id="4755e-118">最も派生した例外の種類を優先します (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="4755e-118">Prefer the most derived exception type, if applicable.</span></span>

 <span data-ttu-id="4755e-119">✔️は、 `ParamName` のサブクラスの1つをスローするときに、プロパティを設定し `ArgumentException` ます。</span><span class="sxs-lookup"><span data-stu-id="4755e-119">✔️ DO set the `ParamName` property when throwing one of the subclasses of `ArgumentException`.</span></span>

 <span data-ttu-id="4755e-120">このプロパティは、例外がスローされる原因となったパラメーターの名前を表します。</span><span class="sxs-lookup"><span data-stu-id="4755e-120">This property represents the name of the parameter that caused the exception to be thrown.</span></span> <span data-ttu-id="4755e-121">プロパティは、コンストラクターのオーバーロードのいずれかを使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="4755e-121">Note that the property can be set using one of the constructor overloads.</span></span>

 <span data-ttu-id="4755e-122">✔️は `value` 、プロパティ setter の暗黙的な値パラメーターの名前にを使用します。</span><span class="sxs-lookup"><span data-stu-id="4755e-122">✔️ DO use `value` for the name of the implicit value parameter of property setters.</span></span>

## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a><span data-ttu-id="4755e-123">NullReferenceException、IndexOutOfRangeException、および Access Ationexception</span><span class="sxs-lookup"><span data-stu-id="4755e-123">NullReferenceException, IndexOutOfRangeException, and AccessViolationException</span></span>

 <span data-ttu-id="4755e-124">❌ パブリックに呼び出し可能な Api が、、、またはを明示的または暗黙的にスローすることを許可しないでください <xref:System.NullReferenceException> <xref:System.AccessViolationException> <xref:System.IndexOutOfRangeException> 。</span><span class="sxs-lookup"><span data-stu-id="4755e-124">❌ DO NOT allow publicly callable APIs to explicitly or implicitly throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, or <xref:System.IndexOutOfRangeException>.</span></span> <span data-ttu-id="4755e-125">これらの例外は、実行エンジンによって予約およびスローされ、ほとんどの場合、バグを示します。</span><span class="sxs-lookup"><span data-stu-id="4755e-125">These exceptions are reserved and thrown by the execution engine and in most cases indicate a bug.</span></span>

 <span data-ttu-id="4755e-126">これらの例外をスローしないように引数をチェックします。</span><span class="sxs-lookup"><span data-stu-id="4755e-126">Do argument checking to avoid throwing these exceptions.</span></span> <span data-ttu-id="4755e-127">これらの例外をスローすると、時間の経過と共に変化する可能性のあるメソッドの実装の詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4755e-127">Throwing these exceptions exposes implementation details of your method that might change over time.</span></span>

## <a name="stackoverflowexception"></a><span data-ttu-id="4755e-128">StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="4755e-128">StackOverflowException</span></span>

 <span data-ttu-id="4755e-129">❌ 明示的にスローしないで <xref:System.StackOverflowException> ください。</span><span class="sxs-lookup"><span data-stu-id="4755e-129">❌ DO NOT explicitly throw <xref:System.StackOverflowException>.</span></span> <span data-ttu-id="4755e-130">例外は、CLR によってのみ明示的にスローされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="4755e-130">The exception should be explicitly thrown only by the CLR.</span></span>

 <span data-ttu-id="4755e-131">❌ キャッチしないで `StackOverflowException` ください。</span><span class="sxs-lookup"><span data-stu-id="4755e-131">❌ DO NOT catch `StackOverflowException`.</span></span>

 <span data-ttu-id="4755e-132">任意のスタックオーバーフローの有無に一貫性を持たせるマネージコードを記述することはほとんど不可能です。</span><span class="sxs-lookup"><span data-stu-id="4755e-132">It is almost impossible to write managed code that remains consistent in the presence of arbitrary stack overflows.</span></span> <span data-ttu-id="4755e-133">CLR のアンマネージ部分は、プローブを使用してスタックオーバーフローを適切に定義された場所に移動することによって一貫性を保ちます。これは、任意のスタックオーバーフローからのバックアップではありません。</span><span class="sxs-lookup"><span data-stu-id="4755e-133">The unmanaged parts of the CLR remain consistent by using probes to move stack overflows to well-defined places rather than by backing out from arbitrary stack overflows.</span></span>

## <a name="outofmemoryexception"></a><span data-ttu-id="4755e-134">OutOfMemoryException</span><span class="sxs-lookup"><span data-stu-id="4755e-134">OutOfMemoryException</span></span>

 <span data-ttu-id="4755e-135">❌ 明示的にスローしないで <xref:System.OutOfMemoryException> ください。</span><span class="sxs-lookup"><span data-stu-id="4755e-135">❌ DO NOT explicitly throw <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="4755e-136">この例外は、CLR インフラストラクチャによってのみスローされます。</span><span class="sxs-lookup"><span data-stu-id="4755e-136">This exception is to be thrown only by the CLR infrastructure.</span></span>

## <a name="comexception-sehexception-and-executionengineexception"></a><span data-ttu-id="4755e-137">ComException、SEHException、および System.executionengineexception</span><span class="sxs-lookup"><span data-stu-id="4755e-137">ComException, SEHException, and ExecutionEngineException</span></span>

 <span data-ttu-id="4755e-138">❌ 、、およびを明示的にスローしないでください <xref:System.Runtime.InteropServices.COMException>  <xref:System.ExecutionEngineException> <xref:System.Runtime.InteropServices.SEHException> 。</span><span class="sxs-lookup"><span data-stu-id="4755e-138">❌ DO NOT explicitly throw <xref:System.Runtime.InteropServices.COMException>,  <xref:System.ExecutionEngineException>, and <xref:System.Runtime.InteropServices.SEHException>.</span></span> <span data-ttu-id="4755e-139">これらの例外は、CLR インフラストラクチャによってのみスローされます。</span><span class="sxs-lookup"><span data-stu-id="4755e-139">These exceptions are to be thrown only by the CLR infrastructure.</span></span>

 <span data-ttu-id="4755e-140">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="4755e-140">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="4755e-141">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="4755e-141">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="4755e-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="4755e-142">See also</span></span>

- [<span data-ttu-id="4755e-143">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="4755e-143">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="4755e-144">例外のデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="4755e-144">Design Guidelines for Exceptions</span></span>](exceptions.md)
