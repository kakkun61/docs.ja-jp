---
title: .NET Core と .NET 5 以降でサポートされていない API
titleSuffix: ''
description: .Net Core と .NET 5.0 以降のバージョンで常に例外をスローする .NET API について学習します。
ms.date: 10/13/2020
ms.openlocfilehash: 51d73557a48910d9cb1c4d3cdced34dfe4d849d8
ms.sourcegitcommit: 6bef8abde346c59771a35f4f76bf037ff61c5ba3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2020
ms.locfileid: "94329782"
---
# <a name="apis-that-always-throw-exceptions-on-net-core-and-net-5"></a><span data-ttu-id="89702-103">.NET Core と .NET 5 以降で常に例外をスローする API</span><span class="sxs-lookup"><span data-stu-id="89702-103">APIs that always throw exceptions on .NET Core and .NET 5+</span></span>

<span data-ttu-id="89702-104">次の API を使用すると、プラットフォームのすべてまたはサブセットの .NET 5.0 以降 (.NET Core のすべてのバージョンを含む) で、<xref:System.PlatformNotSupportedException> が常にスローされます。</span><span class="sxs-lookup"><span data-stu-id="89702-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET 5.0 and later versions (including all versions of .NET Core) on all or a subset of platforms.</span></span>

<span data-ttu-id="89702-105">この記事では、影響を受ける API を名前空間別に整理しています。</span><span class="sxs-lookup"><span data-stu-id="89702-105">This article organizes the affected APIs by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="89702-106">この記事は、作業中です。</span><span class="sxs-lookup"><span data-stu-id="89702-106">This article is a work-in-progress.</span></span> <span data-ttu-id="89702-107">.NET 5 以降で例外をスローする API の完全な一覧ではありません。</span><span class="sxs-lookup"><span data-stu-id="89702-107">It is not a complete list of APIs that throw exceptions on .NET 5+.</span></span>
> - <span data-ttu-id="89702-108">この記事には、.NET 5 以降でスローされるバイナリ シリアル化用の明示的なインターフェイス実装は含まれていません。</span><span class="sxs-lookup"><span data-stu-id="89702-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET 5+.</span></span> <span data-ttu-id="89702-109">詳細については、[.NET Core でのバイナリ シリアル化](../../standard/serialization/binary-serialization.md#net-core)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89702-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="89702-110">システム</span><span class="sxs-lookup"><span data-stu-id="89702-110">System</span></span>

| <span data-ttu-id="89702-111">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-111">Member</span></span> | <span data-ttu-id="89702-112">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="89702-113">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="89702-114">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="89702-115">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="89702-116">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="89702-117">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="89702-118">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="89702-119">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="89702-120">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="89702-121">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="89702-122">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="89702-123">System.CodeDom.Compiler</span><span class="sxs-lookup"><span data-stu-id="89702-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="89702-124">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-124">Member</span></span> | <span data-ttu-id="89702-125">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="89702-126">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="89702-127">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="89702-128">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="89702-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="89702-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="89702-130">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-130">Member</span></span> | <span data-ttu-id="89702-131">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="89702-132">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="89702-133">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="89702-134">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="89702-135">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="89702-135">System.Configuration</span></span>

| <span data-ttu-id="89702-136">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-136">Member</span></span> | <span data-ttu-id="89702-137">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="89702-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (すべてのメンバー)</span><span class="sxs-lookup"><span data-stu-id="89702-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="89702-139">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="89702-140">System.Console</span><span class="sxs-lookup"><span data-stu-id="89702-140">System.Console</span></span>

| <span data-ttu-id="89702-141">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-141">Member</span></span> | <span data-ttu-id="89702-142">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="89702-143">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-143">Linux and macOS</span></span> |
| <span data-ttu-id="89702-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="89702-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="89702-145">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-145">Linux and macOS</span></span> |
| <span data-ttu-id="89702-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="89702-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="89702-147">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-147">Linux and macOS</span></span> |
| <span data-ttu-id="89702-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="89702-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="89702-149">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-149">Linux and macOS</span></span> |
| <span data-ttu-id="89702-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get のみ)</span><span class="sxs-lookup"><span data-stu-id="89702-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="89702-151">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="89702-152">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="89702-153">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="89702-154">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-154">Linux and macOS</span></span> |
| <span data-ttu-id="89702-155"><xref:System.Console.Title?displayProperty=nameWithType> (get のみ)</span><span class="sxs-lookup"><span data-stu-id="89702-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="89702-156">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-156">Linux and macOS</span></span> |
| <span data-ttu-id="89702-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="89702-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="89702-158">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-158">Linux and macOS</span></span> |
| <span data-ttu-id="89702-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="89702-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="89702-160">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-160">Linux and macOS</span></span> |
| <span data-ttu-id="89702-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="89702-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="89702-162">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-162">Linux and macOS</span></span> |
| <span data-ttu-id="89702-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="89702-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="89702-164">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="89702-165">System.Data.Common</span><span class="sxs-lookup"><span data-stu-id="89702-165">System.Data.Common</span></span>

