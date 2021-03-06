---
title: ICorPublishProcessEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum
helpviewer_keywords:
- ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type:
- apiref
ms.openlocfilehash: ebf484524b32d8e917d88c21425fab314dfc41be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95692619"
---
# <a name="icorpublishprocessenum-interface"></a>ICorPublishProcessEnum インターフェイス

[ICorPublishProcess](icorpublishprocess-interface.md)オブジェクトのコレクションを走査するメソッドを提供する[ICorPublishEnum](icorpublishenum-interface.md)インターフェイスのサブクラス。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Next メソッド](icorpublishprocessenum-next-method.md)|現在の位置から開始して、指定した数の `ICorPublishProcess` インスタンスをコレクションから取得します。|  
  
## <a name="remarks"></a>注釈  

 インターフェイスは、 `ICorPublishProcessEnum` 抽象インターフェイス [ICorPublishEnum](icorpublishenum-interface.md)のメソッドを実装します。  
  
 `ICorPublishProcessEnum`インスタンスは、 [ICorPublish:: EnumProcesses](icorpublish-enumprocesses-method.md)メソッドによって作成されます。 オブジェクトのコレクションの走査 `ICorPublishProcess` は、インスタンスの作成時に指定されたフィルター条件に基づいてい `ICorPublishProcessEnum` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorPub .idl、CorPub .h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
- [CorpubPublish コクラス](corpubpublish-coclass.md)
