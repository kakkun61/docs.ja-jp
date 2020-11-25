---
title: ICorDebugModule::EnableJITDebugging メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableJITDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableJITDebugging
helpviewer_keywords:
- ICorDebugModule::EnableJITDebugging method [.NET Framework debugging]
- EnableJITDebugging method [.NET Framework debugging]
ms.assetid: 0a65e2a4-5bb6-496c-ae6f-40474426b5a6
topic_type:
- apiref
ms.openlocfilehash: 359db27878ea4adf794bcd6221d4b5387026e5c0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710312"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a><span data-ttu-id="1b4af-102">ICorDebugModule::EnableJITDebugging メソッド</span><span class="sxs-lookup"><span data-stu-id="1b4af-102">ICorDebugModule::EnableJITDebugging Method</span></span>

<span data-ttu-id="1b4af-103">Just-in-time (JIT) コンパイラが、このモジュール内のメソッドのデバッグ情報を保持するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="1b4af-103">Controls whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b4af-104">構文</span><span class="sxs-lookup"><span data-stu-id="1b4af-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b4af-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1b4af-105">Parameters</span></span>  

 `bTrackJITInfo`  
 <span data-ttu-id="1b4af-106">からこの値をに設定 `true` すると、このモジュールの各メソッドの MSIL (Microsoft 中間言語) バージョンと jit コンパイルバージョンとの間のマッピング情報を jit コンパイラで保持できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1b4af-106">[in] Set this value to `true` to enable the JIT compiler to preserve mapping information between the Microsoft intermediate language (MSIL) version and the JIT-compiled version of each method in this module.</span></span>  
  
 `bAllowJitOpts`  
 <span data-ttu-id="1b4af-107">からこの値をに設定すると `true` 、jit コンパイラはデバッグのために特定の jit 固有の最適化を使用してコードを生成できます。</span><span class="sxs-lookup"><span data-stu-id="1b4af-107">[in] Set this value to `true` to enable the JIT compiler to generate code with certain JIT-specific optimizations for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b4af-108">注釈</span><span class="sxs-lookup"><span data-stu-id="1b4af-108">Remarks</span></span>  

 <span data-ttu-id="1b4af-109">JIT デバッグは、デバッガーがアクティブなときに読み込まれるすべてのモジュールに対して、既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="1b4af-109">JIT debugging is enabled by default for all modules that are loaded when the debugger is active.</span></span> <span data-ttu-id="1b4af-110">プログラムを使用して設定を有効または無効にすると、グローバル設定が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="1b4af-110">Programmatically enabling or disabling the settings overrides global settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b4af-111">要件</span><span class="sxs-lookup"><span data-stu-id="1b4af-111">Requirements</span></span>  

 <span data-ttu-id="1b4af-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b4af-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b4af-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b4af-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b4af-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b4af-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b4af-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b4af-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
