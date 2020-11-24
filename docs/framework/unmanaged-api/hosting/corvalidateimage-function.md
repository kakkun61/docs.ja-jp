---
title: _CorValidateImage 関数
ms.date: 03/30/2017
api_name:
- _CorValidateImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorValidateImage
helpviewer_keywords:
- _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type:
- apiref
ms.openlocfilehash: 2d49a40610bd0e1a7629594e245bde9eacfcc06d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687978"
---
# <a name="_corvalidateimage-function"></a><span data-ttu-id="c00be-102">_CorValidateImage 関数</span><span class="sxs-lookup"><span data-stu-id="c00be-102">_CorValidateImage Function</span></span>

<span data-ttu-id="c00be-103">マネージド モジュール イメージを検証し、それらが読み込まれると、オペレーティング システム ローダーに通知します。</span><span class="sxs-lookup"><span data-stu-id="c00be-103">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c00be-104">構文</span><span class="sxs-lookup"><span data-stu-id="c00be-104">Syntax</span></span>  
  
```cpp  
STDAPI _CorValidateImage (
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c00be-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c00be-105">Parameters</span></span>  

 `ImageBase`  
 <span data-ttu-id="c00be-106">からマネージコードとして検証するイメージの開始位置へのポインター。</span><span class="sxs-lookup"><span data-stu-id="c00be-106">[in] A pointer to the starting location of the image to validate as managed code.</span></span> <span data-ttu-id="c00be-107">イメージは既にメモリに読み込まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c00be-107">The image must already be loaded into memory.</span></span>  
  
 `FileName`  
 <span data-ttu-id="c00be-108">からイメージのファイル名。</span><span class="sxs-lookup"><span data-stu-id="c00be-108">[in] The file name of the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c00be-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="c00be-109">Return Value</span></span>  

 <span data-ttu-id="c00be-110">この関数は、標準値、、 `E_INVALIDARG` `E_OUTOFMEMORY` 、およびを返し `E_UNEXPECTED` `E_FAIL` ます。次の値も返されます。</span><span class="sxs-lookup"><span data-stu-id="c00be-110">This function returns the standard values `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, and `E_FAIL`, as well as the following values.</span></span>  
  
|<span data-ttu-id="c00be-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="c00be-111">Return value</span></span>|<span data-ttu-id="c00be-112">説明</span><span class="sxs-lookup"><span data-stu-id="c00be-112">Description</span></span>|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|<span data-ttu-id="c00be-113">イメージが無効です。</span><span class="sxs-lookup"><span data-stu-id="c00be-113">The image is invalid.</span></span> <span data-ttu-id="c00be-114">この値には HRESULT 0xC000007BL があります。</span><span class="sxs-lookup"><span data-stu-id="c00be-114">This value has the HRESULT 0xC000007BL.</span></span>|  
|`STATUS_SUCCESS`|<span data-ttu-id="c00be-115">イメージは有効です。</span><span class="sxs-lookup"><span data-stu-id="c00be-115">The image is valid.</span></span> <span data-ttu-id="c00be-116">この値には、HRESULT 0x00000000L が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c00be-116">This value has the HRESULT 0x00000000L.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c00be-117">注釈</span><span class="sxs-lookup"><span data-stu-id="c00be-117">Remarks</span></span>  

 <span data-ttu-id="c00be-118">Windows XP 以降のバージョンでは、オペレーティングシステムローダーは、Common Object File Format (COFF) ヘッダーの COM 記述子ディレクトリビットを調べて、マネージモジュールをチェックします。</span><span class="sxs-lookup"><span data-stu-id="c00be-118">In Windows XP and later versions, the operating system loader checks for managed modules by examining the COM Descriptor Directory bit in the common object file format (COFF) header.</span></span> <span data-ttu-id="c00be-119">セットビットはマネージモジュールを示します。</span><span class="sxs-lookup"><span data-stu-id="c00be-119">A set bit indicates a managed module.</span></span> <span data-ttu-id="c00be-120">ローダーがマネージモジュールを検出すると、MsCorEE.dll を読み込み、 `_CorValidateImage` を呼び出します。これにより、次のアクションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="c00be-120">If the loader detects a managed module, it loads MsCorEE.dll and calls `_CorValidateImage`, which performs the following actions:</span></span>  
  
