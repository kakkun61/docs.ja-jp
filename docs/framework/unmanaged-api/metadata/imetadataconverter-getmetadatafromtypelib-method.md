---
title: IMetaDataConverter::GetMetaDataFromTypeLib メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetMetaDataFromTypeLib
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib
helpviewer_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib method [.NET Framework metadata]
- GetMetaDataFromTypeLib method [.NET Framework metadata]
ms.assetid: 97dc3a56-adfa-431f-889e-06a35ac84d51
topic_type:
- apiref
ms.openlocfilehash: ed0902824bdbb4d057bf5a7920db4b1d18eb7347
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714667"
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a><span data-ttu-id="25bfc-102">IMetaDataConverter::GetMetaDataFromTypeLib メソッド</span><span class="sxs-lookup"><span data-stu-id="25bfc-102">IMetaDataConverter::GetMetaDataFromTypeLib Method</span></span>

<span data-ttu-id="25bfc-103">指定したインスタンスによって表されるタイプライブラリのメタデータシグネチャを表す [IMetaDataImport](imetadataimport-interface.md) インスタンスへのインターフェイスポインターを取得し `ITypeLib` ます。</span><span class="sxs-lookup"><span data-stu-id="25bfc-103">Gets an interface pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature of the type library represented by the specified `ITypeLib` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25bfc-104">構文</span><span class="sxs-lookup"><span data-stu-id="25bfc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,
    [out] IMetaDataImport **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25bfc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="25bfc-105">Parameters</span></span>  

 `pITL`  
 <span data-ttu-id="25bfc-106">から `ITypeLib` タイプライブラリを表すオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25bfc-106">[in] Pointer to an `ITypeLib` object that represents the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="25bfc-107">入出力メタデータシグネチャを表すインスタンスのアドレスを受け取る場所へのポインター `IMetaDataImport` 。</span><span class="sxs-lookup"><span data-stu-id="25bfc-107">[out] Pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25bfc-108">要件</span><span class="sxs-lookup"><span data-stu-id="25bfc-108">Requirements</span></span>  

 <span data-ttu-id="25bfc-109">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="25bfc-109">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25bfc-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="25bfc-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="25bfc-111">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="25bfc-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="25bfc-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25bfc-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25bfc-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="25bfc-113">See also</span></span>

- [<span data-ttu-id="25bfc-114">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="25bfc-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="25bfc-115">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="25bfc-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
