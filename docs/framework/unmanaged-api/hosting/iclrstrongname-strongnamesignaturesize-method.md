---
title: ICLRStrongName::StrongNameSignatureSize メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureSize
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureSize method [.NET Framework hosting]
- StrongNameSignatureSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 76d4f93a-5e25-4399-abcc-a1389549481d
topic_type:
- apiref
ms.openlocfilehash: f43a4e65442ca79ece71ce7e5e014309a611d7cc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671617"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="0f5a5-102">ICLRStrongName::StrongNameSignatureSize メソッド</span><span class="sxs-lookup"><span data-stu-id="0f5a5-102">ICLRStrongName::StrongNameSignatureSize Method</span></span>

<span data-ttu-id="0f5a5-103">厳密な名前の署名のサイズが返されます。</span><span class="sxs-lookup"><span data-stu-id="0f5a5-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="0f5a5-104">このメソッドは、通常、遅延署名されたアセンブリを作成するときに、ファイル内で予約する領域の量を決定するためにコンパイラによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="0f5a5-104">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f5a5-105">構文</span><span class="sxs-lookup"><span data-stu-id="0f5a5-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="0f5a5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0f5a5-106">Parameters</span></span>  

 `pbPublicKeyBlob`  
 <span data-ttu-id="0f5a5-107">から厳密な名前の署名を生成するために使用されるキーペアの公開部分を格納する [Publickeyblob](../strong-naming/publickeyblob-structure.md) 型の構造体。</span><span class="sxs-lookup"><span data-stu-id="0f5a5-107">[in] A structure of type [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="0f5a5-108">からのサイズ (バイト単位) `pbPublicKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="0f5a5-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="0f5a5-109">から厳密な名前の署名を格納するために必要なバイト数。</span><span class="sxs-lookup"><span data-stu-id="0f5a5-109">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f5a5-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="0f5a5-110">Return Value</span></span>  

 <span data-ttu-id="0f5a5-111">`S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="0f5a5-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f5a5-112">要件</span><span class="sxs-lookup"><span data-stu-id="0f5a5-112">Requirements</span></span>  

 <span data-ttu-id="0f5a5-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f5a5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f5a5-114">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="0f5a5-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0f5a5-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="0f5a5-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f5a5-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f5a5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f5a5-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="0f5a5-117">See also</span></span>

- [<span data-ttu-id="0f5a5-118">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0f5a5-118">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