- <span data-ttu-id="c00be-121">イメージが有効なマネージモジュールであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c00be-121">Confirms that the image is a valid managed module.</span></span>  
  
- <span data-ttu-id="c00be-122">イメージのエントリポイントを共通言語ランタイム (CLR) のエントリポイントに変更します。</span><span class="sxs-lookup"><span data-stu-id="c00be-122">Changes the entry point in the image to an entry point in the common language runtime (CLR).</span></span>  
  
- <span data-ttu-id="c00be-123">Windows の64ビットバージョンでは、PE32 から PE32 + 形式に変換することによって、メモリ内のイメージを変更します。</span><span class="sxs-lookup"><span data-stu-id="c00be-123">For 64-bit versions of Windows, modifies the image that is in memory by transforming it from PE32 to PE32+ format.</span></span>  
  
- <span data-ttu-id="c00be-124">マネージモジュールイメージが読み込まれると、ローダーに戻ります。</span><span class="sxs-lookup"><span data-stu-id="c00be-124">Returns to the loader when the managed module images are loaded.</span></span>  
  
 <span data-ttu-id="c00be-125">実行可能イメージの場合、オペレーティングシステムローダーは、実行可能ファイルで指定されたエントリポイントに関係なく、 [_CorExeMain](corexemain-function.md) 関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c00be-125">For executable images, the operating system loader then calls the [_CorExeMain](corexemain-function.md) function, regardless of the entry point specified in the executable.</span></span> <span data-ttu-id="c00be-126">DLL アセンブリイメージの場合、ローダーは [_CorDllMain](cordllmain-function.md) 関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c00be-126">For DLL assembly images, the loader calls the [_CorDllMain](cordllmain-function.md) function.</span></span>  
  
 <span data-ttu-id="c00be-127">`_CorExeMain` またはは `_CorDllMain` 、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="c00be-127">`_CorExeMain` or `_CorDllMain` performs the following actions:</span></span>  
  
- <span data-ttu-id="c00be-128">CLR を初期化します。</span><span class="sxs-lookup"><span data-stu-id="c00be-128">Initializes the CLR.</span></span>  
  
- <span data-ttu-id="c00be-129">アセンブリの CLR ヘッダーからマネージエントリポイントを検索します。</span><span class="sxs-lookup"><span data-stu-id="c00be-129">Locates the managed entry point from the assembly's CLR header.</span></span>  
  
- <span data-ttu-id="c00be-130">実行を開始します。</span><span class="sxs-lookup"><span data-stu-id="c00be-130">Begins execution.</span></span>  
  
 <span data-ttu-id="c00be-131">ローダーは、マネージモジュールイメージがアンロードされるときに [_CorImageUnloading](corimageunloading-function.md) 関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c00be-131">The loader calls the [_CorImageUnloading](corimageunloading-function.md) function when managed module images are unloaded.</span></span> <span data-ttu-id="c00be-132">ただし、この関数は何のアクションも実行しません。これはだけを返します。</span><span class="sxs-lookup"><span data-stu-id="c00be-132">However, this function does not perform any action; it just returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c00be-133">要件</span><span class="sxs-lookup"><span data-stu-id="c00be-133">Requirements</span></span>  

 <span data-ttu-id="c00be-134">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c00be-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c00be-135">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="c00be-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c00be-136">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="c00be-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c00be-137">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c00be-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c00be-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="c00be-138">See also</span></span>

- [<span data-ttu-id="c00be-139">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="c00be-139">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
