---
title: ICorDebugRemoteTarget::GetHostName メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget.GetHostName
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::GetHostName
helpviewer_keywords:
- ICorDebugRemoteTarget::GetHostName method [.NET Framework debugging]
- GetHostName method, ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: 1c7276f7-7e54-470c-808c-e13745ac07a1
topic_type:
- apiref
ms.openlocfilehash: 3e946d8a27ec6b568b2f3c3633695c9f6795c938
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712054"
---
# <a name="icordebugremotetargetgethostname-method"></a>ICorDebugRemoteTarget::GetHostName メソッド

リモート デバッグ対象コンピューターの完全修飾ドメイン名または IPv4 アドレスを返します。 IPV6 はこの時点ではサポートされません。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
## <a name="parameters"></a>パラメーター  

 `cchHostName`  
 [入力] `szHostName` バッファーのサイズ (文字単位)。 このパラメーターが 0 である場合、`szHostName` は null であることが必要です。  
  
 `pcchHostName`  
 [出力] 配列に返される文字数。ホスト名または IP アドレスの null 終端文字を含みます。 このパラメーターには、null を指定できます。  
  
 `szHostName`  
 [出力] ホスト名または IP アドレスを含むバッファー。  
  
## <a name="return-value"></a>戻り値  

 S_OK  
 ホスト名または IP アドレスは正常に返されました。  
  
 E_FAIL (またはその他の E_ リターン コード)  
 ホスト名または IP アドレスを返すことができません。  
  
## <a name="remarks"></a>注釈  

 このメソッドは、デバッガー ライターによって実装されます。 これは、複数の呼び出しパラダイムに従う必要があります。1回目の呼び出しでは、呼び出し元がとの両方に null を渡し、 `cchHostName` `szHostName` `pcchHostName` 必要なバッファーのサイズを返します。 第 2 の呼び出しでは、以前に返されたサイズが `cchHostName` に渡され、適切にサイズ設定されたバッファーが `szHostName` に渡されます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug .idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** 3.5 SP1  
  
## <a name="see-also"></a>関連項目

- [ICorDebugRemoteTarget インターフェイス](icordebugremotetarget-interface.md)
- [ICorDebug インターフェイス](icordebug-interface.md)
