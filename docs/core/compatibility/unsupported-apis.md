---
title: .NET Core と .NET 5 以降でサポートされていない API
titleSuffix: ''
description: .Net Core と .NET 5.0 以降のバージョンで常に例外をスローする .NET API について学習します。
ms.date: 10/13/2020
ms.openlocfilehash: 1bd41192d0d6752d2b659da9fb6387dac321b2c3
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/16/2020
ms.locfileid: "97593267"
---
# <a name="apis-that-always-throw-exceptions-on-net-core-and-net-5"></a><span data-ttu-id="2f20f-103">.NET Core と .NET 5 以降で常に例外をスローする API</span><span class="sxs-lookup"><span data-stu-id="2f20f-103">APIs that always throw exceptions on .NET Core and .NET 5+</span></span>

<span data-ttu-id="2f20f-104">次の API を使用すると、プラットフォームのすべてまたはサブセットの .NET 5.0 以降 (.NET Core のすべてのバージョンを含む) で、<xref:System.PlatformNotSupportedException> が常にスローされます。</span><span class="sxs-lookup"><span data-stu-id="2f20f-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET 5.0 and later versions (including all versions of .NET Core) on all or a subset of platforms.</span></span>

<span data-ttu-id="2f20f-105">この記事では、影響を受ける API を名前空間別に整理しています。</span><span class="sxs-lookup"><span data-stu-id="2f20f-105">This article organizes the affected APIs by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="2f20f-106">この記事は、作業中です。</span><span class="sxs-lookup"><span data-stu-id="2f20f-106">This article is a work-in-progress.</span></span> <span data-ttu-id="2f20f-107">.NET 5 以降で例外をスローする API の完全な一覧ではありません。</span><span class="sxs-lookup"><span data-stu-id="2f20f-107">It is not a complete list of APIs that throw exceptions on .NET 5+.</span></span>
> - <span data-ttu-id="2f20f-108">この記事には、.NET 5 以降でスローされるバイナリ シリアル化用の明示的なインターフェイス実装は含まれていません。</span><span class="sxs-lookup"><span data-stu-id="2f20f-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET 5+.</span></span> <span data-ttu-id="2f20f-109">詳細については、[.NET Core でのバイナリ シリアル化](../../standard/serialization/binary-serialization.md#net-core)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f20f-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="2f20f-110">システム</span><span class="sxs-lookup"><span data-stu-id="2f20f-110">System</span></span>

| <span data-ttu-id="2f20f-111">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-111">Member</span></span> | <span data-ttu-id="2f20f-112">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="2f20f-113">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-114">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="2f20f-115">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="2f20f-116">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-117">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="2f20f-118">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="2f20f-119">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="2f20f-120">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-121">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-122">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="2f20f-123">System.CodeDom.Compiler</span><span class="sxs-lookup"><span data-stu-id="2f20f-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="2f20f-124">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-124">Member</span></span> | <span data-ttu-id="2f20f-125">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="2f20f-126">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="2f20f-127">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="2f20f-128">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="2f20f-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="2f20f-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="2f20f-130">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-130">Member</span></span> | <span data-ttu-id="2f20f-131">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2f20f-132">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-133">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-134">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="2f20f-135">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="2f20f-135">System.Configuration</span></span>

| <span data-ttu-id="2f20f-136">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-136">Member</span></span> | <span data-ttu-id="2f20f-137">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="2f20f-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (すべてのメンバー)</span><span class="sxs-lookup"><span data-stu-id="2f20f-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="2f20f-139">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="2f20f-140">System.Console</span><span class="sxs-lookup"><span data-stu-id="2f20f-140">System.Console</span></span>

