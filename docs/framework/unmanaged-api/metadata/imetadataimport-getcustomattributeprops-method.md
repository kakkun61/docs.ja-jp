---
title: IMetaDataImport::GetCustomAttributeProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeProps
helpviewer_keywords:
- GetCustomAttributeProps method [.NET Framework metadata]
- IMetaDataImport::GetCustomAttributeProps method [.NET Framework metadata]
ms.assetid: 6eefb243-a281-41c1-bcdc-7e17513bc446
topic_type:
- apiref
ms.openlocfilehash: b92e9ab714e2d8d2c66ed5546deba16352e8e390
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711144"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a><span data-ttu-id="be394-102">IMetaDataImport::GetCustomAttributeProps メソッド</span><span class="sxs-lookup"><span data-stu-id="be394-102">IMetaDataImport::GetCustomAttributeProps Method</span></span>

<span data-ttu-id="be394-103">指定したメタデータ トークンのカスタム属性の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="be394-103">Gets the value of the custom attribute, given its metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be394-104">構文</span><span class="sxs-lookup"><span data-stu-id="be394-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be394-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="be394-105">Parameters</span></span>  

 `cv`  
 <span data-ttu-id="be394-106">[in] 取得するカスタム属性を表すメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="be394-106">[in] A metadata token that represents the custom attribute to be retrieved.</span></span>  
  
 `ptkObj`  
 <span data-ttu-id="be394-107">[out](省略可能) カスタム属性が変更されるオブジェクトを表すメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="be394-107">[out, optional] A metadata token representing the object that the custom attribute modifies.</span></span> <span data-ttu-id="be394-108">この値には、`mdCustomAttribute` を除く任意の種類のトークンを指定できます。</span><span class="sxs-lookup"><span data-stu-id="be394-108">This value can be any type of metadata token except `mdCustomAttribute`.</span></span>  
  
 `ptkType`  
 <span data-ttu-id="be394-109">[out](省略可能) 返されるカスタム属性の <xref:System.Type> を表す `mdMethodDef` または `mdMemberRef` メタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="be394-109">[out, optional] An `mdMethodDef` or `mdMemberRef` metadata token representing the <xref:System.Type> of the returned custom attribute.</span></span>  
  
 `ppBlob`  
 <span data-ttu-id="be394-110">[out](省略可能) カスタム属性の値であるデータの配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="be394-110">[out, optional] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="be394-111">[out](省略可能) \*`ppBlob` に返されたデータのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="be394-111">[out, optional] The size in bytes of the data returned in \*`ppBlob`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be394-112">注釈</span><span class="sxs-lookup"><span data-stu-id="be394-112">Remarks</span></span>  

 <span data-ttu-id="be394-113">カスタム属性はデータの配列として格納され、その形式はメタデータ エンジンによって解釈されます。</span><span class="sxs-lookup"><span data-stu-id="be394-113">A custom attribute is stored as an array of data, the format which is understood by the metadata engine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be394-114">要件</span><span class="sxs-lookup"><span data-stu-id="be394-114">Requirements</span></span>  

 <span data-ttu-id="be394-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be394-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be394-116">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="be394-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="be394-117">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="be394-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="be394-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be394-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be394-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="be394-119">See also</span></span>

- [<span data-ttu-id="be394-120">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="be394-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="be394-121">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="be394-121">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