| <span data-ttu-id="89702-166">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-166">Member</span></span> | <span data-ttu-id="89702-167">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="89702-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (<xref:System.NotSupportedException> をスローする)</span><span class="sxs-lookup"><span data-stu-id="89702-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="89702-169">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="89702-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="89702-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="89702-171">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-171">Member</span></span> | <span data-ttu-id="89702-172">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="89702-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="89702-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="89702-174">Linux</span><span class="sxs-lookup"><span data-stu-id="89702-174">Linux</span></span> |
| <span data-ttu-id="89702-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="89702-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="89702-176">Linux</span><span class="sxs-lookup"><span data-stu-id="89702-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="89702-177">macOS</span><span class="sxs-lookup"><span data-stu-id="89702-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="89702-178">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="89702-179">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="89702-180">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="89702-181">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="89702-182">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="89702-183">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-183">Linux and macOS</span></span> |
| <span data-ttu-id="89702-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="89702-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="89702-185">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-185">Linux and macOS</span></span> |
| <span data-ttu-id="89702-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get のみ)</span><span class="sxs-lookup"><span data-stu-id="89702-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="89702-187">macOS</span><span class="sxs-lookup"><span data-stu-id="89702-187">macOS</span></span> |
| <span data-ttu-id="89702-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="89702-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="89702-189">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="89702-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="89702-190">System.IO</span></span>

| <span data-ttu-id="89702-191">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-191">Member</span></span> | <span data-ttu-id="89702-192">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="89702-193">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="89702-194">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="89702-195">System.IO.Pipes</span><span class="sxs-lookup"><span data-stu-id="89702-195">System.IO.Pipes</span></span>

| <span data-ttu-id="89702-196">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-196">Member</span></span> | <span data-ttu-id="89702-197">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="89702-198">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="89702-199">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="89702-200">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="89702-201">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-201">Linux and macOS</span></span> |
| <span data-ttu-id="89702-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="89702-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="89702-203">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="89702-204">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="89702-205">System.Media</span><span class="sxs-lookup"><span data-stu-id="89702-205">System.Media</span></span>

| <span data-ttu-id="89702-206">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-206">Member</span></span> | <span data-ttu-id="89702-207">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="89702-208">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="89702-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="89702-209">System.Net</span></span>

| <span data-ttu-id="89702-210">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-210">Member</span></span> | <span data-ttu-id="89702-211">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="89702-212">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="89702-213">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="89702-214">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="89702-215">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="89702-216">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="89702-217">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="89702-218">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="89702-219">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="89702-220">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="89702-221">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="89702-222">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="89702-223">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="89702-224">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="89702-225">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="89702-226">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="89702-227">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="89702-228">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="89702-229">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="89702-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="89702-230">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-230">Member</span></span> | <span data-ttu-id="89702-231">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="89702-232">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="89702-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="89702-233">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="89702-233">System.Net.Sockets</span></span>

| <span data-ttu-id="89702-234">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-234">Member</span></span> | <span data-ttu-id="89702-235">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | <span data-ttu-id="89702-236">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="89702-237">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="89702-238">System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="89702-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="89702-239">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-239">Member</span></span> | <span data-ttu-id="89702-240">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="89702-241">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="89702-242">System.Reflection</span><span class="sxs-lookup"><span data-stu-id="89702-242">System.Reflection</span></span>

| <span data-ttu-id="89702-243">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-243">Member</span></span> | <span data-ttu-id="89702-244">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="89702-245">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="89702-246">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="89702-247">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="89702-248">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | <span data-ttu-id="89702-249">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="89702-250">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="89702-251">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="89702-252">System.Runtime.CompilerServices</span><span class="sxs-lookup"><span data-stu-id="89702-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="89702-253">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-253">Member</span></span> | <span data-ttu-id="89702-254">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="89702-255">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="89702-256">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="89702-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="89702-257">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-257">Member</span></span> | <span data-ttu-id="89702-258">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="89702-259">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="89702-260">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="89702-261">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="89702-262">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="89702-263">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="89702-264">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="89702-265">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="89702-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="89702-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="89702-267">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-267">Member</span></span> | <span data-ttu-id="89702-268">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="89702-269">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="89702-270">System.Security</span><span class="sxs-lookup"><span data-stu-id="89702-270">System.Security</span></span>

