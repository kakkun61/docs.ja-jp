---
title: ICLRDataTarget::GetImageBase メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetImageBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetImageBase
helpviewer_keywords:
- ICLRDataTarget::GetImageBase method [.NET Framework debugging]
- GetImageBase method [.NET Framework debugging]
ms.assetid: 091c5f32-c160-49e3-a75f-4692e084c8e4
topic_type:
- apiref
ms.openlocfilehash: f1b9f55a383f1deb867c6b3e2fa385a82158d1e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703578"
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="6fb25-102">ICLRDataTarget::GetImageBase メソッド</span><span class="sxs-lookup"><span data-stu-id="6fb25-102">ICLRDataTarget::GetImageBase Method</span></span>

<span data-ttu-id="6fb25-103">指定したイメージのベースメモリアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="6fb25-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fb25-104">構文</span><span class="sxs-lookup"><span data-stu-id="6fb25-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6fb25-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6fb25-105">Parameters</span></span>  

 `imagePath`  
 <span data-ttu-id="6fb25-106">からパスを含む、イメージのファイル名。</span><span class="sxs-lookup"><span data-stu-id="6fb25-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="6fb25-107">入出力イメージのベースアドレスを格納する CLRDATA_ADDRESS へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6fb25-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6fb25-108">注釈</span><span class="sxs-lookup"><span data-stu-id="6fb25-108">Remarks</span></span>  

 <span data-ttu-id="6fb25-109">イメージファイル名には、パスを指定することも、パスを指定することもできません。</span><span class="sxs-lookup"><span data-stu-id="6fb25-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="6fb25-110">パスが指定されている場合、パス全体で一致が行われます。それ以外の場合、一致はファイル名でのみ実行されます。</span><span class="sxs-lookup"><span data-stu-id="6fb25-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fb25-111">要件</span><span class="sxs-lookup"><span data-stu-id="6fb25-111">Requirements</span></span>  

 <span data-ttu-id="6fb25-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6fb25-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fb25-113">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="6fb25-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="6fb25-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6fb25-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fb25-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fb25-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fb25-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="6fb25-116">See also</span></span>

- [<span data-ttu-id="6fb25-117">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6fb25-117">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
