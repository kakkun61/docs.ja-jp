---
title: ICeeGen::GetSectionCreate メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionCreate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionCreate
helpviewer_keywords:
- ICeeGen::GetSectionCreate method [.NET Framework metadata]
- GetSectionCreate method [.NET Framework metadata]
ms.assetid: 154b2460-59ce-4874-a9f2-1b3353486ac5
topic_type:
- apiref
ms.openlocfilehash: 4ef3992d840f539ca07c411c2d740fa32b14edbc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722948"
---
# <a name="iceegengetsectioncreate-method"></a><span data-ttu-id="718c1-102">ICeeGen::GetSectionCreate メソッド</span><span class="sxs-lookup"><span data-stu-id="718c1-102">ICeeGen::GetSectionCreate Method</span></span>

<span data-ttu-id="718c1-103">指定された名前とフラグ値を使用して、コードセクションを生成して取得します。</span><span class="sxs-lookup"><span data-stu-id="718c1-103">Generates and gets a code section using the specified name and flag values.</span></span>  
  
 <span data-ttu-id="718c1-104">このメソッドは互換性のために残されています。使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="718c1-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="718c1-105">構文</span><span class="sxs-lookup"><span data-stu-id="718c1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="718c1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="718c1-106">Parameters</span></span>  

 `name`  
 <span data-ttu-id="718c1-107">から作成するセクションの名前を指定する文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="718c1-107">[in] A pointer to a string that specifies the name of the section to be created.</span></span>  
  
 `flags`  
 <span data-ttu-id="718c1-108">からオプションを指定するフラグ。</span><span class="sxs-lookup"><span data-stu-id="718c1-108">[in] Flags that specify options.</span></span>  
  
 `section`  
 <span data-ttu-id="718c1-109">入出力新しく作成されたコードセクションへのポインター。</span><span class="sxs-lookup"><span data-stu-id="718c1-109">[out] A pointer to the newly created code section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="718c1-110">注釈</span><span class="sxs-lookup"><span data-stu-id="718c1-110">Remarks</span></span>  

 <span data-ttu-id="718c1-111">`GetSectionCreate`他のメソッドによって処理されない特殊なセクション要件がある場合にのみ、を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="718c1-111">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="718c1-112">要件</span><span class="sxs-lookup"><span data-stu-id="718c1-112">Requirements</span></span>  

 <span data-ttu-id="718c1-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="718c1-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="718c1-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="718c1-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="718c1-115">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="718c1-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="718c1-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="718c1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="718c1-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="718c1-117">See also</span></span>

- [<span data-ttu-id="718c1-118">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="718c1-118">ICeeGen Interface</span></span>](iceegen-interface.md)
