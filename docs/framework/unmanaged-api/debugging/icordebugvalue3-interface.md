---
title: ICorDebugValue3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3
helpviewer_keywords:
- ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type:
- apiref
ms.openlocfilehash: 419efc7f21f4ac2e68657b2a4d69a8690a2938d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722311"
---
# <a name="icordebugvalue3-interface"></a>ICorDebugValue3 インターフェイス

"ICorDebugValue" インターフェイスと "ICorDebugValue2" インターフェイスを拡張して、2 GB を超える配列のサポートを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetSize64 メソッド](icordebugvalue3-getsize64-method.md)|このオブジェクトのサイズ (バイト単位) を取得し `ICorDebugValue3` ます。|  
  
## <a name="remarks"></a>注釈  

 [ICorDebugValue:: GetSize](icordebugvalue3-getsize64-method.md)メソッドは、0 ~ 2147483647 バイトの範囲のオブジェクトサイズを返します。 .NET Framework 4.5 では、配列のサイズが 2 GB を超える場合があります。 `ICorDebugValue3`インターフェイスを使用すると、これらの配列のサイズを決定できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
