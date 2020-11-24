---
title: SetPEKind メソッド
ms.date: 03/30/2017
api_name:
- IALink2.SetPEKind
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetPEKind
helpviewer_keywords:
- SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type:
- apiref
ms.openlocfilehash: be8a11cbf70e2c6f19ace67648b124515c1fb3c3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680041"
---
# <a name="setpekind-method"></a><span data-ttu-id="5ee7e-102">SetPEKind メソッド</span><span class="sxs-lookup"><span data-stu-id="5ee7e-102">SetPEKind Method</span></span>

<span data-ttu-id="5ee7e-103">ポータブル実行可能ファイルの種類 (マシン固有またはコンピューターに依存しない) を決定します。</span><span class="sxs-lookup"><span data-stu-id="5ee7e-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ee7e-104">構文</span><span class="sxs-lookup"><span data-stu-id="5ee7e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;
```  
  
## <a name="parameters"></a><span data-ttu-id="5ee7e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5ee7e-105">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="5ee7e-106">アセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="5ee7e-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="5ee7e-107">PE の種類を設定するファイルのトークン。</span><span class="sxs-lookup"><span data-stu-id="5ee7e-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="5ee7e-108">がバインドされ `AssemblyID` ていない .netmodule を示していない場合は、NULL にすることができます。</span><span class="sxs-lookup"><span data-stu-id="5ee7e-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="5ee7e-109">[Corpekind 列挙体](../metadata/corpekind-enumeration.md)によって示される PE の種類。</span><span class="sxs-lookup"><span data-stu-id="5ee7e-109">The type of PE, as indicated by the [CorPEKind Enumeration](../metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="5ee7e-110">NT ヘッダーに示されている、対象コンピューターのアーキテクチャ。</span><span class="sxs-lookup"><span data-stu-id="5ee7e-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ee7e-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="5ee7e-111">Return Value</span></span>  

 <span data-ttu-id="5ee7e-112">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="5ee7e-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ee7e-113">要件</span><span class="sxs-lookup"><span data-stu-id="5ee7e-113">Requirements</span></span>  

 <span data-ttu-id="5ee7e-114">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="5ee7e-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ee7e-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ee7e-115">See also</span></span>

- [<span data-ttu-id="5ee7e-116">GetPEKind メソッド</span><span class="sxs-lookup"><span data-stu-id="5ee7e-116">GetPEKind Method</span></span>](../metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="5ee7e-117">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5ee7e-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="5ee7e-118">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5ee7e-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="5ee7e-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="5ee7e-119">ALink API</span></span>](index.md)
