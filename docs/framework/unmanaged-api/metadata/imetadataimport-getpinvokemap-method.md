---
title: IMetaDataImport::GetPinvokeMap メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPinvokeMap
helpviewer_keywords:
- IMetaDataImport::GetPinvokeMap method [.NET Framework metadata]
- GetPinvokeMap method [.NET Framework metadata]
ms.assetid: b8685c1e-b80c-4198-8eb3-748d6f48a99e
topic_type:
- apiref
ms.openlocfilehash: c34215f48190e60bd1a851f31b8b23f09491f4e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729240"
---
# <a name="imetadataimportgetpinvokemap-method"></a><span data-ttu-id="f3405-102">IMetaDataImport::GetPinvokeMap メソッド</span><span class="sxs-lookup"><span data-stu-id="f3405-102">IMetaDataImport::GetPinvokeMap Method</span></span>

<span data-ttu-id="f3405-103">PInvoke 呼び出しの対象アセンブリを表す ModuleRef トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="f3405-103">Gets a ModuleRef token to represent the target assembly of a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3405-104">構文</span><span class="sxs-lookup"><span data-stu-id="f3405-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPinvokeMap (  
   [in]  mdToken       tk,  
   [out] DWORD         *pdwMappingFlags,  
   [out] LPWSTR        szImportName,  
   [in]  ULONG         cchImportName,  
   [out] ULONG         *pchImportName,  
   [out] mdModuleRef   *pmrImportDLL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3405-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f3405-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="f3405-106">からPInvoke マッピングメタデータを取得する FieldDef または MethodDef トークン。</span><span class="sxs-lookup"><span data-stu-id="f3405-106">[in] A FieldDef or MethodDef token to get the PInvoke mapping metadata for.</span></span>  
  
 `pdwMappingFlags`  
 <span data-ttu-id="f3405-107">入出力マッピングに使用されるフラグへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f3405-107">[out] A pointer to flags used for mapping.</span></span> <span data-ttu-id="f3405-108">この値は、 [CorPinvokeMap](corpinvokemap-enumeration.md) 列挙体のビットマスクです。</span><span class="sxs-lookup"><span data-stu-id="f3405-108">This value is a bitmask from the [CorPinvokeMap](corpinvokemap-enumeration.md) enumeration.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="f3405-109">入出力アンマネージターゲット DLL の名前。</span><span class="sxs-lookup"><span data-stu-id="f3405-109">[out] The name of the unmanaged target DLL.</span></span>  
  
 `cchImportName`  
 <span data-ttu-id="f3405-110">からのワイド文字のサイズ `szImportName` 。</span><span class="sxs-lookup"><span data-stu-id="f3405-110">[in] The size in wide characters of `szImportName`.</span></span>  
  
 `pchImportName`  
 <span data-ttu-id="f3405-111">入出力で返されたワイド文字の数 `szImportName` 。</span><span class="sxs-lookup"><span data-stu-id="f3405-111">[out] The number of wide characters returned in `szImportName`.</span></span>  
  
 `pmrImportDLL`  
 <span data-ttu-id="f3405-112">入出力アンマネージターゲットオブジェクトライブラリを表す ModuleRef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f3405-112">[out] A pointer to a ModuleRef token that represents the unmanaged target object library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3405-113">要件</span><span class="sxs-lookup"><span data-stu-id="f3405-113">Requirements</span></span>  

 <span data-ttu-id="f3405-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3405-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3405-115">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="f3405-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3405-116">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="f3405-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f3405-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3405-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3405-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3405-118">See also</span></span>

- [<span data-ttu-id="f3405-119">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f3405-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="f3405-120">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f3405-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
