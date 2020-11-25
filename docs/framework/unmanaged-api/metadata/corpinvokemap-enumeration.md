---
title: CorPinvokeMap 列挙型
ms.date: 03/30/2017
api_name:
- CorPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPinvokeMap
helpviewer_keywords:
- CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type:
- apiref
ms.openlocfilehash: da3ee54b1c3361149c11a9cfad8bdb07a5007ecf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706139"
---
# <a name="corpinvokemap-enumeration"></a><span data-ttu-id="c922a-102">CorPinvokeMap 列挙型</span><span class="sxs-lookup"><span data-stu-id="c922a-102">CorPinvokeMap Enumeration</span></span>

<span data-ttu-id="c922a-103">PInvoke 呼び出しのオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="c922a-103">Specifies options for a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c922a-104">構文</span><span class="sxs-lookup"><span data-stu-id="c922a-104">Syntax</span></span>  
  
```cpp  
typedef enum  CorPinvokeMap {  
  
    pmNoMangle          = 0x0001,  
  
    pmCharSetMask       = 0x0006,  
    pmCharSetNotSpec    = 0x0000,  
    pmCharSetAnsi       = 0x0002,  
    pmCharSetUnicode    = 0x0004,  
    pmCharSetAuto       = 0x0006,  
  
    pmBestFitUseAssem   = 0x0000,  
    pmBestFitEnabled    = 0x0010,  
    pmBestFitDisabled   = 0x0020,  
    pmBestFitMask       = 0x0030,  
  
    pmThrowOnUnmappableCharUseAssem   = 0x0000,  
    pmThrowOnUnmappableCharEnabled    = 0x1000,  
    pmThrowOnUnmappableCharDisabled   = 0x2000,  
    pmThrowOnUnmappableCharMask       = 0x3000,  
  
    pmSupportsLastError = 0x0040,
  
    pmCallConvMask      = 0x0700,  
    pmCallConvWinapi    = 0x0100,  
    pmCallConvCdecl     = 0x0200,  
    pmCallConvStdcall   = 0x0300,  
    pmCallConvThiscall  = 0x0400,  
    pmCallConvFastcall  = 0x0500,  
  
    pmMaxValue          = 0xFFFF  
  
} CorPinvokeMap;  
```  
  
## <a name="members"></a><span data-ttu-id="c922a-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="c922a-105">Members</span></span>  
  
