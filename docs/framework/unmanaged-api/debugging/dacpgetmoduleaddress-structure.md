---
title: DacpGetModuleAddress 構造体
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress Structure
helpviewer.keywords:
- DacpGetModuleAddress Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: a65fa9974165fa36e59a7fb83dca6dd902f7d8dc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724395"
---
# <a name="dacpgetmoduleaddress-structure"></a><span data-ttu-id="efba7-102">DacpGetModuleAddress 構造体</span><span class="sxs-lookup"><span data-stu-id="efba7-102">DacpGetModuleAddress Structure</span></span>

<span data-ttu-id="efba7-103">モジュールアドレス要求のコンテナーを定義します。</span><span class="sxs-lookup"><span data-stu-id="efba7-103">Defines the container for a module address request.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="efba7-104">構文</span><span class="sxs-lookup"><span data-stu-id="efba7-104">Syntax</span></span>

```cpp
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a><span data-ttu-id="efba7-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="efba7-105">Members</span></span>

| <span data-ttu-id="efba7-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="efba7-106">Member</span></span>      | <span data-ttu-id="efba7-107">説明</span><span class="sxs-lookup"><span data-stu-id="efba7-107">Description</span></span>                |
| ----------- | -------------------------- |
| `ModulePtr` | <span data-ttu-id="efba7-108">モジュールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="efba7-108">The pointer to the module.</span></span> |

## <a name="methods"></a><span data-ttu-id="efba7-109">メソッド</span><span class="sxs-lookup"><span data-stu-id="efba7-109">Methods</span></span>

| <span data-ttu-id="efba7-110">メソッド</span><span class="sxs-lookup"><span data-stu-id="efba7-110">Method</span></span>                                                                                               | <span data-ttu-id="efba7-111">説明</span><span class="sxs-lookup"><span data-stu-id="efba7-111">Description</span></span>                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [<span data-ttu-id="efba7-112">Request</span><span class="sxs-lookup"><span data-stu-id="efba7-112">Request</span></span>](dacpgetmoduleaddress-request-method.md) | <span data-ttu-id="efba7-113">指定されたランタイム構造体を構造体に設定する要求を実行します。</span><span class="sxs-lookup"><span data-stu-id="efba7-113">Performs a request to populate the structure from the given runtime structure.</span></span> |

## <a name="remarks"></a><span data-ttu-id="efba7-114">注釈</span><span class="sxs-lookup"><span data-stu-id="efba7-114">Remarks</span></span>

<span data-ttu-id="efba7-115">この構造体はランタイム内に存在し、ヘッダーまたはライブラリファイルを介して公開されることはありません。</span><span class="sxs-lookup"><span data-stu-id="efba7-115">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="efba7-116">これを使用するには、上で指定したように構造体を定義し `CLRDATA_ADDRESS` ます。は、64ビットの符号なし整数です。</span><span class="sxs-lookup"><span data-stu-id="efba7-116">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="efba7-117">要件</span><span class="sxs-lookup"><span data-stu-id="efba7-117">Requirements</span></span>

<span data-ttu-id="efba7-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efba7-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="efba7-119">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="efba7-119">**Header:** None</span></span>  
<span data-ttu-id="efba7-120">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="efba7-120">**Library:** None</span></span>  
<span data-ttu-id="efba7-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="efba7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="efba7-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="efba7-122">See also</span></span>

- [<span data-ttu-id="efba7-123">デバッグ</span><span class="sxs-lookup"><span data-stu-id="efba7-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="efba7-124">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="efba7-124">Debugging Structures</span></span>](debugging-structures.md)
