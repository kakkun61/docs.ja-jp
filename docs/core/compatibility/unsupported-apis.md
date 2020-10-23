---
title: .NET Core と .NET 5 以降でサポートされていない API
titleSuffix: ''
description: .Net Core と .NET 5.0 以降のバージョンで常に例外をスローする .NET API について学習します。
ms.date: 10/13/2020
ms.openlocfilehash: 0164ebff51de82d548a02f9fde754c1052a9c2b5
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159340"
---
# <a name="apis-that-always-throw-exceptions-on-net-core-and-net-5"></a><span data-ttu-id="57f41-103">.NET Core と .NET 5 以降で常に例外をスローする API</span><span class="sxs-lookup"><span data-stu-id="57f41-103">APIs that always throw exceptions on .NET Core and .NET 5+</span></span>

<span data-ttu-id="57f41-104">次の API を使用すると、プラットフォームのすべてまたはサブセットの .NET 5.0 以降 (.NET Core のすべてのバージョンを含む) で、<xref:System.PlatformNotSupportedException> が常にスローされます。</span><span class="sxs-lookup"><span data-stu-id="57f41-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET 5.0 and later versions (including all versions of .NET Core) on all or a subset of platforms.</span></span>

<span data-ttu-id="57f41-105">この記事では、影響を受ける API を名前空間別に整理しています。</span><span class="sxs-lookup"><span data-stu-id="57f41-105">This article organizes the affected APIs by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="57f41-106">この記事は、作業中です。</span><span class="sxs-lookup"><span data-stu-id="57f41-106">This article is a work-in-progress.</span></span> <span data-ttu-id="57f41-107">.NET 5 以降で例外をスローする API の完全な一覧ではありません。</span><span class="sxs-lookup"><span data-stu-id="57f41-107">It is not a complete list of APIs that throw exceptions on .NET 5+.</span></span>
> - <span data-ttu-id="57f41-108">この記事には、.NET 5 以降でスローされるバイナリ シリアル化用の明示的なインターフェイス実装は含まれていません。</span><span class="sxs-lookup"><span data-stu-id="57f41-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET 5+.</span></span> <span data-ttu-id="57f41-109">詳細については、[.NET Core でのバイナリ シリアル化](../../standard/serialization/binary-serialization.md#net-core)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57f41-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="57f41-110">システム</span><span class="sxs-lookup"><span data-stu-id="57f41-110">System</span></span>

| <span data-ttu-id="57f41-111">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-111">Member</span></span> | <span data-ttu-id="57f41-112">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="57f41-113">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="57f41-114">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="57f41-115">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="57f41-116">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="57f41-117">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="57f41-118">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="57f41-119">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="57f41-120">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="57f41-121">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="57f41-122">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="57f41-123">System.CodeDom.Compiler</span><span class="sxs-lookup"><span data-stu-id="57f41-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="57f41-124">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-124">Member</span></span> | <span data-ttu-id="57f41-125">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="57f41-126">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="57f41-127">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="57f41-128">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="57f41-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="57f41-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="57f41-130">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-130">Member</span></span> | <span data-ttu-id="57f41-131">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="57f41-132">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="57f41-133">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="57f41-134">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="57f41-135">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="57f41-135">System.Configuration</span></span>

| <span data-ttu-id="57f41-136">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-136">Member</span></span> | <span data-ttu-id="57f41-137">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="57f41-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (すべてのメンバー)</span><span class="sxs-lookup"><span data-stu-id="57f41-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="57f41-139">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="57f41-140">System.Console</span><span class="sxs-lookup"><span data-stu-id="57f41-140">System.Console</span></span>

| <span data-ttu-id="57f41-141">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-141">Member</span></span> | <span data-ttu-id="57f41-142">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="57f41-143">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-143">Linux and macOS</span></span> |
| <span data-ttu-id="57f41-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="57f41-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="57f41-145">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-145">Linux and macOS</span></span> |
| <span data-ttu-id="57f41-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="57f41-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="57f41-147">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-147">Linux and macOS</span></span> |
| <span data-ttu-id="57f41-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="57f41-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="57f41-149">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-149">Linux and macOS</span></span> |
| <span data-ttu-id="57f41-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get のみ)</span><span class="sxs-lookup"><span data-stu-id="57f41-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="57f41-151">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="57f41-152">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="57f41-153">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="57f41-154">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-154">Linux and macOS</span></span> |
| <span data-ttu-id="57f41-155"><xref:System.Console.Title?displayProperty=nameWithType> (get のみ)</span><span class="sxs-lookup"><span data-stu-id="57f41-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="57f41-156">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-156">Linux and macOS</span></span> |
| <span data-ttu-id="57f41-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="57f41-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="57f41-158">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-158">Linux and macOS</span></span> |
| <span data-ttu-id="57f41-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="57f41-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="57f41-160">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-160">Linux and macOS</span></span> |
| <span data-ttu-id="57f41-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="57f41-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="57f41-162">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-162">Linux and macOS</span></span> |
| <span data-ttu-id="57f41-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="57f41-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="57f41-164">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="57f41-165">System.Data.Common</span><span class="sxs-lookup"><span data-stu-id="57f41-165">System.Data.Common</span></span>

