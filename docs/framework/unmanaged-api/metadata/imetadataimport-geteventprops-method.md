---
title: IMetaDataImport::GetEventProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type:
- apiref
ms.openlocfilehash: 369335deb67d74ee3cb9fa407533e40716aa3a3a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676864"
---
# <a name="imetadataimportgeteventprops-method"></a><span data-ttu-id="3c136-102">IMetaDataImport::GetEventProps メソッド</span><span class="sxs-lookup"><span data-stu-id="3c136-102">IMetaDataImport::GetEventProps Method</span></span>

<span data-ttu-id="3c136-103">宣言する型、デリゲートの add メソッドおよび remove メソッド、すべてのフラグおよびその他の関連データを含む、指定したイベントトークンによって表されるイベントのメタデータ情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="3c136-103">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c136-104">構文</span><span class="sxs-lookup"><span data-stu-id="3c136-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventProps (  
   [in]  mdEvent       ev,  
   [out] mdTypeDef     *pClass,
   [out] LPCWSTR       szEvent,
   [in]  ULONG         cchEvent,
   [out] ULONG         *pchEvent,
   [out] DWORD         *pdwEventFlags,  
   [out] mdToken       *ptkEventType,  
   [out] mdMethodDef   *pmdAddOn,
   [out] mdMethodDef   *pmdRemoveOn,
   [out] mdMethodDef   *pmdFire,
   [out] mdMethodDef   rmdOtherMethod[],
   [in]  ULONG         cMax,  
   [out] ULONG         *pcOtherMethod  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c136-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3c136-105">Parameters</span></span>  

 `ev`  
 <span data-ttu-id="3c136-106">からメタデータを取得するイベントを表すイベントメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="3c136-106">[in] The event metadata token representing the event to get metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="3c136-107">入出力イベントを宣言するクラスを表す TypeDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3c136-107">[out] A pointer to the TypeDef token representing the class that declares the event.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="3c136-108">入出力によって参照されるイベントの名前 `ev` 。</span><span class="sxs-lookup"><span data-stu-id="3c136-108">[out] The name of the event referenced by `ev`.</span></span>  
  
 `pchEvent`  
 <span data-ttu-id="3c136-109">からのワイド文字で要求された長さ `szEvent` 。</span><span class="sxs-lookup"><span data-stu-id="3c136-109">[in] The requested length in wide characters of `szEvent`.</span></span>  
  
 `pdwEventFlags`  
 <span data-ttu-id="3c136-110">入出力のワイド文字で返された長さ `szEvent` 。</span><span class="sxs-lookup"><span data-stu-id="3c136-110">[out] The returned length in wide characters of `szEvent`.</span></span>  
  
 `ptkEventType`  
 <span data-ttu-id="3c136-111">入出力イベントの種類を表す TypeRef または TypeDef メタデータトークンへのポインター <xref:System.Delegate> 。</span><span class="sxs-lookup"><span data-stu-id="3c136-111">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span></span>  
  
 `pmdAddOn`  
 <span data-ttu-id="3c136-112">入出力イベントのハンドラーを追加するメソッドを表すメタデータトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3c136-112">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span></span>  
  
 `pmdRemoveOn`  
 <span data-ttu-id="3c136-113">入出力イベントのハンドラーを削除するメソッドを表すメタデータトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3c136-113">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span></span>  
  
 `pmdFire`  
 <span data-ttu-id="3c136-114">入出力イベントを発生させるメソッドを表すメタデータトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3c136-114">[out] A pointer to the metadata token representing the method that raises the event.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="3c136-115">入出力イベントに関連付けられている他のメソッドへのトークンポインターの配列。</span><span class="sxs-lookup"><span data-stu-id="3c136-115">[out] An array of token pointers to other methods associated with the event.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3c136-116">[in] `rmdOtherMethod` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="3c136-116">[in] The maximum size of the `rmdOtherMethod` array.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="3c136-117">入出力で返されたトークンの数 `rmdOtherMethod` 。</span><span class="sxs-lookup"><span data-stu-id="3c136-117">[out] The number of tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c136-118">要件</span><span class="sxs-lookup"><span data-stu-id="3c136-118">Requirements</span></span>  

 <span data-ttu-id="3c136-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c136-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c136-120">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="3c136-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3c136-121">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="3c136-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3c136-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c136-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c136-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c136-123">See also</span></span>

- [<span data-ttu-id="3c136-124">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3c136-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="3c136-125">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3c136-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
