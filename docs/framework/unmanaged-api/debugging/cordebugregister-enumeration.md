---
title: CorDebugRegister 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugRegister
helpviewer_keywords:
- CorDebugRegister enumeration [.NET Framework debugging]
ms.assetid: 003bb138-7960-4291-ac88-0d87e470ff70
topic_type:
- apiref
ms.openlocfilehash: 85df98e83396c9439c28dd41a3ffa02b820c9c3e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726055"
---
# <a name="cordebugregister-enumeration"></a><span data-ttu-id="4efb3-102">CorDebugRegister 列挙型</span><span class="sxs-lookup"><span data-stu-id="4efb3-102">CorDebugRegister Enumeration</span></span>

<span data-ttu-id="4efb3-103">指定されたプロセッサ アーキテクチャに関連付けられたレジスタを指定します。</span><span class="sxs-lookup"><span data-stu-id="4efb3-103">Specifies the registers associated with a given processor architecture.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4efb3-104">構文</span><span class="sxs-lookup"><span data-stu-id="4efb3-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugRegister {  
  
    REGISTER_INSTRUCTION_POINTER = 0,  
    REGISTER_STACK_POINTER,  
    REGISTER_FRAME_POINTER,  
  
    REGISTER_X86_EIP = 0,  
    REGISTER_X86_ESP,  
    REGISTER_X86_EBP,  
  
    REGISTER_X86_EAX,  
    REGISTER_X86_ECX,  
    REGISTER_X86_EDX,  
    REGISTER_X86_EBX,  
  
    REGISTER_X86_ESI,  
    REGISTER_X86_EDI,  
  
    REGISTER_X86_FPSTACK_0,  
    REGISTER_X86_FPSTACK_1,  
    REGISTER_X86_FPSTACK_2,  
    REGISTER_X86_FPSTACK_3,  
    REGISTER_X86_FPSTACK_4,  
    REGISTER_X86_FPSTACK_5,  
    REGISTER_X86_FPSTACK_6,  
    REGISTER_X86_FPSTACK_7,  
  
    REGISTER_AMD64_RIP = 0,  
    REGISTER_AMD64_RSP,  
    REGISTER_AMD64_RBP,  
    REGISTER_AMD64_RAX,  
    REGISTER_AMD64_RCX,  
    REGISTER_AMD64_RDX,  
    REGISTER_AMD64_RBX,  
    REGISTER_AMD64_RSI,  
    REGISTER_AMD64_RDI,  
    REGISTER_AMD64_R8,  
    REGISTER_AMD64_R9,  
    REGISTER_AMD64_R10,  
    REGISTER_AMD64_R11,  
    REGISTER_AMD64_R12,  
    REGISTER_AMD64_R13,  
    REGISTER_AMD64_R14,  
    REGISTER_AMD64_R15,  
  
    REGISTER_AMD64_XMM0,  
    REGISTER_AMD64_XMM1,  
    REGISTER_AMD64_XMM2,  
    REGISTER_AMD64_XMM3,  
    REGISTER_AMD64_XMM4,  
    REGISTER_AMD64_XMM5,  
    REGISTER_AMD64_XMM6,  
    REGISTER_AMD64_XMM7,  
    REGISTER_AMD64_XMM8,  
    REGISTER_AMD64_XMM9,  
    REGISTER_AMD64_XMM10,  
    REGISTER_AMD64_XMM11,  
    REGISTER_AMD64_XMM12,  
    REGISTER_AMD64_XMM13,  
    REGISTER_AMD64_XMM14,  
    REGISTER_AMD64_XMM15,  
  
    REGISTER_IA64_BSP = REGISTER_FRAME_POINTER,  
    REGISTER_IA64_R0  = REGISTER_IA64_BSP + 1,  
    REGISTER_IA64_F0  = REGISTER_IA64_R0  + 128,  
    REGISTER_ARM_PC = 0,  
    REGISTER_ARM_SP,  
    REGISTER_ARM_R0,  
    REGISTER_ARM_R1,  
    REGISTER_ARM_R2,  
    REGISTER_ARM_R3,  
    REGISTER_ARM_R4,  
    REGISTER_ARM_R5,  
    REGISTER_ARM_R6,  
    REGISTER_ARM_R7,  
    REGISTER_ARM_R8,  
    REGISTER_ARM_R9,  
    REGISTER_ARM_R10,  
    REGISTER_ARM_R11,  
    REGISTER_ARM_R12,  
    REGISTER_ARM_LR,  
  
} CorDebugRegister;  
```  
  
## <a name="members"></a><span data-ttu-id="4efb3-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="4efb3-105">Members</span></span>  
  
|<span data-ttu-id="4efb3-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="4efb3-106">Member</span></span>|<span data-ttu-id="4efb3-107">説明</span><span class="sxs-lookup"><span data-stu-id="4efb3-107">Description</span></span>|  
|------------|-----------------|  
|`REGISTER_INSTRUCTION_POINTER`|<span data-ttu-id="4efb3-108">すべてのプロセッサ上の命令ポインター レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-108">An instruction pointer register on any processor.</span></span>|  
|`REGISTER_STACK_POINTER`|<span data-ttu-id="4efb3-109">すべてのプロセッサ上のスタック ポインター レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-109">A stack pointer register on any processor.</span></span>|  
|`REGISTER_FRAME_POINTER`|<span data-ttu-id="4efb3-110">すべてのプロセッサ上のフレーム ポインター レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-110">A frame pointer register on any processor.</span></span>|  
|`REGISTER_X86_EIP`|<span data-ttu-id="4efb3-111">x86 プロセッサ上の命令ポインター レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-111">The instruction pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_ESP`|<span data-ttu-id="4efb3-112">x86 プロセッサ上のスタック ポインター レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-112">The stack pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_EBP`|<span data-ttu-id="4efb3-113">x86 プロセッサ上の基本ポインター レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-113">The base pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_EAX`|<span data-ttu-id="4efb3-114">x86 プロセッサ上の A データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-114">The A data register on the x86 processor.</span></span>|  
|`REGISTER_X86_ECX`|<span data-ttu-id="4efb3-115">x86 プロセッサ上の C データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-115">The C data register on the x86 processor.</span></span>|  
|`REGISTER_X86_EDX`|<span data-ttu-id="4efb3-116">x86 プロセッサ上の D データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-116">The D data register on the x86 processor.</span></span>|  
|`REGISTER_X86_EBX`|<span data-ttu-id="4efb3-117">x86 プロセッサ上の B データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-117">The B data register on the x86 processor.</span></span>|  
|`REGISTER_X86_ESI`|<span data-ttu-id="4efb3-118">x86 プロセッサ上のソース インデックス レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-118">The source index register on the x86 processor.</span></span>|  
|`REGISTER_X86_EDI`|<span data-ttu-id="4efb3-119">x86 プロセッサ上のターゲット インデックス レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-119">The destination index register on the x86 processor.</span></span>|  
|`REGISTER_X86_FPSTACK_0`|<span data-ttu-id="4efb3-120">x86 浮動小数点 (FP) プロセッサ上のスタック レジスタ 0。</span><span class="sxs-lookup"><span data-stu-id="4efb3-120">The stack register 0 on the x86 floating-point (FP) processor.</span></span>|  
|`REGISTER_X86_FPSTACK_1`|<span data-ttu-id="4efb3-121">x86 FP プロセッサ上の #1 スタック レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-121">The #1 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_2`|<span data-ttu-id="4efb3-122">x86 FP プロセッサ上の #2 スタック レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-122">The #2 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_3`|<span data-ttu-id="4efb3-123">x86 FP プロセッサ上の #3 スタック レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-123">The #3 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_4`|<span data-ttu-id="4efb3-124">x86 FP プロセッサ上の #4 スタック レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-124">The #4 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_5`|<span data-ttu-id="4efb3-125">x86 FP プロセッサ上の #5 スタック レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-125">The #5 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_6`|<span data-ttu-id="4efb3-126">x86 FP プロセッサ上の #6 スタック レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-126">The #6 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_7`|<span data-ttu-id="4efb3-127">x86 FP プロセッサ上の #7 スタック レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-127">The #7 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_AMD64_RIP`|<span data-ttu-id="4efb3-128">AMD64 プロセッサ上の命令ポインター レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-128">The instruction pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RSP`|<span data-ttu-id="4efb3-129">AMD64 プロセッサ上のスタック ポインター レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-129">The stack pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RBP`|<span data-ttu-id="4efb3-130">AMD64 プロセッサ上の基本ポインター レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-130">The base pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RAX`|<span data-ttu-id="4efb3-131">AMD64 プロセッサ上の A データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-131">The A data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RCX`|<span data-ttu-id="4efb3-132">AMD64 プロセッサ上の C データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-132">The C data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RDX`|<span data-ttu-id="4efb3-133">AMD64 プロセッサ上の D データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-133">The D data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RBX`|<span data-ttu-id="4efb3-134">AMD64 プロセッサ上の B データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-134">The B data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RSI`|<span data-ttu-id="4efb3-135">AMD64 プロセッサ上のソース インデックス レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-135">The source index register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RDI`|<span data-ttu-id="4efb3-136">AMD64 プロセッサ上のターゲット インデックス レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-136">The destination index register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R8`|<span data-ttu-id="4efb3-137">AMD64 プロセッサ上の #8 データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-137">The #8 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R9`|<span data-ttu-id="4efb3-138">AMD64 プロセッサ上の #9 データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-138">The #9 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R10`|<span data-ttu-id="4efb3-139">AMD64 プロセッサ上の #10 データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-139">The #10 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R11`|<span data-ttu-id="4efb3-140">AMD64 プロセッサ上の #11 データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-140">The #11 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R12`|<span data-ttu-id="4efb3-141">AMD64 プロセッサ上の #12 データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-141">The #12 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R13`|<span data-ttu-id="4efb3-142">AMD64 プロセッサ上の #13 データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-142">The #13 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R14`|<span data-ttu-id="4efb3-143">AMD64 プロセッサ上の #14 データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-143">The #14 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R15`|<span data-ttu-id="4efb3-144">AMD64 プロセッサ上の #15 データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-144">The #15 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM0`|<span data-ttu-id="4efb3-145">AMD64 プロセッサ上の #0 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-145">The #0 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM1`|<span data-ttu-id="4efb3-146">AMD64 プロセッサ上の #1 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-146">The #1 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM2`|<span data-ttu-id="4efb3-147">AMD64 プロセッサ上の #2 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-147">The #2 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM3`|<span data-ttu-id="4efb3-148">AMD64 プロセッサ上の #3 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-148">The #3 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM4`|<span data-ttu-id="4efb3-149">AMD64 プロセッサ上の #4 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-149">The #4 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM5`|<span data-ttu-id="4efb3-150">AMD64 プロセッサ上の #5 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-150">The #5 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM6`|<span data-ttu-id="4efb3-151">AMD64 プロセッサ上の #6 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-151">The #6 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM7`|<span data-ttu-id="4efb3-152">AMD64 プロセッサ上の #7 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-152">The #7 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM8`|<span data-ttu-id="4efb3-153">AMD64 プロセッサ上の #8 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-153">The #8 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM9`|<span data-ttu-id="4efb3-154">AMD64 プロセッサ上の #9 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-154">The #9 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM10`|<span data-ttu-id="4efb3-155">AMD64 プロセッサ上の #10 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-155">The #10 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM11`|<span data-ttu-id="4efb3-156">AMD64 プロセッサ上の #11 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-156">The #11 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM12`|<span data-ttu-id="4efb3-157">AMD64 プロセッサ上の #12 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-157">The #12 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM13`|<span data-ttu-id="4efb3-158">AMD64 プロセッサ上の #13 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-158">The #13 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM14`|<span data-ttu-id="4efb3-159">AMD64 プロセッサ上の #14 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-159">The #14 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM15`|<span data-ttu-id="4efb3-160">AMD64 プロセッサ上の #15 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-160">The #15 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_IA64_BSP`|<span data-ttu-id="4efb3-161">IA-64 プロセッサ上のスタック ポインター レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-161">The stack pointer register on the IA-64 processor.</span></span>|  
|`REGISTER_IA64_R0`|<span data-ttu-id="4efb3-162">IA-64 プロセッサ上の #0 データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-162">The #0 data register on the IA-64 processor.</span></span>|  
|`REGISTER_IA64_F0`|<span data-ttu-id="4efb3-163">IA-64 プロセッサ上の #0 FP データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="4efb3-163">The #0 FP data register on the IA-64 processor.</span></span>|  
|`REGISTER_ARM_PC`|<span data-ttu-id="4efb3-164">ARM プロセッサ上のプログラム カウンター レジスタ (R15)。</span><span class="sxs-lookup"><span data-stu-id="4efb3-164">The program counter register (R15) on the ARM processor.</span></span>|  
|`REGISTER_ARM_SP`|<span data-ttu-id="4efb3-165">ARM プロセッサ上のスタック ポインター レジスタ (R13)。</span><span class="sxs-lookup"><span data-stu-id="4efb3-165">The stack pointer register (R13) on the ARM processor.</span></span>|  
|`REGISTER_ARM_R0`|<span data-ttu-id="4efb3-166">ARM プロセッサ上のデータ レジスタ R0。</span><span class="sxs-lookup"><span data-stu-id="4efb3-166">Data register R0 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R1`|<span data-ttu-id="4efb3-167">ARM プロセッサ上のデータ レジスタ R1。</span><span class="sxs-lookup"><span data-stu-id="4efb3-167">Data register R1 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R2`|<span data-ttu-id="4efb3-168">ARM プロセッサ上のデータ レジスタ R2。</span><span class="sxs-lookup"><span data-stu-id="4efb3-168">Data register R2 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R3`|<span data-ttu-id="4efb3-169">ARM プロセッサ上のデータ レジスタ R3。</span><span class="sxs-lookup"><span data-stu-id="4efb3-169">Data register R3 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R4`|<span data-ttu-id="4efb3-170">ARM プロセッサ上のレジスタ R4。</span><span class="sxs-lookup"><span data-stu-id="4efb3-170">Register R4 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R5`|<span data-ttu-id="4efb3-171">ARM プロセッサ上のレジスタ R5。</span><span class="sxs-lookup"><span data-stu-id="4efb3-171">Register R5 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R6`|<span data-ttu-id="4efb3-172">ARM プロセッサ上のレジスタ R6。</span><span class="sxs-lookup"><span data-stu-id="4efb3-172">Register R6 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R7`|<span data-ttu-id="4efb3-173">ARM プロセッサ上のレジスタ R7 (THUMB フレーム ポインター)。</span><span class="sxs-lookup"><span data-stu-id="4efb3-173">Register R7 (the THUMB frame pointer) on the ARM processor.</span></span>|  
|`REGISTER_ARM_R8`|<span data-ttu-id="4efb3-174">ARM プロセッサ上のレジスタ R8。</span><span class="sxs-lookup"><span data-stu-id="4efb3-174">Register R8 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R9`|<span data-ttu-id="4efb3-175">ARM プロセッサ上のレジスタ R9。</span><span class="sxs-lookup"><span data-stu-id="4efb3-175">Register R9 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R10`|<span data-ttu-id="4efb3-176">ARM プロセッサ上のレジスタ R10。</span><span class="sxs-lookup"><span data-stu-id="4efb3-176">Register R10 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R11`|<span data-ttu-id="4efb3-177">ARM プロセッサ上のフレーム ポインター。</span><span class="sxs-lookup"><span data-stu-id="4efb3-177">The frame pointer on the ARM processor.</span></span>|  
|`REGISTER_ARM_R12`|<span data-ttu-id="4efb3-178">ARM プロセッサ上のレジスタ R12。</span><span class="sxs-lookup"><span data-stu-id="4efb3-178">Register R12 on the ARM processor.</span></span>|  
|`REGISTER_ARM_LR`|<span data-ttu-id="4efb3-179">ARM プロセッサ上のリンク レジスタ (R14)。</span><span class="sxs-lookup"><span data-stu-id="4efb3-179">The link register (R14) on the ARM processor.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4efb3-180">注釈</span><span class="sxs-lookup"><span data-stu-id="4efb3-180">Remarks</span></span>  

 <span data-ttu-id="4efb3-181">IA-64 プロセッサには、128 個の汎用データ レジスタおよび 128 個の浮動小数点データ レジスタがありますが、提供されているのは `REGISTER_IA64_R0` および `REGISTER_IA64_F0` の値のみです。</span><span class="sxs-lookup"><span data-stu-id="4efb3-181">There are 128 general-purpose data registers and 128 floating-point data registers on the IA-64 processor, but only values `REGISTER_IA64_R0` and `REGISTER_IA64_F0` are provided.</span></span> <span data-ttu-id="4efb3-182">その他の値は、次のように判断されます。</span><span class="sxs-lookup"><span data-stu-id="4efb3-182">The other values can be determined as follows:</span></span>  
  
