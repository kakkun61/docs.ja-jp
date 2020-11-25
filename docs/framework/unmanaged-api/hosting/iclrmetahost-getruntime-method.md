---
title: ICLRMetaHost::GetRuntime メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetRuntime
helpviewer_keywords:
- GetRuntime method [.NET Framework hosting]
- ICLRMetaHost::GetRuntime method [.NET Framework hosting]
ms.assetid: a10749f1-ab91-47cf-982f-d8ccd2e81bd2
topic_type:
- apiref
ms.openlocfilehash: 093fa64a7d51e0c2fdc304d2bb4f1c9f7b03e2ec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730410"
---
# <a name="iclrmetahostgetruntime-method"></a><span data-ttu-id="ce2e7-102">ICLRMetaHost::GetRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="ce2e7-102">ICLRMetaHost::GetRuntime Method</span></span>

<span data-ttu-id="ce2e7-103">共通言語ランタイム (CLR) の特定のバージョンに対応する [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスを取得します。</span><span class="sxs-lookup"><span data-stu-id="ce2e7-103">Gets the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that corresponds to a particular version of the common language runtime (CLR).</span></span> <span data-ttu-id="ce2e7-104">このメソッドは、 [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md)フラグと共に使用される[Corbindtoruntimeex](corbindtoruntimeex-function.md)関数よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="ce2e7-104">This method supersedes the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) flag.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce2e7-105">構文</span><span class="sxs-lookup"><span data-stu-id="ce2e7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in] REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce2e7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ce2e7-106">Parameters</span></span>  

 `pwzVersion`  
 <span data-ttu-id="ce2e7-107">からメタデータに格納されている .NET Framework のコンパイルバージョン。 "v *A と* いう形式になります。*B*[.*X*] "</span><span class="sxs-lookup"><span data-stu-id="ce2e7-107">[in] The .NET Framework compilation version stored in the metadata, in the format "v *A*.*B*[.*X*]".</span></span> <span data-ttu-id="ce2e7-108">*A*、 *B*、および *X* は、メジャーバージョン、マイナーバージョン、およびビルド番号に対応する10進数です。</span><span class="sxs-lookup"><span data-stu-id="ce2e7-108">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce2e7-109">このパラメーターは、C:\windows\ microsoft.net \framework または C:\Windows\Microsoft.NET\Framework64. の下に表示される .NET Framework バージョンのディレクトリ名と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce2e7-109">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework or C:\Windows\Microsoft.NET\Framework64.</span></span>  
  
 <span data-ttu-id="ce2e7-110">値の例としては、"v v1.0.3705"、"v 1.1.4322"、"v v2.0.50727"、および "v4.0" があります。*X*"。ここで *x* は、インストールされているビルド番号に依存します。</span><span class="sxs-lookup"><span data-stu-id="ce2e7-110">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="ce2e7-111">"V" プレフィックスが必要です。</span><span class="sxs-lookup"><span data-stu-id="ce2e7-111">The "v" prefix is required.</span></span>  
  
 `riid`  
 <span data-ttu-id="ce2e7-112">から目的のインターフェイスの識別子。</span><span class="sxs-lookup"><span data-stu-id="ce2e7-112">[in] The identifier for the desired interface.</span></span> <span data-ttu-id="ce2e7-113">現時点では、このパラメーターの有効な値は IID_ICLRRuntimeInfo のみです。</span><span class="sxs-lookup"><span data-stu-id="ce2e7-113">Currently, the only valid value for this parameter is IID_ICLRRuntimeInfo.</span></span>  
  
 `ppRuntime`  
 <span data-ttu-id="ce2e7-114">入出力要求されたランタイムに対応する [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ce2e7-114">[out] A pointer to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that corresponds to the requested runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ce2e7-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="ce2e7-115">Return Value</span></span>  

 <span data-ttu-id="ce2e7-116">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="ce2e7-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ce2e7-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ce2e7-117">HRESULT</span></span>|<span data-ttu-id="ce2e7-118">説明</span><span class="sxs-lookup"><span data-stu-id="ce2e7-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ce2e7-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="ce2e7-119">S_OK</span></span>|<span data-ttu-id="ce2e7-120">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="ce2e7-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="ce2e7-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="ce2e7-121">E_POINTER</span></span>|<span data-ttu-id="ce2e7-122">`pwzVersion` または `ppRuntime` が null です。</span><span class="sxs-lookup"><span data-stu-id="ce2e7-122">`pwzVersion` or `ppRuntime` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce2e7-123">注釈</span><span class="sxs-lookup"><span data-stu-id="ce2e7-123">Remarks</span></span>  

 <span data-ttu-id="ce2e7-124">このメソッドは、 [ICorRuntimeHost](icorruntimehost-interface.md) インターフェイスや、非推奨の関数などの従来の関数のようなレガシインターフェイスと常に相互作用し `CorBindTo*` ます (「.NET FRAMEWORK 2.0 ホスティング API の [非推奨の CLR ホスト関数](deprecated-clr-hosting-functions.md) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="ce2e7-124">This method interacts consistently with legacy interfaces such as the [ICorRuntimeHost](icorruntimehost-interface.md) interface and legacy functions such as the deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span> <span data-ttu-id="ce2e7-125">つまり、レガシ API で読み込まれたランタイムは新しい API から参照でき、新しい API で読み込まれたランタイムはレガシ API から参照できます。</span><span class="sxs-lookup"><span data-stu-id="ce2e7-125">That is, runtimes that are loaded with the legacy API are visible to the new API, and runtimes that are loaded with the new API are visible to the legacy API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce2e7-126">要件</span><span class="sxs-lookup"><span data-stu-id="ce2e7-126">Requirements</span></span>  

 <span data-ttu-id="ce2e7-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce2e7-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce2e7-128">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="ce2e7-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ce2e7-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="ce2e7-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ce2e7-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce2e7-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce2e7-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="ce2e7-131">See also</span></span>

- [<span data-ttu-id="ce2e7-132">ICLRMetaHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ce2e7-132">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="ce2e7-133">非推奨の CLR のホスト インターフェイスおよびコクラス</span><span class="sxs-lookup"><span data-stu-id="ce2e7-133">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)
- [<span data-ttu-id="ce2e7-134">CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ce2e7-134">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="ce2e7-135">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="ce2e7-135">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="ce2e7-136">ホスティング</span><span class="sxs-lookup"><span data-stu-id="ce2e7-136">Hosting</span></span>](index.md)
