---
title: GetPublicKeyToken メソッド
ms.date: 03/30/2017
api_name:
- IALink2.GetPublicKeyToken
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetPublicKeyToken
helpviewer_keywords:
- GetPublicKeyToken method
ms.assetid: 4a16374c-94b0-47b0-9fed-88c2b0cdccd4
topic_type:
- apiref
ms.openlocfilehash: e41be6407076a2609a83a5be3b0c42d28914ec38
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720343"
---
# <a name="getpublickeytoken-method"></a><span data-ttu-id="0b93c-102">GetPublicKeyToken メソッド</span><span class="sxs-lookup"><span data-stu-id="0b93c-102">GetPublicKeyToken Method</span></span>

<span data-ttu-id="0b93c-103">指定されたキーキーまたはキーコンテナーの公開キートークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="0b93c-103">Retrieves the public key token for a given keyfile or key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b93c-104">構文</span><span class="sxs-lookup"><span data-stu-id="0b93c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b93c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0b93c-105">Parameters</span></span>  

 `pszKeyFile`  
 <span data-ttu-id="0b93c-106">キーのファイル名。</span><span class="sxs-lookup"><span data-stu-id="0b93c-106">Filename of the key.</span></span>  
  
 `pszKeyContainer`  
 <span data-ttu-id="0b93c-107">キーコンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="0b93c-107">Name of the key container.</span></span>  
  
 `pvPublicKeyToken`  
 <span data-ttu-id="0b93c-108">キートークンを格納するアドレス。</span><span class="sxs-lookup"><span data-stu-id="0b93c-108">Address where key token is to be stored.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="0b93c-109">によって示されるバッファーのサイズ (バイト単位) を指定し `pvPublicKeyToken` ます。</span><span class="sxs-lookup"><span data-stu-id="0b93c-109">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span></span> <span data-ttu-id="0b93c-110">戻り時には、実際に使用されたバイト数が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0b93c-110">Upon return, contains actual number of bytes used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b93c-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="0b93c-111">Return Value</span></span>  

 <span data-ttu-id="0b93c-112">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="0b93c-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b93c-113">要件</span><span class="sxs-lookup"><span data-stu-id="0b93c-113">Requirements</span></span>  

 <span data-ttu-id="0b93c-114">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="0b93c-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b93c-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b93c-115">See also</span></span>

- [<span data-ttu-id="0b93c-116">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0b93c-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="0b93c-117">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0b93c-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="0b93c-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="0b93c-118">ALink API</span></span>](index.md)
