---
title: IMetaDataImport::GetNativeCallConvFromSig メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNativeCallConvFromSig
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNativeCallConvFromSig
helpviewer_keywords:
- GetNativeCallConvFromSig method [.NET Framework metadata]
- IMetaDataImport::GetNativeCallConvFromSig method [.NET Framework metadata]
ms.assetid: 50e04026-4d4a-47d9-96c1-f4677d6d938b
topic_type:
- apiref
ms.openlocfilehash: d44ad493a786aaa35150515b7c254965490bd714
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701706"
---
# <a name="imetadataimportgetnativecallconvfromsig-method"></a><span data-ttu-id="68023-102">IMetaDataImport::GetNativeCallConvFromSig メソッド</span><span class="sxs-lookup"><span data-stu-id="68023-102">IMetaDataImport::GetNativeCallConvFromSig Method</span></span>

<span data-ttu-id="68023-103">指定したシグネチャ ポインターで表されるメソッドのネイティブな呼び出し規約を取得します。</span><span class="sxs-lookup"><span data-stu-id="68023-103">Gets the native calling convention for the method that is represented by the specified signature pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68023-104">構文</span><span class="sxs-lookup"><span data-stu-id="68023-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeCallConvFromSig (  
   [in]  void const  *pvSig,  
   [in]  ULONG       cbSig,  
   [out] ULONG       *pCallConv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68023-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="68023-105">Parameters</span></span>  

 `pvSig`  
 <span data-ttu-id="68023-106">から呼び出し規約を返すメソッドのメタデータシグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="68023-106">[in] A pointer to the metadata signature of the method to return the calling convention for.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="68023-107">からのサイズ (バイト単位) `pvSig` 。</span><span class="sxs-lookup"><span data-stu-id="68023-107">[in] The size in bytes of `pvSig`.</span></span>  
  
 `pCallConv`  
 <span data-ttu-id="68023-108">入出力ネイティブ呼び出し規約へのポインター。</span><span class="sxs-lookup"><span data-stu-id="68023-108">[out] A pointer to the native calling convention.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68023-109">要件</span><span class="sxs-lookup"><span data-stu-id="68023-109">Requirements</span></span>  

 <span data-ttu-id="68023-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68023-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68023-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="68023-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="68023-112">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="68023-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="68023-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68023-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68023-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="68023-114">See also</span></span>

- <xref:System.Runtime.InteropServices.CallingConvention>
- [<span data-ttu-id="68023-115">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="68023-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="68023-116">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="68023-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
