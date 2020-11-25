---
title: ICorDebugMetaDataLocator::GetMetaData メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugMetaDataLocator.GetMetaData
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMetaDataLocator::GetMetaData
helpviewer_keywords:
- ICorDebugMetaDataLocator::GetMetaData method [.NET Framework debugging]
- GetMetaData method, ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: f9b0ff22-54db-45eb-9cc3-508000a3141d
topic_type:
- apiref
ms.openlocfilehash: 63efb788d8bca84da94921371309704cc7b20ac4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710442"
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a><span data-ttu-id="2e61b-102">ICorDebugMetaDataLocator::GetMetaData メソッド</span><span class="sxs-lookup"><span data-stu-id="2e61b-102">ICorDebugMetaDataLocator::GetMetaData Method</span></span>

<span data-ttu-id="2e61b-103">デバッガーが要求した操作を完了するために必要となるメタデータが含まれているモジュールの完全パスを返すように、デバッガーに求めます。</span><span class="sxs-lookup"><span data-stu-id="2e61b-103">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e61b-104">構文</span><span class="sxs-lookup"><span data-stu-id="2e61b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaData(  
      [in] LPCWSTR wszImagePath,  
      [in] DWORD   dwImageTimeStamp,  
      [in] DWORD   dwImageSize,  
      [in] ULONG32 cchPathBuffer,  
      [out] ULONG32 * pcchPathBuffer,  
      [out, size_is(cchPathBuffer), length_is(*pcchPathBuffer)]  
               WCHAR wszPathBuffer[]  
      );  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e61b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2e61b-105">Parameters</span></span>  

 `wszImagePath`  
 <span data-ttu-id="2e61b-106">[in] ファイルの完全パスを表す null で終わる文字列。</span><span class="sxs-lookup"><span data-stu-id="2e61b-106">[in] A null-terminated string that represents the full path to the file.</span></span> <span data-ttu-id="2e61b-107">完全なパスが使用できない場合は、ファイルの名前と拡張子 (ファイル *名*)。*拡張機能*)。</span><span class="sxs-lookup"><span data-stu-id="2e61b-107">If the full path is not available, the name and extension of the file (*filename*.*extension*).</span></span>  
  
 `dwImageTimeStamp`  
 <span data-ttu-id="2e61b-108">[in] イメージの PE ファイル ヘッダーのタイムスタンプ。</span><span class="sxs-lookup"><span data-stu-id="2e61b-108">[in] The time stamp from the image's PE file headers.</span></span> <span data-ttu-id="2e61b-109">このパラメーターは、シンボルサーバー ([Symsrv](/windows/desktop/debug/using-symsrv)) の検索に使用される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2e61b-109">This parameter can potentially be used for a symbol server ([SymSrv](/windows/desktop/debug/using-symsrv)) lookup.</span></span>  
  
 `dwImageSize`  
 <span data-ttu-id="2e61b-110">[in] PE ファイル ヘッダーのイメージ サイズ。</span><span class="sxs-lookup"><span data-stu-id="2e61b-110">[in] The image size from PE file headers.</span></span> <span data-ttu-id="2e61b-111">このパラメーターは、SymSrv の検索に使用される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2e61b-111">This parameter can potentially be used for a SymSrv lookup.</span></span>  
  
 `cchPathBuffer`  
 <span data-ttu-id="2e61b-112">[in] `wszPathBuffer` の文字数。</span><span class="sxs-lookup"><span data-stu-id="2e61b-112">[in] The character count in `wszPathBuffer`.</span></span>  
  
 `pcchPathBuffer`  
 <span data-ttu-id="2e61b-113">[out] `wszPathBuffer` に書き込まれる `WCHAR` の数。</span><span class="sxs-lookup"><span data-stu-id="2e61b-113">[out] The count of `WCHAR`s written to `wszPathBuffer`.</span></span>  
  
 <span data-ttu-id="2e61b-114">メソッドが E_NOT_SUFFICIENT_BUFFER を返す場合は、パスを格納するために必要な `WCHAR` の数。</span><span class="sxs-lookup"><span data-stu-id="2e61b-114">If the method returns E_NOT_SUFFICIENT_BUFFER, contains the count of `WCHAR`s needed to store the path.</span></span>  
  
 `wszPathBuffer`  
 <span data-ttu-id="2e61b-115">[out] 要求されたメタデータを格納するファイルの完全パスが、デバッガーによりコピーされるバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2e61b-115">[out] Pointer to a buffer into which the debugger will copy the full path of the file that contains the requested metadata.</span></span>  
  
 <span data-ttu-id="2e61b-116">`ofReadOnly` [Coropenflags](../metadata/coropenflags-enumeration.md)列挙のフラグは、このファイル内のメタデータへの読み取り専用アクセスを要求するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="2e61b-116">The `ofReadOnly` flag from the [CorOpenFlags](../metadata/coropenflags-enumeration.md) enumeration is used to request read-only access to the metadata in this file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e61b-117">戻り値</span><span class="sxs-lookup"><span data-stu-id="2e61b-117">Return Value</span></span>  

 <span data-ttu-id="2e61b-118">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="2e61b-118">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span> <span data-ttu-id="2e61b-119">これ以外のエラー HRESULT はすべて、ファイルを取得できないことを示します。</span><span class="sxs-lookup"><span data-stu-id="2e61b-119">All other failure HRESULTs indicate that the file is not retrievable.</span></span>  
  
