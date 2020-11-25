---
title: IMetaDataAssemblyEmit::DefineAssembly メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type:
- apiref
ms.openlocfilehash: 6d783e27c60db7381025f3b2382728e3996323ae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725730"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="bd2ff-102">IMetaDataAssemblyEmit::DefineAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="bd2ff-102">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>

<span data-ttu-id="bd2ff-103">`Assembly`指定したアセンブリのメタデータを格納している構造体を作成し、関連付けられているメタデータトークンを返します。</span><span class="sxs-lookup"><span data-stu-id="bd2ff-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd2ff-104">構文</span><span class="sxs-lookup"><span data-stu-id="bd2ff-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineAssembly (  
    [in]  void                 *pbPublicKey,  
    [in]  ULONG                cbPublicKey,  
    [in]  ULONG                uHashAlgId,  
    [in]  LPCWSTR              szName,
    [in]  ASSEMBLYMETADATA     *pMetaData,  
    [in]  DWORD                dwAssemblyFlags,  
    [out] mdAssembly           *pmda  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd2ff-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bd2ff-105">Parameters</span></span>  

 `pbPublicKey`  
 <span data-ttu-id="bd2ff-106">からアセンブリの発行元を識別する公開キー。アセンブリに厳密な名前が付けられていない場合は NULL。</span><span class="sxs-lookup"><span data-stu-id="bd2ff-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="bd2ff-107">からのサイズ (バイト単位) `pbPublicKey` 。</span><span class="sxs-lookup"><span data-stu-id="bd2ff-107">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="bd2ff-108">からアセンブリ内のファイルを暗号化するために使用するハッシュアルゴリズムの識別子。または、SHA-1 アルゴリズムを指定する場合は NULL。</span><span class="sxs-lookup"><span data-stu-id="bd2ff-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="bd2ff-109">からユーザーが判読できる、アセンブリのテキスト名。</span><span class="sxs-lookup"><span data-stu-id="bd2ff-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="bd2ff-110">この値は、1024文字を超えないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd2ff-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="bd2ff-111">からアセンブリのバージョン、プラットフォーム、およびロケール情報を格納している ASSEMBLYMETADATA インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="bd2ff-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="bd2ff-112">からアセンブリの機能を記述する [Corassemblyflags](corassemblyflags-enumeration.md) 値の組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="bd2ff-112">[in] A combination of [CorAssemblyFlags](corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="bd2ff-113">入出力メタデータトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="bd2ff-113">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd2ff-114">注釈</span><span class="sxs-lookup"><span data-stu-id="bd2ff-114">Remarks</span></span>  

 <span data-ttu-id="bd2ff-115">`Assembly`マニフェスト内で定義できるメタデータ構造は1つだけです。</span><span class="sxs-lookup"><span data-stu-id="bd2ff-115">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd2ff-116">要件</span><span class="sxs-lookup"><span data-stu-id="bd2ff-116">Requirements</span></span>  

 <span data-ttu-id="bd2ff-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd2ff-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd2ff-118">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="bd2ff-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bd2ff-119">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="bd2ff-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bd2ff-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd2ff-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd2ff-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="bd2ff-121">See also</span></span>

- [<span data-ttu-id="bd2ff-122">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bd2ff-122">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
