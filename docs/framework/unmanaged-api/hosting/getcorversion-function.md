---
title: GetCORVersion 関数
ms.date: 03/30/2017
api_name:
- GetCORVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORVersion
helpviewer_keywords:
- GetCORVersion function [.NET Framework hosting]
ms.assetid: 2f09cd37-bf3a-4cc5-87b0-adc42a7eed31
topic_type:
- apiref
ms.openlocfilehash: e7ef3f300c8cfa0c275d15913e171abe09385eea
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681211"
---
# <a name="getcorversion-function"></a><span data-ttu-id="7575e-102">GetCORVersion 関数</span><span class="sxs-lookup"><span data-stu-id="7575e-102">GetCORVersion Function</span></span>

<span data-ttu-id="7575e-103">現在のプロセスで実行されている共通言語ランタイム (CLR) のバージョン番号を返します。</span><span class="sxs-lookup"><span data-stu-id="7575e-103">Returns the version number of the common language runtime (CLR) that is running in the current process.</span></span>  
  
 <span data-ttu-id="7575e-104">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="7575e-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7575e-105">構文</span><span class="sxs-lookup"><span data-stu-id="7575e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="7575e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7575e-106">Parameters</span></span>  

 `pbuffer`  
 <span data-ttu-id="7575e-107">現在プロセスに読み込まれているランタイムのバージョンを指定する文字列を CLR が返すバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7575e-107">A pointer to a buffer in which the CLR returns a string specifying the version of the runtime that is currently loaded into the process.</span></span> <span data-ttu-id="7575e-108">返される文字列は、 [Corbindtoruntimeex](corbindtoruntimeex-function.md)に渡される文字列と同じ形式になります (例、"v 1.0.1216")。</span><span class="sxs-lookup"><span data-stu-id="7575e-108">The returned string takes the same form as strings passed to [CorBindToRuntimeEx](corbindtoruntimeex-function.md), for example, "v1.0.1216".</span></span> <span data-ttu-id="7575e-109">ランタイムがまだプロセスに読み込まれていない場合、関数はコンピューターにインストールされている最新バージョンのランタイムの適切なディレクトリ情報を返します。</span><span class="sxs-lookup"><span data-stu-id="7575e-109">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="7575e-110">`WCHAR`で保持できる文字の数 `pbuffer` です。</span><span class="sxs-lookup"><span data-stu-id="7575e-110">The number of characters (`WCHAR`s) that can be held in `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="7575e-111">で実際に返された文字数へのポインター `pbuffer` 。</span><span class="sxs-lookup"><span data-stu-id="7575e-111">A pointer to the number of characters actually returned in `pbuffer`.</span></span> <span data-ttu-id="7575e-112">`pbuffer`が null ポインターの場合、ランタイムは E_POINTER を返します。</span><span class="sxs-lookup"><span data-stu-id="7575e-112">If `pbuffer` is a null pointer, the runtime returns E_POINTER.</span></span> <span data-ttu-id="7575e-113">文字数がの長さを超える場合 `pbuffer` 、ランタイムは ERROR_INSUFFICIENT_BUFFER を返します。</span><span class="sxs-lookup"><span data-stu-id="7575e-113">If the number of characters is greater then the length of `pbuffer` , the runtime returns ERROR_INSUFFICIENT_BUFFER.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7575e-114">要件</span><span class="sxs-lookup"><span data-stu-id="7575e-114">Requirements</span></span>  

 <span data-ttu-id="7575e-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7575e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7575e-116">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="7575e-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7575e-117">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7575e-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7575e-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7575e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7575e-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="7575e-119">See also</span></span>

- [<span data-ttu-id="7575e-120">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="7575e-120">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
