---
title: GetFileVersion 関数
ms.date: 03/30/2017
api_name:
- GetFileVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetFileVersion
helpviewer_keywords:
- GetFileVersion function [.NET Framework hosting]
ms.assetid: b3222c85-da88-4485-97d7-3a6ee3e8d358
topic_type:
- apiref
ms.openlocfilehash: 57b30824c7849127f48d4da61872945366e7141e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733244"
---
# <a name="getfileversion-function"></a><span data-ttu-id="27fc6-102">GetFileVersion 関数</span><span class="sxs-lookup"><span data-stu-id="27fc6-102">GetFileVersion Function</span></span>

<span data-ttu-id="27fc6-103">指定したバッファーを使用して、指定したファイルの共通言語ランタイム (CLR) のバージョン情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="27fc6-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="27fc6-104">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="27fc6-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27fc6-105">構文</span><span class="sxs-lookup"><span data-stu-id="27fc6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,
    [in, out] LPWSTR   szBuffer,
    [in]  DWORD        cchBuffer,
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27fc6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="27fc6-106">Parameters</span></span>  

 `szFilename`  
 <span data-ttu-id="27fc6-107">から検査するファイルのパス。</span><span class="sxs-lookup"><span data-stu-id="27fc6-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="27fc6-108">[入力、出力]返されたバージョン情報に割り当てられたバッファー。</span><span class="sxs-lookup"><span data-stu-id="27fc6-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="27fc6-109">からのサイズ (ワイド文字単位) `szBuffer` 。</span><span class="sxs-lookup"><span data-stu-id="27fc6-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="27fc6-110">入出力返されたのサイズ (バイト単位) `szBuffer` 。</span><span class="sxs-lookup"><span data-stu-id="27fc6-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27fc6-111">要件</span><span class="sxs-lookup"><span data-stu-id="27fc6-111">Requirements</span></span>  

 <span data-ttu-id="27fc6-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27fc6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27fc6-113">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="27fc6-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="27fc6-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27fc6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27fc6-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="27fc6-115">See also</span></span>

- [<span data-ttu-id="27fc6-116">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="27fc6-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
