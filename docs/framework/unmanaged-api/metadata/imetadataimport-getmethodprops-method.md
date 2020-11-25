---
title: IMetaDataImport::GetMethodProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodProps
helpviewer_keywords:
- GetMethodProps method [.NET Framework metadata]
- IMetaDataImport::GetMethodProps method [.NET Framework metadata]
ms.assetid: e0667ef7-1d31-4c89-a2d3-d426f023f8d2
topic_type:
- apiref
ms.openlocfilehash: 0eb4e9d713581cf32cec18bb02a6bd13542e517a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733185"
---
# <a name="imetadataimportgetmethodprops-method"></a><span data-ttu-id="8295f-102">IMetaDataImport::GetMethodProps メソッド</span><span class="sxs-lookup"><span data-stu-id="8295f-102">IMetaDataImport::GetMethodProps Method</span></span>

<span data-ttu-id="8295f-103">指定した MethodDef トークンによって参照されるメソッドに関連付けられているメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="8295f-103">Gets the metadata associated with the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8295f-104">構文</span><span class="sxs-lookup"><span data-stu-id="8295f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodProps (  
    [in]  mdMethodDef         mb,  
    [out] mdTypeDef           *pClass,  
    [out] LPWSTR              szMethod,  
    [in]  ULONG               cchMethod,  
    [out] ULONG               *pchMethod,  
    [out] DWORD               *pdwAttr,  
    [out] PCCOR_SIGNATURE     *ppvSigBlob,  
    [out] ULONG               *pcbSigBlob,  
    [out] ULONG               *pulCodeRVA,  
    [out] DWORD               *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8295f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8295f-105">Parameters</span></span>  

 `mb`  
 <span data-ttu-id="8295f-106">からメタデータを返すメソッドを表す MethodDef トークン。</span><span class="sxs-lookup"><span data-stu-id="8295f-106">[in] The MethodDef token that represents the method to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="8295f-107">入出力メソッドを実装する型を表す TypeDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8295f-107">[out] A Pointer to a TypeDef token that represents the type that implements the method.</span></span>  
  
 `szMethod`  
 <span data-ttu-id="8295f-108">入出力メソッドの名前を持つバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8295f-108">[out] A Pointer to a buffer that has the method's name.</span></span>  
  
 `cchMethod`  
 <span data-ttu-id="8295f-109">から要求されたのサイズ `szMethod` 。</span><span class="sxs-lookup"><span data-stu-id="8295f-109">[in] The requested size of `szMethod`.</span></span>  
  
 `pchMethod`  
 <span data-ttu-id="8295f-110">入出力のワイド文字のサイズへのポインター `szMethod` 。切り捨ての場合は、メソッド名の実際のワイド文字数。</span><span class="sxs-lookup"><span data-stu-id="8295f-110">[out] A Pointer to the size in wide characters of `szMethod`, or in the case of truncation, the actual number of wide characters in the method name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="8295f-111">入出力メソッドに関連付けられているフラグへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8295f-111">[out] A pointer to any flags associated with the method.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="8295f-112">入出力メソッドのバイナリメタデータシグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8295f-112">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="8295f-113">入出力のサイズ (バイト単位) へのポインター `ppvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="8295f-113">[out] A Pointer to the size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="8295f-114">入出力メソッドの相対仮想アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8295f-114">[out] A pointer to the relative virtual address of the method.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="8295f-115">入出力メソッドの実装フラグへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8295f-115">[out] A pointer to any implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8295f-116">要件</span><span class="sxs-lookup"><span data-stu-id="8295f-116">Requirements</span></span>  

 <span data-ttu-id="8295f-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8295f-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8295f-118">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="8295f-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8295f-119">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="8295f-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8295f-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8295f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8295f-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="8295f-121">See also</span></span>

- [<span data-ttu-id="8295f-122">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8295f-122">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="8295f-123">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8295f-123">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
