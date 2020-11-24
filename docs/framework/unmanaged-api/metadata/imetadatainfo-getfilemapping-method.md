---
title: IMetaDataInfo::GetFileMapping メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataInfo.GetFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataInfo::GetFileMapping
helpviewer_keywords:
- IMetaDataInfo::GetFileMapping method [.NET Framework metadata]
- GetFileMapping method [.NET Framework metadata]
ms.assetid: 2868dfec-c992-4606-88bb-a8e0b6b18271
topic_type:
- apiref
ms.openlocfilehash: 8823f3cc016072d3f20100c29532459da5e97492
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682391"
---
# <a name="imetadatainfogetfilemapping-method"></a><span data-ttu-id="f08d1-102">IMetaDataInfo::GetFileMapping メソッド</span><span class="sxs-lookup"><span data-stu-id="f08d1-102">IMetaDataInfo::GetFileMapping Method</span></span>

<span data-ttu-id="f08d1-103">マップされたファイルのメモリ領域とマッピングの種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="f08d1-103">Gets the memory region of the mapped file, and the type of mapping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f08d1-104">構文</span><span class="sxs-lookup"><span data-stu-id="f08d1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,
    [out] ULONGLONG            *pcbData,
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f08d1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f08d1-105">Parameters</span></span>  

 `ppvData`  
 <span data-ttu-id="f08d1-106">入出力マップされたファイルの先頭へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f08d1-106">[out] A pointer to the start of the mapped file.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="f08d1-107">入出力マップされた領域のサイズ。</span><span class="sxs-lookup"><span data-stu-id="f08d1-107">[out] The size of the mapped region.</span></span> <span data-ttu-id="f08d1-108">がの場合 `pdwMappingType` `fmFlat` 、これはファイルのサイズです。</span><span class="sxs-lookup"><span data-stu-id="f08d1-108">If `pdwMappingType` is `fmFlat`, this is the size of the file.</span></span>  
  
 `pdwMappingType`  
 <span data-ttu-id="f08d1-109">入出力マッピングの種類を示す [CorFileMapping](corfilemapping-enumeration.md) 値です。</span><span class="sxs-lookup"><span data-stu-id="f08d1-109">[out] A [CorFileMapping](corfilemapping-enumeration.md) value that indicates the type of mapping.</span></span> <span data-ttu-id="f08d1-110">共通言語ランタイム (CLR) の現在の実装では、常にを返し `fmFlat` ます。</span><span class="sxs-lookup"><span data-stu-id="f08d1-110">The current implementation of the common language runtime (CLR) always returns `fmFlat`.</span></span> <span data-ttu-id="f08d1-111">他の値は将来使用するために予約されています。</span><span class="sxs-lookup"><span data-stu-id="f08d1-111">Other values are reserved for future use.</span></span> <span data-ttu-id="f08d1-112">ただし、その他の値は将来のバージョンまたはサービスリリースで有効になる可能性があるため、常に戻り値を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f08d1-112">However, you should always verify the returned value, because other values may be enabled in future versions or service releases.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f08d1-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="f08d1-113">Return Value</span></span>  
  
