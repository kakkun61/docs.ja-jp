---
title: IMetaDataDispenser::OpenScopeOnMemory メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScopeOnMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScopeOnMemory
helpviewer_keywords:
- OpenScopeOnMemory method [.NET Framework metadata]
- IMetaDataDispenser::OpenScopeOnMemory method [.NET Framework metadata]
ms.assetid: 14218249-bdec-48ae-b5fc-9f57f7ca8501
topic_type:
- apiref
ms.openlocfilehash: 26293e38a275ca691c7d48dceb12c1e7dd316536
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713419"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="85470-102">IMetaDataDispenser::OpenScopeOnMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="85470-102">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>

<span data-ttu-id="85470-103">既存のメタデータを含むメモリ領域を開きます。</span><span class="sxs-lookup"><span data-stu-id="85470-103">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="85470-104">つまり、このメソッドは、既存のデータがメタデータとして扱われる、指定されたメモリ領域を開きます。</span><span class="sxs-lookup"><span data-stu-id="85470-104">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85470-105">構文</span><span class="sxs-lookup"><span data-stu-id="85470-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,
    [in]  ULONG       cbData,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85470-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="85470-106">Parameters</span></span>  

 `pData`  
 <span data-ttu-id="85470-107">からメモリ領域の開始アドレスを指定するポインター。</span><span class="sxs-lookup"><span data-stu-id="85470-107">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="85470-108">からメモリ領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="85470-108">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="85470-109">から開くためのモード (読み取り、書き込みなど) を指定する [Coropenflags](coropenflags-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="85470-109">[in] A value of the [CorOpenFlags](coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="85470-110">から返される、必要なメタデータインターフェイスの IID。呼び出し元は、インターフェイスを使用して、メタデータのインポート (読み取り) または出力 (書き込み) を行います。</span><span class="sxs-lookup"><span data-stu-id="85470-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="85470-111">の値には `riid` 、"import" インターフェイスまたは "emit" インターフェイスのいずれかを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="85470-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="85470-112">有効な値は、IID_IMetaDataEmit、IID_IMetaDataImport、IID_IMetaDataAssemblyEmit、IID_IMetaDataAssemblyImport、IID_IMetaDataEmit2、または IID_IMetaDataImport2 です。</span><span class="sxs-lookup"><span data-stu-id="85470-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="85470-113">入出力返されたインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="85470-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85470-114">注釈</span><span class="sxs-lookup"><span data-stu-id="85470-114">Remarks</span></span>  

 <span data-ttu-id="85470-115">メタデータのメモリ内コピーは、"import" インターフェイスのいずれかのメソッドを使用してクエリを実行するか、"emit" インターフェイスのいずれかのメソッドを使用してに追加できます。</span><span class="sxs-lookup"><span data-stu-id="85470-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="85470-116">`OpenScopeOnMemory`メソッドは[IMetaDataDispenser:: openscope](imetadatadispenser-openscope-method.md)メソッドに似ていますが、対象のメタデータがディスク上のファイルではなくメモリに既に存在している点が異なります。</span><span class="sxs-lookup"><span data-stu-id="85470-116">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="85470-117">メモリのターゲット領域に共通言語ランタイム (CLR) メタデータが含まれていない場合、 `OpenScopeOnMemory` メソッドは失敗します。</span><span class="sxs-lookup"><span data-stu-id="85470-117">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85470-118">要件</span><span class="sxs-lookup"><span data-stu-id="85470-118">Requirements</span></span>  

 <span data-ttu-id="85470-119">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85470-119">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85470-120">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="85470-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="85470-121">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="85470-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="85470-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85470-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85470-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="85470-123">See also</span></span>

- [<span data-ttu-id="85470-124">IMetaDataDispenser インターフェイス</span><span class="sxs-lookup"><span data-stu-id="85470-124">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="85470-125">IMetaDataDispenserEx インターフェイス</span><span class="sxs-lookup"><span data-stu-id="85470-125">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="85470-126">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="85470-126">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="85470-127">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="85470-127">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="85470-128">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="85470-128">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="85470-129">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="85470-129">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="85470-130">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="85470-130">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="85470-131">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="85470-131">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