| <span data-ttu-id="2f20f-141">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-141">Member</span></span> | <span data-ttu-id="2f20f-142">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="2f20f-143">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-143">Linux and macOS</span></span> |
| <span data-ttu-id="2f20f-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="2f20f-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2f20f-145">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-145">Linux and macOS</span></span> |
| <span data-ttu-id="2f20f-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="2f20f-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2f20f-147">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-147">Linux and macOS</span></span> |
| <span data-ttu-id="2f20f-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="2f20f-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2f20f-149">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-149">Linux and macOS</span></span> |
| <span data-ttu-id="2f20f-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get のみ)</span><span class="sxs-lookup"><span data-stu-id="2f20f-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="2f20f-151">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="2f20f-152">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="2f20f-153">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="2f20f-154">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-154">Linux and macOS</span></span> |
| <span data-ttu-id="2f20f-155"><xref:System.Console.Title?displayProperty=nameWithType> (get のみ)</span><span class="sxs-lookup"><span data-stu-id="2f20f-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="2f20f-156">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-156">Linux and macOS</span></span> |
| <span data-ttu-id="2f20f-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="2f20f-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2f20f-158">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-158">Linux and macOS</span></span> |
| <span data-ttu-id="2f20f-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="2f20f-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2f20f-160">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-160">Linux and macOS</span></span> |
| <span data-ttu-id="2f20f-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="2f20f-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2f20f-162">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-162">Linux and macOS</span></span> |
| <span data-ttu-id="2f20f-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="2f20f-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2f20f-164">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="2f20f-165">System.Data.Common</span><span class="sxs-lookup"><span data-stu-id="2f20f-165">System.Data.Common</span></span>

| <span data-ttu-id="2f20f-166">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-166">Member</span></span> | <span data-ttu-id="2f20f-167">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="2f20f-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (<xref:System.NotSupportedException> をスローする)</span><span class="sxs-lookup"><span data-stu-id="2f20f-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="2f20f-169">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="2f20f-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="2f20f-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="2f20f-171">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-171">Member</span></span> | <span data-ttu-id="2f20f-172">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="2f20f-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="2f20f-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2f20f-174">Linux</span><span class="sxs-lookup"><span data-stu-id="2f20f-174">Linux</span></span> |
| <span data-ttu-id="2f20f-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="2f20f-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2f20f-176">Linux</span><span class="sxs-lookup"><span data-stu-id="2f20f-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="2f20f-177">macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="2f20f-178">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start(System.String,System.String,System.String,System.Security.SecureString,System.String)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-179">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start(System.String,System.String,System.Security.SecureString,System.String)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-180">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="2f20f-181">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="2f20f-182">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="2f20f-183">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-183">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="2f20f-184">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-184">Linux and macOS</span></span> |
| <span data-ttu-id="2f20f-185"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="2f20f-185"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2f20f-186">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-186">Linux and macOS</span></span> |
| <span data-ttu-id="2f20f-187"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get のみ)</span><span class="sxs-lookup"><span data-stu-id="2f20f-187"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="2f20f-188">macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-188">macOS</span></span> |
| <span data-ttu-id="2f20f-189"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="2f20f-189"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2f20f-190">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-190">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="2f20f-191">System.IO</span><span class="sxs-lookup"><span data-stu-id="2f20f-191">System.IO</span></span>

| <span data-ttu-id="2f20f-192">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-192">Member</span></span> | <span data-ttu-id="2f20f-193">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-193">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2f20f-194">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-194">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-195">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-195">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="2f20f-196">System.IO.Pipes</span><span class="sxs-lookup"><span data-stu-id="2f20f-196">System.IO.Pipes</span></span>

| <span data-ttu-id="2f20f-197">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-197">Member</span></span> | <span data-ttu-id="2f20f-198">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-198">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="2f20f-199">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="2f20f-200">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="2f20f-201">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-201">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="2f20f-202">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-202">Linux and macOS</span></span> |
| <span data-ttu-id="2f20f-203"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="2f20f-203"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2f20f-204">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-204">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="2f20f-205">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-205">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="2f20f-206">System.Media</span><span class="sxs-lookup"><span data-stu-id="2f20f-206">System.Media</span></span>

