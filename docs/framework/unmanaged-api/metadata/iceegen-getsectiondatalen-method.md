---
title: ICeeGen::GetSectionDataLen メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionDataLen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionDataLen
helpviewer_keywords:
- ICeeGen::GetSectionDataLen method [.NET Framework metadata]
- GetSectionDataLen method [.NET Framework metadata]
ms.assetid: e2a06ee4-b8ee-49c7-935a-c1031a29eef2
topic_type:
- apiref
ms.openlocfilehash: b45b0a59a29a27e7b0a395f3928215959450f9a5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698469"
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="7c975-102">ICeeGen::GetSectionDataLen メソッド</span><span class="sxs-lookup"><span data-stu-id="7c975-102">ICeeGen::GetSectionDataLen Method</span></span>

<span data-ttu-id="7c975-103">指定したセクションの長さを取得します。</span><span class="sxs-lookup"><span data-stu-id="7c975-103">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="7c975-104">このメソッドは互換性のために残されています。使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="7c975-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c975-105">構文</span><span class="sxs-lookup"><span data-stu-id="7c975-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c975-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7c975-106">Parameters</span></span>  

 `section`  
 <span data-ttu-id="7c975-107">から長さを取得するデータセクション。</span><span class="sxs-lookup"><span data-stu-id="7c975-107">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="7c975-108">入出力指定したセクションの返された長さ。</span><span class="sxs-lookup"><span data-stu-id="7c975-108">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c975-109">注釈</span><span class="sxs-lookup"><span data-stu-id="7c975-109">Remarks</span></span>  

 <span data-ttu-id="7c975-110">`GetSectionDataLen`他のメソッドによって処理されない特殊なセクション要件がある場合にのみ、を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7c975-110">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c975-111">要件</span><span class="sxs-lookup"><span data-stu-id="7c975-111">Requirements</span></span>  

 <span data-ttu-id="7c975-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7c975-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c975-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="7c975-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7c975-114">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="7c975-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7c975-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c975-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c975-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="7c975-116">See also</span></span>

- [<span data-ttu-id="7c975-117">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7c975-117">ICeeGen Interface</span></span>](iceegen-interface.md)
