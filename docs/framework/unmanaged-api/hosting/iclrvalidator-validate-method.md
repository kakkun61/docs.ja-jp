---
title: ICLRValidator::Validate メソッド
ms.date: 03/30/2017
api_name:
- ICLRValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::Validate
helpviewer_keywords:
- Validate method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::Validate method [.NET Framework hosting]
ms.assetid: 0b1b432a-d234-4002-839b-81366c3a8bdc
topic_type:
- apiref
ms.openlocfilehash: 4ce50f7706583f291d2e6a141d40ab6dd3e4b3e2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674386"
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="b8124-102">ICLRValidator::Validate メソッド</span><span class="sxs-lookup"><span data-stu-id="b8124-102">ICLRValidator::Validate Method</span></span>

<span data-ttu-id="b8124-103">指定されたファイル内のポータブル実行可能 (PE) または Microsoft 中間言語 (MSIL) を検証します。</span><span class="sxs-lookup"><span data-stu-id="b8124-103">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8124-104">構文</span><span class="sxs-lookup"><span data-stu-id="b8124-104">Syntax</span></span>  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler        *veh,  
    [in] unsigned long      ulAppDomainId,  
    [in] unsigned long      ulFlags,  
    [in] unsigned long      ulMaxError,  
    [in] unsigned long      token,  
    [in] LPWSTR             fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long      ulSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="b8124-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b8124-105">Parameters</span></span>  

 `veh`  
 <span data-ttu-id="b8124-106">から `IVEHandler` 検証エラーを処理するインスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b8124-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="b8124-107">から現在のの識別子 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="b8124-107">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="b8124-108">から実行する必要のある検証の種類を示す、 [Validatorflags](validatorflags-enumeration.md) 値の組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="b8124-108">[in] A combination of [ValidatorFlags](validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="b8124-109">から検証を終了するまでに許容されるエラーの最大数。</span><span class="sxs-lookup"><span data-stu-id="b8124-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="b8124-110">から未使用.</span><span class="sxs-lookup"><span data-stu-id="b8124-110">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="b8124-111">から検証するファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="b8124-111">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="b8124-112">からファイルバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b8124-112">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="b8124-113">から検証するファイルのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="b8124-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b8124-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="b8124-114">Return Value</span></span>  
  
|<span data-ttu-id="b8124-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b8124-115">HRESULT</span></span>|<span data-ttu-id="b8124-116">説明</span><span class="sxs-lookup"><span data-stu-id="b8124-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b8124-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="b8124-117">S_OK</span></span>|<span data-ttu-id="b8124-118">`Validate` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="b8124-118">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="b8124-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b8124-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b8124-120">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="b8124-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b8124-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b8124-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b8124-122">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="b8124-122">The call timed out.</span></span>|  
|<span data-ttu-id="b8124-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b8124-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b8124-124">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="b8124-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b8124-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b8124-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b8124-126">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="b8124-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b8124-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b8124-127">E_FAIL</span></span>|<span data-ttu-id="b8124-128">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="b8124-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b8124-129">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="b8124-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b8124-130">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="b8124-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b8124-131">要件</span><span class="sxs-lookup"><span data-stu-id="b8124-131">Requirements</span></span>  

 <span data-ttu-id="b8124-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8124-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8124-133">**ヘッダー:** IValidator、IValidator</span><span class="sxs-lookup"><span data-stu-id="b8124-133">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="b8124-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="b8124-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b8124-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8124-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8124-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="b8124-136">See also</span></span>

- [<span data-ttu-id="b8124-137">ICLRValidator インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b8124-137">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)
