---
title: GetCORRequiredVersion 関数
ms.date: 03/30/2017
api_name:
- GetCORRequiredVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetCORRequiredVersion
helpviewer_keywords:
- GetCORRequiredVersion function [.NET Framework hosting]
ms.assetid: 1588fe7b-c378-4f4b-9c4b-48647f1119cc
topic_type:
- apiref
ms.openlocfilehash: 9590d19f4e5f5890af53a108492bd1b6d130fb72
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704501"
---
# <a name="getcorrequiredversion-function"></a><span data-ttu-id="105b4-102">GetCORRequiredVersion 関数</span><span class="sxs-lookup"><span data-stu-id="105b4-102">GetCORRequiredVersion Function</span></span>

<span data-ttu-id="105b4-103">必要な共通言語ランタイム (CLR) のバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="105b4-103">Gets the required common language runtime (CLR) version number.</span></span>  
  
 <span data-ttu-id="105b4-104">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="105b4-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="105b4-105">構文</span><span class="sxs-lookup"><span data-stu-id="105b4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCORRequiredVersion (  
    [out] LPWSTR   pbuffer,  
    [in]  DWORD    cchBuffer,  
    [out] DWORD   *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="105b4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="105b4-106">Parameters</span></span>  

 `pbuffer`  
 <span data-ttu-id="105b4-107">入出力バージョン番号を指定する文字列を格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="105b4-107">[out] A buffer containing a string that specifies the version number.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="105b4-108">からバッファーのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="105b4-108">[in] The size, in bytes, of the buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="105b4-109">入出力バッファーで返されたバイト数。</span><span class="sxs-lookup"><span data-stu-id="105b4-109">[out] The number of bytes returned in the buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="105b4-110">要件</span><span class="sxs-lookup"><span data-stu-id="105b4-110">Requirements</span></span>  

 <span data-ttu-id="105b4-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="105b4-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="105b4-112">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="105b4-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="105b4-113">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="105b4-113">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="105b4-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="105b4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="105b4-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="105b4-115">See also</span></span>

- [<span data-ttu-id="105b4-116">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="105b4-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