- <span data-ttu-id="4efb3-183">IA-64 プロセッサ上の #1 データ レジスタから #127 データ レジスタに対応する、`REGISTER_IA64_R0` から `REGISTER_IA64_R1` までの値の `REGISTER_IA64_R127` にレジスタ番号を追加します。</span><span class="sxs-lookup"><span data-stu-id="4efb3-183">Add the register number to `REGISTER_IA64_R0` for values `REGISTER_IA64_R1` through `REGISTER_IA64_R127`, which correspond to the #1 data register through the #127 data register on the IA-64 processor.</span></span>  
  
- <span data-ttu-id="4efb3-184">IA-64 プロセッサ上の #1 FP データ レジスタから #127 FP データ レジスタに対応する、`REGISTER_IA64_F0` から `REGISTER_IA64_F1` までの値の `REGISTER_IA64_F127` にレジスタ番号を追加します。</span><span class="sxs-lookup"><span data-stu-id="4efb3-184">Add the register number to `REGISTER_IA64_F0` for values `REGISTER_IA64_F1` through `REGISTER_IA64_F127`, which correspond to the #1 FP data register through the #127 FP data register on the IA-64 processor.</span></span>  
  
 <span data-ttu-id="4efb3-185">たとえば、IA-64 プロセッサ上で #83 データ レジスタを指定する必要がある場合、`REGISTER_IA64_R0` + 83 を使用します。</span><span class="sxs-lookup"><span data-stu-id="4efb3-185">For example, if you need to specify the #83 data register on the IA-64 processor, use `REGISTER_IA64_R0` + 83.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4efb3-186">要件</span><span class="sxs-lookup"><span data-stu-id="4efb3-186">Requirements</span></span>  

 <span data-ttu-id="4efb3-187">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4efb3-187">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4efb3-188">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4efb3-188">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4efb3-189">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4efb3-189">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4efb3-190">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4efb3-190">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4efb3-191">関連項目</span><span class="sxs-lookup"><span data-stu-id="4efb3-191">See also</span></span>

- [<span data-ttu-id="4efb3-192">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="4efb3-192">Debugging Enumerations</span></span>](debugging-enumerations.md)