|<span data-ttu-id="f08d1-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f08d1-114">HRESULT</span></span>|<span data-ttu-id="f08d1-115">説明</span><span class="sxs-lookup"><span data-stu-id="f08d1-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f08d1-116">すべての出力が入力されます。</span><span class="sxs-lookup"><span data-stu-id="f08d1-116">All outputs are filled.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="f08d1-117">引数の値として NULL が渡されました。</span><span class="sxs-lookup"><span data-stu-id="f08d1-117">NULL was passed as an argument value.</span></span>|  
|`COR_E_NOTSUPPORTED`|<span data-ttu-id="f08d1-118">CLR 実装では、メモリ領域に関する情報を提供できません。</span><span class="sxs-lookup"><span data-stu-id="f08d1-118">The CLR implementation cannot provide information about the memory region.</span></span> <span data-ttu-id="f08d1-119">これが発生する理由としては次のようなことが考えられます。</span><span class="sxs-lookup"><span data-stu-id="f08d1-119">This can happen for the following reasons:</span></span><br /><br /> <span data-ttu-id="f08d1-120">-メタデータスコープがまたはフラグで開かれました `ofWrite` `ofCopyMemory` 。</span><span class="sxs-lookup"><span data-stu-id="f08d1-120">-   The metadata scope was opened with the `ofWrite` or `ofCopyMemory` flag.</span></span><br /><span data-ttu-id="f08d1-121">-フラグなしでメタデータスコープが開かれました `ofReadOnly` 。</span><span class="sxs-lookup"><span data-stu-id="f08d1-121">-   The metadata scope was opened without the `ofReadOnly` flag.</span></span><br /><span data-ttu-id="f08d1-122">- [IMetaDataDispenser:: OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md) メソッドは、ファイルのメタデータ部分のみを開くために使用されました。</span><span class="sxs-lookup"><span data-stu-id="f08d1-122">-   The [IMetaDataDispenser::OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md) method was used to open only the metadata portion of the file.</span></span><br /><span data-ttu-id="f08d1-123">-ファイルは、ポータブル実行可能 (PE) ファイルではありません。</span><span class="sxs-lookup"><span data-stu-id="f08d1-123">-   The file is not a portable executable (PE) file.</span></span> <span data-ttu-id="f08d1-124">**注:**  これらの条件は CLR の実装によって異なり、CLR の将来のバージョンでは緩和される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f08d1-124">**Note:**  These conditions depend on the CLR implementation, and are likely to be weakened in future versions of the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f08d1-125">注釈</span><span class="sxs-lookup"><span data-stu-id="f08d1-125">Remarks</span></span>  

 <span data-ttu-id="f08d1-126">が指すメモリ `ppvData` は、基になるメタデータスコープが開いている間のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="f08d1-126">The memory that `ppvData` points to is valid only as long as the underlying metadata scope is open.</span></span>  
  
 <span data-ttu-id="f08d1-127">このメソッドを機能させるには、 [IMetaDataDispenser:: OpenScope](imetadatadispenser-openscope-method.md) メソッドを呼び出して、ディスク上のファイルのメタデータをメモリにマップするときに、フラグを指定 `ofReadOnly` し、またはフラグを指定しないようにする必要があり `ofWrite` `ofCopyMemory` ます。</span><span class="sxs-lookup"><span data-stu-id="f08d1-127">In order for this method to work, when you map the metadata of an on-disk file into memory by calling the [IMetaDataDispenser::OpenScope](imetadatadispenser-openscope-method.md) method, you must specify the `ofReadOnly` flag and you must not specify the `ofWrite` or `ofCopyMemory` flag.</span></span>  
  
 <span data-ttu-id="f08d1-128">各スコープでのファイルマッピングの種類の選択は、CLR の特定の実装に固有です。</span><span class="sxs-lookup"><span data-stu-id="f08d1-128">The choice of file mapping type for each scope is specific to a given implementation of the CLR.</span></span> <span data-ttu-id="f08d1-129">ユーザーが設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="f08d1-129">It cannot be set by the user.</span></span> <span data-ttu-id="f08d1-130">CLR の現在の実装では常にが返され `fmFlat` `pdwMappingType` ますが、これは clr の将来のバージョンまたは特定のバージョンの今後のサービスリリースで変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f08d1-130">The current implementation of the CLR always returns `fmFlat` in `pdwMappingType`, but this can change in future versions of the CLR or in future service releases of a given version.</span></span> <span data-ttu-id="f08d1-131">の戻り値は `pdwMappingType` 、型によってレイアウトとオフセットが異なるため、常にでチェックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f08d1-131">You should always check the returned value in `pdwMappingType`, because different types will have different layouts and offsets.</span></span>  
  
 <span data-ttu-id="f08d1-132">3つのパラメーターのいずれかに対して NULL を渡すことはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="f08d1-132">Passing NULL for any of the three parameters is not supported.</span></span> <span data-ttu-id="f08d1-133">このメソッドはを返し `E_INVALIDARG` 、出力はすべて入力されません。</span><span class="sxs-lookup"><span data-stu-id="f08d1-133">The method returns `E_INVALIDARG`, and none of the outputs are filled.</span></span> <span data-ttu-id="f08d1-134">マッピングの種類または領域のサイズを無視すると、プログラムが異常終了する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f08d1-134">Ignoring the mapping type or the size of the region can result in abnormal program termination.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f08d1-135">要件</span><span class="sxs-lookup"><span data-stu-id="f08d1-135">Requirements</span></span>  

 <span data-ttu-id="f08d1-136">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f08d1-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f08d1-137">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="f08d1-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f08d1-138">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="f08d1-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f08d1-139">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f08d1-139">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f08d1-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="f08d1-140">See also</span></span>

- [<span data-ttu-id="f08d1-141">IMetaDataInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f08d1-141">IMetaDataInfo Interface</span></span>](imetadatainfo-interface.md)
- [<span data-ttu-id="f08d1-142">CorFileMapping 列挙体</span><span class="sxs-lookup"><span data-stu-id="f08d1-142">CorFileMapping Enumeration</span></span>](corfilemapping-enumeration.md)
