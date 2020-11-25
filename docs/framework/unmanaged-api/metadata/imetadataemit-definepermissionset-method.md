---
title: IMetaDataEmit::DefinePermissionSet メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePermissionSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePermissionSet
helpviewer_keywords:
- DefinePermissionSet method [.NET Framework metadata]
- IMetaDataEmit::DefinePermissionSet method [.NET Framework metadata]
ms.assetid: 36cffbf7-82ca-4cf9-bf60-50ab491ac2d9
topic_type:
- apiref
ms.openlocfilehash: 3698525c139ed52b59ca577c598e675b6c26eef4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719516"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="462b6-102">IMetaDataEmit::DefinePermissionSet メソッド</span><span class="sxs-lookup"><span data-stu-id="462b6-102">IMetaDataEmit::DefinePermissionSet Method</span></span>

<span data-ttu-id="462b6-103">指定したメタデータシグネチャを持つアクセス許可セットの定義を作成し、そのアクセス許可セットの定義に対するトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="462b6-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="462b6-104">構文</span><span class="sxs-lookup"><span data-stu-id="462b6-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,
    [in]  DWORD          dwAction,
    [in]  void const     *pvPermission,
    [in]  ULONG          cbPermission,
    [out] mdPermission   *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="462b6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="462b6-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="462b6-106">から修飾されるオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="462b6-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="462b6-107">から使用する宣言セキュリティの種類を指定する [CorDeclSecurity](cordeclsecurity-enumeration.md) 値です。</span><span class="sxs-lookup"><span data-stu-id="462b6-107">[in] A [CorDeclSecurity](cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="462b6-108">からアクセス許可 BLOB。</span><span class="sxs-lookup"><span data-stu-id="462b6-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="462b6-109">からのサイズ (バイト単位) `pvPermission` 。</span><span class="sxs-lookup"><span data-stu-id="462b6-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="462b6-110">入出力返されたアクセス許可トークン。</span><span class="sxs-lookup"><span data-stu-id="462b6-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="462b6-111">要件</span><span class="sxs-lookup"><span data-stu-id="462b6-111">Requirements</span></span>  

 <span data-ttu-id="462b6-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="462b6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="462b6-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="462b6-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="462b6-114">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="462b6-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="462b6-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="462b6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="462b6-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="462b6-116">See also</span></span>

- [<span data-ttu-id="462b6-117">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="462b6-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="462b6-118">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="462b6-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
