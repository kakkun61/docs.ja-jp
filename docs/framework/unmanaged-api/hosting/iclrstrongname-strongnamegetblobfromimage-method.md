---
title: ICLRStrongName::StrongNameGetBlobFromImage メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetBlobFromImage method [.NET Framework hosting]
ms.assetid: 0f5a2ec8-e776-4fd8-bda6-937b6834575a
topic_type:
- apiref
ms.openlocfilehash: ad5fa510a17a3ce823ff90c4131b349b0d9efd39
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671747"
---
# <a name="iclrstrongnamestrongnamegetblobfromimage-method"></a><span data-ttu-id="3ec2f-102">ICLRStrongName::StrongNameGetBlobFromImage メソッド</span><span class="sxs-lookup"><span data-stu-id="3ec2f-102">ICLRStrongName::StrongNameGetBlobFromImage Method</span></span>

<span data-ttu-id="3ec2f-103">指定したメモリ アドレスにあるアセンブリ イメージのバイナリ表現が取得されます。</span><span class="sxs-lookup"><span data-stu-id="3ec2f-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ec2f-104">構文</span><span class="sxs-lookup"><span data-stu-id="3ec2f-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ec2f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3ec2f-105">Parameters</span></span>  

 `pbBase`  
 <span data-ttu-id="3ec2f-106">からマップされたアセンブリマニフェストのメモリアドレス。</span><span class="sxs-lookup"><span data-stu-id="3ec2f-106">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="3ec2f-107">からにあるイメージのサイズ (バイト単位) `pbBase` 。</span><span class="sxs-lookup"><span data-stu-id="3ec2f-107">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="3ec2f-108">からイメージのバイナリ表現を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="3ec2f-108">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="3ec2f-109">[入力、出力]要求された最大サイズ (バイト単位) `pbBlob` 。</span><span class="sxs-lookup"><span data-stu-id="3ec2f-109">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="3ec2f-110">戻り時に、の実際のサイズ (バイト単位) `pbBlob` 。</span><span class="sxs-lookup"><span data-stu-id="3ec2f-110">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ec2f-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="3ec2f-111">Return Value</span></span>  

 <span data-ttu-id="3ec2f-112">`S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="3ec2f-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ec2f-113">要件</span><span class="sxs-lookup"><span data-stu-id="3ec2f-113">Requirements</span></span>  

 <span data-ttu-id="3ec2f-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ec2f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ec2f-115">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="3ec2f-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3ec2f-116">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="3ec2f-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3ec2f-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ec2f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ec2f-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="3ec2f-118">See also</span></span>

- [<span data-ttu-id="3ec2f-119">StrongNameGetBlob メソッド</span><span class="sxs-lookup"><span data-stu-id="3ec2f-119">StrongNameGetBlob Method</span></span>](iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="3ec2f-120">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3ec2f-120">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
