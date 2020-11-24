---
title: ExportNestedTypeForwarder メソッド
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedTypeForwarder
helpviewer_keywords:
- ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type:
- apiref
ms.openlocfilehash: 45adda6551e1cec994f59acbb0e8d2b5c56c4df6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684812"
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="cec10-102">ExportNestedTypeForwarder メソッド</span><span class="sxs-lookup"><span data-stu-id="cec10-102">ExportNestedTypeForwarder Method</span></span>

<span data-ttu-id="cec10-103">入れ子になった型の型フォワーダーを、指定されたアセンブリの型テーブルに追加します。</span><span class="sxs-lookup"><span data-stu-id="cec10-103">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cec10-104">構文</span><span class="sxs-lookup"><span data-stu-id="cec10-104">Syntax</span></span>  
  
```cpp  
HRESULT ExportNestedTypeForwarder(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="cec10-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cec10-105">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="cec10-106">エクスポート元のアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="cec10-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="cec10-107">型を定義するファイルのファイルトークンまたはアセンブリ ID。</span><span class="sxs-lookup"><span data-stu-id="cec10-107">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="cec10-108">型のトークン。</span><span class="sxs-lookup"><span data-stu-id="cec10-108">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="cec10-109">親の種類のトークン。</span><span class="sxs-lookup"><span data-stu-id="cec10-109">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="cec10-110">エクスポートする完全修飾型名。</span><span class="sxs-lookup"><span data-stu-id="cec10-110">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="cec10-111">`ComType``tdPublic`やなどのフラグ `tdNested` 。</span><span class="sxs-lookup"><span data-stu-id="cec10-111">`ComType` flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="cec10-112">エクスポートの種類のトークンを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="cec10-112">Receives token of export type.</span></span> <span data-ttu-id="cec10-113">これは、入れ子にされた型を出力する場合にのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="cec10-113">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cec10-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="cec10-114">Return Value</span></span>  

 <span data-ttu-id="cec10-115">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="cec10-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cec10-116">要件</span><span class="sxs-lookup"><span data-stu-id="cec10-116">Requirements</span></span>  

 <span data-ttu-id="cec10-117">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="cec10-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cec10-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="cec10-118">See also</span></span>

- [<span data-ttu-id="cec10-119">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cec10-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="cec10-120">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cec10-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="cec10-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="cec10-121">ALink API</span></span>](index.md)
