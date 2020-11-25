---
title: ICorDebugModule2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugModule2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2
helpviewer_keywords:
- ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type:
- apiref
ms.openlocfilehash: 2b8e6048dd6b8df71ac3dddcc4397f6d512127c7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695882"
---
# <a name="icordebugmodule2-interface"></a><span data-ttu-id="01dd7-102">ICorDebugModule2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="01dd7-102">ICorDebugModule2 Interface</span></span>

<span data-ttu-id="01dd7-103">モジュールインターフェイスの論理拡張機能として機能します。</span><span class="sxs-lookup"><span data-stu-id="01dd7-103">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="01dd7-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="01dd7-104">Methods</span></span>  
  
|<span data-ttu-id="01dd7-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="01dd7-105">Method</span></span>|<span data-ttu-id="01dd7-106">説明</span><span class="sxs-lookup"><span data-stu-id="01dd7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="01dd7-107">ApplyChanges メソッド</span><span class="sxs-lookup"><span data-stu-id="01dd7-107">ApplyChanges Method</span></span>](icordebugmodule2-applychanges-method.md)|<span data-ttu-id="01dd7-108">メタデータの変更と、Microsoft 中間言語 (MSIL) コードの変更を実行中のプロセスに適用します。</span><span class="sxs-lookup"><span data-stu-id="01dd7-108">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="01dd7-109">GetJITCompilerFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="01dd7-109">GetJITCompilerFlags Method</span></span>](icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="01dd7-110">このの just-in-time (JIT) コンパイルを制御するフラグを取得し `ICorDebugModule2` ます。</span><span class="sxs-lookup"><span data-stu-id="01dd7-110">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="01dd7-111">ResolveAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="01dd7-111">ResolveAssembly Method</span></span>](icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="01dd7-112">指定したメタデータトークンによって参照されるアセンブリを解決します。</span><span class="sxs-lookup"><span data-stu-id="01dd7-112">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="01dd7-113">SetJITCompilerFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="01dd7-113">SetJITCompilerFlags Method</span></span>](icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="01dd7-114">このの JIT コンパイルを制御するフラグを設定 `ICorDebugModule2` します。</span><span class="sxs-lookup"><span data-stu-id="01dd7-114">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="01dd7-115">SetJMCStatus メソッド</span><span class="sxs-lookup"><span data-stu-id="01dd7-115">SetJMCStatus Method</span></span>](icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="01dd7-116">こののすべてのクラスのすべてのメソッドのマイコードのみ (JMC) の状態を、 `ICorDebugModule2` 指定した値に設定し `pTokens` ます。ただし、逆の値に設定されている配列内のすべてのメソッドを除きます。</span><span class="sxs-lookup"><span data-stu-id="01dd7-116">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01dd7-117">注釈</span><span class="sxs-lookup"><span data-stu-id="01dd7-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01dd7-118">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="01dd7-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01dd7-119">要件</span><span class="sxs-lookup"><span data-stu-id="01dd7-119">Requirements</span></span>  

 <span data-ttu-id="01dd7-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01dd7-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01dd7-121">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01dd7-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01dd7-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01dd7-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01dd7-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01dd7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01dd7-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="01dd7-124">See also</span></span>

- [<span data-ttu-id="01dd7-125">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="01dd7-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
