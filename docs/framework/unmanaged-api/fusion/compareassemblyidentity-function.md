---
title: CompareAssemblyIdentity 関数
ms.date: 03/30/2017
api_name:
- CompareAssemblyIdentity
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CompareAssemblyIdentity
helpviewer_keywords:
- CompareAssemblyIdentity function [.NET Framework fusion]
ms.assetid: 8b364ae1-8efa-4744-a7da-81fd093d84d6
topic_type:
- apiref
ms.openlocfilehash: da32ce6a40378a6f88cf71bd7707be2079d71068
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717592"
---
# <a name="compareassemblyidentity-function"></a><span data-ttu-id="d5666-102">CompareAssemblyIdentity 関数</span><span class="sxs-lookup"><span data-stu-id="d5666-102">CompareAssemblyIdentity Function</span></span>

<span data-ttu-id="d5666-103">2つのアセンブリ id を比較して、それらが等しいかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="d5666-103">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5666-104">構文</span><span class="sxs-lookup"><span data-stu-id="d5666-104">Syntax</span></span>  
  
```cpp  
STDAPI CompareAssemblyIdentity (  
    [in]  LPCWSTR                  pwzAssemblyIdentity1,  
    [in]  BOOL                     fUnified1,  
    [in]  LPCWSTR                  pwzAssemblyIdentity2,  
    [in]  BOOL                     fUnified2,  
    [out] BOOL                     *pfEquivalent,  
    [out] AssemblyComparisonResult *pResult  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5666-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d5666-105">Parameters</span></span>  

 `pwzAssemblyIdentity1`  
 <span data-ttu-id="d5666-106">から比較対象の最初のアセンブリのテキスト id。</span><span class="sxs-lookup"><span data-stu-id="d5666-106">[in] The textual identity of the first assembly in the comparison.</span></span>  
  
 `fUnified1`  
 <span data-ttu-id="d5666-107">からのユーザー指定の統一を示すブール型のフラグ `pwzAssemblyIdentity1` 。</span><span class="sxs-lookup"><span data-stu-id="d5666-107">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity1`.</span></span>  
  
 `pwzAssemblyIdentity2`  
 <span data-ttu-id="d5666-108">から比較対象の2番目のアセンブリのテキスト id。</span><span class="sxs-lookup"><span data-stu-id="d5666-108">[in] The textual identity of the second assembly in the comparison.</span></span>  
  
 `fUnified2`  
 <span data-ttu-id="d5666-109">からのユーザー指定の統一を示すブール型のフラグ `pwzAssemblyIdentity2` 。</span><span class="sxs-lookup"><span data-stu-id="d5666-109">[in] A Boolean flag that indicates user-specified unification for `pwzAssemblyIdentity2`.</span></span>  
  
 `pfEquivalent`  
 <span data-ttu-id="d5666-110">入出力2つのアセンブリが等しいかどうかを示すブール型のフラグ。</span><span class="sxs-lookup"><span data-stu-id="d5666-110">[out] A Boolean flag that indicates whether the two assemblies are equivalent.</span></span>  
  
 `pResult`  
 <span data-ttu-id="d5666-111">入出力比較に関する詳細情報を含む [AssemblyComparisonResult](assemblycomparisonresult-enumeration.md) 列挙です。</span><span class="sxs-lookup"><span data-stu-id="d5666-111">[out] An [AssemblyComparisonResult](assemblycomparisonresult-enumeration.md) enumeration that contains detailed information about the comparison.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5666-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="d5666-112">Return Value</span></span>  

 <span data-ttu-id="d5666-113">`pfEquivalent` 2つのアセンブリが等しいかどうかを示すブール値を返します。</span><span class="sxs-lookup"><span data-stu-id="d5666-113">`pfEquivalent` returns a Boolean value that indicates whether the two assemblies are equivalent.</span></span> <span data-ttu-id="d5666-114">`pResult` 値の1つを返し `AssemblyComparisonResult` 、の値のより詳細な理由を指定し `pfEquivalent` ます。</span><span class="sxs-lookup"><span data-stu-id="d5666-114">`pResult` returns one of the `AssemblyComparisonResult` values, to give a more detailed reason for the value of `pfEquivalent`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5666-115">注釈</span><span class="sxs-lookup"><span data-stu-id="d5666-115">Remarks</span></span>  

 <span data-ttu-id="d5666-116">`CompareAssemblyIdentity` とが等価かどうかを確認し `pwzAssemblyIdentity1` `pwzAssemblyIdentity2` ます。</span><span class="sxs-lookup"><span data-stu-id="d5666-116">`CompareAssemblyIdentity` checks whether `pwzAssemblyIdentity1` and `pwzAssemblyIdentity2` are equivalent.</span></span> <span data-ttu-id="d5666-117">`pfEquivalent` は `true` 、次の条件の1つ以上でに設定されます。</span><span class="sxs-lookup"><span data-stu-id="d5666-117">`pfEquivalent` is set to `true` under one or more of the following conditions:</span></span>  
  
