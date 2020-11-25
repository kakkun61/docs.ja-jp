---
title: CorLaunchApplication 関数
ms.date: 03/30/2017
api_name:
- CorLaunchApplication
api_location:
- mscoree.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CorLaunchApplication
helpviewer_keywords:
- CorLaunchApplication function [.NET Framework hosting]
ms.assetid: 71f362a9-8fe2-47ce-9302-05a645cf3d7d
topic_type:
- apiref
ms.openlocfilehash: ca427439f03d92b20e7714b9724d90b240e9cecb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704072"
---
# <a name="corlaunchapplication-function"></a><span data-ttu-id="24110-102">CorLaunchApplication 関数</span><span class="sxs-lookup"><span data-stu-id="24110-102">CorLaunchApplication Function</span></span>

<span data-ttu-id="24110-103">指定したネットワーク パスのアプリケーションを、指定したマニフェストとその他のアプリケーション データを使用して起動します。</span><span class="sxs-lookup"><span data-stu-id="24110-103">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 <span data-ttu-id="24110-104">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="24110-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24110-105">構文</span><span class="sxs-lookup"><span data-stu-id="24110-105">Syntax</span></span>  
  
```cpp  
HRESULT CorLaunchApplication (  
    [in]  HOST_TYPE                dwClickOnceHost,  
    [in]  LPCWSTR                  pwzAppFullName,  
    [in]  DWORD                    dwManifestPaths,  
    [in]  LPCWSTR                 *ppwzManifestPaths,  
    [in]  DWORD                    dwActivationData,  
    [in]  LPCWSTR                 *ppwzActivationData,  
    [out] LPPROCESS_INFORMATION    lpProcessInformation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24110-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="24110-106">Parameters</span></span>  

 `dwClickOnceHost`  
 <span data-ttu-id="24110-107">からアプリケーションを起動しているホストの種類を指定する [HOST_TYPE](host-type-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="24110-107">[in] A value of the [HOST_TYPE](host-type-enumeration.md) enumeration that specifies the type of host that is launching the application.</span></span>  
  
 `pwzAppFullName`  
 <span data-ttu-id="24110-108">から起動されるアプリケーションの完全な名前。</span><span class="sxs-lookup"><span data-stu-id="24110-108">[in] The full name of the application that is being launched.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="24110-109">からアプリケーションのマニフェストパスの数。</span><span class="sxs-lookup"><span data-stu-id="24110-109">[in] The number of manifest paths for the application.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="24110-110">から文字列の配列。それぞれが、起動されるアプリケーションのマニフェストへのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="24110-110">[in] An array of strings, each of which specifies a path to a manifest for the application that is being launched.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="24110-111">から起動されるアプリケーションのアクティブ化データ項目の数。</span><span class="sxs-lookup"><span data-stu-id="24110-111">[in] The number of activation data items for the application that is being launched.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="24110-112">から文字列の配列。各文字列は、起動されるアプリケーションのアクティベーションデータ項目です。</span><span class="sxs-lookup"><span data-stu-id="24110-112">[in] An array of strings, each of which is an activation data item for the application that is being launched.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="24110-113">入出力アプリケーションが読み込まれたプロセスに関する情報へのポインター。</span><span class="sxs-lookup"><span data-stu-id="24110-113">[out] A pointer to information about the process in which the application has been loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24110-114">要件</span><span class="sxs-lookup"><span data-stu-id="24110-114">Requirements</span></span>  

 <span data-ttu-id="24110-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24110-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24110-116">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="24110-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="24110-117">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="24110-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="24110-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24110-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24110-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="24110-119">See also</span></span>

- [<span data-ttu-id="24110-120">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="24110-120">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
