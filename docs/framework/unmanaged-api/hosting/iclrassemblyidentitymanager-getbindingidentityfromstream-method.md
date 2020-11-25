---
title: ICLRAssemblyIdentityManager::GetBindingIdentityFromStream メソッド
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetBindingIdentityFromStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream
helpviewer_keywords:
- GetBindingIdentityFromStream method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream method [.NET Framework hosting]
ms.assetid: 40123b30-a589-46b3-95d3-af7b2b0baa05
topic_type:
- apiref
ms.openlocfilehash: f1e6a47c0838782ae0610d49ca7fce3eb8554458
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716708"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="6ee93-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream メソッド</span><span class="sxs-lookup"><span data-stu-id="6ee93-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>

<span data-ttu-id="6ee93-103">指定したストリーム内のアセンブリの正規アセンブリ id データを取得します。</span><span class="sxs-lookup"><span data-stu-id="6ee93-103">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ee93-104">構文</span><span class="sxs-lookup"><span data-stu-id="6ee93-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ee93-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6ee93-105">Parameters</span></span>  

 `pStream`  
 <span data-ttu-id="6ee93-106">から評価されるアセンブリストリーム。</span><span class="sxs-lookup"><span data-stu-id="6ee93-106">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="6ee93-107">から将来の拡張のために提供されます。</span><span class="sxs-lookup"><span data-stu-id="6ee93-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="6ee93-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT は、共通言語ランタイム (CLR) の現在のバージョンでサポートされている唯一の値です。</span><span class="sxs-lookup"><span data-stu-id="6ee93-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="6ee93-109">入出力非透過アセンブリ id データを格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="6ee93-109">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="6ee93-110">[入力、出力]のサイズ `pwzBuffer` 。</span><span class="sxs-lookup"><span data-stu-id="6ee93-110">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ee93-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="6ee93-111">Return Value</span></span>  
  
|<span data-ttu-id="6ee93-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6ee93-112">HRESULT</span></span>|<span data-ttu-id="6ee93-113">説明</span><span class="sxs-lookup"><span data-stu-id="6ee93-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6ee93-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="6ee93-114">S_OK</span></span>|<span data-ttu-id="6ee93-115">メソッドから正常に値が返されました。</span><span class="sxs-lookup"><span data-stu-id="6ee93-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="6ee93-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="6ee93-116">E_INVALIDARG</span></span>|<span data-ttu-id="6ee93-117">指定された `pStream` が null です。</span><span class="sxs-lookup"><span data-stu-id="6ee93-117">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="6ee93-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="6ee93-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="6ee93-119">のサイズ `pwzBuffer` が小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="6ee93-119">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="6ee93-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6ee93-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6ee93-121">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="6ee93-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6ee93-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6ee93-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6ee93-123">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="6ee93-123">The call timed out.</span></span>|  
|<span data-ttu-id="6ee93-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6ee93-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6ee93-125">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="6ee93-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6ee93-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6ee93-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6ee93-127">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="6ee93-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6ee93-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6ee93-128">E_FAIL</span></span>|<span data-ttu-id="6ee93-129">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="6ee93-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6ee93-130">メソッドが E_FAIL を返す場合、そのプロセス内で CLR は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="6ee93-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6ee93-131">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="6ee93-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6ee93-132">要件</span><span class="sxs-lookup"><span data-stu-id="6ee93-132">Requirements</span></span>  

 <span data-ttu-id="6ee93-133">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ee93-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ee93-134">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="6ee93-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6ee93-135">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="6ee93-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ee93-136">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ee93-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ee93-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ee93-137">See also</span></span>

- [<span data-ttu-id="6ee93-138">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6ee93-138">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="6ee93-139">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6ee93-139">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
