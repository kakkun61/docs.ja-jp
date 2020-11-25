---
title: CorDebugDebugEventKind 列挙体
ms.date: 03/30/2017
api_name:
- CorDebugDebugEventKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6075a6cd-97e6-4472-a090-0dd14860d1f3
topic_type:
- apiref
ms.openlocfilehash: e348e0070a5ce619f95dad9ebe4085d17f7ade6d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733374"
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="5aecf-102">CorDebugDebugEventKind 列挙体</span><span class="sxs-lookup"><span data-stu-id="5aecf-102">CorDebugDebugEventKind Enumeration</span></span>

<span data-ttu-id="5aecf-103">[DecodeEvent](icordebugprocess6-decodeevent-method.md)メソッドによって情報がデコードされるイベントの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="5aecf-103">Indicates the type of event whose information is decoded by the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5aecf-104">構文</span><span class="sxs-lookup"><span data-stu-id="5aecf-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugDebugEventKind {  
    DEBUG_EVENT_KIND_MODULE_LOADED                          = 1,  
    DEBUG_EVENT_KIND_MODULE_UNLOADED                        = 2,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE         = 3,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE    = 4,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND  = 5,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED            = 6  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="5aecf-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="5aecf-105">Members</span></span>  
  
|<span data-ttu-id="5aecf-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="5aecf-106">Member</span></span>|<span data-ttu-id="5aecf-107">説明</span><span class="sxs-lookup"><span data-stu-id="5aecf-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="5aecf-108">モジュールの読み込みイベント。</span><span class="sxs-lookup"><span data-stu-id="5aecf-108">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="5aecf-109">モジュールのアンロード イベント。</span><span class="sxs-lookup"><span data-stu-id="5aecf-109">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="5aecf-110">初回例外。</span><span class="sxs-lookup"><span data-stu-id="5aecf-110">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="5aecf-111">ユーザーの初回例外。</span><span class="sxs-lookup"><span data-stu-id="5aecf-111">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="5aecf-112">`catch` ハンドラーが存在する例外。</span><span class="sxs-lookup"><span data-stu-id="5aecf-112">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="5aecf-113">未処理の例外。</span><span class="sxs-lookup"><span data-stu-id="5aecf-113">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5aecf-114">注釈</span><span class="sxs-lookup"><span data-stu-id="5aecf-114">Remarks</span></span>  

 <span data-ttu-id="5aecf-115">この列挙体のメンバーは、 `CorDebugDebugEventKind` によっては、の [イベント:: GetEventKind](icordebugdebugevent-geteventkind-method.md) メソッドを呼び出すことによって返されます。</span><span class="sxs-lookup"><span data-stu-id="5aecf-115">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5aecf-116">この列挙型は .NET ネイティブのデバッグ シナリオのみで使用することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="5aecf-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5aecf-117">要件</span><span class="sxs-lookup"><span data-stu-id="5aecf-117">Requirements</span></span>  

 <span data-ttu-id="5aecf-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5aecf-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5aecf-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5aecf-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5aecf-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5aecf-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5aecf-121">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5aecf-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5aecf-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="5aecf-122">See also</span></span>

- [<span data-ttu-id="5aecf-123">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="5aecf-123">Debugging Enumerations</span></span>](debugging-enumerations.md)
