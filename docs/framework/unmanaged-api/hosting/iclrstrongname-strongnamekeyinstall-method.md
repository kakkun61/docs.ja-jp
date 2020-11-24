---
title: ICLRStrongName::StrongNameKeyInstall メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyInstall
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyInstall method [.NET Framework hosting]
- StrongNameKeyInstall method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5c15cf3b-164c-49d1-8e57-e42949d55acf
topic_type:
- apiref
ms.openlocfilehash: 7e0c689dad0c288e3af3a3d64ee1bba1c44053c1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674529"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="9f5df-102">ICLRStrongName::StrongNameKeyInstall メソッド</span><span class="sxs-lookup"><span data-stu-id="9f5df-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>

<span data-ttu-id="9f5df-103">公開/秘密キーの組がコンテナーにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="9f5df-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f5df-104">構文</span><span class="sxs-lookup"><span data-stu-id="9f5df-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f5df-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9f5df-105">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="9f5df-106">からキーコンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="9f5df-106">[in] The name of the key container.</span></span> <span data-ttu-id="9f5df-107">`wszKeyContainer` は空でない文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f5df-107">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="9f5df-108">からバイナリキーペア。</span><span class="sxs-lookup"><span data-stu-id="9f5df-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="9f5df-109">からのサイズ (バイト単位) `pbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="9f5df-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9f5df-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="9f5df-110">Return Value</span></span>  

 <span data-ttu-id="9f5df-111">`S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="9f5df-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f5df-112">注釈</span><span class="sxs-lookup"><span data-stu-id="9f5df-112">Remarks</span></span>  

 <span data-ttu-id="9f5df-113">[ICLRStrongName:: StrongNameKeyDelete](iclrstrongname-strongnamekeydelete-method.md)メソッドを使用して、キーコンテナーを削除します。</span><span class="sxs-lookup"><span data-stu-id="9f5df-113">Use the [ICLRStrongName::StrongNameKeyDelete](iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f5df-114">要件</span><span class="sxs-lookup"><span data-stu-id="9f5df-114">Requirements</span></span>  

 <span data-ttu-id="9f5df-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f5df-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f5df-116">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="9f5df-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9f5df-117">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="9f5df-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9f5df-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f5df-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f5df-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="9f5df-119">See also</span></span>

- [<span data-ttu-id="9f5df-120">StrongNameKeyDelete メソッド</span><span class="sxs-lookup"><span data-stu-id="9f5df-120">StrongNameKeyDelete Method</span></span>](iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="9f5df-121">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9f5df-121">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
