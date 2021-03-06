---
title: IHostManualEvent インターフェイス
ms.date: 03/30/2017
api_name:
- IHostManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent
helpviewer_keywords:
- IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 300c2661-b7d1-4c39-b080-9ebdef0fd523
topic_type:
- apiref
ms.openlocfilehash: 50e37b770e3ee6e0a5cdfca61fc5b09749e5735f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673203"
---
# <a name="ihostmanualevent-interface"></a>IHostManualEvent インターフェイス

手動リセットイベントの表現のホストの実装を提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Reset メソッド](ihostmanualevent-reset-method.md)|現在の `IHostManualEvent` インスタンスをシグナル状態以外の状態にリセットします。|  
|[Set メソッド](ihostmanualevent-set-method.md)|現在の `IHostManualEvent` インスタンスをシグナル状態に設定します。|  
|[Wait メソッド](ihostmanualevent-wait-method.md)|現在の `IHostManualEvent` インスタンスが所有されるか、指定された時間が経過するまで待機するようにします。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRSyncManager インターフェイス](iclrsyncmanager-interface.md)
- [IHostAutoEvent インターフェイス](ihostautoevent-interface.md)
- [IHostSemaphore インターフェイス](ihostsemaphore-interface.md)
- [IHostSyncManager インターフェイス](ihostsyncmanager-interface.md)
- [ホスト インターフェイス](hosting-interfaces.md)
