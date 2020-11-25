---
title: IMapToken::Map メソッド
ms.date: 03/30/2017
api_name:
- IMapToken.Map
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMapToken::Map
helpviewer_keywords:
- IMapToken::Map method [.NET Framework metadata]
- Map method [.NET Framework metadata]
ms.assetid: b9b4bf2f-1098-43d6-9619-a99b4bda1940
topic_type:
- apiref
ms.openlocfilehash: 51cca1ab61027090b0d22781dfd740038bc9372d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718203"
---
# <a name="imaptokenmap-method"></a><span data-ttu-id="cdc66-102">IMapToken::Map メソッド</span><span class="sxs-lookup"><span data-stu-id="cdc66-102">IMapToken::Map Method</span></span>

<span data-ttu-id="cdc66-103">メタデータシグネチャを使用して、アセンブリ間のリレーションシップをマップします。</span><span class="sxs-lookup"><span data-stu-id="cdc66-103">Maps a relationship between the assemblies using metadata signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdc66-104">構文</span><span class="sxs-lookup"><span data-stu-id="cdc66-104">Syntax</span></span>  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cdc66-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cdc66-105">Parameters</span></span>  

 `tkImp`  
 <span data-ttu-id="cdc66-106">からインポートされたコードオブジェクトを表すメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="cdc66-106">[in] The metadata token that represents the imported code object.</span></span>  
  
 `tkEmit`  
 <span data-ttu-id="cdc66-107">から出力されたコードオブジェクトを表すメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="cdc66-107">[in] The metadata token that represents the emitted code object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cdc66-108">注釈</span><span class="sxs-lookup"><span data-stu-id="cdc66-108">Remarks</span></span>  

 <span data-ttu-id="cdc66-109">マージ中にトークンの再マップが行われると、元のトークンはインポートされた (ソース) メタデータスコープ内でスコープが設定され、新しいトークンのスコープは、出力された (ターゲット) メタデータスコープに設定されます。</span><span class="sxs-lookup"><span data-stu-id="cdc66-109">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdc66-110">要件</span><span class="sxs-lookup"><span data-stu-id="cdc66-110">Requirements</span></span>  

 <span data-ttu-id="cdc66-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cdc66-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdc66-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="cdc66-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cdc66-113">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="cdc66-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cdc66-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdc66-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdc66-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="cdc66-115">See also</span></span>

- [<span data-ttu-id="cdc66-116">IMapToken インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cdc66-116">IMapToken Interface</span></span>](imaptoken-interface.md)
