---
title: IHostMemoryManager::RegisterMemoryNotificationCallback メソッド
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.RegisterMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback
helpviewer_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback method [.NET Framework hosting]
- RegisterMemoryNotificationCallback method [.NET Framework hosting]
ms.assetid: 65d301f6-4dbb-4b5f-8eff-82540e2b6465
topic_type:
- apiref
ms.openlocfilehash: edb29378412583d7cdec804b08f8f622d642b02f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731307"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a>IHostMemoryManager::RegisterMemoryNotificationCallback メソッド

コンピューターの現在のメモリ負荷を共通言語ランタイム (CLR) に通知するために、ホストが呼び出すコールバック関数へのポインターを登録します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pCallback`  
 からCLR によって実装される [ICLRMemoryNotificationCallback](iclrmemorynotificationcallback-interface.md) インスタンスへのインターフェイスポインター。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`RegisterMemoryNotificationCallback` 正常に返されました。|  
|HOST_E_CLRNOTAVAILABLE|CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。|  
|E_FAIL|原因不明の致命的なエラーが発生しました。 メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。 後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。|  
  
## <a name="remarks"></a>注釈  

 インターフェイスで `ICLRMemoryNotificationCallback` 定義されるメソッドは1つだけであるため ([ICLRMemoryNotificationCallback:: OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md))、 `pCallback` は `ICLRMemoryNotificationCallback` CLR によって提供されるインスタンスへのポインターであるため、コールバック関数自体に対して実際に登録が行われます。 ホストは、 `OnMemoryNotification` 標準の Win32 関数を使用するのではなく、メモリ不足状態を報告するためにを呼び出し `CreateMemoryResourceNotification` ます。 詳細については、Windows プラットフォームのドキュメントを参照してください。  
  
> [!NOTE]
> を呼び出しても `OnMemoryNotification` ブロックされません。 常に直ちに返されます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRMemoryNotificationCallback インターフェイス](iclrmemorynotificationcallback-interface.md)
- [IHostMemoryManager インターフェイス](ihostmemorymanager-interface.md)
