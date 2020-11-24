---
title: CREATE_ASM_NAME_OBJ_FLAGS 列挙型
ms.date: 03/30/2017
api_name:
- CREATE_ASM_NAME_OBJ_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS
helpviewer_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS enumeration [.NET Framework fusion]
ms.assetid: a5ed2fd0-c7d2-4603-aaca-5d0caad92675
topic_type:
- apiref
ms.openlocfilehash: 52d5ad3a18c102422e90621c7d1e23b2692c0000
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683234"
---
# <a name="create_asm_name_obj_flags-enumeration"></a><span data-ttu-id="f1f9b-102">CREATE_ASM_NAME_OBJ_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="f1f9b-102">CREATE_ASM_NAME_OBJ_FLAGS Enumeration</span></span>

<span data-ttu-id="f1f9b-103">[Createassemblynameobject](createassemblynameobject-function.md)関数によって構築されるときに、 [IAssemblyName Interface](iassemblyname-interface.md)オブジェクトの属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="f1f9b-103">Specifies the attributes of an [IAssemblyName Interface](iassemblyname-interface.md) object when it is constructed by the [CreateAssemblyNameObject](createassemblynameobject-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1f9b-104">構文</span><span class="sxs-lookup"><span data-stu-id="f1f9b-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="f1f9b-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="f1f9b-105">Members</span></span>  
  
|<span data-ttu-id="f1f9b-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="f1f9b-106">Member</span></span>|<span data-ttu-id="f1f9b-107">説明</span><span class="sxs-lookup"><span data-stu-id="f1f9b-107">Description</span></span>|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|<span data-ttu-id="f1f9b-108">渡されたパラメーターがテキスト形式の id であることを示します。</span><span class="sxs-lookup"><span data-stu-id="f1f9b-108">Indicates that the parameter passed is a textual identity.</span></span>|  
|`CANOF_SET_DEFAULT_VALUES`|<span data-ttu-id="f1f9b-109">いくつかの既定値を設定します。</span><span class="sxs-lookup"><span data-stu-id="f1f9b-109">Sets a few default values.</span></span>|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|<span data-ttu-id="f1f9b-110">フレンドアセンブリの規則 (名前と公開キーのみ) を確認します。</span><span class="sxs-lookup"><span data-stu-id="f1f9b-110">Verifies the friend assembly rule (only name and public key).</span></span> <span data-ttu-id="f1f9b-111">このメンバーは内部でのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="f1f9b-111">This member is for internal use only.</span></span>|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|<span data-ttu-id="f1f9b-112">`CANOF_PARSE_DISPLAY_NAME`フラグとフラグの組み合わせ `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` 。</span><span class="sxs-lookup"><span data-stu-id="f1f9b-112">A combination of the `CANOF_PARSE_DISPLAY_NAME` and `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` flags.</span></span> <span data-ttu-id="f1f9b-113">このメンバーは内部でのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="f1f9b-113">This member is for internal use only.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f1f9b-114">要件</span><span class="sxs-lookup"><span data-stu-id="f1f9b-114">Requirements</span></span>  

 <span data-ttu-id="f1f9b-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1f9b-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1f9b-116">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="f1f9b-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f1f9b-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1f9b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1f9b-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1f9b-118">See also</span></span>

- [<span data-ttu-id="f1f9b-119">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1f9b-119">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="f1f9b-120">CreateAssemblyNameObject 関数</span><span class="sxs-lookup"><span data-stu-id="f1f9b-120">CreateAssemblyNameObject Function</span></span>](createassemblynameobject-function.md)
- [<span data-ttu-id="f1f9b-121">fusion 列挙体</span><span class="sxs-lookup"><span data-stu-id="f1f9b-121">Fusion Enumerations</span></span>](fusion-enumerations.md)
