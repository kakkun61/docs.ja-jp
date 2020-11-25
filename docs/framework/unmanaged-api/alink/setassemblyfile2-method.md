---
title: SetAssemblyFile2 メソッド
ms.date: 03/30/2017
api_name:
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
ms.openlocfilehash: 131f5d951e524ef48f2cfe1e3e88ef80ac21c452
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703682"
---
# <a name="setassemblyfile2-method"></a><span data-ttu-id="c1517-102">SetAssemblyFile2 メソッド</span><span class="sxs-lookup"><span data-stu-id="c1517-102">SetAssemblyFile2 Method</span></span>

<span data-ttu-id="c1517-103">新しいアセンブリのオプションとオプションの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="c1517-103">Sets the name of and options for a new assembly.</span></span> <span data-ttu-id="c1517-104">バインドされていないモジュールを生成する場合は、このメソッドを呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="c1517-104">Do not call this method when you produce unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1517-105">構文</span><span class="sxs-lookup"><span data-stu-id="c1517-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1517-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c1517-106">Parameters</span></span>  

 `pszFilename`  
 <span data-ttu-id="c1517-107">マニフェストファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="c1517-107">Name of manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="c1517-108">このファイルの[IMetaDataEmit2 インターフェイス](../metadata/imetadataemit2-interface.md)インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="c1517-108">[IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface for this file.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="c1517-109">[Assemblyflags 列挙体](../metadata/assemblyflags-enumeration.md)によって表されるオプション。</span><span class="sxs-lookup"><span data-stu-id="c1517-109">Options represented by [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="c1517-110">構築されるアセンブリの一意の ID を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="c1517-110">Receives unique ID for the assembly being constructed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1517-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="c1517-111">Return Value</span></span>  

 <span data-ttu-id="c1517-112">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="c1517-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1517-113">要件</span><span class="sxs-lookup"><span data-stu-id="c1517-113">Requirements</span></span>  

 <span data-ttu-id="c1517-114">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="c1517-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1517-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1517-115">See also</span></span>

- [<span data-ttu-id="c1517-116">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c1517-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c1517-117">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c1517-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c1517-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="c1517-118">ALink API</span></span>](index.md)
