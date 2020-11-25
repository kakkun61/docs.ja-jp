---
title: IMetaDataAssemblyImport::EnumFiles メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumFiles
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumFiles
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumFiles method [.NET Framework metadata]
- EnumFiles method [.NET Framework metadata]
ms.assetid: f0d721e2-b946-426d-8e20-9124bd04e4cb
topic_type:
- apiref
ms.openlocfilehash: f9af770f3bdca98f6b3d06d8b0fe6c92745f73e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731624"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="e7ab9-102">IMetaDataAssemblyImport::EnumFiles メソッド</span><span class="sxs-lookup"><span data-stu-id="e7ab9-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>

<span data-ttu-id="e7ab9-103">現在のアセンブリマニフェストで参照されているファイルを列挙します。</span><span class="sxs-lookup"><span data-stu-id="e7ab9-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7ab9-104">構文</span><span class="sxs-lookup"><span data-stu-id="e7ab9-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,
    [out] mdFile          rFiles[],
    [in]  ULONG           cMax,
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7ab9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e7ab9-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="e7ab9-106">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e7ab9-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="e7ab9-107">このメソッドの最初の呼び出しでは、null 値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e7ab9-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="e7ab9-108">入出力メタデータトークンを格納するために使用される配列 `mdFile` 。</span><span class="sxs-lookup"><span data-stu-id="e7ab9-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e7ab9-109">から `mdFile` に格納できるトークンの最大数 `rFiles` 。</span><span class="sxs-lookup"><span data-stu-id="e7ab9-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="e7ab9-110">入出力 `mdFile` 実際に配置されたトークンの数 `rFiles` 。</span><span class="sxs-lookup"><span data-stu-id="e7ab9-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e7ab9-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="e7ab9-111">Return Value</span></span>  
  
|<span data-ttu-id="e7ab9-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e7ab9-112">HRESULT</span></span>|<span data-ttu-id="e7ab9-113">説明</span><span class="sxs-lookup"><span data-stu-id="e7ab9-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e7ab9-114">`EnumFiles` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="e7ab9-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e7ab9-115">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="e7ab9-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="e7ab9-116">この場合、 `pcTokens` は0に設定されます。</span><span class="sxs-lookup"><span data-stu-id="e7ab9-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e7ab9-117">要件</span><span class="sxs-lookup"><span data-stu-id="e7ab9-117">Requirements</span></span>  

 <span data-ttu-id="e7ab9-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7ab9-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7ab9-119">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="e7ab9-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e7ab9-120">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="e7ab9-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e7ab9-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7ab9-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7ab9-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="e7ab9-122">See also</span></span>

- [<span data-ttu-id="e7ab9-123">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e7ab9-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
