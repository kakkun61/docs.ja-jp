---
title: CVStruct 構造体
ms.date: 03/30/2017
api_name:
- CVStruct
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CVStruct
helpviewer_keywords:
- CVStruct structure [.NET Framework metadata]
ms.assetid: e9e4e497-d5fb-464b-991c-3bdd824664fd
topic_type:
- apiref
ms.openlocfilehash: db36b94fafe20b58b9bcbb886b8d285326960f67
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715577"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="23b7c-102">CVStruct 構造体</span><span class="sxs-lookup"><span data-stu-id="23b7c-102">CVStruct Structure</span></span>

<span data-ttu-id="23b7c-103">モジュールまたは複合イメージをインストールするときに使用する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="23b7c-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23b7c-104">構文</span><span class="sxs-lookup"><span data-stu-id="23b7c-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="23b7c-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="23b7c-105">Members</span></span>  
  
|<span data-ttu-id="23b7c-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="23b7c-106">Member</span></span>|<span data-ttu-id="23b7c-107">説明</span><span class="sxs-lookup"><span data-stu-id="23b7c-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="23b7c-108">Major</span><span class="sxs-lookup"><span data-stu-id="23b7c-108">Major</span></span>|<span data-ttu-id="23b7c-109">メジャーバージョンのビルド番号。</span><span class="sxs-lookup"><span data-stu-id="23b7c-109">Major version build number.</span></span>|  
|<span data-ttu-id="23b7c-110">マイナー</span><span class="sxs-lookup"><span data-stu-id="23b7c-110">Minor</span></span>|<span data-ttu-id="23b7c-111">マイナーバージョンのビルド番号。</span><span class="sxs-lookup"><span data-stu-id="23b7c-111">Minor version build number.</span></span>|  
|<span data-ttu-id="23b7c-112">Sub</span><span class="sxs-lookup"><span data-stu-id="23b7c-112">Sub</span></span>|<span data-ttu-id="23b7c-113">サブビルド番号。</span><span class="sxs-lookup"><span data-stu-id="23b7c-113">Sub-build number.</span></span>|  
|<span data-ttu-id="23b7c-114">ビルド</span><span class="sxs-lookup"><span data-stu-id="23b7c-114">Build</span></span>|<span data-ttu-id="23b7c-115">ビルド番号。</span><span class="sxs-lookup"><span data-stu-id="23b7c-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="23b7c-116">要件</span><span class="sxs-lookup"><span data-stu-id="23b7c-116">Requirements</span></span>  

 <span data-ttu-id="23b7c-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23b7c-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23b7c-118">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="23b7c-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="23b7c-119">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="23b7c-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="23b7c-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23b7c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23b7c-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="23b7c-121">See also</span></span>

- [<span data-ttu-id="23b7c-122">メタデータ構造体</span><span class="sxs-lookup"><span data-stu-id="23b7c-122">Metadata Structures</span></span>](metadata-structures.md)
