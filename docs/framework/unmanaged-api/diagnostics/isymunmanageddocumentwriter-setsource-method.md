---
title: ISymUnmanagedDocumentWriter::SetSource メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetSource
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetSource method [.NET Framework debugging]
- SetSource method [.NET Framework debugging]
ms.assetid: ea5b9d9f-ff06-4bd3-8de5-6435343aba59
topic_type:
- apiref
ms.openlocfilehash: 31475b08b569b925aab9cab869545f0912c4ecf8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95691592"
---
# <a name="isymunmanageddocumentwritersetsource-method"></a>ISymUnmanagedDocumentWriter::SetSource メソッド

書き込まれるドキュメントの埋め込み元を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
## <a name="parameters"></a>パラメーター  

 `sourceSize`  
 から `ULONG32` バッファーのサイズを格納している `source` 。  
  
 `source`  
 から埋め込みソースを格納するバッファー。  
  
## <a name="return-value"></a>戻り値  

 メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedDocumentWriter インターフェイス](isymunmanageddocumentwriter-interface.md)
