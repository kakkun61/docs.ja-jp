---
title: ICLRStrongName::GetHashFromHandle メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromHandle
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromHandle method [.NET Framework hosting]
ms.assetid: 3bedbb7d-3cdd-4175-b370-10ae734062db
topic_type:
- apiref
ms.openlocfilehash: 68bfdb2f66147b54c75b8f577a01278016e248b7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685735"
---
# <a name="iclrstrongnamegethashfromhandle-method"></a><span data-ttu-id="f0ff3-102">ICLRStrongName::GetHashFromHandle メソッド</span><span class="sxs-lookup"><span data-stu-id="f0ff3-102">ICLRStrongName::GetHashFromHandle Method</span></span>

<span data-ttu-id="f0ff3-103">指定したハッシュアルゴリズムを使用して、指定したファイルハンドルを持つファイルの内容に対してハッシュを生成します。</span><span class="sxs-lookup"><span data-stu-id="f0ff3-103">Generates a hash over the contents of the file that has the specified file handle, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0ff3-104">構文</span><span class="sxs-lookup"><span data-stu-id="f0ff3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0ff3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f0ff3-105">Parameters</span></span>  

 `hFile`  
 <span data-ttu-id="f0ff3-106">からハッシュされるファイルのハンドル。</span><span class="sxs-lookup"><span data-stu-id="f0ff3-106">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="f0ff3-107">[入力、出力]ハッシュアルゴリズムを指定する定数。</span><span class="sxs-lookup"><span data-stu-id="f0ff3-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="f0ff3-108">既定のアルゴリズムには0を使用します。</span><span class="sxs-lookup"><span data-stu-id="f0ff3-108">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="f0ff3-109">入出力返されたハッシュバッファー。</span><span class="sxs-lookup"><span data-stu-id="f0ff3-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="f0ff3-110">から要求された最大サイズ `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="f0ff3-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="f0ff3-111">入出力返されたのサイズ (バイト単位) `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="f0ff3-111">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0ff3-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="f0ff3-112">Return Value</span></span>  

 <span data-ttu-id="f0ff3-113">`S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="f0ff3-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0ff3-114">要件</span><span class="sxs-lookup"><span data-stu-id="f0ff3-114">Requirements</span></span>  

 <span data-ttu-id="f0ff3-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0ff3-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0ff3-116">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="f0ff3-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f0ff3-117">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="f0ff3-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0ff3-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0ff3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0ff3-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="f0ff3-119">See also</span></span>

- [<span data-ttu-id="f0ff3-120">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f0ff3-120">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
