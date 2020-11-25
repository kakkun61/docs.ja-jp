---
title: ICLRDataTarget インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget
helpviewer_keywords:
- ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: e2f05155-9bef-4e11-b703-7f05890665ca
topic_type:
- apiref
ms.openlocfilehash: 0d3e6a95d8fd71a67b97923dac53c1f615dfe666
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703422"
---
# <a name="iclrdatatarget-interface"></a><span data-ttu-id="a5e88-102">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5e88-102">ICLRDataTarget Interface</span></span>

<span data-ttu-id="a5e88-103">共通言語ランタイム (CLR) のターゲット項目と対話するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a5e88-103">Provides methods for interaction with a target item of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a5e88-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="a5e88-104">Methods</span></span>  
  
|<span data-ttu-id="a5e88-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a5e88-105">Method</span></span>|<span data-ttu-id="a5e88-106">説明</span><span class="sxs-lookup"><span data-stu-id="a5e88-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a5e88-107">GetCurrentThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="a5e88-107">GetCurrentThreadID Method</span></span>](iclrdatatarget-getcurrentthreadid-method.md)|<span data-ttu-id="a5e88-108">現在のスレッドのオペレーティングシステム id を取得します。</span><span class="sxs-lookup"><span data-stu-id="a5e88-108">Gets the operating system identifier for the current thread.</span></span>|  
|[<span data-ttu-id="a5e88-109">GetImageBase メソッド</span><span class="sxs-lookup"><span data-stu-id="a5e88-109">GetImageBase Method</span></span>](iclrdatatarget-getimagebase-method.md)|<span data-ttu-id="a5e88-110">指定したイメージのベースメモリアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="a5e88-110">Gets the base memory address for the specified image.</span></span>|  
|[<span data-ttu-id="a5e88-111">GetMachineType メソッド</span><span class="sxs-lookup"><span data-stu-id="a5e88-111">GetMachineType Method</span></span>](iclrdatatarget-getmachinetype-method.md)|<span data-ttu-id="a5e88-112">ターゲットプロセスが使用している命令セットの種類の識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="a5e88-112">Gets an identifier for the kind of instruction set that the target process is using.</span></span>|  
|[<span data-ttu-id="a5e88-113">GetPointerSize メソッド</span><span class="sxs-lookup"><span data-stu-id="a5e88-113">GetPointerSize Method</span></span>](iclrdatatarget-getpointersize-method.md)|<span data-ttu-id="a5e88-114">現在のターゲットへのポインターのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="a5e88-114">Gets the size, in bytes, of a pointer to the current target.</span></span>|  
|[<span data-ttu-id="a5e88-115">GetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="a5e88-115">GetThreadContext Method</span></span>](iclrdatatarget-getthreadcontext-method.md)|<span data-ttu-id="a5e88-116">指定した識別子を持つスレッドのコンテキストへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="a5e88-116">Gets a pointer to the context of the thread with the specified identifier.</span></span>|  
|[<span data-ttu-id="a5e88-117">GetTLSValue メソッド</span><span class="sxs-lookup"><span data-stu-id="a5e88-117">GetTLSValue Method</span></span>](iclrdatatarget-gettlsvalue-method.md)|<span data-ttu-id="a5e88-118">指定したスレッドの指定したインデックスにあるスレッドローカルストレージ (TLS) の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="a5e88-118">Gets a value in thread local storage (TLS) at the specified index for the specified thread.</span></span>|  
|[<span data-ttu-id="a5e88-119">ReadVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="a5e88-119">ReadVirtual Method</span></span>](iclrdatatarget-readvirtual-method.md)|<span data-ttu-id="a5e88-120">指定された仮想メモリアドレスから指定されたバッファーにデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="a5e88-120">Reads data from the specified virtual memory address into the specified buffer.</span></span>|  
|[<span data-ttu-id="a5e88-121">Request Method (要求メソッド)</span><span class="sxs-lookup"><span data-stu-id="a5e88-121">Request Method</span></span>](iclrdatatarget-request-method.md)|<span data-ttu-id="a5e88-122">実装で定義されているように、操作を要求するために、共通言語ランタイム (CLR) データアクセスサービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a5e88-122">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>|  
|[<span data-ttu-id="a5e88-123">SetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="a5e88-123">SetThreadContext Method</span></span>](iclrdatatarget-setthreadcontext-method.md)|<span data-ttu-id="a5e88-124">ターゲットプロセス内の指定されたスレッドの現在のコンテキストを設定します。</span><span class="sxs-lookup"><span data-stu-id="a5e88-124">Sets the current context of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="a5e88-125">SetTLSValue メソッド</span><span class="sxs-lookup"><span data-stu-id="a5e88-125">SetTLSValue Method</span></span>](iclrdatatarget-settlsvalue-method.md)|<span data-ttu-id="a5e88-126">ターゲットプロセス内の指定したスレッドのスレッドローカルストレージ (TLS) の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="a5e88-126">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="a5e88-127">WriteVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="a5e88-127">WriteVirtual Method</span></span>](iclrdatatarget-writevirtual-method.md)|<span data-ttu-id="a5e88-128">指定されたバッファーから指定された仮想メモリアドレスにデータを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="a5e88-128">Writes data from the specified buffer to the specified virtual memory address.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5e88-129">注釈</span><span class="sxs-lookup"><span data-stu-id="a5e88-129">Remarks</span></span>  

 <span data-ttu-id="a5e88-130">API クライアント (つまり、デバッガー) は、特定のターゲット項目に適した方法でこのインターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5e88-130">The API client (that is, the debugger) must implement this interface as appropriate for the particular target item.</span></span> <span data-ttu-id="a5e88-131">たとえば、ライブ プロセスの実装は、メモリ ダンプの実装とは異なります。</span><span class="sxs-lookup"><span data-stu-id="a5e88-131">For example, a live process would have an implementation different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5e88-132">要件</span><span class="sxs-lookup"><span data-stu-id="a5e88-132">Requirements</span></span>  

 <span data-ttu-id="a5e88-133">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5e88-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5e88-134">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="a5e88-134">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="a5e88-135">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5e88-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5e88-136">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5e88-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5e88-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="a5e88-137">See also</span></span>

- [<span data-ttu-id="a5e88-138">ICLRDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5e88-138">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="a5e88-139">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5e88-139">Debugging Interfaces</span></span>](debugging-interfaces.md)
