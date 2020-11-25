---
title: GetRequestedRuntimeVersion 関数
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersion
helpviewer_keywords:
- GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type:
- apiref
ms.openlocfilehash: 6c16b02a5ae323ba80d44937f322810022dfa9f5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711638"
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="da278-102">GetRequestedRuntimeVersion 関数</span><span class="sxs-lookup"><span data-stu-id="da278-102">GetRequestedRuntimeVersion Function</span></span>

<span data-ttu-id="da278-103">指定したアプリケーションによって要求された共通言語ランタイム (CLR) のバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="da278-103">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="da278-104">そのバージョンがインストールされていない場合は、要求されるバージョンより前にインストールされた最も新しいバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="da278-104">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="da278-105">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="da278-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da278-106">構文</span><span class="sxs-lookup"><span data-stu-id="da278-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da278-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="da278-107">Parameters</span></span>  

 `pExe`  
 <span data-ttu-id="da278-108">からアプリケーションの名前。</span><span class="sxs-lookup"><span data-stu-id="da278-108">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="da278-109">入出力正常に完了したときのバージョン番号の文字列を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="da278-109">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="da278-110">からバージョンバッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="da278-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="da278-111">入出力バージョン番号文字列の長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="da278-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da278-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="da278-112">Return Value</span></span>  

 <span data-ttu-id="da278-113">このメソッドは、次の値に加えて、Winerror.h で定義されている標準のコンポーネントオブジェクトモデル (COM) エラーコードを返します。</span><span class="sxs-lookup"><span data-stu-id="da278-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="da278-114">リターン コード</span><span class="sxs-lookup"><span data-stu-id="da278-114">Return code</span></span>|<span data-ttu-id="da278-115">説明</span><span class="sxs-lookup"><span data-stu-id="da278-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="da278-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="da278-116">S_OK</span></span>|<span data-ttu-id="da278-117">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="da278-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="da278-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="da278-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="da278-119">バージョンバッファーが、バージョン文字列を格納するのに十分な大きさではありません。</span><span class="sxs-lookup"><span data-stu-id="da278-119">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="da278-120">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="da278-120">E_POINTER</span></span>|<span data-ttu-id="da278-121">`pdwLength` が null です。</span><span class="sxs-lookup"><span data-stu-id="da278-121">`pdwLength` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="da278-122">要件</span><span class="sxs-lookup"><span data-stu-id="da278-122">Requirements</span></span>  

 <span data-ttu-id="da278-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="da278-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da278-124">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="da278-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="da278-125">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="da278-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="da278-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da278-126">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da278-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="da278-127">See also</span></span>

- [<span data-ttu-id="da278-128">GetRequestedRuntimeInfo 関数</span><span class="sxs-lookup"><span data-stu-id="da278-128">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="da278-129">GetVersionFromProcess 関数</span><span class="sxs-lookup"><span data-stu-id="da278-129">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)
- [<span data-ttu-id="da278-130">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="da278-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
