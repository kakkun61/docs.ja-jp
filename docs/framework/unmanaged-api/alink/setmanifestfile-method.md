---
title: SetManifestFile メソッド
ms.date: 03/30/2017
api_name:
- IALink3.SetManifestFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetManifestFile
helpviewer_keywords:
- SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type:
- apiref
ms.openlocfilehash: a4518e93db887dbdc4397636479be8bf5a705c2d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733725"
---
# <a name="setmanifestfile-method"></a><span data-ttu-id="5d04f-102">SetManifestFile メソッド</span><span class="sxs-lookup"><span data-stu-id="5d04f-102">SetManifestFile Method</span></span>

<span data-ttu-id="5d04f-103">リンカーがアセンブリを作成するときに使用するマニフェストファイルを指定またはリセットできます。</span><span class="sxs-lookup"><span data-stu-id="5d04f-103">Enables you to specify or reset the manifest file that the linker uses when it creates the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d04f-104">構文</span><span class="sxs-lookup"><span data-stu-id="5d04f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d04f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5d04f-105">Parameters</span></span>  

 `pszFile`  
  
 <span data-ttu-id="5d04f-106">コンテンツが Win32 リソース blob に格納されるマニフェストファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="5d04f-106">The name of the manifest file whose contents are put into the Win32 resources blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d04f-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="5d04f-107">Return Value</span></span>  

 <span data-ttu-id="5d04f-108">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="5d04f-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d04f-109">注釈</span><span class="sxs-lookup"><span data-stu-id="5d04f-109">Remarks</span></span>  

 <span data-ttu-id="5d04f-110">Win32ResBlob を要求する前に、これを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5d04f-110">Call this before asking for the Win32ResBlob.</span></span> <span data-ttu-id="5d04f-111">パラメーターの値 `pszFile` は、コンテンツが読み取られ、ID が RT_MANIFEST の Win32 リソースに配置されるマニフェストファイルの名前です。</span><span class="sxs-lookup"><span data-stu-id="5d04f-111">The value of the `pszFile` parameter is the name of the manifest file whose contents are read and put in the Win32 resources with ID of RT_MANIFEST.</span></span> <span data-ttu-id="5d04f-112">NULL のパラメーターを使用して呼び出されると、以前に読み取られたマニフェストはクリアされます。</span><span class="sxs-lookup"><span data-stu-id="5d04f-112">When called by using a parameter of NULL, any previously read manifest is cleared.</span></span> <span data-ttu-id="5d04f-113">これにより、1つのリンカーの状態を初期化時間にリセットできます。</span><span class="sxs-lookup"><span data-stu-id="5d04f-113">This enables one to reset the state of the linker to that of initialization time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d04f-114">要件</span><span class="sxs-lookup"><span data-stu-id="5d04f-114">Requirements</span></span>  

 <span data-ttu-id="5d04f-115">ALink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="5d04f-115">Requires aLink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d04f-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="5d04f-116">See also</span></span>

- [<span data-ttu-id="5d04f-117">IALink3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5d04f-117">IALink3 Interface</span></span>](ialink3-interface.md)
- [<span data-ttu-id="5d04f-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="5d04f-118">ALink API</span></span>](index.md)
- [<span data-ttu-id="5d04f-119">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5d04f-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="5d04f-120">Al.exe (アセンブリ リンカー)</span><span class="sxs-lookup"><span data-stu-id="5d04f-120">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
