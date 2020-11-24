---
title: IMetaDataAssemblyEmit::DefineAssemblyRef メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssemblyRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssemblyRef
helpviewer_keywords:
- DefineAssemblyRef method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineAssemblyRef method [.NET Framework metadata]
ms.assetid: 0b284b18-0084-4b3a-912a-5ebe9f29c88b
topic_type:
- apiref
ms.openlocfilehash: ba53ff30f0b6d0ae7fed7db422b7c0a242204a2c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689434"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a><span data-ttu-id="3368a-102">IMetaDataAssemblyEmit::DefineAssemblyRef メソッド</span><span class="sxs-lookup"><span data-stu-id="3368a-102">IMetaDataAssemblyEmit::DefineAssemblyRef Method</span></span>

<span data-ttu-id="3368a-103">このアセンブリが参照するアセンブリのメタデータを含む `AssemblyRef` 構造体を作成し、関連付けられたメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="3368a-103">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3368a-104">構文</span><span class="sxs-lookup"><span data-stu-id="3368a-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineAssemblyRef (  
    [in]  void                *pbPublicKeyOrToken,  
    [in]  ULONG               cbPublicKeyOrToken,  
    [in]  LPCWSTR             szName,  
    [in]  ASSEMBLYMETADATA    pMetaData,  
    [in]  void                *pbHashValue,  
    [in]  ULONG               cbHashValue,  
    [in]  DWORD               dwAssemblyRefFlags,  
    [out] mdAssemblyRef       *pmdar  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3368a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3368a-105">Parameters</span></span>  

 `pbPublicKeyOrToken`  
 <span data-ttu-id="3368a-106">から参照アセンブリの発行元の公開キー。</span><span class="sxs-lookup"><span data-stu-id="3368a-106">[in] The public key of the publisher of the referenced assembly.</span></span> <span data-ttu-id="3368a-107">ヘルパー関数 [StrongNameTokenFromAssembly](../strong-naming/strongnametokenfromassembly-function.md) を使用して、このパラメーターとして渡す公開キーのハッシュを取得できます。</span><span class="sxs-lookup"><span data-stu-id="3368a-107">The helper function [StrongNameTokenFromAssembly](../strong-naming/strongnametokenfromassembly-function.md) can be used to get the hash of the public key to pass as this parameter.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="3368a-108">からのサイズ (バイト単位) `pbPublicKeyOrToken` 。</span><span class="sxs-lookup"><span data-stu-id="3368a-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="3368a-109">からユーザーが判読できる、アセンブリのテキスト名。</span><span class="sxs-lookup"><span data-stu-id="3368a-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="3368a-110">この値は、1024文字を超えないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3368a-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="3368a-111">から参照されたアセンブリのバージョン、プラットフォーム、およびロケール情報を格納している ASSEMBLYMETADATA インスタンス。</span><span class="sxs-lookup"><span data-stu-id="3368a-111">[in] An ASSEMBLYMETADATA instance that contains the version, platform and locale information of the referenced assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="3368a-112">から参照アセンブリに関連付けられているハッシュデータ。</span><span class="sxs-lookup"><span data-stu-id="3368a-112">[in] The hash data associated with the referenced assembly.</span></span> <span data-ttu-id="3368a-113">省略可能。</span><span class="sxs-lookup"><span data-stu-id="3368a-113">Optional.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="3368a-114">からのサイズ (バイト単位) `pbHashValue` 。</span><span class="sxs-lookup"><span data-stu-id="3368a-114">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="3368a-115">から実行エンジンの動作に影響を与える [Corassemblyflags](corassemblyflags-enumeration.md) 値のビットごとの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="3368a-115">[in] A bitwise combination of [CorAssemblyFlags](corassemblyflags-enumeration.md) values that influence the behavior of the execution engine.</span></span>  
  
 `pmdar`  
 <span data-ttu-id="3368a-116">入出力返された `AssemblyRef` メタデータトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3368a-116">[out] A pointer to the returned `AssemblyRef` metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3368a-117">注釈</span><span class="sxs-lookup"><span data-stu-id="3368a-117">Remarks</span></span>  

 <span data-ttu-id="3368a-118">`AssemblyRef`このアセンブリが参照するアセンブリごとに1つのメタデータ構造を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3368a-118">One `AssemblyRef` metadata structure must be defined for each assembly that this assembly references.</span></span>  
  
 <span data-ttu-id="3368a-119">実行時には、参照されたアセンブリの詳細がアセンブリリゾルバーに渡され、"ビルド済み" の情報を表すことが示されます。</span><span class="sxs-lookup"><span data-stu-id="3368a-119">At run time, the details of a referenced assembly are passed to the assembly resolver with an indication that they represent the "as built" information.</span></span> <span data-ttu-id="3368a-120">次に、アセンブリリゾルバーがポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="3368a-120">The assembly resolver then applies policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3368a-121">要件</span><span class="sxs-lookup"><span data-stu-id="3368a-121">Requirements</span></span>  

 <span data-ttu-id="3368a-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3368a-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3368a-123">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="3368a-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3368a-124">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="3368a-124">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3368a-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3368a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3368a-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="3368a-126">See also</span></span>

- [<span data-ttu-id="3368a-127">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3368a-127">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
