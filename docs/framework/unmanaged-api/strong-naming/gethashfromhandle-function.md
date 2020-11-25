---
title: GetHashFromHandle 関数
ms.date: 03/30/2017
api_name:
- GetHashFromHandle
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle function [.NET Framework strong naming]
ms.assetid: 9e00337f-b307-4602-9bc3-965a8dbf02cd
topic_type:
- apiref
ms.openlocfilehash: 904dcb707e704cfec2dba4e6587f7e3acaf7b538
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732334"
---
# <a name="gethashfromhandle-function"></a><span data-ttu-id="c60bc-102">GetHashFromHandle 関数</span><span class="sxs-lookup"><span data-stu-id="c60bc-102">GetHashFromHandle Function</span></span>

<span data-ttu-id="c60bc-103">指定したハッシュ アルゴリズムを使用して、指定したファイル ハンドルを含むファイルの内容に対してハッシュが作成されます。</span><span class="sxs-lookup"><span data-stu-id="c60bc-103">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="c60bc-104">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="c60bc-104">This function has been deprecated.</span></span> <span data-ttu-id="c60bc-105">代わりに [ICLRStrongName:: GetHashFromHandle](../hosting/iclrstrongname-gethashfromhandle-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="c60bc-105">Use the [ICLRStrongName::GetHashFromHandle](../hosting/iclrstrongname-gethashfromhandle-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c60bc-106">構文</span><span class="sxs-lookup"><span data-stu-id="c60bc-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c60bc-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c60bc-107">Parameters</span></span>  

 `hFile`  
 <span data-ttu-id="c60bc-108">からハッシュされるファイルのハンドル。</span><span class="sxs-lookup"><span data-stu-id="c60bc-108">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="c60bc-109">[入力、出力]ハッシュアルゴリズムを指定する定数。</span><span class="sxs-lookup"><span data-stu-id="c60bc-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="c60bc-110">既定のアルゴリズムには0を使用します。</span><span class="sxs-lookup"><span data-stu-id="c60bc-110">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="c60bc-111">入出力返されたハッシュバッファー。</span><span class="sxs-lookup"><span data-stu-id="c60bc-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="c60bc-112">から要求された最大サイズ `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="c60bc-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="c60bc-113">入出力返されたのサイズ (バイト単位) `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="c60bc-113">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c60bc-114">要件</span><span class="sxs-lookup"><span data-stu-id="c60bc-114">Requirements</span></span>  

 <span data-ttu-id="c60bc-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c60bc-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c60bc-116">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="c60bc-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="c60bc-117">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="c60bc-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c60bc-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c60bc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c60bc-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="c60bc-119">See also</span></span>

- [<span data-ttu-id="c60bc-120">GetHashFromHandle メソッド</span><span class="sxs-lookup"><span data-stu-id="c60bc-120">GetHashFromHandle Method</span></span>](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="c60bc-121">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c60bc-121">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