- <span data-ttu-id="d5666-118">2つのアセンブリ id は同等です。</span><span class="sxs-lookup"><span data-stu-id="d5666-118">The two assembly identities are equivalent.</span></span> <span data-ttu-id="d5666-119">厳密な名前が付けられたアセンブリの場合、等価性には、アセンブリ名、バージョン、公開キートークン、およびカルチャが同一である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5666-119">For strongly named assemblies, equivalency requires the assembly name, version, public key token, and culture to be identical.</span></span> <span data-ttu-id="d5666-120">単純な名前付きアセンブリの場合、等価性にはアセンブリ名とカルチャの一致が必要です。</span><span class="sxs-lookup"><span data-stu-id="d5666-120">For simply named assemblies, equivalency requires a match on the assembly name and culture.</span></span>  
  
- <span data-ttu-id="d5666-121">どちらのアセンブリ id も、.NET Framework で実行されるアセンブリを参照します。</span><span class="sxs-lookup"><span data-stu-id="d5666-121">Both assembly identities refer to assemblies that run on the .NET Framework.</span></span> <span data-ttu-id="d5666-122">この条件は `true` 、アセンブリのバージョン番号が一致しない場合でもを返します。</span><span class="sxs-lookup"><span data-stu-id="d5666-122">This condition returns `true` even if the assembly version numbers do not match.</span></span>  
  
- <span data-ttu-id="d5666-123">2つのアセンブリはマネージアセンブリではありませんが、 `fUnified1` または `fUnified2` がに設定されてい `true` ます。</span><span class="sxs-lookup"><span data-stu-id="d5666-123">The two assemblies are not managed assemblies, but `fUnified1` or `fUnified2` was set to `true`.</span></span>  
  
 <span data-ttu-id="d5666-124">フラグは、 `fUnified` 厳密な名前が付けられたアセンブリのバージョン番号までのすべてのバージョン番号が、厳密に名前が付けられたアセンブリと同等であると見なされることを示します。</span><span class="sxs-lookup"><span data-stu-id="d5666-124">The `fUnified` flag indicates that all version numbers up to the version number of the strongly named assembly are considered equivalent to the strongly named assembly.</span></span> <span data-ttu-id="d5666-125">たとえば、の値 `pwzAssemblyIndentity1` が "MyAssembly, version = 3.0.0.0, culture = ニュートラル, publicKeyToken =..." で、の値がの場合、 `fUnified1` `true` バージョン0.0.0.0 から3.0.0.0 のすべてのバージョンの MyAssembly が同等として扱われることを示します。</span><span class="sxs-lookup"><span data-stu-id="d5666-125">For example, if the value of `pwzAssemblyIndentity1` is "MyAssembly, version=3.0.0.0, culture=neutral, publicKeyToken=....", and the value of `fUnified1` is `true`, this indicates that all versions of MyAssembly from version 0.0.0.0 to 3.0.0.0 should be treated as equivalent.</span></span> <span data-ttu-id="d5666-126">このような場合、 `pwzAssemblyIndentity2` がと同じアセンブリを参照している場合は、 `pwzAssemblyIndentity1` バージョン番号が低い点が `pfEquivalent` に設定され `true` ます。</span><span class="sxs-lookup"><span data-stu-id="d5666-126">In such a case, if `pwzAssemblyIndentity2` refers to the same assembly as `pwzAssemblyIndentity1`, except that it has a lower version number, `pfEquivalent` is set to `true`.</span></span> <span data-ttu-id="d5666-127">が `pwzAssemblyIdentity2` より上位のバージョン番号を参照している場合、 `pfEquivalent` の値がである場合にのみがに設定され `true` `fUnified2` `true` ます。</span><span class="sxs-lookup"><span data-stu-id="d5666-127">If `pwzAssemblyIdentity2` refers to a higher version number, `pfEquivalent` is set to `true` only if the value of `fUnified2` is `true`.</span></span>  
  
 <span data-ttu-id="d5666-128">パラメーターには、 `pResult` 2 つのアセンブリが同等であるかどうかについての特定の情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d5666-128">The `pResult` parameter includes specific information about why the two assemblies are considered equivalent or not equivalent.</span></span> <span data-ttu-id="d5666-129">詳細については、「 [AssemblyComparisonResult 列挙型](assemblycomparisonresult-enumeration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5666-129">For more information, see [AssemblyComparisonResult Enumeration](assemblycomparisonresult-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5666-130">要件</span><span class="sxs-lookup"><span data-stu-id="d5666-130">Requirements</span></span>  

 <span data-ttu-id="d5666-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5666-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5666-132">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="d5666-132">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d5666-133">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="d5666-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d5666-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5666-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5666-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5666-135">See also</span></span>

- [<span data-ttu-id="d5666-136">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="d5666-136">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="d5666-137">AssemblyComparisonResult 列挙型</span><span class="sxs-lookup"><span data-stu-id="d5666-137">AssemblyComparisonResult Enumeration</span></span>](assemblycomparisonresult-enumeration.md)
