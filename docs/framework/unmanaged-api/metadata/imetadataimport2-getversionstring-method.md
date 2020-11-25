---
title: IMetaDataImport2::GetVersionString メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type:
- apiref
ms.openlocfilehash: 3e62b1177c0161883ad03086723cc43b71292df5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702564"
---
# <a name="imetadataimport2getversionstring-method"></a><span data-ttu-id="0343d-102">IMetaDataImport2::GetVersionString メソッド</span><span class="sxs-lookup"><span data-stu-id="0343d-102">IMetaDataImport2::GetVersionString Method</span></span>

<span data-ttu-id="0343d-103">アセンブリのビルドに使用されたランタイムのバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="0343d-103">Gets the version number of the runtime that was used to build the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0343d-104">構文</span><span class="sxs-lookup"><span data-stu-id="0343d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0343d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0343d-105">Parameters</span></span>  

 `pwzBuf`  
 <span data-ttu-id="0343d-106">入出力バージョンを指定する文字列を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="0343d-106">[out] An array to store the string that specifies the version.</span></span>  
  
 `ccBufSize`  
 <span data-ttu-id="0343d-107">から配列のサイズ (ワイド文字単位) `pwzBuf` 。</span><span class="sxs-lookup"><span data-stu-id="0343d-107">[in] The size, in wide characters, of the `pwzBuf` array.</span></span>  
  
 `pccBufSize`  
 <span data-ttu-id="0343d-108">入出力配列内で返された、null 終端文字を含むワイド文字の数 `pwzBuf` 。</span><span class="sxs-lookup"><span data-stu-id="0343d-108">[out] The number of wide characters, including a null terminator, returned in the `pwzBuf` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0343d-109">注釈</span><span class="sxs-lookup"><span data-stu-id="0343d-109">Remarks</span></span>  

 <span data-ttu-id="0343d-110">メソッドは、 `GetVersionString` 現在のメタデータスコープの組み込みバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="0343d-110">The `GetVersionString` method gets the built-for version of the current metadata scope.</span></span> <span data-ttu-id="0343d-111">スコープが一度も保存されていない場合は、ビルドされたバージョンがないため、空の文字列が返されます。</span><span class="sxs-lookup"><span data-stu-id="0343d-111">If the scope has never been saved, it will not have a built-for version, and an empty string will be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0343d-112">要件</span><span class="sxs-lookup"><span data-stu-id="0343d-112">Requirements</span></span>  

 <span data-ttu-id="0343d-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0343d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0343d-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="0343d-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0343d-115">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="0343d-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0343d-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0343d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0343d-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="0343d-117">See also</span></span>

- [<span data-ttu-id="0343d-118">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0343d-118">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="0343d-119">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0343d-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