| <span data-ttu-id="57f41-166">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-166">Member</span></span> | <span data-ttu-id="57f41-167">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="57f41-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (<xref:System.NotSupportedException> をスローする)</span><span class="sxs-lookup"><span data-stu-id="57f41-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="57f41-169">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="57f41-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="57f41-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="57f41-171">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-171">Member</span></span> | <span data-ttu-id="57f41-172">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="57f41-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="57f41-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="57f41-174">Linux</span><span class="sxs-lookup"><span data-stu-id="57f41-174">Linux</span></span> |
| <span data-ttu-id="57f41-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="57f41-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="57f41-176">Linux</span><span class="sxs-lookup"><span data-stu-id="57f41-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="57f41-177">macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="57f41-178">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="57f41-179">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="57f41-180">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="57f41-181">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="57f41-182">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="57f41-183">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-183">Linux and macOS</span></span> |
| <span data-ttu-id="57f41-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="57f41-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="57f41-185">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-185">Linux and macOS</span></span> |
| <span data-ttu-id="57f41-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get のみ)</span><span class="sxs-lookup"><span data-stu-id="57f41-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="57f41-187">macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-187">macOS</span></span> |
| <span data-ttu-id="57f41-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="57f41-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="57f41-189">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="57f41-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="57f41-190">System.IO</span></span>

| <span data-ttu-id="57f41-191">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-191">Member</span></span> | <span data-ttu-id="57f41-192">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="57f41-193">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="57f41-194">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="57f41-195">System.IO.Pipes</span><span class="sxs-lookup"><span data-stu-id="57f41-195">System.IO.Pipes</span></span>

| <span data-ttu-id="57f41-196">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-196">Member</span></span> | <span data-ttu-id="57f41-197">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="57f41-198">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="57f41-199">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="57f41-200">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="57f41-201">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-201">Linux and macOS</span></span> |
| <span data-ttu-id="57f41-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="57f41-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="57f41-203">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="57f41-204">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="57f41-205">System.Media</span><span class="sxs-lookup"><span data-stu-id="57f41-205">System.Media</span></span>

| <span data-ttu-id="57f41-206">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-206">Member</span></span> | <span data-ttu-id="57f41-207">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="57f41-208">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="57f41-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="57f41-209">System.Net</span></span>

| <span data-ttu-id="57f41-210">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-210">Member</span></span> | <span data-ttu-id="57f41-211">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="57f41-212">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="57f41-213">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="57f41-214">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="57f41-215">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="57f41-216">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="57f41-217">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="57f41-218">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="57f41-219">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="57f41-220">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="57f41-221">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="57f41-222">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="57f41-223">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="57f41-224">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="57f41-225">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="57f41-226">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="57f41-227">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="57f41-228">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="57f41-229">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="57f41-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="57f41-230">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-230">Member</span></span> | <span data-ttu-id="57f41-231">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="57f41-232">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="57f41-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="57f41-233">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="57f41-233">System.Net.Sockets</span></span>

| <span data-ttu-id="57f41-234">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-234">Member</span></span> | <span data-ttu-id="57f41-235">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | <span data-ttu-id="57f41-236">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="57f41-237">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="57f41-238">System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="57f41-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="57f41-239">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-239">Member</span></span> | <span data-ttu-id="57f41-240">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="57f41-241">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="57f41-242">System.Reflection</span><span class="sxs-lookup"><span data-stu-id="57f41-242">System.Reflection</span></span>

| <span data-ttu-id="57f41-243">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-243">Member</span></span> | <span data-ttu-id="57f41-244">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="57f41-245">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="57f41-246">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="57f41-247">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="57f41-248">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | <span data-ttu-id="57f41-249">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="57f41-250">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="57f41-251">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="57f41-252">System.Runtime.CompilerServices</span><span class="sxs-lookup"><span data-stu-id="57f41-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="57f41-253">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-253">Member</span></span> | <span data-ttu-id="57f41-254">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="57f41-255">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="57f41-256">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="57f41-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="57f41-257">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-257">Member</span></span> | <span data-ttu-id="57f41-258">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="57f41-259">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="57f41-260">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="57f41-261">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="57f41-262">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="57f41-263">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="57f41-264">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="57f41-265">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="57f41-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="57f41-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="57f41-267">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-267">Member</span></span> | <span data-ttu-id="57f41-268">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="57f41-269">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="57f41-270">System.Security</span><span class="sxs-lookup"><span data-stu-id="57f41-270">System.Security</span></span>

