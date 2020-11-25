---
title: IMetaDataImport::GetNameFromToken メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNameFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNameFromToken
helpviewer_keywords:
- GetNameFromToken method [.NET Framework metadata]
- IMetaDataImport::GetNameFromToken method [.NET Framework metadata]
ms.assetid: 32114ecf-8916-4ab2-a201-179c017344f1
topic_type:
- apiref
ms.openlocfilehash: 867fb0ee4bc1a093eb7fd46e25497d585c4d9b6b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727498"
---
# <a name="imetadataimportgetnamefromtoken-method"></a><span data-ttu-id="7814e-102">IMetaDataImport::GetNameFromToken メソッド</span><span class="sxs-lookup"><span data-stu-id="7814e-102">IMetaDataImport::GetNameFromToken Method</span></span>

<span data-ttu-id="7814e-103">指定したメタデータ トークンによって参照されるオブジェクトの UTF-8 名を取得します。</span><span class="sxs-lookup"><span data-stu-id="7814e-103">Gets the UTF-8 name of the object referenced by the specified metadata token.</span></span> <span data-ttu-id="7814e-104">このメソッドは、互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="7814e-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7814e-105">構文</span><span class="sxs-lookup"><span data-stu-id="7814e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7814e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7814e-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="7814e-107">から名前を返すオブジェクトを表すトークン。</span><span class="sxs-lookup"><span data-stu-id="7814e-107">[in] The token representing the object to return the name for.</span></span>  
  
 `pszUtf8NamePtr`  
 <span data-ttu-id="7814e-108">入出力ヒープ内の UTF-8 オブジェクト名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="7814e-108">[out] A pointer to the UTF-8 object name in the heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7814e-109">注釈</span><span class="sxs-lookup"><span data-stu-id="7814e-109">Remarks</span></span>  

 <span data-ttu-id="7814e-110">`GetNameFromToken` は互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="7814e-110">`GetNameFromToken` is obsolete.</span></span> <span data-ttu-id="7814e-111">別の方法として、フィールドやメソッドなど、必要な特定の種類のトークンのプロパティを取得するには、メソッドを呼び出し `GetFieldProps` `GetMethodProps` ます。</span><span class="sxs-lookup"><span data-stu-id="7814e-111">As an alternative, call a method to get the properties of the particular type of token required, such as `GetFieldProps` for a field or `GetMethodProps` for a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7814e-112">要件</span><span class="sxs-lookup"><span data-stu-id="7814e-112">Requirements</span></span>  

 <span data-ttu-id="7814e-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7814e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7814e-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="7814e-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7814e-115">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="7814e-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7814e-116">**.NET Framework のバージョン:** 1.0</span><span class="sxs-lookup"><span data-stu-id="7814e-116">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7814e-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="7814e-117">See also</span></span>

- [<span data-ttu-id="7814e-118">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7814e-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="7814e-119">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7814e-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
