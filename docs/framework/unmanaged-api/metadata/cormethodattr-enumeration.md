---
title: CorMethodAttr 列挙型
ms.date: 03/30/2017
api_name:
- CorMethodAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodAttr
helpviewer_keywords:
- CorMethodAttr enumeration [.NET Framework metadata]
ms.assetid: 4e0c3521-e54d-43c1-9857-cc76b49b8ffc
topic_type:
- apiref
ms.openlocfilehash: 6c3e721c24da217eaf2e8857377359e1c51b7b59
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677025"
---
# <a name="cormethodattr-enumeration"></a><span data-ttu-id="7aab9-102">CorMethodAttr 列挙型</span><span class="sxs-lookup"><span data-stu-id="7aab9-102">CorMethodAttr Enumeration</span></span>

<span data-ttu-id="7aab9-103">メソッドの機能を記述する値を格納します。</span><span class="sxs-lookup"><span data-stu-id="7aab9-103">Contains values that describe the features of a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7aab9-104">構文</span><span class="sxs-lookup"><span data-stu-id="7aab9-104">Syntax</span></span>  
  
```cpp  
typedef enum CorMethodAttr {  
  
    mdMemberAccessMask          =   0x0007,  
    mdPrivateScope              =   0x0000,  
    mdPrivate                   =   0x0001,  
    mdFamANDAssem               =   0x0002,  
    mdAssem                     =   0x0003,  
    mdFamily                    =   0x0004,  
    mdFamORAssem                =   0x0005,  
    mdPublic                    =   0x0006,  
  
    mdStatic                    =   0x0010,  
    mdFinal                     =   0x0020,  
    mdVirtual                   =   0x0040,  
    mdHideBySig                 =   0x0080,  
  
    mdVtableLayoutMask          =   0x0100,  
    mdReuseSlot                 =   0x0000,  
    mdNewSlot                   =   0x0100,  
  
    mdCheckAccessOnOverride     =   0x0200,  
    mdAbstract                  =   0x0400,  
    mdSpecialName               =   0x0800,  
  
    mdPinvokeImpl               =   0x2000,  
    mdUnmanagedExport           =   0x0008,  
  
    mdReservedMask              =   0xd000,  
    mdRTSpecialName             =   0x1000,  
    mdHasSecurity               =   0x4000,  
    mdRequireSecObject          =   0x8000,  
  
} CorMethodAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="7aab9-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="7aab9-105">Members</span></span>  
  
|<span data-ttu-id="7aab9-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="7aab9-106">Member</span></span>|<span data-ttu-id="7aab9-107">説明</span><span class="sxs-lookup"><span data-stu-id="7aab9-107">Description</span></span>|  
|------------|-----------------|  
|`mdMemberAccessMask`|<span data-ttu-id="7aab9-108">メンバーアクセスを指定します。</span><span class="sxs-lookup"><span data-stu-id="7aab9-108">Specifies member access.</span></span>|  
|`mdPrivateScope`|<span data-ttu-id="7aab9-109">メンバーを参照できないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="7aab9-109">Specifies that the member cannot be referenced.</span></span>|  
|`mdPrivate`|<span data-ttu-id="7aab9-110">メンバーが親の型によってのみアクセス可能であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="7aab9-110">Specifies that the member is accessible only by the parent type.</span></span>|  
|`mdFamANDAssem`|<span data-ttu-id="7aab9-111">このアセンブリ内のサブタイプだけがメンバーにアクセスできることを指定します。</span><span class="sxs-lookup"><span data-stu-id="7aab9-111">Specifies that the member is accessible by subtypes only in this assembly.</span></span>|  
|`mdAssem`|<span data-ttu-id="7aab9-112">メンバーがアセンブリ内のすべてのユーザーによって accessibly されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="7aab9-112">Specifies that the member is accessibly by anyone in the assembly.</span></span>|  
|`mdFamily`|<span data-ttu-id="7aab9-113">メンバーが型とサブタイプによってのみアクセス可能であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="7aab9-113">Specifies that the member is accessible only by type and subtypes.</span></span>|  
|`mdFamORAssem`|<span data-ttu-id="7aab9-114">メンバーが、派生クラスおよびそのアセンブリ内の他の型によってアクセス可能であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="7aab9-114">Specifies that the member is accessible by derived classes and by other types in its assembly.</span></span>|  
|`mdPublic`|<span data-ttu-id="7aab9-115">スコープへのアクセス権を持つすべての型からメンバーにアクセスできることを指定します。</span><span class="sxs-lookup"><span data-stu-id="7aab9-115">Specifies that the member is accessible by all types with access to the scope.</span></span>|  
|`mdStatic`|<span data-ttu-id="7aab9-116">メンバーがインスタンスのメンバーとしてではなく、型の一部として定義されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="7aab9-116">Specifies that the member is defined as part of the type rather than as a member of an instance.</span></span>|  
|`mdFinal`|<span data-ttu-id="7aab9-117">メソッドをオーバーライドできないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="7aab9-117">Specifies that the method cannot be overridden.</span></span>|  
|`mdVirtual`|<span data-ttu-id="7aab9-118">メソッドをオーバーライドできることを指定します。</span><span class="sxs-lookup"><span data-stu-id="7aab9-118">Specifies that the method can be overridden.</span></span>|  
|`mdHideBySig`|<span data-ttu-id="7aab9-119">メソッドが名前だけではなく、名前とシグネチャで非表示になるように指定します。</span><span class="sxs-lookup"><span data-stu-id="7aab9-119">Specifies that the method hides by name and signature, rather than just by name.</span></span>|  
|`mdVtableLayoutMask`|<span data-ttu-id="7aab9-120">仮想テーブルのレイアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="7aab9-120">Specifies virtual table layout.</span></span>|  
|`mdReuseSlot`|<span data-ttu-id="7aab9-121">仮想テーブルでこのメソッドに使用されるスロットを再利用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="7aab9-121">Specifies that the slot used for this method in the virtual table be reused.</span></span> <span data-ttu-id="7aab9-122">これは既定値です。</span><span class="sxs-lookup"><span data-stu-id="7aab9-122">This is the default.</span></span>|  
|`mdNewSlot`|<span data-ttu-id="7aab9-123">メソッドが常に仮想テーブル内の新しいスロットを取得することを指定します。</span><span class="sxs-lookup"><span data-stu-id="7aab9-123">Specifies that the method always gets a new slot in the virtual table.</span></span>|  
|`mdCheckAccessOnOverride`|<span data-ttu-id="7aab9-124">メソッドを、表示されているのと同じ型でオーバーライドできることを指定します。</span><span class="sxs-lookup"><span data-stu-id="7aab9-124">Specifies that the method can be overridden by the same types to which it is visible.</span></span>|  
|`mdAbstract`|<span data-ttu-id="7aab9-125">メソッドが実装されていないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="7aab9-125">Specifies that the method is not implemented.</span></span>|  
|`mdSpecialName`|<span data-ttu-id="7aab9-126">メソッドが特別であり、その名前がどのように説明するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="7aab9-126">Specifies that the method is special, and that its name describes how.</span></span>|  
|`mdPinvokeImpl`|<span data-ttu-id="7aab9-127">メソッドの実装が PInvoke を使用して転送されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="7aab9-127">Specifies that the method implementation is forwarded using PInvoke.</span></span>|  
|`mdUnmanagedExport`|<span data-ttu-id="7aab9-128">メソッドがアンマネージコードにエクスポートされたマネージメソッドであることを指定します。</span><span class="sxs-lookup"><span data-stu-id="7aab9-128">Specifies that the method is a managed method exported to unmanaged code.</span></span>|  
|`mdReservedMask`|<span data-ttu-id="7aab9-129">共通言語ランタイムによる内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="7aab9-129">Reserved for internal use by the common language runtime.</span></span>|  
|`mdRTSpecialName`|<span data-ttu-id="7aab9-130">共通言語ランタイムがメソッド名のエンコーディングを確認する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="7aab9-130">Specifies that the common language runtime should check the encoding of the method name.</span></span>|  
|`mdHasSecurity`|<span data-ttu-id="7aab9-131">メソッドにセキュリティが関連付けられていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="7aab9-131">Specifies that the method has security associated with it.</span></span>|  
|`mdRequireSecObject`|<span data-ttu-id="7aab9-132">メソッドが、セキュリティコードを含む別のメソッドを呼び出すことを指定します。</span><span class="sxs-lookup"><span data-stu-id="7aab9-132">Specifies that the method calls another method containing security code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7aab9-133">要件</span><span class="sxs-lookup"><span data-stu-id="7aab9-133">Requirements</span></span>  

 <span data-ttu-id="7aab9-134">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7aab9-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7aab9-135">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="7aab9-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="7aab9-136">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7aab9-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aab9-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="7aab9-137">See also</span></span>

- [<span data-ttu-id="7aab9-138">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="7aab9-138">Metadata Enumerations</span></span>](metadata-enumerations.md)
