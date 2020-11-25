---
title: LockClrVersion 関数
ms.date: 03/30/2017
api_name:
- LockClrVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LockClrVersion
helpviewer_keywords:
- LockClrVersion function [.NET Framework hosting]
ms.assetid: 1318ee37-c43b-40eb-bbe8-88fc46453d74
topic_type:
- apiref
ms.openlocfilehash: 2ff08ec8f194ccc9e968b3a7ee017afe788f4b03
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704943"
---
# <a name="lockclrversion-function"></a><span data-ttu-id="874b7-102">LockClrVersion 関数</span><span class="sxs-lookup"><span data-stu-id="874b7-102">LockClrVersion Function</span></span>

<span data-ttu-id="874b7-103">CLR を明示的に初期化する前に、プロセス内で使用される共通言語ランタイム (CLR) のバージョンをホストが判断できるようにします。</span><span class="sxs-lookup"><span data-stu-id="874b7-103">Allows the host to determine which version of the common language runtime (CLR) will be used within the process before explicitly initializing the CLR.</span></span>  
  
 <span data-ttu-id="874b7-104">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="874b7-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="874b7-105">構文</span><span class="sxs-lookup"><span data-stu-id="874b7-105">Syntax</span></span>  
  
```cpp  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="874b7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="874b7-106">Parameters</span></span>  

 `hostCallback`  
 <span data-ttu-id="874b7-107">から初期化時に CLR によって呼び出される関数。</span><span class="sxs-lookup"><span data-stu-id="874b7-107">[in] The function to be called by the CLR upon initialization.</span></span>  
  
 `pBeginHostSetup`  
 <span data-ttu-id="874b7-108">から初期化を開始することを CLR に通知するために、ホストによって呼び出される関数。</span><span class="sxs-lookup"><span data-stu-id="874b7-108">[in] The function to be called by the host to inform the CLR that initialization is starting.</span></span>  
  
 `pEndHostSetup`  
 <span data-ttu-id="874b7-109">から初期化が完了したことを CLR に通知するために、ホストによって呼び出される関数。</span><span class="sxs-lookup"><span data-stu-id="874b7-109">[in] The function to be called by the host to inform the CLR that initialization is complete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="874b7-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="874b7-110">Return Value</span></span>  

 <span data-ttu-id="874b7-111">このメソッドは、次の値に加えて、Winerror.h で定義されている標準の COM エラーコードを返します。</span><span class="sxs-lookup"><span data-stu-id="874b7-111">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="874b7-112">リターン コード</span><span class="sxs-lookup"><span data-stu-id="874b7-112">Return code</span></span>|<span data-ttu-id="874b7-113">説明</span><span class="sxs-lookup"><span data-stu-id="874b7-113">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="874b7-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="874b7-114">S_OK</span></span>|<span data-ttu-id="874b7-115">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="874b7-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="874b7-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="874b7-116">E_INVALIDARG</span></span>|<span data-ttu-id="874b7-117">1つ以上の引数が null です。</span><span class="sxs-lookup"><span data-stu-id="874b7-117">One or more of the arguments is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="874b7-118">注釈</span><span class="sxs-lookup"><span data-stu-id="874b7-118">Remarks</span></span>  

 <span data-ttu-id="874b7-119">CLR を初期化する前に、ホストがを呼び出し `LockClrVersion` ます。</span><span class="sxs-lookup"><span data-stu-id="874b7-119">The host calls `LockClrVersion` before initializing the CLR.</span></span> <span data-ttu-id="874b7-120">`LockClrVersion` は、3つのパラメーターを受け取ります。これらはすべて [Flockclrversioncallback](flockclrversioncallback-function-pointer.md)型のコールバックです。</span><span class="sxs-lookup"><span data-stu-id="874b7-120">`LockClrVersion` takes three parameters, all of which are callbacks of type [FLockClrVersionCallback](flockclrversioncallback-function-pointer.md).</span></span> <span data-ttu-id="874b7-121">この型は次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="874b7-121">This type is defined as follows.</span></span>  
  
```cpp  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 <span data-ttu-id="874b7-122">ランタイムの初期化時には、次の手順が実行されます。</span><span class="sxs-lookup"><span data-stu-id="874b7-122">The following steps occur upon initialization of the runtime:</span></span>  
  
