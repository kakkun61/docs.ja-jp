---
title: ICorDebugILFrame2::EnumerateTypeParameters メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugILFrame2 interface [.NET Framework debugging]
- ICorDebugILFrame2::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 722d0d74-e0df-491f-98c4-62d501dfaf6f
topic_type:
- apiref
ms.openlocfilehash: 73c17864047270302dbc115667eec4bf5ea1569d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725046"
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a><span data-ttu-id="b61d0-102">ICorDebugILFrame2::EnumerateTypeParameters メソッド</span><span class="sxs-lookup"><span data-stu-id="b61d0-102">ICorDebugILFrame2::EnumerateTypeParameters Method</span></span>

<span data-ttu-id="b61d0-103">このフレームのパラメーターを格納している、テキスト型の型の列挙体オブジェクトを取得し <xref:System.Type> ます。</span><span class="sxs-lookup"><span data-stu-id="b61d0-103">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b61d0-104">構文</span><span class="sxs-lookup"><span data-stu-id="b61d0-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b61d0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b61d0-105">Parameters</span></span>  

 `ppTyParEnum`  
 <span data-ttu-id="b61d0-106">型パラメーターの列挙を可能にする、テキスト型のインターフェイスオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b61d0-106">A pointer to the address of a ICorDebugTypeEnum interface object that allows enumeration of type parameters.</span></span>  
  
 <span data-ttu-id="b61d0-107">型パラメーターの一覧には、クラス型パラメーター (存在する場合) と、その後にメソッド型パラメーター (存在する場合) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b61d0-107">The list of type parameters include the class type parameters (if any) followed by the method type parameters (if any).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b61d0-108">注釈</span><span class="sxs-lookup"><span data-stu-id="b61d0-108">Remarks</span></span>  

 <span data-ttu-id="b61d0-109">[IMetaDataImport2:: EnumGenericParams](../metadata/imetadataimport2-enumgenericparams-method.md)メソッドを使用して、このリストに含まれるクラス型パラメーターとメソッド型パラメーターの数を確認します。</span><span class="sxs-lookup"><span data-stu-id="b61d0-109">Use the [IMetaDataImport2::EnumGenericParams](../metadata/imetadataimport2-enumgenericparams-method.md) method to determine how many class type parameters and method type parameters this list contains.</span></span>  
  
 <span data-ttu-id="b61d0-110">型パラメーターは常に使用できるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="b61d0-110">The type parameters are not always available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b61d0-111">要件</span><span class="sxs-lookup"><span data-stu-id="b61d0-111">Requirements</span></span>  

 <span data-ttu-id="b61d0-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b61d0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b61d0-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b61d0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b61d0-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b61d0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b61d0-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b61d0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
