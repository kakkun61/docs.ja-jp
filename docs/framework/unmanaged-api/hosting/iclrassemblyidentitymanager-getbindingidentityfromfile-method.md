---
title: ICLRAssemblyIdentityManager::GetBindingIdentityFromFile メソッド
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetBindingIdentityFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetBindingIdentityFromFile
helpviewer_keywords:
- GetBindingIdentityFromFile method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentifyFromFile method [.NET Framework hosting]
ms.assetid: 7797562d-7b4c-4bd9-8b93-f35e0e2869e4
topic_type:
- apiref
ms.openlocfilehash: 443acfa77dc8103008263f19bed116d02e7ea676
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716741"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a><span data-ttu-id="bf6ed-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile メソッド</span><span class="sxs-lookup"><span data-stu-id="bf6ed-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Method</span></span>

<span data-ttu-id="bf6ed-103">指定したファイルパスにあるアセンブリのアセンブリ id バインドデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="bf6ed-103">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf6ed-104">構文</span><span class="sxs-lookup"><span data-stu-id="bf6ed-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf6ed-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bf6ed-105">Parameters</span></span>  

 `pwzFilePath`  
 <span data-ttu-id="bf6ed-106">から評価されるファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="bf6ed-106">[in] The path to the file to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="bf6ed-107">からアセンブリの id 型を示す [Eclrassemblyidentity flags](eclrassemblyidentityflags-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="bf6ed-107">[in] A value of the [ECLRAssemblyIdentityFlags](eclrassemblyidentityflags-enumeration.md) enumeration that indicates an assembly's identity type.</span></span> <span data-ttu-id="bf6ed-108">将来の拡張のために提供されます。</span><span class="sxs-lookup"><span data-stu-id="bf6ed-108">Provided for future extensibility.</span></span> <span data-ttu-id="bf6ed-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT は、共通言語ランタイム (CLR) バージョン2.0 でサポートされている唯一の値です。</span><span class="sxs-lookup"><span data-stu-id="bf6ed-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the common language runtime (CLR) version 2.0 supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="bf6ed-110">入出力非透過アセンブリ id データを格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="bf6ed-110">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="bf6ed-111">[入力、出力]のサイズへのポインター `pwzBuffer` 。</span><span class="sxs-lookup"><span data-stu-id="bf6ed-111">[in, out] A pointer to the size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf6ed-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="bf6ed-112">Return Value</span></span>  
  
|<span data-ttu-id="bf6ed-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bf6ed-113">HRESULT</span></span>|<span data-ttu-id="bf6ed-114">説明</span><span class="sxs-lookup"><span data-stu-id="bf6ed-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bf6ed-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="bf6ed-115">S_OK</span></span>|<span data-ttu-id="bf6ed-116">メソッドから正常に値が返されました。</span><span class="sxs-lookup"><span data-stu-id="bf6ed-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="bf6ed-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="bf6ed-117">E_INVALIDARG</span></span>|<span data-ttu-id="bf6ed-118">指定された `pwzFilePath` が null です。</span><span class="sxs-lookup"><span data-stu-id="bf6ed-118">The supplied `pwzFilePath` is null.</span></span>|  
|<span data-ttu-id="bf6ed-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="bf6ed-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="bf6ed-120">のサイズ `pwzBuffer` が小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="bf6ed-120">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="bf6ed-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bf6ed-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bf6ed-122">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="bf6ed-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bf6ed-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bf6ed-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bf6ed-124">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="bf6ed-124">The call timed out.</span></span>|  
|<span data-ttu-id="bf6ed-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bf6ed-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bf6ed-126">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="bf6ed-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bf6ed-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bf6ed-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bf6ed-128">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="bf6ed-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bf6ed-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bf6ed-129">E_FAIL</span></span>|<span data-ttu-id="bf6ed-130">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="bf6ed-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bf6ed-131">メソッドが E_FAIL を返す場合、そのプロセス内で CLR は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="bf6ed-131">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bf6ed-132">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="bf6ed-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf6ed-133">注釈</span><span class="sxs-lookup"><span data-stu-id="bf6ed-133">Remarks</span></span>  

 <span data-ttu-id="bf6ed-134">`GetBindingIdentityFromFile` は通常、2回呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="bf6ed-134">`GetBindingIdentityFromFile` is typically called twice.</span></span> <span data-ttu-id="bf6ed-135">最初の呼び出しでは、に null 値が指定され、 `pwzBuffer` メソッドはの適切なサイズを返し `pcchBufferSize` ます。</span><span class="sxs-lookup"><span data-stu-id="bf6ed-135">The first call supplies a null value for `pwzBuffer`, and the method returns the appropriate size in `pcchBufferSize`.</span></span> <span data-ttu-id="bf6ed-136">2番目の呼び出しでは、適切に割り当てられたバッファーが提供され、メソッドは完了時に実際のバッファーデータと共にを返します。</span><span class="sxs-lookup"><span data-stu-id="bf6ed-136">The second call supplies an appropriately allocated buffer, and the method returns with the actual buffer data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf6ed-137">要件</span><span class="sxs-lookup"><span data-stu-id="bf6ed-137">Requirements</span></span>  

 <span data-ttu-id="bf6ed-138">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf6ed-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf6ed-139">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="bf6ed-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bf6ed-140">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="bf6ed-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bf6ed-141">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf6ed-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf6ed-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf6ed-142">See also</span></span>

- [<span data-ttu-id="bf6ed-143">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bf6ed-143">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="bf6ed-144">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bf6ed-144">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="bf6ed-145">ICLRHostBindingPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bf6ed-145">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
