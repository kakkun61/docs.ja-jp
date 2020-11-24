---
title: ICorDebugAppDomain インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain
helpviewer_keywords:
- ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type:
- apiref
ms.openlocfilehash: 98273a5d4602c023863758045bdb2a6a502ba7a7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687230"
---
# <a name="icordebugappdomain-interface"></a><span data-ttu-id="97dc7-102">ICorDebugAppDomain インターフェイス</span><span class="sxs-lookup"><span data-stu-id="97dc7-102">ICorDebugAppDomain Interface</span></span>

<span data-ttu-id="97dc7-103">アプリケーション ドメインをデバッグするためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="97dc7-103">Provides methods for debugging application domains.</span></span> <span data-ttu-id="97dc7-104">このインターフェイスは、というコントロールのサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="97dc7-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="97dc7-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="97dc7-105">Methods</span></span>  
  
|<span data-ttu-id="97dc7-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="97dc7-106">Method</span></span>|<span data-ttu-id="97dc7-107">説明</span><span class="sxs-lookup"><span data-stu-id="97dc7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="97dc7-108">Attach メソッド</span><span class="sxs-lookup"><span data-stu-id="97dc7-108">Attach Method</span></span>](icordebugappdomain-attach-method.md)|<span data-ttu-id="97dc7-109">デバッガーをアプリケーションドメインにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="97dc7-109">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="97dc7-110">EnumerateAssemblies メソッド</span><span class="sxs-lookup"><span data-stu-id="97dc7-110">EnumerateAssemblies Method</span></span>](icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="97dc7-111">アプリケーションドメイン内のアセンブリの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="97dc7-111">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="97dc7-112">EnumerateBreakpoints メソッド</span><span class="sxs-lookup"><span data-stu-id="97dc7-112">EnumerateBreakpoints Method</span></span>](icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="97dc7-113">アプリケーションドメイン内のすべてのアクティブなブレークポイントの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="97dc7-113">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="97dc7-114">EnumerateSteppers メソッド</span><span class="sxs-lookup"><span data-stu-id="97dc7-114">EnumerateSteppers Method</span></span>](icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="97dc7-115">アプリケーションドメイン内のすべてのアクティブな steppers の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="97dc7-115">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="97dc7-116">GetId メソッド</span><span class="sxs-lookup"><span data-stu-id="97dc7-116">GetId Method</span></span>](icordebugappdomain-getid-method.md)|<span data-ttu-id="97dc7-117">アプリケーションドメインの一意の ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="97dc7-117">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="97dc7-118">GetModuleFromMetaDataInterface メソッド</span><span class="sxs-lookup"><span data-stu-id="97dc7-118">GetModuleFromMetaDataInterface Method</span></span>](icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="97dc7-119">指定されたメタデータインターフェイスを持つ、のモジュールオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="97dc7-119">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="97dc7-120">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="97dc7-120">GetName Method</span></span>](icordebugappdomain-getname-method.md)|<span data-ttu-id="97dc7-121">アプリケーションドメインの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="97dc7-121">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="97dc7-122">GetObject メソッド</span><span class="sxs-lookup"><span data-stu-id="97dc7-122">GetObject Method</span></span>](icordebugappdomain-getobject-method.md)|<span data-ttu-id="97dc7-123">共通言語ランタイム (CLR) アプリケーションドメインへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="97dc7-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="97dc7-124">GetProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="97dc7-124">GetProcess Method</span></span>](icordebugappdomain-getprocess-method.md)|<span data-ttu-id="97dc7-125">アプリケーションドメインを格納しているプロセスを取得します。</span><span class="sxs-lookup"><span data-stu-id="97dc7-125">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="97dc7-126">IsAttached メソッド</span><span class="sxs-lookup"><span data-stu-id="97dc7-126">IsAttached Method</span></span>](icordebugappdomain-isattached-method.md)|<span data-ttu-id="97dc7-127">デバッガーがアプリケーションドメインにアタッチされているかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="97dc7-127">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97dc7-128">注釈</span><span class="sxs-lookup"><span data-stu-id="97dc7-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="97dc7-129">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="97dc7-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97dc7-130">要件</span><span class="sxs-lookup"><span data-stu-id="97dc7-130">Requirements</span></span>  

 <span data-ttu-id="97dc7-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="97dc7-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97dc7-132">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="97dc7-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97dc7-133">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97dc7-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97dc7-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97dc7-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97dc7-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="97dc7-135">See also</span></span>

- [<span data-ttu-id="97dc7-136">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="97dc7-136">Debugging Interfaces</span></span>](debugging-interfaces.md)
