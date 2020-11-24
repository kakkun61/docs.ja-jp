---
title: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream メソッド
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetReferencedAssembliesFromStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream method [.NET Framework hosting]
- GetReferencedAssembliesFromStream method [.NET Framework hosting]
ms.assetid: fe9849c1-c3fc-477b-a31f-e8619f5516f5
topic_type:
- apiref
ms.openlocfilehash: a5e71d6ca90c8d0aa489176eb5a90bfe6896b1cb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679322"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromstream-method"></a><span data-ttu-id="705d6-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream メソッド</span><span class="sxs-lookup"><span data-stu-id="705d6-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Method</span></span>

<span data-ttu-id="705d6-103">指定したストリーム内のアセンブリによって参照されるアセンブリのアセンブリ id データを格納する [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) オブジェクトへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="705d6-103">Gets a pointer to an [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="705d6-104">構文</span><span class="sxs-lookup"><span data-stu-id="705d6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferencedAssembliesFromStream (  
    [in]  IStream *pStream,  
    [in]  DWORD    dwFlags,  
    [in]  ICLRAssemblyReferenceList  *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="705d6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="705d6-105">Parameters</span></span>  

 `pStream`  
 <span data-ttu-id="705d6-106">から `IStream` 評価されるアセンブリを格納しているへのインターフェイスポインター。</span><span class="sxs-lookup"><span data-stu-id="705d6-106">[in] An interface pointer to an `IStream` containing the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="705d6-107">から将来の拡張のために提供されます。</span><span class="sxs-lookup"><span data-stu-id="705d6-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="705d6-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT は、共通言語ランタイム (CLR) の現在のバージョンでサポートされている唯一の値です。</span><span class="sxs-lookup"><span data-stu-id="705d6-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="705d6-109">から除外されるアセンブリのアセンブリ id データを格納する [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) オブジェクトへのポインター `ppReferenceEnum` 。</span><span class="sxs-lookup"><span data-stu-id="705d6-109">[in] A pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) object that contains assembly identity data for the assemblies to be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="705d6-110">入出力内のアセンブリによって参照されるアセンブリのアセンブリ id データを格納するオブジェクトのアドレスへのポインター `ICLRReferenceAssemblyEnum` `pStream` (内のアセンブリは除く) `pExcludeAssembliesList` 。</span><span class="sxs-lookup"><span data-stu-id="705d6-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in `pStream`, excluding the assemblies in `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="705d6-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="705d6-111">Return Value</span></span>  
  
|<span data-ttu-id="705d6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="705d6-112">HRESULT</span></span>|<span data-ttu-id="705d6-113">説明</span><span class="sxs-lookup"><span data-stu-id="705d6-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="705d6-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="705d6-114">S_OK</span></span>|<span data-ttu-id="705d6-115">メソッドから正常に値が返されました。</span><span class="sxs-lookup"><span data-stu-id="705d6-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="705d6-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="705d6-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="705d6-117">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="705d6-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="705d6-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="705d6-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="705d6-119">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="705d6-119">The call timed out.</span></span>|  
|<span data-ttu-id="705d6-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="705d6-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="705d6-121">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="705d6-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="705d6-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="705d6-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="705d6-123">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="705d6-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="705d6-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="705d6-124">E_FAIL</span></span>|<span data-ttu-id="705d6-125">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="705d6-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="705d6-126">メソッドが E_FAIL を返す場合、そのプロセス内で CLR は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="705d6-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="705d6-127">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="705d6-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="705d6-128">注釈</span><span class="sxs-lookup"><span data-stu-id="705d6-128">Remarks</span></span>  

 <span data-ttu-id="705d6-129">呼び出し元は、返された一覧から一連の既知のアセンブリ参照を除外することを選択できます。</span><span class="sxs-lookup"><span data-stu-id="705d6-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="705d6-130">このセットはによって定義され `pExcludeAssembliesList` ます。</span><span class="sxs-lookup"><span data-stu-id="705d6-130">This set is defined by `pExcludeAssembliesList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="705d6-131">要件</span><span class="sxs-lookup"><span data-stu-id="705d6-131">Requirements</span></span>  

 <span data-ttu-id="705d6-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="705d6-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="705d6-133">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="705d6-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="705d6-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="705d6-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="705d6-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="705d6-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="705d6-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="705d6-136">See also</span></span>

- [<span data-ttu-id="705d6-137">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="705d6-137">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="705d6-138">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="705d6-138">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="705d6-139">ICLRReferenceAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="705d6-139">ICLRReferenceAssemblyEnum Interface</span></span>](iclrreferenceassemblyenum-interface.md)
