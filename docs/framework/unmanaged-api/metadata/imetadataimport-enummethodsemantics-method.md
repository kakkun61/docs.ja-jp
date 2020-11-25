---
title: IMetaDataImport::EnumMethodSemantics メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodSemantics
helpviewer_keywords:
- EnumMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::EnumMethodSemantics method [.NET Framework metadata]
ms.assetid: e7e3c630-9691-46d6-94df-b5593a7bb08a
topic_type:
- apiref
ms.openlocfilehash: 3d14aea92633c944d21d867c8152767ae6f1f291
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720972"
---
# <a name="imetadataimportenummethodsemantics-method"></a><span data-ttu-id="0d8cd-102">IMetaDataImport::EnumMethodSemantics メソッド</span><span class="sxs-lookup"><span data-stu-id="0d8cd-102">IMetaDataImport::EnumMethodSemantics Method</span></span>

<span data-ttu-id="0d8cd-103">指定したメソッドが関連付けられているプロパティおよびプロパティ変更イベントを列挙します。</span><span class="sxs-lookup"><span data-stu-id="0d8cd-103">Enumerates the properties and the property-change events to which the specified method is related.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d8cd-104">構文</span><span class="sxs-lookup"><span data-stu-id="0d8cd-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d8cd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0d8cd-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="0d8cd-106">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="0d8cd-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="0d8cd-107">このメソッドの最初の呼び出しでは、この値は NULL である必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d8cd-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="0d8cd-108">から列挙型のスコープを制限する MethodDef トークン。</span><span class="sxs-lookup"><span data-stu-id="0d8cd-108">[in] A MethodDef token that limits the scope of the enumeration.</span></span>  
  
 `rEventProp`  
 <span data-ttu-id="0d8cd-109">入出力イベントまたはプロパティを格納するために使用される配列。</span><span class="sxs-lookup"><span data-stu-id="0d8cd-109">[out] The array used to store the events or properties.</span></span>  
  
 `cMax`  
 <span data-ttu-id="0d8cd-110">[in] `rEventProp` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="0d8cd-110">[in] The maximum size of the `rEventProp` array.</span></span>  
  
 `pcEventProp`  
 <span data-ttu-id="0d8cd-111">入出力で返されたイベントまたはプロパティの数 `rEventProp` 。</span><span class="sxs-lookup"><span data-stu-id="0d8cd-111">[out] The number of events or properties returned in `rEventProp`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d8cd-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="0d8cd-112">Return Value</span></span>  
  
|<span data-ttu-id="0d8cd-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0d8cd-113">HRESULT</span></span>|<span data-ttu-id="0d8cd-114">説明</span><span class="sxs-lookup"><span data-stu-id="0d8cd-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="0d8cd-115">`EnumMethodSemantics` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="0d8cd-115">`EnumMethodSemantics` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="0d8cd-116">列挙するイベントやプロパティはありません。</span><span class="sxs-lookup"><span data-stu-id="0d8cd-116">There are no events or properties to enumerate.</span></span> <span data-ttu-id="0d8cd-117">この場合、 `pcEventProp` は0になります。</span><span class="sxs-lookup"><span data-stu-id="0d8cd-117">In that case, `pcEventProp` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d8cd-118">注釈</span><span class="sxs-lookup"><span data-stu-id="0d8cd-118">Remarks</span></span>  

 <span data-ttu-id="0d8cd-119">多くの共通言語ランタイム型 *Property* `Changed` では、プロパティイベントとプロパティ `On` *Property* `Changed` に関連するプロパティメソッドが定義されています。</span><span class="sxs-lookup"><span data-stu-id="0d8cd-119">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span></span> <span data-ttu-id="0d8cd-120">たとえば、型は、 <xref:System.Windows.Forms.Control?displayProperty=nameWithType> <xref:System.Windows.Forms.Control.Font%2A> プロパティ、 <xref:System.Windows.Forms.Control.FontChanged> イベント、およびメソッドを定義し <xref:System.Windows.Forms.Control.OnFontChanged%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="0d8cd-120">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span></span> <span data-ttu-id="0d8cd-121">プロパティの set アクセサーメソッドは、メソッドを呼び出します。このメソッドは、 <xref:System.Windows.Forms.Control.Font%2A> イベントを発生さ <xref:System.Windows.Forms.Control.OnFontChanged%2A> せ <xref:System.Windows.Forms.Control.FontChanged> ます。</span><span class="sxs-lookup"><span data-stu-id="0d8cd-121">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span> <span data-ttu-id="0d8cd-122">`EnumMethodSemantics` <xref:System.Windows.Forms.Control.OnFontChanged%2A> プロパティとイベントへの参照を取得するには、の MethodDef を使用してを呼び出し <xref:System.Windows.Forms.Control.Font%2A> <xref:System.Windows.Forms.Control.FontChanged> ます。</span><span class="sxs-lookup"><span data-stu-id="0d8cd-122">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d8cd-123">要件</span><span class="sxs-lookup"><span data-stu-id="0d8cd-123">Requirements</span></span>  

 <span data-ttu-id="0d8cd-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d8cd-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d8cd-125">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="0d8cd-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0d8cd-126">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="0d8cd-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0d8cd-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d8cd-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d8cd-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="0d8cd-128">See also</span></span>

- [<span data-ttu-id="0d8cd-129">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0d8cd-129">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="0d8cd-130">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0d8cd-130">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