| <span data-ttu-id="2f20f-207">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-207">Member</span></span> | <span data-ttu-id="2f20f-208">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-208">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2f20f-209">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-209">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="2f20f-210">System.Net</span><span class="sxs-lookup"><span data-stu-id="2f20f-210">System.Net</span></span>

| <span data-ttu-id="2f20f-211">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-211">Member</span></span> | <span data-ttu-id="2f20f-212">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-212">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-213">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-213">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-214">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-214">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2f20f-215">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-215">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-216">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-216">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2f20f-217">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-217">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-218">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2f20f-219">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-219">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-220">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2f20f-221">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-221">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-222">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-222">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2f20f-223">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-223">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="2f20f-224">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-224">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="2f20f-225">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-225">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2f20f-226">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-226">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-227">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-227">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2f20f-228">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-228">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-229">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-229">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="2f20f-230">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="2f20f-230">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="2f20f-231">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-231">Member</span></span> | <span data-ttu-id="2f20f-232">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-232">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="2f20f-233">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="2f20f-233">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="2f20f-234">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="2f20f-234">System.Net.Sockets</span></span>

| <span data-ttu-id="2f20f-235">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-235">Member</span></span> | <span data-ttu-id="2f20f-236">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-236">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | <span data-ttu-id="2f20f-237">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-237">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-238">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-238">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="2f20f-239">System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="2f20f-239">System.Net.WebSockets</span></span>

| <span data-ttu-id="2f20f-240">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-240">Member</span></span> | <span data-ttu-id="2f20f-241">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-241">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="2f20f-242">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-242">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="2f20f-243">System.Reflection</span><span class="sxs-lookup"><span data-stu-id="2f20f-243">System.Reflection</span></span>

| <span data-ttu-id="2f20f-244">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-244">Member</span></span> | <span data-ttu-id="2f20f-245">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-245">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="2f20f-246">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-246">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-247">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-248">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-248">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-249">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | <span data-ttu-id="2f20f-250">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2f20f-251">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-251">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="2f20f-252">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-252">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="2f20f-253">System.Runtime.CompilerServices</span><span class="sxs-lookup"><span data-stu-id="2f20f-253">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="2f20f-254">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-254">Member</span></span> | <span data-ttu-id="2f20f-255">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-255">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="2f20f-256">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-256">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="2f20f-257">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="2f20f-257">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="2f20f-258">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-258">Member</span></span> | <span data-ttu-id="2f20f-259">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-259">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-260">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="2f20f-261">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-262">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-262">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-263">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-263">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-264">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-265">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-265">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-266">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-266">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="2f20f-267">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="2f20f-267">System.Runtime.Serialization</span></span>

| <span data-ttu-id="2f20f-268">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-268">Member</span></span> | <span data-ttu-id="2f20f-269">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-269">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="2f20f-270">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-270">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="2f20f-271">System.Security</span><span class="sxs-lookup"><span data-stu-id="2f20f-271">System.Security</span></span>

| <span data-ttu-id="2f20f-272">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-272">Member</span></span> | <span data-ttu-id="2f20f-273">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-273">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="2f20f-274">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-274">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="2f20f-275">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-275">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-276">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-276">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="2f20f-277">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-277">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="2f20f-278">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-278">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="2f20f-279">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-279">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="2f20f-280">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-280">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="2f20f-281">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="2f20f-282">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-282">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="2f20f-283">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-283">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="2f20f-284">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-284">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-285">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="2f20f-286">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-286">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="2f20f-287">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-287">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="2f20f-288">System.Security.Claims</span><span class="sxs-lookup"><span data-stu-id="2f20f-288">System.Security.Claims</span></span>

