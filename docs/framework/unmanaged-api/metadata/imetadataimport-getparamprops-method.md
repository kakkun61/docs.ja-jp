---
title: IMetaDataImport::GetParamProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type:
- apiref
ms.openlocfilehash: a16621f4c9b06f049239dc4e2335d70a167dd756
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729266"
---
# <a name="imetadataimportgetparamprops-method"></a><span data-ttu-id="67940-102">IMetaDataImport::GetParamProps メソッド</span><span class="sxs-lookup"><span data-stu-id="67940-102">IMetaDataImport::GetParamProps Method</span></span>

<span data-ttu-id="67940-103">指定した ParamDef トークンによって参照されるパラメーターのメタデータ値を取得します。</span><span class="sxs-lookup"><span data-stu-id="67940-103">Gets metadata values for the parameter referenced by the specified ParamDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67940-104">構文</span><span class="sxs-lookup"><span data-stu-id="67940-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67940-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="67940-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="67940-106">からメタデータを返すパラメーターを表す ParamDef トークン。</span><span class="sxs-lookup"><span data-stu-id="67940-106">[in] A ParamDef token that represents the parameter to return metadata for.</span></span>  
  
 `pmd`  
 <span data-ttu-id="67940-107">入出力パラメーターを受け取るメソッドを表す MethodDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="67940-107">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span></span>  
  
 `pulSequence`  
 <span data-ttu-id="67940-108">入出力メソッド引数リスト内のパラメーターの序数位置。</span><span class="sxs-lookup"><span data-stu-id="67940-108">[out] The ordinal position of the parameter in the method argument list.</span></span>  
  
 `szName`  
 <span data-ttu-id="67940-109">入出力パラメーターの名前を保持するバッファー。</span><span class="sxs-lookup"><span data-stu-id="67940-109">[out] A buffer to hold the name of the parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="67940-110">からのワイド文字で要求されたサイズ `szName` 。</span><span class="sxs-lookup"><span data-stu-id="67940-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="67940-111">入出力のワイド文字で返されたサイズ `szName` 。</span><span class="sxs-lookup"><span data-stu-id="67940-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="67940-112">入出力パラメーターに関連付けられているすべての属性フラグへのポインター。</span><span class="sxs-lookup"><span data-stu-id="67940-112">[out] A pointer to any attribute flags associated with the parameter.</span></span> <span data-ttu-id="67940-113">これは、値のビットマスクです `CorParamAttr` 。</span><span class="sxs-lookup"><span data-stu-id="67940-113">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="67940-114">入出力パラメーターがであることを示すフラグへのポインター <xref:System.ValueType> 。</span><span class="sxs-lookup"><span data-stu-id="67940-114">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="67940-115">入出力パラメーターによって返される定数文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="67940-115">[out] A pointer to a constant string returned by the parameter.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="67940-116">入出力のサイズ `ppValue` 。ワイド文字の場合は `ppValue` 。が文字列を保持しない場合は0。</span><span class="sxs-lookup"><span data-stu-id="67940-116">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67940-117">注釈</span><span class="sxs-lookup"><span data-stu-id="67940-117">Remarks</span></span>

<span data-ttu-id="67940-118">パラメーターの場合、のシーケンス値は `pulSequence` 1 から始まります。</span><span class="sxs-lookup"><span data-stu-id="67940-118">The sequence values in `pulSequence` begin with 1 for parameters.</span></span> <span data-ttu-id="67940-119">戻り値のシーケンス番号は0です。</span><span class="sxs-lookup"><span data-stu-id="67940-119">A return value has a sequence number of 0.</span></span>

## <a name="requirements"></a><span data-ttu-id="67940-120">要件</span><span class="sxs-lookup"><span data-stu-id="67940-120">Requirements</span></span>  

 <span data-ttu-id="67940-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67940-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67940-122">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="67940-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="67940-123">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="67940-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="67940-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67940-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67940-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="67940-125">See also</span></span>

- [<span data-ttu-id="67940-126">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="67940-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="67940-127">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="67940-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
