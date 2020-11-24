---
title: ICorDebugProcess2::SetDesiredNGENCompilerFlags メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags method [.NET Framework debugging]
- SetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: 98320175-7c5e-4dbb-8683-86fa82e2641f
topic_type:
- apiref
ms.openlocfilehash: 40b944f6a1204bfe506ed64408be30f68adf3170
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675257"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a><span data-ttu-id="e06df-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="e06df-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags Method</span></span>

<span data-ttu-id="e06df-103">ランタイムがそのイメージを現在のプロセスに読み込むために、プリコンパイル済みイメージに埋め込む必要があるフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="e06df-103">Sets the flags that must be embedded in a precompiled image in order for the runtime to load that image into the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e06df-104">構文</span><span class="sxs-lookup"><span data-stu-id="e06df-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e06df-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e06df-105">Parameters</span></span>  

 `pdwFlags`  
 <span data-ttu-id="e06df-106">から適切なプリコンパイル済みイメージを選択するために使用されるコンパイラフラグを指定する [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="e06df-106">[in] A value of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration that specifies the compiler flags used to select the correct pre-compiled image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e06df-107">注釈</span><span class="sxs-lookup"><span data-stu-id="e06df-107">Remarks</span></span>  

 <span data-ttu-id="e06df-108">メソッドは、 `SetDesiredNGENCompilerFlags` プリコンパイル済みイメージに埋め込まれる必要があるフラグを指定します。これにより、ランタイムはそのイメージをこのプロセスに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="e06df-108">The `SetDesiredNGENCompilerFlags` method specifies the flags that must be embedded in a precompiled image so that the runtime will load that image into this process.</span></span> <span data-ttu-id="e06df-109">このメソッドによって設定されるフラグは、正しいプリコンパイル済みイメージを選択するためにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="e06df-109">The flags set by this method are used only to select the correct precompiled image.</span></span> <span data-ttu-id="e06df-110">そのようなイメージが存在しない場合、ランタイムは Microsoft 中間言語 (MSIL) イメージと just-in-time (JIT) コンパイラを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="e06df-110">If no such image exists, the runtime will load the Microsoft intermediate language (MSIL) image and the just-in-time (JIT) compiler instead.</span></span> <span data-ttu-id="e06df-111">その場合でも、デバッガーは [ICorDebugModule2:: SetJITCompilerFlags](icordebugmodule2-setjitcompilerflags-method.md) メソッドを使用して、JIT コンパイルに必要なフラグを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e06df-111">In that case, the debugger must still use the [ICorDebugModule2::SetJITCompilerFlags](icordebugmodule2-setjitcompilerflags-method.md) method to set the flags as desired for the JIT compilation.</span></span>  
  
 <span data-ttu-id="e06df-112">イメージが読み込まれるときに、そのイメージに対して一部の JIT コンパイルを実行する必要がある場合 (イメージにジェネリックが含まれている場合)、メソッドによって指定されたコンパイラフラグ `SetDesiredNGENCompilerFlags` が追加の jit コンパイルに適用されます。</span><span class="sxs-lookup"><span data-stu-id="e06df-112">If an image is loaded, but some JIT compiling must take place for that image (which will be the case if the image contains generics), the compiler flags specified by the `SetDesiredNGENCompilerFlags` method will apply to the extra JIT compilation.</span></span>  
  
 <span data-ttu-id="e06df-113">このメソッドは、の `SetDesiredNGENCompilerFlags` メソッドを[ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md)呼び出さなければなりません。</span><span class="sxs-lookup"><span data-stu-id="e06df-113">The `SetDesiredNGENCompilerFlags` method must be called during the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="e06df-114">その後、メソッドを呼び出そうとすると `SetDesiredNGENCompilerFlags` 失敗します。</span><span class="sxs-lookup"><span data-stu-id="e06df-114">Attempts to call the `SetDesiredNGENCompilerFlags` method afterwards will fail.</span></span> <span data-ttu-id="e06df-115">また、列挙型で定義されていないフラグや、指定されたプロセスに対して有効ではないフラグを設定しようとすると `CorDebugJITCompilerFlags` 失敗します。</span><span class="sxs-lookup"><span data-stu-id="e06df-115">Also, attempts to set flags that are either not defined in the `CorDebugJITCompilerFlags` enumeration or are not legal for the given process will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e06df-116">要件</span><span class="sxs-lookup"><span data-stu-id="e06df-116">Requirements</span></span>  

 <span data-ttu-id="e06df-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e06df-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e06df-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e06df-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e06df-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e06df-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e06df-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e06df-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e06df-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="e06df-121">See also</span></span>

- [<span data-ttu-id="e06df-122">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e06df-122">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="e06df-123">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e06df-123">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
