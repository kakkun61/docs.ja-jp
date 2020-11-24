---
title: EmitAssemblyCustomAttribute メソッド
ms.date: 03/30/2017
api_name:
- IALink.EmitAssemblyCustomAttribute
- EmitAssemblyCustomAttribute
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssemblyCustomAttribute
helpviewer_keywords:
- EmitAssemblyCustomAttribute method
ms.assetid: b72f5409-79af-4fa7-90a7-7630eec170f1
topic_type:
- apiref
ms.openlocfilehash: 2070d1ec2aec80638c20c764eed5086c4a42e0fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676362"
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="eeaaf-102">EmitAssemblyCustomAttribute メソッド</span><span class="sxs-lookup"><span data-stu-id="eeaaf-102">EmitAssemblyCustomAttribute Method</span></span>

<span data-ttu-id="eeaaf-103">を呼び出して、アセンブリレベルのカスタム属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="eeaaf-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eeaaf-104">構文</span><span class="sxs-lookup"><span data-stu-id="eeaaf-104">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssemblyCustomAttribute(  
    mdAssembly   AssemblyID,  
    mdToken      FileToken,  
    mdToken      tkType,  
    void const*  pCustomValue,  
    DWORD        cbCustomValue,  
    BOOL         bSecurity,  
    BOOL         bAllowMulti  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="eeaaf-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eeaaf-105">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="eeaaf-106">アセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="eeaaf-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="eeaaf-107">属性をなするファイル。</span><span class="sxs-lookup"><span data-stu-id="eeaaf-107">File that defiles the attribute.</span></span> <span data-ttu-id="eeaaf-108">がバインドされ `AssemblyID` ていない .netmodule を示していない場合は、NULL にすることができます。</span><span class="sxs-lookup"><span data-stu-id="eeaaf-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="eeaaf-109">カスタム属性の型。</span><span class="sxs-lookup"><span data-stu-id="eeaaf-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="eeaaf-110">カスタム値データ。</span><span class="sxs-lookup"><span data-stu-id="eeaaf-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="eeaaf-111">カスタム値データの長さ。</span><span class="sxs-lookup"><span data-stu-id="eeaaf-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="eeaaf-112">カスタム属性がアセンブリ署名に関連付けられている場合は TRUE。</span><span class="sxs-lookup"><span data-stu-id="eeaaf-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="eeaaf-113">複数の属性を出力する場合は TRUE。</span><span class="sxs-lookup"><span data-stu-id="eeaaf-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eeaaf-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="eeaaf-114">Return Value</span></span>  

 <span data-ttu-id="eeaaf-115">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="eeaaf-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eeaaf-116">要件</span><span class="sxs-lookup"><span data-stu-id="eeaaf-116">Requirements</span></span>  

 <span data-ttu-id="eeaaf-117">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="eeaaf-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeaaf-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="eeaaf-118">See also</span></span>

- [<span data-ttu-id="eeaaf-119">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eeaaf-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="eeaaf-120">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eeaaf-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="eeaaf-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="eeaaf-121">ALink API</span></span>](index.md)
