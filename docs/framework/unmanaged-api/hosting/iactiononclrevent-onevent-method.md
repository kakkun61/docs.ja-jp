---
title: IActionOnCLREvent::OnEvent メソッド
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent.OnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent::OnEvent
helpviewer_keywords:
- OnEvent method [.NET Framework hosting]
- IActionOnCLREvent::OnEvent method [.NET Framework hosting]
ms.assetid: 0970f10c-4304-4c12-91c0-83e51455afb4
topic_type:
- apiref
ms.openlocfilehash: 3bfcb01e30b4cb33ec9276f1d3c6ac2f3bde4b58
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721765"
---
# <a name="iactiononclreventonevent-method"></a>IActionOnCLREvent::OnEvent メソッド

[ICLROnEventManager:: RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md)メソッドの呼び出しを使用して登録されたイベントに対してコールバックを実行します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `event`  
 からイベントの種類を示す、 [Eclrevent](eclrevent-enumeration.md) の値の1つ。  
  
 `data`  
 からの詳細を格納しているオブジェクトへのポインター `event` 。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`OnEvent` 正常に返されました。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。|  
|E_FAIL|原因不明の致命的なエラーが発生しました。 メソッドが E_FAIL を返す場合、そのプロセス内で CLR は使用できなくなります。 後続のホストメソッドを呼び出すと HOST_E_CLRNOTAVAILABLE が返されます。|  
  
## <a name="remarks"></a>注釈  

 `data`パラメーターが、指定されていない型のオブジェクトへのポインターです。 `event`パラメーターがの場合 `Event_DomainUnload` 、 `data` は、 <xref:System.AppDomain> アンロードされたの数値識別子です。 ホストは、この識別子をキーとして使用して適切なアクションを実行できます。  
  
 がの場合 `event` `Event_MDAFired` 、 `data` はマネージデバッグアシスタント (MDA) からのメッセージ出力を格納する [MDAInfo](mdainfo-structure.md) インスタンスへのポインターです。 Mda は、開発者がデバッグを支援する CLR の機能です。これは、特にトラップが困難なイベントに関する XML メッセージを生成することによって行われます。 このようなメッセージは、マネージコードとアンマネージコードの間の遷移をデバッグする場合に特に役立ちます。 詳細については、「 [マネージデバッグアシスタントによるエラーの診断](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)」を参照してください。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [マネージド デバッグ アシスタントによるエラーの診断](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [EClrEvent 列挙型](eclrevent-enumeration.md)
- [IActionOnCLREvent インターフェイス](iactiononclrevent-interface.md)
- [ICLRControl インターフェイス](iclrcontrol-interface.md)
- [ICLROnEventManager インターフェイス](iclroneventmanager-interface.md)
- [MDAInfo 構造体](mdainfo-structure.md)
