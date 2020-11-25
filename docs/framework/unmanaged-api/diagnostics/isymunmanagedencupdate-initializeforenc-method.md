---
title: ISymUnmanagedENCUpdate::InitializeForEnc メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.InitializeForEnc
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::InitializeForEnc
helpviewer_keywords:
- ISymUnmanagedENCUpdate::InitializeForEnc method [.NET Framework debugging]
- InitializeForEnc method [.NET Framework debugging]
ms.assetid: 796b2154-b53c-4d07-9e67-80fd6064725a
topic_type:
- apiref
ms.openlocfilehash: 96ac27bfd155eaf95b1880c2f4dee0e24330e446
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729045"
---
# <a name="isymunmanagedencupdateinitializeforenc-method"></a><span data-ttu-id="05730-102">ISymUnmanagedENCUpdate::InitializeForEnc メソッド</span><span class="sxs-lookup"><span data-stu-id="05730-102">ISymUnmanagedENCUpdate::InitializeForEnc Method</span></span>

<span data-ttu-id="05730-103">[ISymUnmanagedENCUpdate:: UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md)メソッドの最初の呼び出しの前にメソッドの境界を計算できるようにします。</span><span class="sxs-lookup"><span data-stu-id="05730-103">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05730-104">構文</span><span class="sxs-lookup"><span data-stu-id="05730-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForEnc();  
```  
  
## <a name="return-value"></a><span data-ttu-id="05730-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="05730-105">Return Value</span></span>  

 <span data-ttu-id="05730-106">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="05730-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05730-107">要件</span><span class="sxs-lookup"><span data-stu-id="05730-107">Requirements</span></span>  

 <span data-ttu-id="05730-108">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="05730-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05730-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="05730-109">See also</span></span>

- [<span data-ttu-id="05730-110">ISymUnmanagedENCUpdate インターフェイス</span><span class="sxs-lookup"><span data-stu-id="05730-110">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