| <span data-ttu-id="2f20f-289">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-289">Member</span></span> | <span data-ttu-id="2f20f-290">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-290">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2f20f-291">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-292">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | <span data-ttu-id="2f20f-293">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2f20f-294">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-294">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-295">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-295">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="2f20f-296">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="2f20f-296">System.Security.Cryptography</span></span>

| <span data-ttu-id="2f20f-297">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-297">Member</span></span> | <span data-ttu-id="2f20f-298">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-298">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-299">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-299">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | <span data-ttu-id="2f20f-300">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="2f20f-301">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="2f20f-302">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="2f20f-303">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="2f20f-304">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="2f20f-305">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="2f20f-306">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="2f20f-307">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="2f20f-308">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="2f20f-309">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="2f20f-310">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="2f20f-311">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="2f20f-312">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-312">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="2f20f-313">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="2f20f-314">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-315">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="2f20f-316">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="2f20f-317">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-317">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="2f20f-318">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="2f20f-319">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-319">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-320">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-320">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="2f20f-321">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="2f20f-322">Linux と macOS</span><span class="sxs-lookup"><span data-stu-id="2f20f-322">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="2f20f-323">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-323">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="2f20f-324">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="2f20f-325">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-325">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-326">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-326">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="2f20f-327">System.Security.Cryptography.Pkcs</span><span class="sxs-lookup"><span data-stu-id="2f20f-327">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="2f20f-328">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-328">Member</span></span> | <span data-ttu-id="2f20f-329">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-329">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | <span data-ttu-id="2f20f-330">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="2f20f-331">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="2f20f-332">System.Security.Cryptography.X509Certificates</span><span class="sxs-lookup"><span data-stu-id="2f20f-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="2f20f-333">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-333">Member</span></span> | <span data-ttu-id="2f20f-334">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2f20f-335">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="2f20f-336">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2f20f-337">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-337">All</span></span> |
| <span data-ttu-id="2f20f-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set のみ)</span><span class="sxs-lookup"><span data-stu-id="2f20f-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="2f20f-339">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="2f20f-340">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="2f20f-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="2f20f-341">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-341">Member</span></span> | <span data-ttu-id="2f20f-342">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2f20f-343">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="2f20f-344">System.Security.Policy</span><span class="sxs-lookup"><span data-stu-id="2f20f-344">System.Security.Policy</span></span>

| <span data-ttu-id="2f20f-345">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-345">Member</span></span> | <span data-ttu-id="2f20f-346">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-347">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="2f20f-348">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="2f20f-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="2f20f-349">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-349">Member</span></span> | <span data-ttu-id="2f20f-350">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="2f20f-351">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="2f20f-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="2f20f-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="2f20f-353">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-353">Member</span></span> | <span data-ttu-id="2f20f-354">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="2f20f-355">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="2f20f-356">System.Threading</span><span class="sxs-lookup"><span data-stu-id="2f20f-356">System.Threading</span></span>

| <span data-ttu-id="2f20f-357">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-357">Member</span></span> | <span data-ttu-id="2f20f-358">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-359">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-360">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="2f20f-361">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="2f20f-362">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="2f20f-363">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="2f20f-364">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="2f20f-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="2f20f-365">System.Xml</span></span>

| <span data-ttu-id="2f20f-366">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f20f-366">Member</span></span> | <span data-ttu-id="2f20f-367">スローするプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="2f20f-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-368">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-369">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="2f20f-370">すべて</span><span class="sxs-lookup"><span data-stu-id="2f20f-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="2f20f-371">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f20f-371">See also</span></span>

- [<span data-ttu-id="2f20f-372">.NET Framework から .NET Core への移行の破壊的変更</span><span class="sxs-lookup"><span data-stu-id="2f20f-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](fx-core.md)
- [<span data-ttu-id="2f20f-373">.NET Core でのバイナリ シリアル化</span><span class="sxs-lookup"><span data-stu-id="2f20f-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="2f20f-374">.NET Portability Analyzer</span><span class="sxs-lookup"><span data-stu-id="2f20f-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
