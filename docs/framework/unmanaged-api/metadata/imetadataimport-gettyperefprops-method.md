---
title: IMetaDataImport::GetTypeRefProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeRefProps
helpviewer_keywords:
- IMetaDataImport::GetTypeRefProps method [.NET Framework metadata]
- GetTypeRefProps method [.NET Framework metadata]
ms.assetid: 01837955-ce1e-4068-b338-fd473bd77d1d
topic_type:
- apiref
ms.openlocfilehash: 5d98481d7934b4c96178aaa32fb0f9378eb359fc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729171"
---
# <a name="imetadataimportgettyperefprops-method"></a><span data-ttu-id="4ad12-102">IMetaDataImport::GetTypeRefProps メソッド</span><span class="sxs-lookup"><span data-stu-id="4ad12-102">IMetaDataImport::GetTypeRefProps Method</span></span>

<span data-ttu-id="4ad12-103"><xref:System.Type>指定した TypeRef トークンによって参照されるに関連付けられているメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="4ad12-103">Gets the metadata associated with the <xref:System.Type> referenced by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ad12-104">構文</span><span class="sxs-lookup"><span data-stu-id="4ad12-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ad12-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4ad12-105">Parameters</span></span>  

 `tr`  
 <span data-ttu-id="4ad12-106">からメタデータを返す型を表す TypeRef トークン。</span><span class="sxs-lookup"><span data-stu-id="4ad12-106">[in] The TypeRef token that represents the type to return metadata for.</span></span>  
  
 `ptkResolutionScope`  
 <span data-ttu-id="4ad12-107">入出力参照が行われるスコープへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4ad12-107">[out] A pointer to the scope in which the reference is made.</span></span> <span data-ttu-id="4ad12-108">この値は、AssemblyRef または ModuleRef トークンです。</span><span class="sxs-lookup"><span data-stu-id="4ad12-108">This value is an AssemblyRef or ModuleRef token.</span></span>  
  
 `szName`  
 <span data-ttu-id="4ad12-109">入出力型名を格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="4ad12-109">[out] A buffer containing the type name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="4ad12-110">からのワイド文字で要求されたサイズ `szName` 。</span><span class="sxs-lookup"><span data-stu-id="4ad12-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="4ad12-111">入出力のワイド文字で返されたサイズ `szName` 。</span><span class="sxs-lookup"><span data-stu-id="4ad12-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ad12-112">要件</span><span class="sxs-lookup"><span data-stu-id="4ad12-112">Requirements</span></span>  

 <span data-ttu-id="4ad12-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ad12-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ad12-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="4ad12-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4ad12-115">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="4ad12-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4ad12-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ad12-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ad12-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ad12-117">See also</span></span>

- [<span data-ttu-id="4ad12-118">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4ad12-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="4ad12-119">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4ad12-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