1. <span data-ttu-id="874b7-123">ホストは [Corbindtoruntimeex](corbindtoruntimeex-function.md) またはその他のランタイム初期化関数のいずれかを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="874b7-123">The host calls [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or one of the other runtime initialization functions.</span></span> <span data-ttu-id="874b7-124">また、ホストは COM オブジェクトアクティベーションを使用してランタイムを初期化することもできます。</span><span class="sxs-lookup"><span data-stu-id="874b7-124">Alternatively, the host could initialize the runtime using COM object activation.</span></span>  
  
2. <span data-ttu-id="874b7-125">ランタイムは、パラメーターによって指定された関数を呼び出し `hostCallback` ます。</span><span class="sxs-lookup"><span data-stu-id="874b7-125">The runtime calls the function specified by the `hostCallback` parameter.</span></span>  
  
3. <span data-ttu-id="874b7-126">によって指定された関数は、 `hostCallback` 次の一連の呼び出しを行います。</span><span class="sxs-lookup"><span data-stu-id="874b7-126">The function specified by `hostCallback` then makes the following sequence of calls:</span></span>  
  
    - <span data-ttu-id="874b7-127">パラメーターによって指定された関数 `pBeginHostSetup` 。</span><span class="sxs-lookup"><span data-stu-id="874b7-127">The function specified by the `pBeginHostSetup` parameter.</span></span>  
  
    - <span data-ttu-id="874b7-128">`CorBindToRuntimeEx` (または別のランタイム初期化関数)。</span><span class="sxs-lookup"><span data-stu-id="874b7-128">`CorBindToRuntimeEx` (or another runtime initialization function).</span></span>  
  
    - <span data-ttu-id="874b7-129">[ICLRRuntimeHost:: SetHostControl](iclrruntimehost-sethostcontrol-method.md)。</span><span class="sxs-lookup"><span data-stu-id="874b7-129">[ICLRRuntimeHost::SetHostControl](iclrruntimehost-sethostcontrol-method.md).</span></span>  
  
    - <span data-ttu-id="874b7-130">[ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md)。</span><span class="sxs-lookup"><span data-stu-id="874b7-130">[ICLRRuntimeHost::Start](iclrruntimehost-start-method.md).</span></span>  
  
    - <span data-ttu-id="874b7-131">パラメーターによって指定された関数 `pEndHostSetup` 。</span><span class="sxs-lookup"><span data-stu-id="874b7-131">The function specified by the `pEndHostSetup` parameter.</span></span>  
  
 <span data-ttu-id="874b7-132">からへのすべての呼び出しは、 `pBeginHostSetup` `pEndHostSetup` 同じ論理スタックを持つ1つのスレッドまたはファイバーに対して行われる必要があります。</span><span class="sxs-lookup"><span data-stu-id="874b7-132">All the calls from `pBeginHostSetup` to `pEndHostSetup` must occur on a single thread or fiber, with the same logical stack.</span></span> <span data-ttu-id="874b7-133">このスレッドは、が呼び出されたときのスレッドとは異なる場合があり `hostCallback` ます。</span><span class="sxs-lookup"><span data-stu-id="874b7-133">This thread can be different from the thread upon which `hostCallback` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="874b7-134">要件</span><span class="sxs-lookup"><span data-stu-id="874b7-134">Requirements</span></span>  

 <span data-ttu-id="874b7-135">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="874b7-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="874b7-136">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="874b7-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="874b7-137">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="874b7-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="874b7-138">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="874b7-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="874b7-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="874b7-139">See also</span></span>

- [<span data-ttu-id="874b7-140">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="874b7-140">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
