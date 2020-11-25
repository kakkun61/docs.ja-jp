---
title: ICLRRuntimeInfo::GetRuntimeDirectory メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetRuntimeDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetRuntimeDirectory
helpviewer_keywords:
- GetRuntimeDirectory method [.NET Framework hosting]
- ICLRRuntimeInfo::GetRuntimeDirectory method [.NET Framework hosting]
ms.assetid: 4401546e-4d48-453f-a1fb-b2ebda54df5c
topic_type:
- apiref
ms.openlocfilehash: 24679118e4255282f7da3ff8be2ce9c08250e181
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732048"
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a><span data-ttu-id="acba6-102">ICLRRuntimeInfo::GetRuntimeDirectory メソッド</span><span class="sxs-lookup"><span data-stu-id="acba6-102">ICLRRuntimeInfo::GetRuntimeDirectory Method</span></span>

<span data-ttu-id="acba6-103">このインターフェイスに関連付けられている共通言語ランタイム (CLR) のインストールディレクトリを取得します。</span><span class="sxs-lookup"><span data-stu-id="acba6-103">Gets the installation directory of the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="acba6-104">このメソッドは、.NET Framework バージョン2.0、3.0、および3.5 で提供される [Getcorsystemdirectory](getcorsystemdirectory-function.md) 関数よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="acba6-104">This method supersedes the [GetCORSystemDirectory](getcorsystemdirectory-function.md) function provided in the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acba6-105">構文</span><span class="sxs-lookup"><span data-stu-id="acba6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="acba6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="acba6-106">Parameters</span></span>  

 `pwzBuffer`  
 <span data-ttu-id="acba6-107">入出力CLR インストールディレクトリを返します。</span><span class="sxs-lookup"><span data-stu-id="acba6-107">[out] Returns the CLR installation directory.</span></span> <span data-ttu-id="acba6-108">インストールパスは完全修飾されています。たとえば、"c:\windows\microsoft.net\framework\v1.0.3705" のように \\ なります。</span><span class="sxs-lookup"><span data-stu-id="acba6-108">The installation path is fully qualified; for example, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="acba6-109">[入力、出力] `pwzBuffer` バッファーオーバーランを回避するためののサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="acba6-109">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="acba6-110">`pwzBuffer`が null の場合、は `pchBuffer` 必要なサイズを返し `pwzBuffer` ます。</span><span class="sxs-lookup"><span data-stu-id="acba6-110">If `pwzBuffer` is null, `pchBuffer` returns the required size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="acba6-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="acba6-111">Return Value</span></span>  

 <span data-ttu-id="acba6-112">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="acba6-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="acba6-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="acba6-113">HRESULT</span></span>|<span data-ttu-id="acba6-114">説明</span><span class="sxs-lookup"><span data-stu-id="acba6-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="acba6-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="acba6-115">S_OK</span></span>|<span data-ttu-id="acba6-116">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="acba6-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="acba6-117">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="acba6-117">E_POINTER</span></span>|<span data-ttu-id="acba6-118">`pwzBuffer` または `pchBuffer` が null です。</span><span class="sxs-lookup"><span data-stu-id="acba6-118">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acba6-119">解説</span><span class="sxs-lookup"><span data-stu-id="acba6-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acba6-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="acba6-120">Requirements</span></span>  

 <span data-ttu-id="acba6-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="acba6-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acba6-122">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="acba6-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="acba6-123">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="acba6-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="acba6-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acba6-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acba6-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="acba6-125">See also</span></span>

- [<span data-ttu-id="acba6-126">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="acba6-126">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="acba6-127">ホスティング</span><span class="sxs-lookup"><span data-stu-id="acba6-127">Hosting</span></span>](index.md)
