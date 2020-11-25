---
title: IMetaDataAssemblyImport::FindAssembliesByName メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindAssembliesByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindAssembliesByName
helpviewer_keywords:
- FindAssembliesByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindAssembliesByName method [.NET Framework metadata]
ms.assetid: 4db97cf9-e4c1-4233-8efa-cbdc0e14a8e4
topic_type:
- apiref
ms.openlocfilehash: a2bf0335f8d75c7dbd1a651afdb54da8c7be2460
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731625"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a><span data-ttu-id="b6e5f-102">IMetaDataAssemblyImport::FindAssembliesByName メソッド</span><span class="sxs-lookup"><span data-stu-id="b6e5f-102">IMetaDataAssemblyImport::FindAssembliesByName Method</span></span>

<span data-ttu-id="b6e5f-103">`szAssemblyName`参照を解決するために共通言語ランタイム (CLR) によって採用されている標準規則を使用して、指定したパラメーターを持つアセンブリの配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="b6e5f-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6e5f-104">構文</span><span class="sxs-lookup"><span data-stu-id="b6e5f-104">Syntax</span></span>  
  
```cpp  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,
    [in]  LPCWSTR     szPrivateBin,
    [in]  LPCWSTR     szAssemblyName,
    [out] IUnknown    *ppIUnk[],
    [in]  ULONG       cMax,
    [out] ULONG       *pcAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6e5f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b6e5f-105">Parameters</span></span>  

 `szAppBase`  
 <span data-ttu-id="b6e5f-106">から指定されたアセンブリを検索するルートディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="b6e5f-106">[in] The root directory in which to search for the given assembly.</span></span> <span data-ttu-id="b6e5f-107">この値がに設定されている場合 `null` 、 `FindAssembliesByName` はアセンブリのグローバルアセンブリキャッシュ内だけを検索します。</span><span class="sxs-lookup"><span data-stu-id="b6e5f-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="b6e5f-108">からルートディレクトリの下のセミコロンで区切られたサブディレクトリ (たとえば、"bin; bin2") の一覧。このディレクトリで、アセンブリを検索します。</span><span class="sxs-lookup"><span data-stu-id="b6e5f-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span></span> <span data-ttu-id="b6e5f-109">これらのディレクトリは、既定のプローブルールで指定されているものに加えてプローブされます。</span><span class="sxs-lookup"><span data-stu-id="b6e5f-109">These directories are probed in addition to those specified in the default probing rules.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="b6e5f-110">から検索するアセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="b6e5f-110">[in] The name of the assembly to find.</span></span> <span data-ttu-id="b6e5f-111">この文字列の形式は、のクラス参照ページで定義されてい <xref:System.Reflection.AssemblyName> ます。</span><span class="sxs-lookup"><span data-stu-id="b6e5f-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="b6e5f-112">からインターフェイスポインターを格納する [IUnknown](/cpp/atl/iunknown) 型の配列 `IMetadataAssemblyImport` 。</span><span class="sxs-lookup"><span data-stu-id="b6e5f-112">[in] An array of type [IUnknown](/cpp/atl/iunknown) in which to put the `IMetadataAssemblyImport` interface pointers.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b6e5f-113">入出力に配置できるインターフェイスポインターの最大数 `ppIUnk` 。</span><span class="sxs-lookup"><span data-stu-id="b6e5f-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span></span>  
  
 `pcAssemblies`  
 <span data-ttu-id="b6e5f-114">入出力返されたインターフェイスポインターの数。</span><span class="sxs-lookup"><span data-stu-id="b6e5f-114">[out] The number of interface pointers returned.</span></span> <span data-ttu-id="b6e5f-115">つまり、実際に配置されたインターフェイスポインターの数 `ppIUnk` 。</span><span class="sxs-lookup"><span data-stu-id="b6e5f-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6e5f-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="b6e5f-116">Return Value</span></span>  
  
|<span data-ttu-id="b6e5f-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b6e5f-117">HRESULT</span></span>|<span data-ttu-id="b6e5f-118">説明</span><span class="sxs-lookup"><span data-stu-id="b6e5f-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b6e5f-119">`FindAssembliesByName` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="b6e5f-119">`FindAssembliesByName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b6e5f-120">アセンブリがありません。</span><span class="sxs-lookup"><span data-stu-id="b6e5f-120">There are no assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6e5f-121">注釈</span><span class="sxs-lookup"><span data-stu-id="b6e5f-121">Remarks</span></span>  

 <span data-ttu-id="b6e5f-122">アセンブリ名が指定されている場合、メソッドは、 `FindAssembliesByName` アセンブリ参照を解決するための標準の規則に従って、アセンブリを検索します。</span><span class="sxs-lookup"><span data-stu-id="b6e5f-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span></span> <span data-ttu-id="b6e5f-123">(詳細については、「 [ランタイムがアセンブリを検索する方法](../../deployment/how-the-runtime-locates-assemblies.md)」を参照してください)。 `FindAssembliesByName` 呼び出し元は、アプリケーションベースやプライベート検索パスなど、アセンブリリゾルバーコンテキストのさまざまな側面を構成できます。</span><span class="sxs-lookup"><span data-stu-id="b6e5f-123">(For more information, see [How the Runtime Locates Assemblies](../../deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span></span>  
  
 <span data-ttu-id="b6e5f-124">`FindAssembliesByName`メソッドでは、アセンブリ解決ロジックを呼び出すために、プロセスで CLR を初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6e5f-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span></span> <span data-ttu-id="b6e5f-125">したがって、を呼び出す前に[Coinitializeee](../hosting/coinitializeee-function.md) (COINITEE_DEFAULT を渡す) を呼び出してから、CoUninitializeCor の呼び出しを実行する必要があり `FindAssembliesByName` [CoUninitializeCor](../hosting/couninitializecor-function.md)ます。</span><span class="sxs-lookup"><span data-stu-id="b6e5f-125">Therefore, you must call [CoInitializeEE](../hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../hosting/couninitializecor-function.md).</span></span>  
  
 <span data-ttu-id="b6e5f-126">`FindAssembliesByName` 渡されたアセンブリ名のアセンブリマニフェストを格納しているファイルへの [IMetaDataImport](imetadataimport-interface.md) ポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="b6e5f-126">`FindAssembliesByName` returns an [IMetaDataImport](imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span></span> <span data-ttu-id="b6e5f-127">指定したアセンブリ名が完全に指定されていない場合 (たとえば、バージョンが含まれていない場合) は、複数のアセンブリが返されることがあります。</span><span class="sxs-lookup"><span data-stu-id="b6e5f-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span></span>  
  
 <span data-ttu-id="b6e5f-128">`FindAssembliesByName` は、コンパイル時に参照アセンブリの検索を試行するコンパイラによって一般的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="b6e5f-128">`FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6e5f-129">要件</span><span class="sxs-lookup"><span data-stu-id="b6e5f-129">Requirements</span></span>  

 <span data-ttu-id="b6e5f-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6e5f-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6e5f-131">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="b6e5f-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b6e5f-132">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="b6e5f-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b6e5f-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6e5f-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6e5f-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6e5f-134">See also</span></span>

- [<span data-ttu-id="b6e5f-135">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="b6e5f-135">How the Runtime Locates Assemblies</span></span>](../../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="b6e5f-136">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b6e5f-136">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