|<span data-ttu-id="2e61b-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2e61b-120">HRESULT</span></span>|<span data-ttu-id="2e61b-121">説明</span><span class="sxs-lookup"><span data-stu-id="2e61b-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2e61b-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="2e61b-122">S_OK</span></span>|<span data-ttu-id="2e61b-123">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="2e61b-123">The method completed successfully.</span></span> <span data-ttu-id="2e61b-124">`wszPathBuffer` にはファイルの完全パスが含まれます。また終端は null です。</span><span class="sxs-lookup"><span data-stu-id="2e61b-124">`wszPathBuffer` contains the full path to the file and is null-terminated.</span></span>|  
|<span data-ttu-id="2e61b-125">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="2e61b-125">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="2e61b-126">`wszPathBuffer` の現在のサイズが十分ではないため、完全パスを保持できません。</span><span class="sxs-lookup"><span data-stu-id="2e61b-126">The current size of `wszPathBuffer` is not sufficient to hold the full path.</span></span> <span data-ttu-id="2e61b-127">この場合、`pcchPathBuffer` に必要な `WCHAR` の数 (終端の null 文字も含む) が格納され、要求されたバッファー サイズで `GetMetaData` がもう一度呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2e61b-127">In this case, `pcchPathBuffer` contains the needed count of `WCHAR`s, including the terminating null character, and `GetMetaData` is called a second time with the requested buffer size.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e61b-128">注釈</span><span class="sxs-lookup"><span data-stu-id="2e61b-128">Remarks</span></span>  

 <span data-ttu-id="2e61b-129">`wszImagePath` にダンプのモジュールの完全パスが格納されている場合は、ダンプが収集されたコンピューターからのパスを示しています。</span><span class="sxs-lookup"><span data-stu-id="2e61b-129">If `wszImagePath` contains a full path for a module from a dump, it specifies the path from the computer where the dump was collected.</span></span> <span data-ttu-id="2e61b-130">この場所にはファイルが存在しない、または同じ名前の正しくないファイルがパス上に格納されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2e61b-130">The file may not exist at this location, or an incorrect file with the same name may be stored on the path.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e61b-131">要件</span><span class="sxs-lookup"><span data-stu-id="2e61b-131">Requirements</span></span>  

 <span data-ttu-id="2e61b-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e61b-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e61b-133">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2e61b-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e61b-134">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e61b-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e61b-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e61b-135">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e61b-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="2e61b-136">See also</span></span>

- [<span data-ttu-id="2e61b-137">ICorDebugThread4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2e61b-137">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="2e61b-138">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="2e61b-138">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="2e61b-139">デバッグ</span><span class="sxs-lookup"><span data-stu-id="2e61b-139">Debugging</span></span>](index.md)
