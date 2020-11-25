---
title: ICorDebugAssembly インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly
helpviewer_keywords:
- ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 9d657a28-6984-4c5e-8a54-89d20080baff
topic_type:
- apiref
ms.openlocfilehash: 821eae8ea5b4147408e9fe60d1e5b70c7936959e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696246"
---
# <a name="icordebugassembly-interface"></a><span data-ttu-id="d5e08-102">ICorDebugAssembly インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d5e08-102">ICorDebugAssembly Interface</span></span>

<span data-ttu-id="d5e08-103">アセンブリを表します。</span><span class="sxs-lookup"><span data-stu-id="d5e08-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d5e08-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="d5e08-104">Methods</span></span>  
  
|<span data-ttu-id="d5e08-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="d5e08-105">Method</span></span>|<span data-ttu-id="d5e08-106">説明</span><span class="sxs-lookup"><span data-stu-id="d5e08-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d5e08-107">EnumerateModules メソッド</span><span class="sxs-lookup"><span data-stu-id="d5e08-107">EnumerateModules Method</span></span>](icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="d5e08-108">アセンブリに格納されているモジュールの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="d5e08-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="d5e08-109">GetAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="d5e08-109">GetAppDomain Method</span></span>](icordebugassembly-getappdomain-method.md)|<span data-ttu-id="d5e08-110">このインスタンスを含むアプリケーションドメインへのインターフェイスポインターを取得し `ICorDebugAssembly` ます。</span><span class="sxs-lookup"><span data-stu-id="d5e08-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="d5e08-111">GetCodeBase メソッド</span><span class="sxs-lookup"><span data-stu-id="d5e08-111">GetCodeBase Method</span></span>](icordebugassembly-getcodebase-method.md)|<span data-ttu-id="d5e08-112">.NET Framework の現在のバージョンでは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="d5e08-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="d5e08-113">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="d5e08-113">GetName Method</span></span>](icordebugassembly-getname-method.md)|<span data-ttu-id="d5e08-114">アセンブリの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="d5e08-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="d5e08-115">GetProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="d5e08-115">GetProcess Method</span></span>](icordebugassembly-getprocess-method.md)|<span data-ttu-id="d5e08-116">アセンブリが実行されている、のプロセスインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="d5e08-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5e08-117">注釈</span><span class="sxs-lookup"><span data-stu-id="d5e08-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5e08-118">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="d5e08-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5e08-119">要件</span><span class="sxs-lookup"><span data-stu-id="d5e08-119">Requirements</span></span>  

 <span data-ttu-id="d5e08-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5e08-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5e08-121">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d5e08-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5e08-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5e08-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5e08-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5e08-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5e08-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5e08-124">See also</span></span>

- [<span data-ttu-id="d5e08-125">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d5e08-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
