---
title: GetHashFromFileW 関数
ms.date: 03/30/2017
api_name:
- GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW function [.NET Framework strong naming]
ms.assetid: 97c2d7a6-5376-45a1-ba65-146a249147cc
topic_type:
- apiref
ms.openlocfilehash: 8038d0abc93e058e6bde897bbf2261d8f1df885a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732324"
---
# <a name="gethashfromfilew-function"></a><span data-ttu-id="b20cf-102">GetHashFromFileW 関数</span><span class="sxs-lookup"><span data-stu-id="b20cf-102">GetHashFromFileW Function</span></span>

<span data-ttu-id="b20cf-103">Unicode 文字列で指定されたファイルの内容に対してハッシュが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b20cf-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
 <span data-ttu-id="b20cf-104">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="b20cf-104">This function has been deprecated.</span></span> <span data-ttu-id="b20cf-105">代わりに [ICLRStrongName:: GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="b20cf-105">Use the [ICLRStrongName::GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b20cf-106">構文</span><span class="sxs-lookup"><span data-stu-id="b20cf-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="b20cf-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b20cf-107">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="b20cf-108">からハッシュするファイルの Unicode 名。</span><span class="sxs-lookup"><span data-stu-id="b20cf-108">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="b20cf-109">[入力、出力]ハッシュを生成するときに使用するアルゴリズム。</span><span class="sxs-lookup"><span data-stu-id="b20cf-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="b20cf-110">有効なアルゴリズムは、Win32 CryptoAPI によって定義されているものです。</span><span class="sxs-lookup"><span data-stu-id="b20cf-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="b20cf-111">が0に設定されている場合は、 `piHashAlg` 既定のアルゴリズム CALG_SHA-1 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b20cf-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="b20cf-112">入出力生成されたハッシュを格納しているバイト配列。</span><span class="sxs-lookup"><span data-stu-id="b20cf-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="b20cf-113">からが指すバッファーの最大サイズ `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="b20cf-113">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="b20cf-114">入出力のサイズ (バイト単位) `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="b20cf-114">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b20cf-115">注釈</span><span class="sxs-lookup"><span data-stu-id="b20cf-115">Remarks</span></span>  

 <span data-ttu-id="b20cf-116">この関数は [GetHashFromFile](gethashfromfile-function.md)と同じですが、ファイル名の指定は ANSI ではなく Unicode である点が異なります。</span><span class="sxs-lookup"><span data-stu-id="b20cf-116">This function is the same as [GetHashFromFile](gethashfromfile-function.md), except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b20cf-117">要件</span><span class="sxs-lookup"><span data-stu-id="b20cf-117">Requirements</span></span>  

 <span data-ttu-id="b20cf-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b20cf-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b20cf-119">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="b20cf-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="b20cf-120">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="b20cf-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b20cf-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b20cf-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b20cf-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="b20cf-122">See also</span></span>

- [<span data-ttu-id="b20cf-123">GetHashFromFileW メソッド</span><span class="sxs-lookup"><span data-stu-id="b20cf-123">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="b20cf-124">GetHashFromFile メソッド</span><span class="sxs-lookup"><span data-stu-id="b20cf-124">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="b20cf-125">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b20cf-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
