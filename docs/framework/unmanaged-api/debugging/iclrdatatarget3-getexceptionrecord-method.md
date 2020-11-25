---
title: ICLRDataTarget3::GetExceptionRecord メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetExceptionRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6643c2af-2ee6-4789-aa25-1d8eaf500c94
topic_type:
- apiref
ms.openlocfilehash: 8f6eaa6ad310e9a01b2307bff091b670c3e1d6cb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723611"
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a><span data-ttu-id="b07c4-102">ICLRDataTarget3::GetExceptionRecord メソッド</span><span class="sxs-lookup"><span data-stu-id="b07c4-102">ICLRDataTarget3::GetExceptionRecord Method</span></span>

<span data-ttu-id="b07c4-103">ターゲット プロセスに関連付けられた例外レコードを取得するために、共通言語ランタイム (CLR: Common Language Runtime) データ アクセス サービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b07c4-103">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span> <span data-ttu-id="b07c4-104">たとえば、ダンプターゲットの場合、これは `ExceptionParam` Windows デバッグヘルプライブラリ (dbghelp) の [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) 関数の引数を通じて渡された例外レコードと同じになります。</span><span class="sxs-lookup"><span data-stu-id="b07c4-104">For example, for a dump target, this would be equivalent to the exception record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b07c4-105">構文</span><span class="sxs-lookup"><span data-stu-id="b07c4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b07c4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b07c4-106">Parameters</span></span>  

 `bufferSize`  
 <span data-ttu-id="b07c4-107">[入力] 入力バッファー サイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="b07c4-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="b07c4-108">これは MINIDUMP_EXCEPTION と同じである必要があり `sizeof(` [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) `)` ます。</span><span class="sxs-lookup"><span data-stu-id="b07c4-108">This must be equal to `sizeof(`[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception)`)`.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="b07c4-109">[出力] 実際にバッファーに書き込まれるバイト数を受け取る `ULONG32` 型へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b07c4-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="b07c4-110">[出力] 例外レコードのコピーを受信するメモリ バッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b07c4-110">[out] A pointer to a memory buffer that receives a copy of the exception record.</span></span> <span data-ttu-id="b07c4-111">例外レコードは [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) 型として返されます。</span><span class="sxs-lookup"><span data-stu-id="b07c4-111">The exception record is returned as a [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b07c4-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="b07c4-112">Return Value</span></span>  

 <span data-ttu-id="b07c4-113">戻り値は、成功の場合は `S_OK` で、失敗の場合は `HRESULT` コードです。</span><span class="sxs-lookup"><span data-stu-id="b07c4-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="b07c4-114">次が `HRESULT` コードに含まれることはありますが、限定されているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="b07c4-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="b07c4-115">リターン コード</span><span class="sxs-lookup"><span data-stu-id="b07c4-115">Return code</span></span>|<span data-ttu-id="b07c4-116">説明</span><span class="sxs-lookup"><span data-stu-id="b07c4-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="b07c4-117">メソッドが成功しました。</span><span class="sxs-lookup"><span data-stu-id="b07c4-117">Method succeeded.</span></span> <span data-ttu-id="b07c4-118">例外レコードは出力バッファーにコピーされました。</span><span class="sxs-lookup"><span data-stu-id="b07c4-118">The exception record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="b07c4-119">例外レコードはターゲットに関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="b07c4-119">No exception record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="b07c4-120">入力バッファーのサイズは `sizeof(MINIDUMP_EXCEPTION)` と等しくありません。</span><span class="sxs-lookup"><span data-stu-id="b07c4-120">The input buffer size is not equal to `sizeof(MINIDUMP_EXCEPTION)`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b07c4-121">注釈</span><span class="sxs-lookup"><span data-stu-id="b07c4-121">Remarks</span></span>  

 <span data-ttu-id="b07c4-122">[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) は、Windows SDK の dbghelp .h と imagehlp.dll に定義されている構造体です。</span><span class="sxs-lookup"><span data-stu-id="b07c4-122">[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) is a structure defined in dbghelp.h and imagehlp.h in the Windows SDK.</span></span>  
  
 <span data-ttu-id="b07c4-123">このメソッドは、デバッグ アプリケーションの作成者によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="b07c4-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b07c4-124">要件</span><span class="sxs-lookup"><span data-stu-id="b07c4-124">Requirements</span></span>  

 <span data-ttu-id="b07c4-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b07c4-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b07c4-126">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="b07c4-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="b07c4-127">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b07c4-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b07c4-128">**.NET Framework のバージョン:**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b07c4-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b07c4-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="b07c4-129">See also</span></span>

- [<span data-ttu-id="b07c4-130">ICLRDataTarget3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b07c4-130">ICLRDataTarget3 Interface</span></span>](iclrdatatarget3-interface.md)
- [<span data-ttu-id="b07c4-131">GetExceptionContextRecord メソッド</span><span class="sxs-lookup"><span data-stu-id="b07c4-131">GetExceptionContextRecord Method</span></span>](iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="b07c4-132">GetExceptionThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="b07c4-132">GetExceptionThreadID Method</span></span>](iclrdatatarget3-getexceptionthreadid-method.md)
