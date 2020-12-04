---
title: 型システムランタイムイベント
description: TypeLoadStart や Typeloadstart など、.NET 型システムに固有の診断情報を収集する .NET ランタイムイベントを参照してください。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- type system events (CoreCLR)
- ETW, EventPipe, LTTng type system events (CoreCLR)
ms.openlocfilehash: 8eee89cddb0098da2cb449a4be21945adac725e3
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "96594037"
---
# <a name="net-runtime-type-events"></a><span data-ttu-id="b022e-103">.NET ランタイム型イベント</span><span class="sxs-lookup"><span data-stu-id="b022e-103">.NET runtime type events</span></span>

<span data-ttu-id="b022e-104">これらのイベントは、型の読み込みに関する情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="b022e-104">These events collect information relating to loading types.</span></span> <span data-ttu-id="b022e-105">診断のためにこれらのイベントを使用する方法の詳細については、「 [.net アプリケーションのログ記録とトレース](../../core/diagnostics/logging-tracing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b022e-105">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="typeloadstart-event"></a><span data-ttu-id="b022e-106">TypeLoadStart イベント</span><span class="sxs-lookup"><span data-stu-id="b022e-106">TypeLoadStart Event</span></span>

|<span data-ttu-id="b022e-107">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="b022e-107">Keyword for raising the event</span></span>|<span data-ttu-id="b022e-108">event</span><span class="sxs-lookup"><span data-stu-id="b022e-108">Event</span></span>|<span data-ttu-id="b022e-109">Level</span><span class="sxs-lookup"><span data-stu-id="b022e-109">Level</span></span>|  
|-----------------------------------|-----------|-----------|  
|<span data-ttu-id="b022e-110">`TypeDiagnosticKeyword` 0x8000000000</span><span class="sxs-lookup"><span data-stu-id="b022e-110">`TypeDiagnosticKeyword` (0x8000000000)</span></span>|<span data-ttu-id="b022e-111">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="b022e-111">Informational (4)</span></span>|  

|<span data-ttu-id="b022e-112">event</span><span class="sxs-lookup"><span data-stu-id="b022e-112">Event</span></span>|<span data-ttu-id="b022e-113">イベント ID</span><span class="sxs-lookup"><span data-stu-id="b022e-113">Event ID</span></span>|<span data-ttu-id="b022e-114">説明</span><span class="sxs-lookup"><span data-stu-id="b022e-114">Description</span></span>|  
|-----------|--------------|-----------------|  
|`TypeLoadStart`|<span data-ttu-id="b022e-115">73</span><span class="sxs-lookup"><span data-stu-id="b022e-115">73</span></span>|<span data-ttu-id="b022e-116">型の読み込みが開始されました。</span><span class="sxs-lookup"><span data-stu-id="b022e-116">A type load has started.</span></span>|

|<span data-ttu-id="b022e-117">フィールド名</span><span class="sxs-lookup"><span data-stu-id="b022e-117">Field name</span></span>|<span data-ttu-id="b022e-118">データ型</span><span class="sxs-lookup"><span data-stu-id="b022e-118">Data type</span></span>|<span data-ttu-id="b022e-119">説明</span><span class="sxs-lookup"><span data-stu-id="b022e-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|`TypeLoadStartID`|`win:UInt32`|<span data-ttu-id="b022e-120">型の読み込み操作の ID。</span><span class="sxs-lookup"><span data-stu-id="b022e-120">ID for the type load operation.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="b022e-121">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="b022e-121">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="typeloadstop-event"></a><span data-ttu-id="b022e-122">TypeLoadStop イベント</span><span class="sxs-lookup"><span data-stu-id="b022e-122">TypeLoadStop Event</span></span>

|<span data-ttu-id="b022e-123">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="b022e-123">Keyword for raising the event</span></span>|<span data-ttu-id="b022e-124">Level</span><span class="sxs-lookup"><span data-stu-id="b022e-124">Level</span></span>|  
|-----------------------------------|-----------|-----------|  
|<span data-ttu-id="b022e-125">`TypeDiagnosticKeyword` 0x8000000000</span><span class="sxs-lookup"><span data-stu-id="b022e-125">`TypeDiagnosticKeyword` (0x8000000000)</span></span>|<span data-ttu-id="b022e-126">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="b022e-126">Informational (4)</span></span>|  

|<span data-ttu-id="b022e-127">event</span><span class="sxs-lookup"><span data-stu-id="b022e-127">Event</span></span>|<span data-ttu-id="b022e-128">イベント ID</span><span class="sxs-lookup"><span data-stu-id="b022e-128">Event ID</span></span>|<span data-ttu-id="b022e-129">説明</span><span class="sxs-lookup"><span data-stu-id="b022e-129">Description</span></span>|  
|-----------|--------------|-----------------|  
|`TypeLoadStop`|<span data-ttu-id="b022e-130">74</span><span class="sxs-lookup"><span data-stu-id="b022e-130">74</span></span>|<span data-ttu-id="b022e-131">型の読み込みが完了しました。</span><span class="sxs-lookup"><span data-stu-id="b022e-131">A type load is finished.</span></span>|

|<span data-ttu-id="b022e-132">フィールド名</span><span class="sxs-lookup"><span data-stu-id="b022e-132">Field name</span></span>|<span data-ttu-id="b022e-133">データ型</span><span class="sxs-lookup"><span data-stu-id="b022e-133">Data type</span></span>|<span data-ttu-id="b022e-134">説明</span><span class="sxs-lookup"><span data-stu-id="b022e-134">Description</span></span>|  
|----------------|---------------|-----------------|  
|`TypeLoadStartID`|`win:UInt32`|<span data-ttu-id="b022e-135">型の読み込み操作の ID (対応する TypeLoadStart イベントの TypeLoadStartID と一致します)。</span><span class="sxs-lookup"><span data-stu-id="b022e-135">ID for the type load operation (matches the corresponding TypeLoadStart event's TypeLoadStartID).</span></span>|
|`LoadLevel`|`win:UInt16`|<span data-ttu-id="b022e-136">「読み込みレベル」と入力します。</span><span class="sxs-lookup"><span data-stu-id="b022e-136">Type load level.</span></span>|
|`TypeID`|`win:UInt64`|<span data-ttu-id="b022e-137">型ハンドルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b022e-137">Pointer to the type handle.</span></span>|
|`TypeName`|`win:UnicodeString`|<span data-ttu-id="b022e-138">型の名前。</span><span class="sxs-lookup"><span data-stu-id="b022e-138">Name of the type.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="b022e-139">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="b022e-139">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
