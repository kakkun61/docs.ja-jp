---
title: CeeSectionRelocType 列挙型
ms.date: 03/30/2017
api_name:
- CeeSectionRelocType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionRelocType
helpviewer_keywords:
- CeeSectionRelocType enumeration [.NET Framework metadata]
ms.assetid: 124656f6-0dad-4ceb-9043-d3869ab65cde
topic_type:
- apiref
ms.openlocfilehash: f7aa9699e9929608c90020c6b2d66c301fc11955
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732711"
---
# <a name="ceesectionreloctype-enumeration"></a><span data-ttu-id="733cd-102">CeeSectionRelocType 列挙型</span><span class="sxs-lookup"><span data-stu-id="733cd-102">CeeSectionRelocType Enumeration</span></span>

<span data-ttu-id="733cd-103">`reloc` [ICeeGen:: AddSectionReloc](iceegen-addsectionreloc-method.md)の呼び出しで生成された命令の種類に影響する値を提供します。</span><span class="sxs-lookup"><span data-stu-id="733cd-103">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](iceegen-addsectionreloc-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="733cd-104">構文</span><span class="sxs-lookup"><span data-stu-id="733cd-104">Syntax</span></span>  
  
```cpp  
typedef enum  {  
    srRelocAbsolute,  
    srRelocHighLow          = 3,  
    srRelocHighAdj,
    srRelocMapToken,  
    srRelocRelative,  
    srRelocFilePos,  
    srRelocCodeRelative,  
    srRelocIA64Imm64,  
    srRelocDir64,  
    srRelocIA64PcRel25,  
    srRelocIA64PcRel64,    srRelocAbsoluteTagged,    srRelocSentinel,    srNoBaseReloc       = 0x4000,  
    srRelocPtr          = 0x8000,  
    srRelocAbsolutePtr      = srRelocPtr + srRelocAbsolute,  
    srRelocHighLowPtr       = srRelocPtr + srRelocHighLow,  
    srRelocRelativePtr      = srRelocPtr + srRelocRelative,  
    srRelocIA64Imm64Ptr     = srRelocPtr + srRelocIA64Imm64,  
    srRelocDir64Ptr         = srRelocPtr + srRelocDir64  
    } CeeSectionRelocType;  
```  
  
## <a name="members"></a><span data-ttu-id="733cd-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="733cd-105">Members</span></span>  
  
|<span data-ttu-id="733cd-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="733cd-106">Member</span></span>|<span data-ttu-id="733cd-107">説明</span><span class="sxs-lookup"><span data-stu-id="733cd-107">Description</span></span>|  
|------------|-----------------|  
|`srRelocAbsolute`|<span data-ttu-id="733cd-108">は、セクションに対して相対的なを生成し `reloc` 、reloc セクションには何も送信しません。</span><span class="sxs-lookup"><span data-stu-id="733cd-108">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span>|  
|`srRelocHighLow`|<span data-ttu-id="733cd-109">`reloc`ポインターサイズの位置のを生成します。</span><span class="sxs-lookup"><span data-stu-id="733cd-109">Generates a `reloc` for a pointer-sized location.</span></span> <span data-ttu-id="733cd-110">これは、プラットフォームに応じて BASED_HIGHLOW または BASED_DIR64 に変換されます。</span><span class="sxs-lookup"><span data-stu-id="733cd-110">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span></span>|  
|`srRelocHighAdj`|<span data-ttu-id="733cd-111">は、 `reloc` 32 ビットの数値の上位16ビットに対してを生成します。下位16ビットは、reloc テーブルの次の単語に含まれます。</span><span class="sxs-lookup"><span data-stu-id="733cd-111">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span></span>|  
|`srRelocMapToken`|<span data-ttu-id="733cd-112">トークンマップの再配置を生成し、reloc セクションに何も送信しません。</span><span class="sxs-lookup"><span data-stu-id="733cd-112">Generates a token map relocation, sending nothing into a .reloc section.</span></span>|  
|`srRelocRelative`|<span data-ttu-id="733cd-113">値が相対アドレスの修正であることを示します。</span><span class="sxs-lookup"><span data-stu-id="733cd-113">Indicates that the value is a relative address fixup.</span></span>|  
|`srRelocFilePos`|<span data-ttu-id="733cd-114">は、セクションに対して相対的なを生成し `reloc` 、reloc セクションには何も送信しません。</span><span class="sxs-lookup"><span data-stu-id="733cd-114">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span> <span data-ttu-id="733cd-115">これは、セクションの `reloc` 仮想アドレスではなく、セクションのファイル位置に対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="733cd-115">This `reloc` is relative to the file position of the section, not the section's virtual address.</span></span>|  
|`srRelocCodeRelative`|<span data-ttu-id="733cd-116">コード相対アドレスのフィックスアップを指定します。</span><span class="sxs-lookup"><span data-stu-id="733cd-116">Specifies a code-relative address fixup.</span></span>|  
|`srRelocIA64Imm64`|<span data-ttu-id="733cd-117">`reloc`Ia64 命令で64ビットアドレスのを生成 `movl` します。</span><span class="sxs-lookup"><span data-stu-id="733cd-117">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span></span>|  
|`srRelocDir64`|<span data-ttu-id="733cd-118">`reloc`64 ビットアドレスのを生成します。</span><span class="sxs-lookup"><span data-stu-id="733cd-118">Generates a `reloc` for a 64-bit address.</span></span>|  
|`srRelocIA64PcRel25`|<span data-ttu-id="733cd-119">`reloc`Ia64 命令で25ビット PC 相対アドレスのを生成 `br.call` します。</span><span class="sxs-lookup"><span data-stu-id="733cd-119">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span></span>|  
|`srRelocIA64PcRel64`|<span data-ttu-id="733cd-120">`reloc`Ia64 命令で64ビット PC 相対アドレスのを生成 `brl.call` します。</span><span class="sxs-lookup"><span data-stu-id="733cd-120">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span></span>|  
|`srRelocAbsoluteTagged`|<span data-ttu-id="733cd-121">`reloc`タグ付きポインター値に使用される、30ビットのセクション相対を生成します。</span><span class="sxs-lookup"><span data-stu-id="733cd-121">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span></span>|  
|`srRelocSentinel`|<span data-ttu-id="733cd-122">この列挙型への追加が内部名配列に反映されるようにするための sentinel 値 `reloc` 。</span><span class="sxs-lookup"><span data-stu-id="733cd-122">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span></span>|  
|`srNoBaseReloc`|<span data-ttu-id="733cd-123">ベースを生成しないことを指定し `reloc` ます。</span><span class="sxs-lookup"><span data-stu-id="733cd-123">Specifies not to emit a base `reloc`.</span></span>|  
|`srRelocPtr`|<span data-ttu-id="733cd-124">メモリの事前修正の内容が、セクションオフセットではなくポインターであることを示す値。</span><span class="sxs-lookup"><span data-stu-id="733cd-124">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="733cd-125">要件</span><span class="sxs-lookup"><span data-stu-id="733cd-125">Requirements</span></span>  

 <span data-ttu-id="733cd-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="733cd-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="733cd-127">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="733cd-127">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="733cd-128">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="733cd-128">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="733cd-129">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="733cd-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="733cd-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="733cd-130">See also</span></span>

- [<span data-ttu-id="733cd-131">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="733cd-131">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="733cd-132">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="733cd-132">ICeeGen Interface</span></span>](iceegen-interface.md)
- [<span data-ttu-id="733cd-133">AddSectionReloc メソッド</span><span class="sxs-lookup"><span data-stu-id="733cd-133">AddSectionReloc Method</span></span>](iceegen-addsectionreloc-method.md)
