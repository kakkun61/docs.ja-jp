---
title: ICLRDataTarget2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2
helpviewer_keywords:
- ICLRDataTarget2 interface [.NET Framework debugging]
ms.assetid: 94249397-861b-4294-a538-cf01466a66d3
topic_type:
- apiref
ms.openlocfilehash: dee5108439610b67c3397cebcd8ee5f84d4eacea
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723637"
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="6eb96-102">ICLRDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6eb96-102">ICLRDataTarget2 Interface</span></span>

<span data-ttu-id="6eb96-103">ターゲットプロセスの仮想メモリ領域を操作するためにデータアクセスサービス層によって使用される [ICLRDataTarget](iclrdatatarget-interface.md) のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="6eb96-103">A subclass of [ICLRDataTarget](iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6eb96-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="6eb96-104">Methods</span></span>  
  
|<span data-ttu-id="6eb96-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="6eb96-105">Method</span></span>|<span data-ttu-id="6eb96-106">説明</span><span class="sxs-lookup"><span data-stu-id="6eb96-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6eb96-107">AllocVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="6eb96-107">AllocVirtual Method</span></span>](iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="6eb96-108">ターゲットプロセスのアドレス空間にメモリを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="6eb96-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="6eb96-109">FreeVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="6eb96-109">FreeVirtual Method</span></span>](iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="6eb96-110">ターゲットプロセスのアドレス空間で以前に割り当てられたメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="6eb96-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6eb96-111">注釈</span><span class="sxs-lookup"><span data-stu-id="6eb96-111">Remarks</span></span>  

 <span data-ttu-id="6eb96-112">API クライアント (つまりデバッガー) は、特定のターゲット プロセスに応じてこのインターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6eb96-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="6eb96-113">たとえば、ライブ プロセスの実装は、メモリ ダンプの実装とは異なります。</span><span class="sxs-lookup"><span data-stu-id="6eb96-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="6eb96-114">ターゲットは、メモリ領域の変更をサポートしない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6eb96-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6eb96-115">要件</span><span class="sxs-lookup"><span data-stu-id="6eb96-115">Requirements</span></span>  

 <span data-ttu-id="6eb96-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6eb96-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6eb96-117">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="6eb96-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="6eb96-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6eb96-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6eb96-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6eb96-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eb96-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="6eb96-120">See also</span></span>

- [<span data-ttu-id="6eb96-121">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6eb96-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
- [<span data-ttu-id="6eb96-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="6eb96-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
