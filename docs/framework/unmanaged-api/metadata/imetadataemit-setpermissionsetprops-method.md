---
title: IMetaDataEmit::SetPermissionSetProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPermissionSetProps
helpviewer_keywords:
- SetPermissionSetProps method [.NET Framework metadata]
- IMetaDataEmit::SetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 8eaee971-40bf-45e2-a3d8-6e57674213b6
topic_type:
- apiref
ms.openlocfilehash: 4c3e0953d71020ba62ee4ab68aa9e21ea3f0f521
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675036"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="1f58e-102">IMetaDataEmit::SetPermissionSetProps メソッド</span><span class="sxs-lookup"><span data-stu-id="1f58e-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>

<span data-ttu-id="1f58e-103">[IMetaDataEmit::D efinepermissionset](imetadataemit-definepermissionset-method.md)の前の呼び出しで定義されたアクセス許可セットのメタデータ署名の機能を設定または更新します。</span><span class="sxs-lookup"><span data-stu-id="1f58e-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f58e-104">構文</span><span class="sxs-lookup"><span data-stu-id="1f58e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPermissionSetProps (
    [in]  mdToken         tk,
    [in]  DWORD           dwAction,
    [in]  void const      *pvPermission,
    [in]  ULONG           cbPermission,
    [out] mdPermission    *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f58e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1f58e-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="1f58e-106">から修飾されるオブジェクトを表すメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="1f58e-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="1f58e-107">から使用する宣言セキュリティの種類を指定する [CorDeclSecurity](cordeclsecurity-enumeration.md) 値です。</span><span class="sxs-lookup"><span data-stu-id="1f58e-107">[in] A [CorDeclSecurity](cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="1f58e-108">からアクセス許可 BLOB。</span><span class="sxs-lookup"><span data-stu-id="1f58e-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="1f58e-109">からのサイズ (バイト単位) `pvPermission` 。</span><span class="sxs-lookup"><span data-stu-id="1f58e-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="1f58e-110">入出力 `mdPermission` 更新されたアクセス許可を表すメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="1f58e-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f58e-111">要件</span><span class="sxs-lookup"><span data-stu-id="1f58e-111">Requirements</span></span>  

 <span data-ttu-id="1f58e-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f58e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f58e-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="1f58e-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1f58e-114">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="1f58e-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1f58e-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f58e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f58e-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f58e-116">See also</span></span>

- [<span data-ttu-id="1f58e-117">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1f58e-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="1f58e-118">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1f58e-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
