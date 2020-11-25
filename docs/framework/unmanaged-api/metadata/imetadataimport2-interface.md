---
title: IMetaDataImport2 インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataImport2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2
helpviewer_keywords:
- IMetaDataImport2 interface [.NET Framework metadata]
ms.assetid: d39b2b87-ba53-4771-ae53-952a68452511
topic_type:
- apiref
ms.openlocfilehash: a845ecfde6583d625d2a8f165443344ff9e40d05
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702551"
---
# <a name="imetadataimport2-interface"></a><span data-ttu-id="82050-102">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="82050-102">IMetaDataImport2 Interface</span></span>

<span data-ttu-id="82050-103">[IMetaDataImport](imetadataimport-interface.md)インターフェイスを拡張して、ジェネリック型を処理する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="82050-103">Extends the [IMetaDataImport](imetadataimport-interface.md) interface to provide the capability of working with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="82050-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="82050-104">Methods</span></span>  
  
|<span data-ttu-id="82050-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="82050-105">Method</span></span>|<span data-ttu-id="82050-106">説明</span><span class="sxs-lookup"><span data-stu-id="82050-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="82050-107">EnumGenericParamConstraints メソッド</span><span class="sxs-lookup"><span data-stu-id="82050-107">EnumGenericParamConstraints Method</span></span>](imetadataimport2-enumgenericparamconstraints-method.md)|<span data-ttu-id="82050-108">指定したトークンによって表されるジェネリックパラメーターに関連付けられているジェネリックパラメーター制約の配列の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="82050-108">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="82050-109">EnumGenericParams メソッド</span><span class="sxs-lookup"><span data-stu-id="82050-109">EnumGenericParams Method</span></span>](imetadataimport2-enumgenericparams-method.md)|<span data-ttu-id="82050-110">指定した TypeDef または MethodDef トークンに関連付けられているジェネリックパラメータートークンの配列の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="82050-110">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>|  
|[<span data-ttu-id="82050-111">EnumMethodSpecs メソッド</span><span class="sxs-lookup"><span data-stu-id="82050-111">EnumMethodSpecs Method</span></span>](imetadataimport2-enummethodspecs-method.md)|<span data-ttu-id="82050-112">指定した MethodDef または MemberRef トークンに関連付けられている MethodSpec トークンの配列の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="82050-112">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>|  
|[<span data-ttu-id="82050-113">GetGenericParamConstraintProps メソッド</span><span class="sxs-lookup"><span data-stu-id="82050-113">GetGenericParamConstraintProps Method</span></span>](imetadataimport2-getgenericparamconstraintprops-method.md)|<span data-ttu-id="82050-114">指定された制約トークンによって表されるジェネリックパラメーター制約に関連付けられているメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="82050-114">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>|  
|[<span data-ttu-id="82050-115">GetGenericParamProps メソッド</span><span class="sxs-lookup"><span data-stu-id="82050-115">GetGenericParamProps Method</span></span>](imetadataimport2-getgenericparamprops-method.md)|<span data-ttu-id="82050-116">指定したトークンによって表されるジェネリックパラメーターに関連付けられているメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="82050-116">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="82050-117">GetMethodSpecProps メソッド</span><span class="sxs-lookup"><span data-stu-id="82050-117">GetMethodSpecProps Method</span></span>](imetadataimport2-getmethodspecprops-method.md)|<span data-ttu-id="82050-118">指定した MethodSpec トークンによって参照されるメソッドのメタデータシグネチャを取得します。</span><span class="sxs-lookup"><span data-stu-id="82050-118">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>|  
|[<span data-ttu-id="82050-119">GetPEKind メソッド</span><span class="sxs-lookup"><span data-stu-id="82050-119">GetPEKind Method</span></span>](imetadataimport2-getpekind-method.md)|<span data-ttu-id="82050-120">移植可能な実行可能 (PE) ファイルのコードの性質を示す値を取得します。通常は、現在のメタデータスコープで定義されている DLL または EXE ファイルです。</span><span class="sxs-lookup"><span data-stu-id="82050-120">Gets a value identifying the nature of the code in a portable executable (PE) file, typically a DLL or EXE file, defined in the current metadata scope</span></span>|  
|[<span data-ttu-id="82050-121">GetVersionString メソッド</span><span class="sxs-lookup"><span data-stu-id="82050-121">GetVersionString Method</span></span>](imetadataimport2-getversionstring-method.md)|<span data-ttu-id="82050-122">アセンブリのビルドに使用されたランタイムのバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="82050-122">Gets the version number of the runtime that was used to build the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="82050-123">要件</span><span class="sxs-lookup"><span data-stu-id="82050-123">Requirements</span></span>  

 <span data-ttu-id="82050-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="82050-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82050-125">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="82050-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="82050-126">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="82050-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="82050-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82050-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82050-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="82050-128">See also</span></span>

- <xref:System.Reflection.PortableExecutableKinds>
- [<span data-ttu-id="82050-129">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="82050-129">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="82050-130">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="82050-130">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
