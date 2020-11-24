---
title: _EFN_GetManagedObjectName 関数
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectName
helpviewer_keywords:
- _EFN_GetManagedObjectName function [.NET Framework debugging]
ms.assetid: 6e7c6bee-7ced-495f-bf6c-2a5f0c716f7e
topic_type:
- apiref
ms.openlocfilehash: 0fb694cf85256c0f3ac5ae179e53ff504ab707e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676206"
---
# <a name="_efn_getmanagedobjectname-function"></a><span data-ttu-id="0bf0a-102">\_EFN \_ GetManagedObjectName 関数</span><span class="sxs-lookup"><span data-stu-id="0bf0a-102">\_EFN\_GetManagedObjectName Function</span></span>

<span data-ttu-id="0bf0a-103">指定されたマネージオブジェクトポインターを使用して、型の名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="0bf0a-103">Gets the name of a type using the provided managed object pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bf0a-104">構文</span><span class="sxs-lookup"><span data-stu-id="0bf0a-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0bf0a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0bf0a-105">Parameters</span></span>  

 `Client`  
 <span data-ttu-id="0bf0a-106">からデバッグクライアントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0bf0a-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="0bf0a-107">からマネージオブジェクトポインター。</span><span class="sxs-lookup"><span data-stu-id="0bf0a-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="0bf0a-108">szName</span><span class="sxs-lookup"><span data-stu-id="0bf0a-108">szName</span></span>  
 <span data-ttu-id="0bf0a-109">入出力型の名前。</span><span class="sxs-lookup"><span data-stu-id="0bf0a-109">[out] The name of the type.</span></span>  
  
 `cbName`  
 <span data-ttu-id="0bf0a-110">入出力文字列バッファーで使用できる文字数。</span><span class="sxs-lookup"><span data-stu-id="0bf0a-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bf0a-111">注釈</span><span class="sxs-lookup"><span data-stu-id="0bf0a-111">Remarks</span></span>  

 <span data-ttu-id="0bf0a-112">現在コンテキスト内にあるスレッドにマネージコードがない場合、関数は、ファシリティ値が0xa0 でエラーコードが0x1000 の HRESULT SOS_E_NOMANAGEDCODE を返します。</span><span class="sxs-lookup"><span data-stu-id="0bf0a-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bf0a-113">要件</span><span class="sxs-lookup"><span data-stu-id="0bf0a-113">Requirements</span></span>  

 <span data-ttu-id="0bf0a-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0bf0a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bf0a-115">**ヘッダー:** SOS_Stacktrace</span><span class="sxs-lookup"><span data-stu-id="0bf0a-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="0bf0a-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bf0a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bf0a-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="0bf0a-117">See also</span></span>

- [<span data-ttu-id="0bf0a-118">デバッグ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="0bf0a-118">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
