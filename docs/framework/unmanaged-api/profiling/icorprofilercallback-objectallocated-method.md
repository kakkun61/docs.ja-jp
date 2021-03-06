---
title: ICorProfilerCallback::ObjectAllocated メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectAllocated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectAllocated
helpviewer_keywords:
- ObjectAllocated method [.NET Framework profiling]
- ICorProfilerCallback::ObjectAllocated method [.NET Framework profiling]
ms.assetid: eb412622-77cc-4abd-a2cd-c910fe8edd54
topic_type:
- apiref
ms.openlocfilehash: fda234a6a280aeea1f497ad195d6d41efb6aa951
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674344"
---
# <a name="icorprofilercallbackobjectallocated-method"></a>ICorProfilerCallback::ObjectAllocated メソッド

ヒープ内のメモリがオブジェクトに割り当てられたことをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a>パラメーター  

 `objectId`  
 からメモリが割り当てられたオブジェクトの ID。  
  
 `classId`  
 からオブジェクトがインスタンスとして使用されているクラスの ID。  
  
## <a name="remarks"></a>注釈  

 メソッドは、 `ObjectedAllocated` スタックまたはアンマネージメモリからの割り当てのために呼び出されません。 パラメーターは、 `classId` まだ読み込まれていないマネージコード内のクラスを参照できます。 プロファイラーは、コールバックの直後に、そのクラスのクラス読み込みコールバックを受け取り `ObjectAllocated` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](icorprofilercallback-interface.md)
- [ClassLoadStarted メソッド](icorprofilercallback-classloadstarted-method.md)
- [ClassLoadFinished メソッド](icorprofilercallback-classloadfinished-method.md)
