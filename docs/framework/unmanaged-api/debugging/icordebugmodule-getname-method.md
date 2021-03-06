---
title: ICorDebugModule::GetName メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetName
helpviewer_keywords:
- ICorDebugModule::GetName method [.NET Framework debugging]
- GetName method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: db499637-7ba9-421e-b8b1-35856995e80b
topic_type:
- apiref
ms.openlocfilehash: c2aecadf8688e763a69bd40ca877e44bc0ce5c29
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710039"
---
# <a name="icordebugmodulegetname-method"></a>ICorDebugModule::GetName メソッド

モジュールのファイル名を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `cchname`  
 [in] `szName` 配列のサイズ。  
  
 `pcchName`  
 から返された名前の長さへのポインター。  
  
 `szName`  
 入出力返された名前を格納する配列。  
  
## <a name="remarks"></a>注釈  

 `GetName`モジュールのファイル名がディスク上の名前と一致する場合、メソッドは S_OK HRESULT を返します。 `GetName` 動的またはメモリ内モジュールの場合など、名前が使用されている場合は S_FALSE HRESULT を返します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
