---
title: ICLRStrongName::GetHashFromFile メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromFile method [.NET Framework hosting]
- GetHashFromFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 9e50480a-8ada-4044-b2a5-97bb14ed3525
topic_type:
- apiref
ms.openlocfilehash: ff346d8f7ba321904a8d91079298b58039e6eb54
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727609"
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="ff0ea-102">ICLRStrongName::GetHashFromFile メソッド</span><span class="sxs-lookup"><span data-stu-id="ff0ea-102">ICLRStrongName::GetHashFromFile Method</span></span>

<span data-ttu-id="ff0ea-103">指定したファイルの内容に対してハッシュが生成されます。</span><span class="sxs-lookup"><span data-stu-id="ff0ea-103">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff0ea-104">構文</span><span class="sxs-lookup"><span data-stu-id="ff0ea-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff0ea-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff0ea-105">Parameters</span></span>  

 `szFilePath`  
 <span data-ttu-id="ff0ea-106">からハッシュするファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="ff0ea-106">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="ff0ea-107">[入力、出力]ハッシュを生成するときに使用するアルゴリズム。</span><span class="sxs-lookup"><span data-stu-id="ff0ea-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="ff0ea-108">有効なアルゴリズムは、Win32 CryptoAPI によって定義されているものです。</span><span class="sxs-lookup"><span data-stu-id="ff0ea-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="ff0ea-109">が0に設定されている場合は、 `piHashAlg` 既定のアルゴリズム CALG_SHA-1 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="ff0ea-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="ff0ea-110">入出力生成されたハッシュを格納しているバイト配列。</span><span class="sxs-lookup"><span data-stu-id="ff0ea-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="ff0ea-111">からが指すバッファーの最大サイズ `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="ff0ea-111">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="ff0ea-112">入出力返されたのサイズ (バイト単位) `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="ff0ea-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ff0ea-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff0ea-113">Return Value</span></span>  

 <span data-ttu-id="ff0ea-114">`S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="ff0ea-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff0ea-115">注釈</span><span class="sxs-lookup"><span data-stu-id="ff0ea-115">Remarks</span></span>  

 <span data-ttu-id="ff0ea-116">このメソッドは [ICLRStrongName:: GetHashFromFileW](iclrstrongname-gethashfromfilew-method.md) メソッドと同じですが、ファイル名の指定は Unicode ではなく ANSI です。</span><span class="sxs-lookup"><span data-stu-id="ff0ea-116">This method is the same as the [ICLRStrongName::GetHashFromFileW](iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff0ea-117">要件</span><span class="sxs-lookup"><span data-stu-id="ff0ea-117">Requirements</span></span>  

 <span data-ttu-id="ff0ea-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff0ea-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff0ea-119">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="ff0ea-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ff0ea-120">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="ff0ea-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff0ea-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff0ea-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff0ea-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff0ea-122">See also</span></span>

- [<span data-ttu-id="ff0ea-123">GetHashFromFileW メソッド</span><span class="sxs-lookup"><span data-stu-id="ff0ea-123">GetHashFromFileW Method</span></span>](iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="ff0ea-124">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ff0ea-124">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
