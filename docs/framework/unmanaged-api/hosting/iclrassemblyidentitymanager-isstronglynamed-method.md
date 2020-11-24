---
title: ICLRAssemblyIdentityManager::IsStronglyNamed メソッド
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.IsStronglyNamed
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::IsStronglyNamed
helpviewer_keywords:
- IsStronglyNamed method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::IsStronglyNamed method [.NET Framework hosting]
ms.assetid: 954bd386-2076-4d00-9d46-38c728aa9cab
topic_type:
- apiref
ms.openlocfilehash: 9ac3b2ae349a696ba0cea1bad3e3484bb1c113fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679248"
---
# <a name="iclrassemblyidentitymanagerisstronglynamed-method"></a><span data-ttu-id="9ed94-102">ICLRAssemblyIdentityManager::IsStronglyNamed メソッド</span><span class="sxs-lookup"><span data-stu-id="9ed94-102">ICLRAssemblyIdentityManager::IsStronglyNamed Method</span></span>

<span data-ttu-id="9ed94-103">指定したアセンブリに厳密な名前が付けられているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="9ed94-103">Gets a value that indicates whether the specified assembly is strongly named.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ed94-104">構文</span><span class="sxs-lookup"><span data-stu-id="9ed94-104">Syntax</span></span>  
  
```cpp  
RESULT IsStronglyNamed (  
    [in]  LPCWSTR  pwzAssemblyIdentity,  
    [out] BOOL    *pbIsStronglyNamed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ed94-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ed94-105">Parameters</span></span>  

 `pwzAssemblyIdentity`  
 <span data-ttu-id="9ed94-106">から評価されるアセンブリの非透過正規アセンブリ id データ。</span><span class="sxs-lookup"><span data-stu-id="9ed94-106">[in] The opaque canonical assembly identity data of the assembly to be evaluated.</span></span>  
  
 `pbIsStronglyNamed`  
 <span data-ttu-id="9ed94-107">[out] `true` 。パラメーターによって参照されるアセンブリに `pwzAssemblyIdentity` 厳密な名前が付けられている場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="9ed94-107">[out] `true`, if the assembly referenced by the `pwzAssemblyIdentity` parameter is strongly named; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ed94-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="9ed94-108">Return Value</span></span>  
  
|<span data-ttu-id="9ed94-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9ed94-109">HRESULT</span></span>|<span data-ttu-id="9ed94-110">説明</span><span class="sxs-lookup"><span data-stu-id="9ed94-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9ed94-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9ed94-111">S_OK</span></span>|<span data-ttu-id="9ed94-112">メソッドから正常に値が返されました。</span><span class="sxs-lookup"><span data-stu-id="9ed94-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="9ed94-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9ed94-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9ed94-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="9ed94-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9ed94-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9ed94-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9ed94-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="9ed94-116">The call timed out.</span></span>|  
|<span data-ttu-id="9ed94-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9ed94-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9ed94-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="9ed94-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9ed94-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9ed94-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9ed94-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="9ed94-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9ed94-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9ed94-121">E_FAIL</span></span>|<span data-ttu-id="9ed94-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="9ed94-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9ed94-123">メソッドが E_FAIL を返す場合、そのプロセス内で CLR は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="9ed94-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9ed94-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="9ed94-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9ed94-125">要件</span><span class="sxs-lookup"><span data-stu-id="9ed94-125">Requirements</span></span>  

 <span data-ttu-id="9ed94-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ed94-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ed94-127">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9ed94-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9ed94-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="9ed94-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ed94-129">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ed94-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ed94-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ed94-130">See also</span></span>

- [<span data-ttu-id="9ed94-131">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ed94-131">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
