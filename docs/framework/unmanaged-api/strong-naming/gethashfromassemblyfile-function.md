---
title: GetHashFromAssemblyFile 関数
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFile
helpviewer_keywords:
- GetHashFromAssemblyFile function [.NET Framework strong naming]
ms.assetid: 751ed69f-b7ab-4e07-80de-e17ca9319b0c
topic_type:
- apiref
ms.openlocfilehash: caefc9773b0d208f8b20847b664f7bc017d2c076
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730995"
---
# <a name="gethashfromassemblyfile-function"></a><span data-ttu-id="e0b15-102">GetHashFromAssemblyFile 関数</span><span class="sxs-lookup"><span data-stu-id="e0b15-102">GetHashFromAssemblyFile Function</span></span>

<span data-ttu-id="e0b15-103">指定したハッシュ アルゴリズムを使用して、指定したアセンブリ ファイルのハッシュ値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="e0b15-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="e0b15-104">この関数は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="e0b15-104">This function has been deprecated.</span></span> <span data-ttu-id="e0b15-105">代わりに [ICLRStrongName:: GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="e0b15-105">Use the [ICLRStrongName::GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0b15-106">構文</span><span class="sxs-lookup"><span data-stu-id="e0b15-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0b15-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e0b15-107">Parameters</span></span>  

 `szFilePath`  
 <span data-ttu-id="e0b15-108">からハッシュされるファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="e0b15-108">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="e0b15-109">[入力、出力]ハッシュアルゴリズムを指定する定数。</span><span class="sxs-lookup"><span data-stu-id="e0b15-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="e0b15-110">既定のハッシュアルゴリズムには0を使用します。</span><span class="sxs-lookup"><span data-stu-id="e0b15-110">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="e0b15-111">入出力返されたハッシュバッファー。</span><span class="sxs-lookup"><span data-stu-id="e0b15-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="e0b15-112">から要求された最大サイズ `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="e0b15-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="e0b15-113">入出力の返されたサイズ (バイト単位) `pbHash` 。</span><span class="sxs-lookup"><span data-stu-id="e0b15-113">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0b15-114">要件</span><span class="sxs-lookup"><span data-stu-id="e0b15-114">Requirements</span></span>  

 <span data-ttu-id="e0b15-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0b15-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0b15-116">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="e0b15-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="e0b15-117">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="e0b15-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e0b15-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0b15-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0b15-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="e0b15-119">See also</span></span>

- [<span data-ttu-id="e0b15-120">GetHashFromAssemblyFile メソッド</span><span class="sxs-lookup"><span data-stu-id="e0b15-120">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="e0b15-121">GetHashFromAssemblyFileW メソッド</span><span class="sxs-lookup"><span data-stu-id="e0b15-121">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="e0b15-122">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e0b15-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
