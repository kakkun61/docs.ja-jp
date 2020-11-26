---
title: 相互運用 ETW イベント
description: .NET での Microsoft 中間言語 (MSIL) スタブ生成 & キャッシュに関する情報をキャプチャする、interop ETW (event tracing for Windows) イベントを確認します。
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
ms.openlocfilehash: 8e92a1492d0295fb71473843752cb4c6184d3604
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242189"
---
# <a name="interop-etw-events"></a><span data-ttu-id="636f7-103">相互運用 ETW イベント</span><span class="sxs-lookup"><span data-stu-id="636f7-103">Interop ETW Events</span></span>

<span data-ttu-id="636f7-104">相互運用イベントは、Microsoft intermediate language (MSIL) のスタブ生成とキャッシュに関する情報をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="636f7-104">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  

## <a name="ilstubgenerated-event"></a><span data-ttu-id="636f7-105">ILStubGenerated イベント</span><span class="sxs-lookup"><span data-stu-id="636f7-105">ILStubGenerated Event</span></span>

<span data-ttu-id="636f7-106">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="636f7-106">The following table shows the keyword and level.</span></span> <span data-ttu-id="636f7-107">(詳細については、「 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="636f7-107">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="636f7-108">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="636f7-108">Keyword for raising the event</span></span>|<span data-ttu-id="636f7-109">Level</span><span class="sxs-lookup"><span data-stu-id="636f7-109">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="636f7-110">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="636f7-110">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="636f7-111">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="636f7-111">Informational(4)</span></span>|  
  
 <span data-ttu-id="636f7-112">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="636f7-112">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="636f7-113">Event</span><span class="sxs-lookup"><span data-stu-id="636f7-113">Event</span></span>|<span data-ttu-id="636f7-114">イベント ID</span><span class="sxs-lookup"><span data-stu-id="636f7-114">Event ID</span></span>|<span data-ttu-id="636f7-115">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="636f7-115">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="636f7-116">88</span><span class="sxs-lookup"><span data-stu-id="636f7-116">88</span></span>|<span data-ttu-id="636f7-117">MSIL スタブが生成された。</span><span class="sxs-lookup"><span data-stu-id="636f7-117">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="636f7-118">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="636f7-118">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="636f7-119">フィールド名</span><span class="sxs-lookup"><span data-stu-id="636f7-119">Field name</span></span>|<span data-ttu-id="636f7-120">データ型</span><span class="sxs-lookup"><span data-stu-id="636f7-120">Data type</span></span>|<span data-ttu-id="636f7-121">説明</span><span class="sxs-lookup"><span data-stu-id="636f7-121">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="636f7-122">ModuleID</span><span class="sxs-lookup"><span data-stu-id="636f7-122">ModuleID</span></span>|<span data-ttu-id="636f7-123">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="636f7-123">win:UInt16</span></span>|<span data-ttu-id="636f7-124">モジュールの ID です。</span><span class="sxs-lookup"><span data-stu-id="636f7-124">The module identifier.</span></span>|  
|<span data-ttu-id="636f7-125">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="636f7-125">StubMethodID</span></span>|<span data-ttu-id="636f7-126">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="636f7-126">win:UInt64</span></span>|<span data-ttu-id="636f7-127">スタブのメソッド識別子。</span><span class="sxs-lookup"><span data-stu-id="636f7-127">The stub method identifier.</span></span>|  
|<span data-ttu-id="636f7-128">StubFlags</span><span class="sxs-lookup"><span data-stu-id="636f7-128">StubFlags</span></span>|<span data-ttu-id="636f7-129">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="636f7-129">win:UInt64</span></span>|<span data-ttu-id="636f7-130">スタブのフラグ:</span><span class="sxs-lookup"><span data-stu-id="636f7-130">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="636f7-131">0x1 - 逆方向の相互運用。</span><span class="sxs-lookup"><span data-stu-id="636f7-131">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="636f7-132">0x2 - COM 相互運用。</span><span class="sxs-lookup"><span data-stu-id="636f7-132">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="636f7-133">0x4 - NGen.exe で生成されたスタブ。</span><span class="sxs-lookup"><span data-stu-id="636f7-133">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="636f7-134">0x8 - デリゲート。</span><span class="sxs-lookup"><span data-stu-id="636f7-134">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="636f7-135">0x10-可変個引数。</span><span class="sxs-lookup"><span data-stu-id="636f7-135">0x10 - Variable argument.</span></span><br /><br /> <span data-ttu-id="636f7-136">0x20 - アンマネージ呼び出し先。</span><span class="sxs-lookup"><span data-stu-id="636f7-136">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="636f7-137">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="636f7-137">ManagedInteropMethodToken</span></span>|<span data-ttu-id="636f7-138">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="636f7-138">win:UInt32</span></span>|<span data-ttu-id="636f7-139">マネージド相互運用メソッドのトークンです。</span><span class="sxs-lookup"><span data-stu-id="636f7-139">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="636f7-140">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="636f7-140">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="636f7-141">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="636f7-141">win:UnicodeString</span></span>|<span data-ttu-id="636f7-142">マネージド相互運用メソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="636f7-142">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="636f7-143">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="636f7-143">ManagedInteropMethodName</span></span>|<span data-ttu-id="636f7-144">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="636f7-144">win:UnicodeString</span></span>|<span data-ttu-id="636f7-145">マネージド相互運用メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="636f7-145">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="636f7-146">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="636f7-146">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="636f7-147">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="636f7-147">win:UnicodeString</span></span>|<span data-ttu-id="636f7-148">マネージド相互運用メソッドのシグネチャ。</span><span class="sxs-lookup"><span data-stu-id="636f7-148">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="636f7-149">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="636f7-149">NativeMethodSignature</span></span>|<span data-ttu-id="636f7-150">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="636f7-150">win:UnicodeString</span></span>|<span data-ttu-id="636f7-151">ネイティブ メソッド シグネチャ。</span><span class="sxs-lookup"><span data-stu-id="636f7-151">The native method signature.</span></span>|  
|<span data-ttu-id="636f7-152">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="636f7-152">StubMethodSignature</span></span>|<span data-ttu-id="636f7-153">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="636f7-153">win:UnicodeString</span></span>|<span data-ttu-id="636f7-154">スタブ メソッド シグネチャ。</span><span class="sxs-lookup"><span data-stu-id="636f7-154">The stub method signature.</span></span>|  
|<span data-ttu-id="636f7-155">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="636f7-155">StubMethodILCode</span></span>|<span data-ttu-id="636f7-156">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="636f7-156">win:UnicodeString</span></span>|<span data-ttu-id="636f7-157">スタブ メソッドの MSIL コード。</span><span class="sxs-lookup"><span data-stu-id="636f7-157">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="636f7-158">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="636f7-158">ClrInstanceID</span></span>|<span data-ttu-id="636f7-159">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="636f7-159">win:UInt16</span></span>|<span data-ttu-id="636f7-160">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="636f7-160">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="ilstubcachehit-event"></a><span data-ttu-id="636f7-161">ILStubCacheHit イベント</span><span class="sxs-lookup"><span data-stu-id="636f7-161">ILStubCacheHit Event</span></span>  

<span data-ttu-id="636f7-162">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="636f7-162">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="636f7-163">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="636f7-163">Keyword for raising the event</span></span>|<span data-ttu-id="636f7-164">Level</span><span class="sxs-lookup"><span data-stu-id="636f7-164">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="636f7-165">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="636f7-165">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="636f7-166">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="636f7-166">Informational(4)</span></span>|  
  
 <span data-ttu-id="636f7-167">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="636f7-167">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="636f7-168">Event</span><span class="sxs-lookup"><span data-stu-id="636f7-168">Event</span></span>|<span data-ttu-id="636f7-169">イベント ID</span><span class="sxs-lookup"><span data-stu-id="636f7-169">Event ID</span></span>|<span data-ttu-id="636f7-170">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="636f7-170">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="636f7-171">89</span><span class="sxs-lookup"><span data-stu-id="636f7-171">89</span></span>|<span data-ttu-id="636f7-172">MSIL のキャッシュにアクセスがあった。</span><span class="sxs-lookup"><span data-stu-id="636f7-172">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="636f7-173">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="636f7-173">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="636f7-174">フィールド名</span><span class="sxs-lookup"><span data-stu-id="636f7-174">Field name</span></span>|<span data-ttu-id="636f7-175">データ型</span><span class="sxs-lookup"><span data-stu-id="636f7-175">Data type</span></span>|<span data-ttu-id="636f7-176">説明</span><span class="sxs-lookup"><span data-stu-id="636f7-176">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="636f7-177">ModuleID</span><span class="sxs-lookup"><span data-stu-id="636f7-177">ModuleID</span></span>|<span data-ttu-id="636f7-178">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="636f7-178">win:UInt16</span></span>|<span data-ttu-id="636f7-179">モジュールの ID です。</span><span class="sxs-lookup"><span data-stu-id="636f7-179">The module identifier.</span></span>|  
|<span data-ttu-id="636f7-180">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="636f7-180">StubMethodID</span></span>|<span data-ttu-id="636f7-181">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="636f7-181">win:UInt64</span></span>|<span data-ttu-id="636f7-182">スタブのメソッド識別子。</span><span class="sxs-lookup"><span data-stu-id="636f7-182">The stub method identifier.</span></span>|  
|<span data-ttu-id="636f7-183">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="636f7-183">ManagedInteropMethodToken</span></span>|<span data-ttu-id="636f7-184">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="636f7-184">win:UInt32</span></span>|<span data-ttu-id="636f7-185">マネージド相互運用メソッドのトークンです。</span><span class="sxs-lookup"><span data-stu-id="636f7-185">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="636f7-186">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="636f7-186">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="636f7-187">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="636f7-187">win:UnicodeString</span></span>|<span data-ttu-id="636f7-188">マネージド相互運用メソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="636f7-188">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="636f7-189">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="636f7-189">ManagedInteropMethodName</span></span>|<span data-ttu-id="636f7-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="636f7-190">win:UnicodeString</span></span>|<span data-ttu-id="636f7-191">マネージド相互運用メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="636f7-191">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="636f7-192">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="636f7-192">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="636f7-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="636f7-193">win:UnicodeString</span></span>|<span data-ttu-id="636f7-194">マネージド相互運用メソッドのシグネチャ。</span><span class="sxs-lookup"><span data-stu-id="636f7-194">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="636f7-195">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="636f7-195">ClrInstanceID</span></span>|<span data-ttu-id="636f7-196">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="636f7-196">win:UInt16</span></span>|<span data-ttu-id="636f7-197">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="636f7-197">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="636f7-198">関連項目</span><span class="sxs-lookup"><span data-stu-id="636f7-198">See also</span></span>

- [<span data-ttu-id="636f7-199">CLR ETW イベント</span><span class="sxs-lookup"><span data-stu-id="636f7-199">CLR ETW Events</span></span>](clr-etw-events.md)
