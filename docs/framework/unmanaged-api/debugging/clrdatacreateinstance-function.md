---
title: CLRDataCreateInstance 関数
ms.date: 03/30/2017
api_name:
- CLRDataCreateInstance
api_location:
- mscordbi.dll
- mscordacwks.dll
api_type:
- COM
f1_keywords:
- CLRDataCreateInstance
helpviewer_keywords:
- CLRDataCreateInstance function [.NET Framework debugging]
ms.assetid: 440bad90-5a88-45e7-9157-4596801d8d19
topic_type:
- apiref
ms.openlocfilehash: 2ffc575cfcef1089a70ef3b6d38787a5b4c50443
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729825"
---
# <a name="clrdatacreateinstance-function"></a><span data-ttu-id="eed93-102">CLRDataCreateInstance 関数</span><span class="sxs-lookup"><span data-stu-id="eed93-102">CLRDataCreateInstance Function</span></span>

<span data-ttu-id="eed93-103">指定したターゲット項目のインターフェイスオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="eed93-103">Creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eed93-104">構文</span><span class="sxs-lookup"><span data-stu-id="eed93-104">Syntax</span></span>  
  
```cpp  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,
    [in]  ICLRDataTarget  *target,
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eed93-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eed93-105">Parameters</span></span>  

 `iid`  
 <span data-ttu-id="eed93-106">からインスタンス化するインターフェイスの識別子。</span><span class="sxs-lookup"><span data-stu-id="eed93-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="eed93-107">からインターフェイスオブジェクトの作成対象となる項目を表す、ユーザーによって実装された [ICLRDataTarget](iclrdatatarget-interface.md) オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eed93-107">[in] A pointer to a user-implemented [ICLRDataTarget](iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="eed93-108">入出力返されたインターフェイスオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eed93-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eed93-109">注釈</span><span class="sxs-lookup"><span data-stu-id="eed93-109">Remarks</span></span>  

 <span data-ttu-id="eed93-110">`ICLRDataTarget`オブジェクトは、デバッグアプリケーションのライターによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="eed93-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="eed93-111">実装は、表示されるターゲット項目の種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="eed93-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="eed93-112">ターゲット項目には、プロセス、メモリダンプ、リモートコンピューターなどがあります。</span><span class="sxs-lookup"><span data-stu-id="eed93-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eed93-113">要件</span><span class="sxs-lookup"><span data-stu-id="eed93-113">Requirements</span></span>  

 <span data-ttu-id="eed93-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eed93-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eed93-115">**ヘッダー:** ClrData .idl</span><span class="sxs-lookup"><span data-stu-id="eed93-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="eed93-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eed93-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eed93-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eed93-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eed93-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="eed93-118">See also</span></span>

- [<span data-ttu-id="eed93-119">デバッグ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="eed93-119">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
