---
title: IMetaDataAssemblyEmit::SetFileProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetFileProps
helpviewer_keywords:
- IMetaDataAssemblyEmit::SetFileProps method [.NET Framework metadata]
- SetFileProps method [.NET Framework metadata]
ms.assetid: 85667d38-611c-45a9-938d-930ac7a7b681
topic_type:
- apiref
ms.openlocfilehash: 9cf5f3d926c1e742dd9134e7bf292df53e1a4909
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720179"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="b04a7-102">IMetaDataAssemblyEmit::SetFileProps メソッド</span><span class="sxs-lookup"><span data-stu-id="b04a7-102">IMetaDataAssemblyEmit::SetFileProps Method</span></span>

<span data-ttu-id="b04a7-103">指定された `File` メタデータ構造体を変更します。</span><span class="sxs-lookup"><span data-stu-id="b04a7-103">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b04a7-104">構文</span><span class="sxs-lookup"><span data-stu-id="b04a7-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b04a7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b04a7-105">Parameters</span></span>  

 `file`  
 <span data-ttu-id="b04a7-106">から変更するメタデータ構造を指定するメタデータトークン `File` 。</span><span class="sxs-lookup"><span data-stu-id="b04a7-106">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="b04a7-107">からファイルに関連付けられているハッシュデータへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b04a7-107">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="b04a7-108">からのサイズ (バイト単位) `pbHashValue` 。</span><span class="sxs-lookup"><span data-stu-id="b04a7-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="b04a7-109">からファイルのさまざまな属性を指定する [Corfileflags](corfileflags-enumeration.md) 値のビットごとの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="b04a7-109">[in] A bitwise combination of [CorFileFlags](corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b04a7-110">注釈</span><span class="sxs-lookup"><span data-stu-id="b04a7-110">Remarks</span></span>  

 <span data-ttu-id="b04a7-111">メタデータ構造を作成するには `File` 、 [IMetaDataAssemblyEmit::D efineFile](imetadataassemblyemit-definefile-method.md) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="b04a7-111">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b04a7-112">要件</span><span class="sxs-lookup"><span data-stu-id="b04a7-112">Requirements</span></span>  

 <span data-ttu-id="b04a7-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b04a7-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b04a7-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="b04a7-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b04a7-115">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="b04a7-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b04a7-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b04a7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b04a7-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="b04a7-117">See also</span></span>

- [<span data-ttu-id="b04a7-118">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b04a7-118">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
