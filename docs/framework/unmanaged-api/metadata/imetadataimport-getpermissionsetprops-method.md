---
title: IMetaDataImport::GetPermissionSetProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPermissionSetProps
helpviewer_keywords:
- GetPermissionSetProps method [.NET Framework metadata]
- IMetaDataImport::GetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 9855f0e4-12c0-4d3d-ab5d-d6bc52d25eae
topic_type:
- apiref
ms.openlocfilehash: 89c45c049ebadf9e1f16bef8d2626b4e2a17fb70
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729253"
---
# <a name="imetadataimportgetpermissionsetprops-method"></a><span data-ttu-id="762e7-102">IMetaDataImport::GetPermissionSetProps メソッド</span><span class="sxs-lookup"><span data-stu-id="762e7-102">IMetaDataImport::GetPermissionSetProps Method</span></span>

<span data-ttu-id="762e7-103">指定した <xref:System.Security.PermissionSet?displayProperty=nameWithType> アクセス許可トークンによって表されるに関連付けられているメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="762e7-103">Gets the metadata associated with the <xref:System.Security.PermissionSet?displayProperty=nameWithType> represented by the specified Permission token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="762e7-104">構文</span><span class="sxs-lookup"><span data-stu-id="762e7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,
   [out] void const        **ppvPermission,
   [out] ULONG             *pcbPermission  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="762e7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="762e7-105">Parameters</span></span>  

 `pm`  
 <span data-ttu-id="762e7-106">からメタデータプロパティを取得するアクセス許可セットを表すアクセス許可メタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="762e7-106">[in] The Permission metadata token that represents the permission set to get the metadata properties for.</span></span>  
  
 `pdwAction`  
 <span data-ttu-id="762e7-107">入出力アクセス許可セットへのポインター。</span><span class="sxs-lookup"><span data-stu-id="762e7-107">[out] A pointer to the permission set.</span></span>  
  
 `ppvPermission`  
 <span data-ttu-id="762e7-108">入出力アクセス許可セットのバイナリメタデータシグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="762e7-108">[out] A pointer to the binary metadata signature of the permission set.</span></span>  
  
 `pcbPermission`  
 <span data-ttu-id="762e7-109">入出力のサイズ (バイト単位) `ppvPermission` 。</span><span class="sxs-lookup"><span data-stu-id="762e7-109">[out] The size in bytes of `ppvPermission`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="762e7-110">要件</span><span class="sxs-lookup"><span data-stu-id="762e7-110">Requirements</span></span>  

 <span data-ttu-id="762e7-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="762e7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="762e7-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="762e7-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="762e7-113">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="762e7-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="762e7-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="762e7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="762e7-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="762e7-115">See also</span></span>

- <xref:System.Security.PermissionSet>
- [<span data-ttu-id="762e7-116">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="762e7-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="762e7-117">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="762e7-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
