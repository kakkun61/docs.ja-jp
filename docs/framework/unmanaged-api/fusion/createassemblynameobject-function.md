---
title: CreateAssemblyNameObject 関数
ms.date: 03/30/2017
api_name:
- CreateAssemblyNameObject
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyNameObject
helpviewer_keywords:
- CreateAssemblyNameObject function [.NET Framework fusion]
ms.assetid: 55c8b41e-fbe4-4ae0-aa29-68fbb2311691
topic_type:
- apiref
ms.openlocfilehash: 995f1064c2f40005c4a19ef034d7edfd668b5d51
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704163"
---
# <a name="createassemblynameobject-function"></a><span data-ttu-id="08b86-102">CreateAssemblyNameObject 関数</span><span class="sxs-lookup"><span data-stu-id="08b86-102">CreateAssemblyNameObject Function</span></span>

<span data-ttu-id="08b86-103">指定された名前を持つアセンブリの一意の id を表す [IAssemblyName](iassemblyname-interface.md) インスタンスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="08b86-103">Gets an interface pointer to an [IAssemblyName](iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08b86-104">構文</span><span class="sxs-lookup"><span data-stu-id="08b86-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="08b86-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="08b86-105">Parameters</span></span>  

 `ppAssemblyNameObj`  
 <span data-ttu-id="08b86-106">入出力返された `IAssemblyName` 。</span><span class="sxs-lookup"><span data-stu-id="08b86-106">[out] The returned `IAssemblyName`.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="08b86-107">から新しいインスタンスを作成する対象のアセンブリの名前 `IAssemblyName` 。</span><span class="sxs-lookup"><span data-stu-id="08b86-107">[in] The name of the assembly for which to create the new `IAssemblyName` instance.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="08b86-108">からオブジェクトコンストラクターに渡すフラグ。</span><span class="sxs-lookup"><span data-stu-id="08b86-108">[in] Flags to pass to the object constructor.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="08b86-109">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="08b86-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="08b86-110">`pvReserved` null 参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="08b86-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08b86-111">要件</span><span class="sxs-lookup"><span data-stu-id="08b86-111">Requirements</span></span>  

 <span data-ttu-id="08b86-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08b86-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08b86-113">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="08b86-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="08b86-114">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="08b86-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="08b86-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08b86-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08b86-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="08b86-116">See also</span></span>

- [<span data-ttu-id="08b86-117">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="08b86-117">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="08b86-118">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="08b86-118">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
