---
title: SetAssemblyFile メソッド
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile
helpviewer_keywords:
- SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type:
- apiref
ms.openlocfilehash: 45eed17b91f70d4188d1d89fc91a41455f3e845b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732646"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="84da5-102">SetAssemblyFile メソッド</span><span class="sxs-lookup"><span data-stu-id="84da5-102">SetAssemblyFile Method</span></span>

<span data-ttu-id="84da5-103">ビルドされるアセンブリの名前を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="84da5-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="84da5-104">非バインドモジュールの生成時には使用しません。</span><span class="sxs-lookup"><span data-stu-id="84da5-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84da5-105">構文</span><span class="sxs-lookup"><span data-stu-id="84da5-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="84da5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="84da5-106">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="84da5-107">マニフェストファイルの完全修飾名。</span><span class="sxs-lookup"><span data-stu-id="84da5-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="84da5-108">[IMetaDataEmit インターフェイス](../metadata/imetadataemit-interface.md)インターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="84da5-108">Pointer to [IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="84da5-109">[Assemblyflags 列挙型](../metadata/assemblyflags-enumeration.md)で定義されているフラグ。</span><span class="sxs-lookup"><span data-stu-id="84da5-109">Flags as defined in [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="84da5-110">結果として得られるアセンブリの ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="84da5-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84da5-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="84da5-111">Return Value</span></span>  

 <span data-ttu-id="84da5-112">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="84da5-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84da5-113">要件</span><span class="sxs-lookup"><span data-stu-id="84da5-113">Requirements</span></span>  

 <span data-ttu-id="84da5-114">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="84da5-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84da5-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="84da5-115">See also</span></span>

- [<span data-ttu-id="84da5-116">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="84da5-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="84da5-117">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="84da5-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="84da5-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="84da5-118">ALink API</span></span>](index.md)