|<span data-ttu-id="c922a-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="c922a-106">Member</span></span>|<span data-ttu-id="c922a-107">説明</span><span class="sxs-lookup"><span data-stu-id="c922a-107">Description</span></span>|  
|------------|-----------------|  
|`pmNoMangle`|<span data-ttu-id="c922a-108">各メンバー名は、指定されたとおりに使用します。</span><span class="sxs-lookup"><span data-stu-id="c922a-108">Use each member name as specified.</span></span>|  
|`pmCharSetMask`|<span data-ttu-id="c922a-109">予約済み。</span><span class="sxs-lookup"><span data-stu-id="c922a-109">Reserved.</span></span>|  
|`pmCharSetNotSpec`|<span data-ttu-id="c922a-110">予約済み。</span><span class="sxs-lookup"><span data-stu-id="c922a-110">Reserved.</span></span>|  
|`pmCharSetAnsi`|<span data-ttu-id="c922a-111">マルチバイト文字として文字列をマーシャリングします。</span><span class="sxs-lookup"><span data-stu-id="c922a-111">Marshal strings as multiple-byte character strings.</span></span>|  
|`pmCharSetUnicode`|<span data-ttu-id="c922a-112">Unicode 2 バイト文字として文字列をマーシャリングします。</span><span class="sxs-lookup"><span data-stu-id="c922a-112">Marshal strings as Unicode 2-byte characters.</span></span>|  
|`pmCharSetAuto`|<span data-ttu-id="c922a-113">対象オペレーティング システムに適するように、自動的に文字列をマーシャリングします。</span><span class="sxs-lookup"><span data-stu-id="c922a-113">Automatically marshal strings appropriately for the target operating system.</span></span> <span data-ttu-id="c922a-114">既定値は、Windows NT、Windows 2000、Windows XP、および Windows Server 2003 ファミリの Unicode です。Windows 98 および Windows Me では、既定値は ANSI です。</span><span class="sxs-lookup"><span data-stu-id="c922a-114">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span></span>|  
|`pmBestFitUseAssem`|<span data-ttu-id="c922a-115">予約済み。</span><span class="sxs-lookup"><span data-stu-id="c922a-115">Reserved.</span></span>|  
|`pmBestFitEnabled`|<span data-ttu-id="c922a-116">ANSI 文字セットと完全に一致しない Unicode 文字の最適マッピングを実行します。</span><span class="sxs-lookup"><span data-stu-id="c922a-116">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span></span>|  
|`pmBestFitDisabled`|<span data-ttu-id="c922a-117">Unicode 文字の最適マッピングを実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="c922a-117">Do not perform best-fit mapping of Unicode characters.</span></span> <span data-ttu-id="c922a-118">この場合、マップされていないすべての文字は、'? ' に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="c922a-118">In this case, all unmappable characters will be replaced by a ‘?’.</span></span>|  
|`pmBestFitMask`|<span data-ttu-id="c922a-119">予約済み。</span><span class="sxs-lookup"><span data-stu-id="c922a-119">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharUseAssem`|<span data-ttu-id="c922a-120">予約済み。</span><span class="sxs-lookup"><span data-stu-id="c922a-120">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharEnabled`|<span data-ttu-id="c922a-121">相互運用マーシャラーがマップされていない文字を検出したときに、例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="c922a-121">Throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharDisabled`|<span data-ttu-id="c922a-122">相互運用マーシャラーがマップ不可能な文字を検出した場合は、例外をスローしないでください。</span><span class="sxs-lookup"><span data-stu-id="c922a-122">Do not throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharMask`|<span data-ttu-id="c922a-123">予約されています。</span><span class="sxs-lookup"><span data-stu-id="c922a-123">Reserved</span></span>|  
|`pmSupportsLastError`|<span data-ttu-id="c922a-124">`SetLastError`属性付きメソッドから戻る前に、呼び出し先が Win32 関数を呼び出すことができるようにします。</span><span class="sxs-lookup"><span data-stu-id="c922a-124">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span></span>|  
|`pmCallConvMask`|<span data-ttu-id="c922a-125">予約されています。</span><span class="sxs-lookup"><span data-stu-id="c922a-125">Reserved</span></span>|  
|`pmCallConvWinapi`|<span data-ttu-id="c922a-126">既定のプラットフォーム呼び出し規約を使用します。</span><span class="sxs-lookup"><span data-stu-id="c922a-126">Use the default platform calling convention.</span></span> <span data-ttu-id="c922a-127">たとえば、Windows では、既定値はで `StdCall` あり、Windows CE .net ではです `Cdecl` 。</span><span class="sxs-lookup"><span data-stu-id="c922a-127">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span></span>|  
|`pmCallConvCdecl`|<span data-ttu-id="c922a-128">呼び出し規約を使用し `Cdecl` ます。</span><span class="sxs-lookup"><span data-stu-id="c922a-128">Use the `Cdecl` calling convention.</span></span> <span data-ttu-id="c922a-129">この場合、呼び出し元はスタックを消去します。</span><span class="sxs-lookup"><span data-stu-id="c922a-129">In this case, the caller cleans the stack.</span></span> <span data-ttu-id="c922a-130">これにより `varargs` 、(つまり、可変個のパラメーターを受け取る関数) を使用して関数を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="c922a-130">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span></span>|  
|`pmCallConvStdcall`|<span data-ttu-id="c922a-131">呼び出し規約を使用し `StdCall` ます。</span><span class="sxs-lookup"><span data-stu-id="c922a-131">Use the `StdCall` calling convention.</span></span> <span data-ttu-id="c922a-132">この場合、呼び出し先がスタックを消去します。</span><span class="sxs-lookup"><span data-stu-id="c922a-132">In this case, the callee cleans the stack.</span></span> <span data-ttu-id="c922a-133">これは、プラットフォーム呼び出しでアンマネージ関数を呼び出すための既定の規約です。</span><span class="sxs-lookup"><span data-stu-id="c922a-133">This is the default convention for calling unmanaged functions with platform invoke.</span></span>|  
|`pmCallConvThiscall`|<span data-ttu-id="c922a-134">呼び出し規約を使用し `ThisCall` ます。</span><span class="sxs-lookup"><span data-stu-id="c922a-134">Use the `ThisCall` calling convention.</span></span> <span data-ttu-id="c922a-135">この場合、最初のパラメーターはポインターであり、 `this` レジスタ ECX に格納されます。</span><span class="sxs-lookup"><span data-stu-id="c922a-135">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span></span> <span data-ttu-id="c922a-136">その他のパラメーターは、スタックにプッシュされます。</span><span class="sxs-lookup"><span data-stu-id="c922a-136">Other parameters are pushed on the stack.</span></span> <span data-ttu-id="c922a-137">`ThisCall`呼び出し規約は、アンマネージ DLL からエクスポートされたクラスのメソッドを呼び出すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c922a-137">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span></span>|  
|`pmCallConvFastcall`|<span data-ttu-id="c922a-138">予約済み。</span><span class="sxs-lookup"><span data-stu-id="c922a-138">Reserved.</span></span>|  
|`pmMaxValue`|<span data-ttu-id="c922a-139">予約済み。</span><span class="sxs-lookup"><span data-stu-id="c922a-139">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c922a-140">要件</span><span class="sxs-lookup"><span data-stu-id="c922a-140">Requirements</span></span>  

 <span data-ttu-id="c922a-141">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c922a-141">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c922a-142">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="c922a-142">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c922a-143">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c922a-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c922a-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="c922a-144">See also</span></span>

- [<span data-ttu-id="c922a-145">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="c922a-145">Metadata Enumerations</span></span>](metadata-enumerations.md)