| <span data-ttu-id="89702-271">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-271">Member</span></span> | <span data-ttu-id="89702-272">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="89702-273">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="89702-274">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="89702-275">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="89702-276">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="89702-277">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="89702-278">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="89702-279">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="89702-280">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="89702-281">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="89702-282">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="89702-283">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="89702-284">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="89702-285">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="89702-286">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="89702-287">System.Security.Claims</span><span class="sxs-lookup"><span data-stu-id="89702-287">System.Security.Claims</span></span>

| <span data-ttu-id="89702-288">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-288">Member</span></span> | <span data-ttu-id="89702-289">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="89702-290">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="89702-291">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | <span data-ttu-id="89702-292">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="89702-293">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="89702-294">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="89702-295">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="89702-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="89702-296">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-296">Member</span></span> | <span data-ttu-id="89702-297">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="89702-298">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | <span data-ttu-id="89702-299">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="89702-300">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="89702-301">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="89702-302">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="89702-303">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="89702-304">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="89702-305">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="89702-306">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="89702-307">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="89702-308">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="89702-309">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="89702-310">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="89702-311">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="89702-312">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="89702-313">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="89702-314">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="89702-315">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="89702-316">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="89702-317">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="89702-318">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="89702-319">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="89702-320">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="89702-321">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="89702-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="89702-322">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="89702-323">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="89702-324">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="89702-325">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="89702-326">System.Security.Cryptography.Pkcs</span><span class="sxs-lookup"><span data-stu-id="89702-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="89702-327">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-327">Member</span></span> | <span data-ttu-id="89702-328">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | <span data-ttu-id="89702-329">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="89702-330">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-330">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="89702-331">System.Security.Cryptography.X509Certificates</span><span class="sxs-lookup"><span data-stu-id="89702-331">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="89702-332">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-332">Member</span></span> | <span data-ttu-id="89702-333">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-333">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="89702-334">All</span><span class="sxs-lookup"><span data-stu-id="89702-334">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="89702-335">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="89702-336">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-336">All</span></span> |
| <span data-ttu-id="89702-337"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="89702-337"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="89702-338">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-338">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="89702-339">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="89702-339">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="89702-340">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-340">Member</span></span> | <span data-ttu-id="89702-341">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-341">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="89702-342">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-342">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="89702-343">System.Security.Policy</span><span class="sxs-lookup"><span data-stu-id="89702-343">System.Security.Policy</span></span>

| <span data-ttu-id="89702-344">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-344">Member</span></span> | <span data-ttu-id="89702-345">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-345">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="89702-346">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-346">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="89702-347">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="89702-347">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="89702-348">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-348">Member</span></span> | <span data-ttu-id="89702-349">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-349">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="89702-350">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-350">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="89702-351">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="89702-351">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="89702-352">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-352">Member</span></span> | <span data-ttu-id="89702-353">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-353">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="89702-354">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-354">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="89702-355">System.Threading</span><span class="sxs-lookup"><span data-stu-id="89702-355">System.Threading</span></span>

| <span data-ttu-id="89702-356">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-356">Member</span></span> | <span data-ttu-id="89702-357">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-357">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="89702-358">All</span><span class="sxs-lookup"><span data-stu-id="89702-358">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="89702-359">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-359">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="89702-360">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-360">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="89702-361">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-361">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="89702-362">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-362">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="89702-363">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-363">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="89702-364">System.Xml</span><span class="sxs-lookup"><span data-stu-id="89702-364">System.Xml</span></span>

| <span data-ttu-id="89702-365">メンバー</span><span class="sxs-lookup"><span data-stu-id="89702-365">Member</span></span> | <span data-ttu-id="89702-366">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89702-366">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="89702-367">All</span><span class="sxs-lookup"><span data-stu-id="89702-367">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="89702-368">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="89702-369">すべて</span><span class="sxs-lookup"><span data-stu-id="89702-369">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="89702-370">関連項目</span><span class="sxs-lookup"><span data-stu-id="89702-370">See also</span></span>

- [<span data-ttu-id="89702-371">.NET Framework から .NET Core への移行の破壊的変更</span><span class="sxs-lookup"><span data-stu-id="89702-371">Breaking changes for migration from .NET Framework to .NET Core</span></span>](fx-core.md)
- [<span data-ttu-id="89702-372">.NET Core でのバイナリ シリアル化</span><span class="sxs-lookup"><span data-stu-id="89702-372">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="89702-373">.NET Portability Analyzer</span><span class="sxs-lookup"><span data-stu-id="89702-373">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
