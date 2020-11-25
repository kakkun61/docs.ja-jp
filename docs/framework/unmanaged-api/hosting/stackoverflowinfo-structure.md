---
title: StackOverflowInfo 構造体
ms.date: 03/30/2017
api_name:
- StackOverflowInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowInfo
helpviewer_keywords:
- StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type:
- apiref
ms.openlocfilehash: a8a57cfcaf36949d4d10c6ec267a5f55a2aee5eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729929"
---
# <a name="stackoverflowinfo-structure"></a><span data-ttu-id="a299f-102">StackOverflowInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="a299f-102">StackOverflowInfo Structure</span></span>

<span data-ttu-id="a299f-103">発生したオーバーフローの種類とオーバーフローによってスローされた例外に関する情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="a299f-103">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a299f-104">構文</span><span class="sxs-lookup"><span data-stu-id="a299f-104">Syntax</span></span>  
  
```cpp  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="a299f-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="a299f-105">Members</span></span>  
  
|<span data-ttu-id="a299f-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="a299f-106">Member</span></span>|<span data-ttu-id="a299f-107">説明</span><span class="sxs-lookup"><span data-stu-id="a299f-107">Description</span></span>|  
|------------|-----------------|  
|`soType`|<span data-ttu-id="a299f-108">オーバーフローの種類を指定する [StackOverflowType](stackoverflowtype-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="a299f-108">A value of the [StackOverflowType](stackoverflowtype-enumeration.md) enumeration that specifies the type of overflow.</span></span>|  
|`pExceptionInfo`|<span data-ttu-id="a299f-109">Win32 オブジェクトへのポインター。このオブジェクトには、例外 `EXCEPTION_POINTERS` のコンピューターに依存しない記述と、例外の発生時にプロセッサコンテキストのコンピューターに依存する記述を持つコンテキストレコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a299f-109">A pointer to a Win32 `EXCEPTION_POINTERS` object, which contains an exception record with a machine-independent description of an exception and a context record with a machine-dependent description of the processor context at the time of the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a299f-110">注釈</span><span class="sxs-lookup"><span data-stu-id="a299f-110">Remarks</span></span>  

 <span data-ttu-id="a299f-111">`StackOverflowInfo`オブジェクトは、イベントの[Iactiononclrevent:: OnEvent](iactiononclrevent-onevent-method.md)メソッドに渡され `Event_StackOverflow` ます。</span><span class="sxs-lookup"><span data-stu-id="a299f-111">A `StackOverflowInfo` object is passed to the [IActionOnCLREvent::OnEvent](iactiononclrevent-onevent-method.md) method for `Event_StackOverflow` events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a299f-112">要件</span><span class="sxs-lookup"><span data-stu-id="a299f-112">Requirements</span></span>  

 <span data-ttu-id="a299f-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a299f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a299f-114">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a299f-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="a299f-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="a299f-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a299f-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a299f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a299f-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="a299f-117">See also</span></span>

- [<span data-ttu-id="a299f-118">ホスト構造体</span><span class="sxs-lookup"><span data-stu-id="a299f-118">Hosting Structures</span></span>](hosting-structures.md)
