---
title: CeeSectionAttr 列挙型
ms.date: 03/30/2017
api_name:
- CeeSectionAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionAttr
helpviewer_keywords:
- CeeSectionAttr enumeration [.NET Framework metadata]
ms.assetid: 0db51881-b869-4677-a715-1726a9216489
topic_type:
- apiref
ms.openlocfilehash: 4b2fb80298f6eef331b5b7ae4a46222ce97ede6f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732737"
---
# <a name="ceesectionattr-enumeration"></a>CeeSectionAttr 列挙型

[ICeeGen](iceegen-interface.md)インターフェイスで使用するセクションの属性を指定する値を提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum  {  
    sdNone      = 0,  
    sdReadOnly  = IMAGE_SCN_CNT_INITIALIZED_DATA |  
                  IMAGE_SCN_MEM_READ,  
    sdReadWrite = sdReadOnly | IMAGE_SCN_MEM_WRITE,  
    sdExecute   = IMAGE_SCN_MEM_READ | IMAGE_SCN_CNT_CODE |  
                  IMAGE_SCN_MEM_EXECUTE  
} CeeSectionAttr;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`sdNone`|Section には属性がありません。|  
|`sdReadOnly`|セクションには、読み取りのみが可能な、更新されていない初期化済みのデータが含まれています。|  
|`sdReadWrite`|セクションには、読み取りまたは更新が可能な初期化済みのデータが含まれています。|  
|`sdExecute`|セクションには、読み取りと実行が許可されている実行可能コードが含まれています。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ列挙体](metadata-enumerations.md)
