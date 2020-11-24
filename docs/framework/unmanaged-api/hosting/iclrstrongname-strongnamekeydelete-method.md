---
title: ICLRStrongName::StrongNameKeyDelete メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyDelete method [.NET Framework hosting]
ms.assetid: 0163412f-f617-4428-89e0-03992fec31e8
topic_type:
- apiref
ms.openlocfilehash: 46345ae570673c9c9c0c58fb6edea1464ba8dd91
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671695"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="9d453-102">ICLRStrongName::StrongNameKeyDelete メソッド</span><span class="sxs-lookup"><span data-stu-id="9d453-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>

<span data-ttu-id="9d453-103">指定したキー コンテナーが削除されます。</span><span class="sxs-lookup"><span data-stu-id="9d453-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d453-104">構文</span><span class="sxs-lookup"><span data-stu-id="9d453-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d453-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9d453-105">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="9d453-106">から削除するキーコンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="9d453-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d453-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="9d453-107">Return Value</span></span>  

 <span data-ttu-id="9d453-108">`S_OK` メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="9d453-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d453-109">注釈</span><span class="sxs-lookup"><span data-stu-id="9d453-109">Remarks</span></span>  

 <span data-ttu-id="9d453-110">[ICLRStrongName:: StrongNameKeyInstall](iclrstrongname-strongnamekeyinstall-method.md)メソッドを使用して、公開キーと秘密キーのペアをコンテナーにインポートします。</span><span class="sxs-lookup"><span data-stu-id="9d453-110">Use the [ICLRStrongName::StrongNameKeyInstall](iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d453-111">要件</span><span class="sxs-lookup"><span data-stu-id="9d453-111">Requirements</span></span>  

 <span data-ttu-id="9d453-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d453-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d453-113">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="9d453-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9d453-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="9d453-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d453-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d453-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d453-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d453-116">See also</span></span>

- [<span data-ttu-id="9d453-117">StrongNameKeyInstall メソッド</span><span class="sxs-lookup"><span data-stu-id="9d453-117">StrongNameKeyInstall Method</span></span>](iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="9d453-118">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9d453-118">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
