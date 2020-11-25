---
title: IMetaDataEmit::DefineImportMember メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportMember
helpviewer_keywords:
- DefineImportMember method [.NET Framework metadata]
- IMetaDataEmit::DefineImportMember method [.NET Framework metadata]
ms.assetid: c7dd94c6-335b-46ff-9dfe-505056db5673
topic_type:
- apiref
ms.openlocfilehash: 60210bc8f93294c3c3380c36096f3e80e5b26643
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723260"
---
# <a name="imetadataemitdefineimportmember-method"></a><span data-ttu-id="439d1-102">IMetaDataEmit::DefineImportMember メソッド</span><span class="sxs-lookup"><span data-stu-id="439d1-102">IMetaDataEmit::DefineImportMember Method</span></span>

<span data-ttu-id="439d1-103">現在のスコープの外部で定義されている型またはモジュールの指定したメンバーへの参照を作成し、その参照のトークンを定義します。</span><span class="sxs-lookup"><span data-stu-id="439d1-103">Creates a reference to the specified member of a type or module that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="439d1-104">構文</span><span class="sxs-lookup"><span data-stu-id="439d1-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineImportMember (
    [in]  IMetaDataAssemblyImport  *pAssemImport,
    [in]  const void               *pbHashValue,
    [in]  ULONG                    cbHashValue,  
    [in]  IMetaDataImport          *pImport,
    [in]  mdToken                  mbMember,
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,
    [in]  mdToken                  tkParent,
    [out] mdMemberRef              *pmr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="439d1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="439d1-105">Parameters</span></span>  

 `pAssemImport`  
 <span data-ttu-id="439d1-106">からターゲットメンバーのインポート元のアセンブリを表す [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="439d1-106">[in] An [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) interface that represents the assembly from which the target member is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="439d1-107">からによって指定されたアセンブリのハッシュを格納している配列 `pAssemImport` 。</span><span class="sxs-lookup"><span data-stu-id="439d1-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="439d1-108">[in] `pbHashValue` 配列のバイト数。</span><span class="sxs-lookup"><span data-stu-id="439d1-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="439d1-109">からターゲットメンバーのインポート元のメタデータスコープを表す [IMetaDataImport](imetadataimport-interface.md) インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="439d1-109">[in] An [IMetaDataImport](imetadataimport-interface.md) interface that represents the metadata scope from which the target member is imported.</span></span>  
  
 `mbMember`  
 <span data-ttu-id="439d1-110">からターゲットメンバーを指定するメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="439d1-110">[in] The metadata token that specifies the target member.</span></span> <span data-ttu-id="439d1-111">トークンには、 `mdMethodDef` (メンバーメソッドの場合)、(メンバープロパティの場合)、 `mdProperty` または `mdFieldDef` (メンバーフィールドの場合) トークンを指定できます。</span><span class="sxs-lookup"><span data-stu-id="439d1-111">The token can be an `mdMethodDef` (for a member method), `mdProperty` (for a member property), or `mdFieldDef` (for a member field) token.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="439d1-112">からターゲットメンバーがインポートされるアセンブリを表す [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="439d1-112">[in] An [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) interface that represents the assembly into which the target member is imported.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="439d1-113">から `mdTypeRef` `mdModuleRef` ターゲットメンバーを所有する型またはモジュールのトークンまたはトークン。</span><span class="sxs-lookup"><span data-stu-id="439d1-113">[in] The `mdTypeRef` or `mdModuleRef` token for the type or module, respectively, that owns the target member.</span></span>  
  
 `pmr`  
 <span data-ttu-id="439d1-114">入出力 `mdMemberRef` メンバー参照の現在のスコープで定義されているトークン。</span><span class="sxs-lookup"><span data-stu-id="439d1-114">[out] The `mdMemberRef` token that is defined in the current scope for the member reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="439d1-115">注釈</span><span class="sxs-lookup"><span data-stu-id="439d1-115">Remarks</span></span>  

 <span data-ttu-id="439d1-116">メソッドは、で指定された `DefineImportMember` メンバーを検索し `mbMember` ます。このメンバーは、で指定した別のスコープで定義され、 `pImport` そのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="439d1-116">The `DefineImportMember` method looks up the member, specified by `mbMember`, that is defined in another scope, specified by `pImport`, and retrieves its properties.</span></span> <span data-ttu-id="439d1-117">この情報を使用して、現在のスコープで [IMetaDataEmit::D efinememberref](imetadataemit-definememberref-method.md) メソッドを呼び出し、メンバー参照を作成します。</span><span class="sxs-lookup"><span data-stu-id="439d1-117">It uses this information to call the [IMetaDataEmit::DefineMemberRef](imetadataemit-definememberref-method.md) method in the current scope to create the member reference.</span></span>  
  
 <span data-ttu-id="439d1-118">一般に、メソッドを使用する前に、 `DefineImportMember` ターゲットメンバーの親クラス、インターフェイス、またはモジュールの型参照またはモジュール参照を、現在のスコープで作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="439d1-118">Generally, before you use the `DefineImportMember` method, you must create, in the current scope, a type reference or module reference for the target member's parent class, interface, or module.</span></span> <span data-ttu-id="439d1-119">その後、この参照のメタデータトークンが引数として渡され `tkParent` ます。</span><span class="sxs-lookup"><span data-stu-id="439d1-119">The metadata token for this reference is then passed in the `tkParent` argument.</span></span> <span data-ttu-id="439d1-120">後でコンパイラまたはリンカーによって解決される場合は、ターゲットメンバーの親への参照を作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="439d1-120">You do not need to create a reference to the target member's parent if it will be resolved later by the compiler or linker.</span></span> <span data-ttu-id="439d1-121">まとめると次のようになります。</span><span class="sxs-lookup"><span data-stu-id="439d1-121">To summarize:</span></span>  
  
- <span data-ttu-id="439d1-122">ターゲットメンバーがフィールドまたはメソッドの場合は、 [IMetaDataEmit::D efinetyperefbyname](imetadataemit-definetyperefbyname-method.md) または [IMetaDataEmit::D efineImportType](imetadataemit-defineimporttype-method.md) メソッドを使用して、メンバーの親クラスまたは親インターフェイスの型参照を現在のスコープ内に作成します。</span><span class="sxs-lookup"><span data-stu-id="439d1-122">If the target member is a field or method, use either the [IMetaDataEmit::DefineTypeRefByName](imetadataemit-definetyperefbyname-method.md) or the [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md) method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
- <span data-ttu-id="439d1-123">ターゲットメンバーがグローバル変数またはグローバル関数 (つまり、クラスまたはインターフェイスのメンバーではない) である場合は、 [IMetaDataEmit::D efinemoduleref](imetadataemit-definemoduleref-method.md) メソッドを使用して、メンバーの親モジュールに対して、現在のスコープでモジュール参照を作成します。</span><span class="sxs-lookup"><span data-stu-id="439d1-123">If the target member is a global variable or global function (that is, not a member of a class or interface), use the [IMetaDataEmit::DefineModuleRef](imetadataemit-definemoduleref-method.md) method to create a module reference, in the current scope, for the member's parent module.</span></span>  
  
- <span data-ttu-id="439d1-124">ターゲットメンバーの親が、後でコンパイラまたはリンカーによって解決される場合は、を渡し `mdTokenNil` `tkParent` ます。</span><span class="sxs-lookup"><span data-stu-id="439d1-124">If the target member's parent will be resolved later by the compiler or linker, then pass `mdTokenNil` in `tkParent`.</span></span> <span data-ttu-id="439d1-125">これが適用される唯一のシナリオは、グローバル関数またはグローバル変数が、最終的に現在のモジュールにリンクされ、メタデータがマージされる .obj ファイルからインポートされる場合です。</span><span class="sxs-lookup"><span data-stu-id="439d1-125">The only scenario in which this applies is when a global function or global variable is being imported from a .obj file that will ultimately be linked into the current module and the metadata merged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="439d1-126">要件</span><span class="sxs-lookup"><span data-stu-id="439d1-126">Requirements</span></span>  

 <span data-ttu-id="439d1-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="439d1-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="439d1-128">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="439d1-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="439d1-129">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="439d1-129">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="439d1-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="439d1-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="439d1-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="439d1-131">See also</span></span>

- [<span data-ttu-id="439d1-132">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="439d1-132">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="439d1-133">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="439d1-133">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