| <span data-ttu-id="57f41-271">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-271">Member</span></span> | <span data-ttu-id="57f41-272">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="57f41-273">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="57f41-274">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="57f41-275">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="57f41-276">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="57f41-277">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="57f41-278">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="57f41-279">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="57f41-280">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="57f41-281">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="57f41-282">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="57f41-283">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="57f41-284">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="57f41-285">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="57f41-286">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="57f41-287">System.Security.Claims</span><span class="sxs-lookup"><span data-stu-id="57f41-287">System.Security.Claims</span></span>

| <span data-ttu-id="57f41-288">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-288">Member</span></span> | <span data-ttu-id="57f41-289">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor> | <span data-ttu-id="57f41-290">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="57f41-291">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | <span data-ttu-id="57f41-292">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="57f41-293">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="57f41-294">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="57f41-295">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="57f41-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="57f41-296">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-296">Member</span></span> | <span data-ttu-id="57f41-297">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="57f41-298">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | <span data-ttu-id="57f41-299">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="57f41-300">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="57f41-301">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="57f41-302">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="57f41-303">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="57f41-304">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="57f41-305">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="57f41-306">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="57f41-307">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="57f41-308">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="57f41-309">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="57f41-310">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="57f41-311">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="57f41-312">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="57f41-313">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="57f41-314">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="57f41-315">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="57f41-316">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="57f41-317">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="57f41-318">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="57f41-319">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="57f41-320">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="57f41-321">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="57f41-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="57f41-322">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="57f41-323">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="57f41-324">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="57f41-325">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="57f41-326">System.Security.Cryptography.Pkcs</span><span class="sxs-lookup"><span data-stu-id="57f41-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="57f41-327">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-327">Member</span></span> | <span data-ttu-id="57f41-328">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | <span data-ttu-id="57f41-329">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="57f41-330">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-330">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="57f41-331">System.Security.Cryptography.X509Certificates</span><span class="sxs-lookup"><span data-stu-id="57f41-331">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="57f41-332">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-332">Member</span></span> | <span data-ttu-id="57f41-333">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-333">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="57f41-334">All</span><span class="sxs-lookup"><span data-stu-id="57f41-334">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="57f41-335">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="57f41-336">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-336">All</span></span> |
| <span data-ttu-id="57f41-337"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="57f41-337"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="57f41-338">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-338">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="57f41-339">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="57f41-339">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="57f41-340">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-340">Member</span></span> | <span data-ttu-id="57f41-341">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-341">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="57f41-342">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-342">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="57f41-343">System.Security.Policy</span><span class="sxs-lookup"><span data-stu-id="57f41-343">System.Security.Policy</span></span>

| <span data-ttu-id="57f41-344">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-344">Member</span></span> | <span data-ttu-id="57f41-345">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-345">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="57f41-346">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-346">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="57f41-347">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="57f41-347">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="57f41-348">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-348">Member</span></span> | <span data-ttu-id="57f41-349">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-349">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="57f41-350">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-350">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="57f41-351">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="57f41-351">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="57f41-352">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-352">Member</span></span> | <span data-ttu-id="57f41-353">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-353">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="57f41-354">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-354">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="57f41-355">System.Threading</span><span class="sxs-lookup"><span data-stu-id="57f41-355">System.Threading</span></span>

| <span data-ttu-id="57f41-356">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-356">Member</span></span> | <span data-ttu-id="57f41-357">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-357">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="57f41-358">All</span><span class="sxs-lookup"><span data-stu-id="57f41-358">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="57f41-359">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-359">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="57f41-360">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-360">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="57f41-361">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-361">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="57f41-362">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-362">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="57f41-363">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-363">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="57f41-364">System.Xml</span><span class="sxs-lookup"><span data-stu-id="57f41-364">System.Xml</span></span>

| <span data-ttu-id="57f41-365">メンバー</span><span class="sxs-lookup"><span data-stu-id="57f41-365">Member</span></span> | <span data-ttu-id="57f41-366">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="57f41-366">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="57f41-367">All</span><span class="sxs-lookup"><span data-stu-id="57f41-367">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="57f41-368">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="57f41-369">すべて</span><span class="sxs-lookup"><span data-stu-id="57f41-369">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="57f41-370">関連項目</span><span class="sxs-lookup"><span data-stu-id="57f41-370">See also</span></span>

- [<span data-ttu-id="57f41-371">.NET Framework から .NET Core への移行の破壊的変更</span><span class="sxs-lookup"><span data-stu-id="57f41-371">Breaking changes for migration from .NET Framework to .NET Core</span></span>](fx-core.md)
- [<span data-ttu-id="57f41-372">.NET Core でのバイナリ シリアル化</span><span class="sxs-lookup"><span data-stu-id="57f41-372">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="57f41-373">.NET Portability Analyzer</span><span class="sxs-lookup"><span data-stu-id="57f41-373">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
