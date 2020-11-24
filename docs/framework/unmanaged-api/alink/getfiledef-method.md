---
title: GetFileDef メソッド
ms.date: 03/30/2017
api_name:
- IALink2.GetFileDef
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetFileDef
helpviewer_keywords:
- GetFileDef method
ms.assetid: 4e3fbe6c-b82a-4181-ab17-7faa1263f5b3
topic_type:
- apiref
ms.openlocfilehash: 42935813579d7f1d55a9f1daf9d8c6c1241f85be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684708"
---
# <a name="getfiledef-method"></a><span data-ttu-id="7f709-102">GetFileDef メソッド</span><span class="sxs-lookup"><span data-stu-id="7f709-102">GetFileDef Method</span></span>

<span data-ttu-id="7f709-103">ALink によって割り当てられたトークンとは対照的に、メタデータで使用される実際の FileDef トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="7f709-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f709-104">構文</span><span class="sxs-lookup"><span data-stu-id="7f709-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f709-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7f709-105">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="7f709-106">アセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="7f709-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="7f709-107">AddFile メソッドまたは AddImport メソッドから取得された追加ファイルのトークン。</span><span class="sxs-lookup"><span data-stu-id="7f709-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="7f709-108">FileDef トークンを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="7f709-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f709-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="7f709-109">Return Value</span></span>  

 <span data-ttu-id="7f709-110">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="7f709-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f709-111">要件</span><span class="sxs-lookup"><span data-stu-id="7f709-111">Requirements</span></span>  

 <span data-ttu-id="7f709-112">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="7f709-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f709-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="7f709-113">See also</span></span>

- [<span data-ttu-id="7f709-114">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7f709-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="7f709-115">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7f709-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="7f709-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="7f709-116">ALink API</span></span>](index.md)
