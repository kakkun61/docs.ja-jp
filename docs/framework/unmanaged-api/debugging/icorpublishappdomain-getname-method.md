---
title: ICorPublishAppDomain::GetName メソッド
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetName
helpviewer_keywords:
- GetName method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetName method [.NET Framework debugging]
ms.assetid: 6ef8ac9b-9803-4b65-8b13-25f3e0b1bc6b
topic_type:
- apiref
ms.openlocfilehash: d6b05333b9e02c4202c0fd9bdee9b5c055aa4da3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95694361"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="05b0c-102">ICorPublishAppDomain::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="05b0c-102">ICorPublishAppDomain::GetName Method</span></span>

<span data-ttu-id="05b0c-103">この [ICorPublishAppDomain](icorpublishappdomain-interface.md)によって表されるアプリケーションドメインの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="05b0c-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05b0c-104">構文</span><span class="sxs-lookup"><span data-stu-id="05b0c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05b0c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="05b0c-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="05b0c-106">[in] `szName` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="05b0c-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="05b0c-107">入出力配列に返された、null 文字を含むワイド文字の数へのポインター `szName` 。</span><span class="sxs-lookup"><span data-stu-id="05b0c-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="05b0c-108">入出力名前を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="05b0c-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05b0c-109">注釈</span><span class="sxs-lookup"><span data-stu-id="05b0c-109">Remarks</span></span>  

 <span data-ttu-id="05b0c-110">`szName`が null 以外の場合、 `GetName` メソッドは最大 `cchName` 文字 (null ターミネータを含む) をにコピー `szName` します。</span><span class="sxs-lookup"><span data-stu-id="05b0c-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="05b0c-111">で null 以外の値が返された場合 `pcchName` 、名前の実際の文字数 (null ターミネータを含む) が配列に格納され `szName` ます。</span><span class="sxs-lookup"><span data-stu-id="05b0c-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="05b0c-112">メソッドは、 `GetName` コピーされた文字数に関係なく、S_OK HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="05b0c-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05b0c-113">要件</span><span class="sxs-lookup"><span data-stu-id="05b0c-113">Requirements</span></span>  

 <span data-ttu-id="05b0c-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05b0c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05b0c-115">**ヘッダー:** CorPub .idl、CorPub .h</span><span class="sxs-lookup"><span data-stu-id="05b0c-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="05b0c-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05b0c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05b0c-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05b0c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05b0c-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="05b0c-118">See also</span></span>

- [<span data-ttu-id="05b0c-119">ICorPublishAppDomain インターフェイス</span><span class="sxs-lookup"><span data-stu-id="05b0c-119">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)
