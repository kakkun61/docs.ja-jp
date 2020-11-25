---
title: CorDebugNGenPolicy 列挙型
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugNGenPolicy
helpviewer_keywords:
- CorDebugNgenPolicy enumeration [.NET Framework debugging]
ms.assetid: edb4e4d2-3166-44d4-8b17-bf302f7ea093
topic_type:
- apiref
ms.openlocfilehash: b64de0fa2ecbddd2decf69a4099d9897ec42a563
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696428"
---
# <a name="cordebugngenpolicy-enumeration"></a><span data-ttu-id="02c1f-102">CorDebugNGenPolicy 列挙型</span><span class="sxs-lookup"><span data-stu-id="02c1f-102">CorDebugNGenPolicy Enumeration</span></span>

<span data-ttu-id="02c1f-103">デバッガーがネイティブ イメージ キャッシュからネイティブ (NGen) イメージを読み込むかどうかを指定する値を提供します。</span><span class="sxs-lookup"><span data-stu-id="02c1f-103">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02c1f-104">構文</span><span class="sxs-lookup"><span data-stu-id="02c1f-104">Syntax</span></span>  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="02c1f-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="02c1f-105">Members</span></span>  
  
|<span data-ttu-id="02c1f-106">メンバー名</span><span class="sxs-lookup"><span data-stu-id="02c1f-106">Member name</span></span>|<span data-ttu-id="02c1f-107">説明</span><span class="sxs-lookup"><span data-stu-id="02c1f-107">Description</span></span>|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|<span data-ttu-id="02c1f-108">Windows 8.x ストアアプリでは、ローカルのネイティブイメージキャッシュからのイメージの使用は無効になっています。</span><span class="sxs-lookup"><span data-stu-id="02c1f-108">In a Windows 8.x Store app, the use of images from the local native image cache is disabled.</span></span> <span data-ttu-id="02c1f-109">デスクトップアプリでは、この設定による影響はありません。</span><span class="sxs-lookup"><span data-stu-id="02c1f-109">In a desktop app, this setting has no effect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02c1f-110">注釈</span><span class="sxs-lookup"><span data-stu-id="02c1f-110">Remarks</span></span>  

 <span data-ttu-id="02c1f-111">`CorDebugNGENPolicy`列挙体は、 [ICorDebugProcess5:: EnableNGENPolicy](icordebugprocess5-enablengenpolicy-method.md)メソッドによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="02c1f-111">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](icordebugprocess5-enablengenpolicy-method.md) method.</span></span> <span data-ttu-id="02c1f-112">ローカルのネイティブイメージキャッシュからのイメージの使用を無効にすると、最適化されたネイティブイメージの代わりにデバッグ可能な JIT コンパイルイメージをデバッガーが読み込むことができるため、一貫したデバッグエクスペリエンスを実現できます。</span><span class="sxs-lookup"><span data-stu-id="02c1f-112">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02c1f-113">要件</span><span class="sxs-lookup"><span data-stu-id="02c1f-113">Requirements</span></span>  

 <span data-ttu-id="02c1f-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="02c1f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02c1f-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="02c1f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02c1f-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02c1f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02c1f-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02c1f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02c1f-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="02c1f-118">See also</span></span>

- [<span data-ttu-id="02c1f-119">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="02c1f-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
