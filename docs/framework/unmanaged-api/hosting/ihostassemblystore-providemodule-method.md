---
title: IHostAssemblyStore::ProvideModule メソッド
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideModule
helpviewer_keywords:
- IHostAssemblyStore::ProvideModule method [.NET Framework hosting]
- ProvideModule method [.NET Framework hosting]
ms.assetid: f42e3dd0-c88e-4748-b6c0-4c515a633180
topic_type:
- apiref
ms.openlocfilehash: 35805d277774e1de03bb7dee1740a2e1305a97c9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732997"
---
# <a name="ihostassemblystoreprovidemodule-method"></a><span data-ttu-id="a2383-102">IHostAssemblyStore::ProvideModule メソッド</span><span class="sxs-lookup"><span data-stu-id="a2383-102">IHostAssemblyStore::ProvideModule Method</span></span>

<span data-ttu-id="a2383-103">アセンブリ内のモジュール、またはリンクされている (埋め込みではない) リソースファイル内のモジュールを解決します。</span><span class="sxs-lookup"><span data-stu-id="a2383-103">Resolves a module within an assembly or a linked (but not an embedded) resource file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2383-104">構文</span><span class="sxs-lookup"><span data-stu-id="a2383-104">Syntax</span></span>  
  
```cpp  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2383-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a2383-105">Parameters</span></span>  

 `pBindInfo`  
 <span data-ttu-id="a2383-106">から要求されたモジュールの、アセンブリ、およびモジュール名を記述する [Modulebindinfo](modulebindinfo-structure.md) インスタンスへのポインター <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="a2383-106">[in] A pointer to a [ModuleBindInfo](modulebindinfo-structure.md) instance that describes the requested module's <xref:System.AppDomain>, assembly, and module name.</span></span>  
  
 `pdwModuleId`  
 <span data-ttu-id="a2383-107">入出力読み込まれたモジュールを格納しているの一意の識別子へのポインター `IStream` 。</span><span class="sxs-lookup"><span data-stu-id="a2383-107">[out] A pointer to a unique identifier for the `IStream` containing the loaded module.</span></span>  
  
 `ppStmModuleImage`  
 <span data-ttu-id="a2383-108">入出力読み込み対象の `IStream` ポータブル実行可能 (PE) イメージを格納しているオブジェクトのアドレスへのポインター。モジュールが見つからなかった場合は null。</span><span class="sxs-lookup"><span data-stu-id="a2383-108">[out] A pointer to the address of an `IStream` object, which contains the portable executable (PE) image to be loaded, or null if the module could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="a2383-109">入出力 `IStream` 要求されたモジュールのプログラムデバッグ (PDB) 情報を格納しているオブジェクトのアドレスへのポインター、または .pdb ファイルが見つからなかった場合は null。</span><span class="sxs-lookup"><span data-stu-id="a2383-109">[out] A pointer to the address of an `IStream` object, which contains the program debug (PDB) information for the requested module, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2383-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="a2383-110">Return Value</span></span>  
  
|<span data-ttu-id="a2383-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a2383-111">HRESULT</span></span>|<span data-ttu-id="a2383-112">説明</span><span class="sxs-lookup"><span data-stu-id="a2383-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a2383-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="a2383-113">S_OK</span></span>|<span data-ttu-id="a2383-114">`ProvideModule` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="a2383-114">`ProvideModule` returned successfully.</span></span>|  
|<span data-ttu-id="a2383-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a2383-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a2383-116">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="a2383-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a2383-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a2383-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a2383-118">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="a2383-118">The call timed out.</span></span>|  
|<span data-ttu-id="a2383-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a2383-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a2383-120">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="a2383-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a2383-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a2383-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a2383-122">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="a2383-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a2383-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a2383-123">E_FAIL</span></span>|<span data-ttu-id="a2383-124">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="a2383-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a2383-125">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="a2383-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a2383-126">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="a2383-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a2383-127">COR_E_FILENOTFOUND (0x80070002)</span><span class="sxs-lookup"><span data-stu-id="a2383-127">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="a2383-128">要求されたアセンブリまたはリンクされたリソースが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="a2383-128">The requested assembly or linked resource could not be located.</span></span>|  
|<span data-ttu-id="a2383-129">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="a2383-129">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="a2383-130">`pdwModuleId` は、ホストが返す識別子を格納するのに十分な大きさではありません。</span><span class="sxs-lookup"><span data-stu-id="a2383-130">`pdwModuleId` is not large enough to contain the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2383-131">注釈</span><span class="sxs-lookup"><span data-stu-id="a2383-131">Remarks</span></span>  

 <span data-ttu-id="a2383-132">に対して返される id 値 `pdwModuleId` は、ホストによって指定されます。</span><span class="sxs-lookup"><span data-stu-id="a2383-132">The identity value returned for `pdwModuleId` is specified by the host.</span></span> <span data-ttu-id="a2383-133">識別子は、プロセスの有効期間内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2383-133">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="a2383-134">CLR は、この値を、関連付けられているストリームの一意の識別子として使用します。</span><span class="sxs-lookup"><span data-stu-id="a2383-134">The CLR uses this value as the unique identifier for the associated stream.</span></span> <span data-ttu-id="a2383-135">これは、各値を、の `pAssemblyId` 呼び出しによって返された値と比較し [、の](ihostassemblystore-provideassembly-method.md) `pdwModuleId` 他の呼び出しによって返された値と比較して確認 `ProvideModule` します。</span><span class="sxs-lookup"><span data-stu-id="a2383-135">It checks each value against the values for `pAssemblyId` returned by calls to [ProvideAssembly](ihostassemblystore-provideassembly-method.md) and against the values for `pdwModuleId` returned by other calls to `ProvideModule`.</span></span> <span data-ttu-id="a2383-136">ホストが別のと同じ識別子の値を返した場合、 `IStream` CLR は、そのストリームの内容が既にマップされているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="a2383-136">If the host returns the same identifier value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="a2383-137">その場合、CLR は新しいイメージをマップするのではなく、イメージの既存のコピーを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="a2383-137">If so, the CLR loads the existing copy of the image instead of mapping a new one.</span></span> <span data-ttu-id="a2383-138">したがって、識別子も、から返されるアセンブリ識別子と重複しないようにする必要があり `ProvideAssembly` ます。</span><span class="sxs-lookup"><span data-stu-id="a2383-138">Therefore, the identifier must also not overlap with the assembly identifiers returned from `ProvideAssembly`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2383-139">要件</span><span class="sxs-lookup"><span data-stu-id="a2383-139">Requirements</span></span>  

 <span data-ttu-id="a2383-140">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2383-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2383-141">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a2383-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a2383-142">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="a2383-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a2383-143">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2383-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2383-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="a2383-144">See also</span></span>

- [<span data-ttu-id="a2383-145">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a2383-145">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="a2383-146">IHostAssemblyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a2383-146">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="a2383-147">IHostAssemblyStore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a2383-147">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
