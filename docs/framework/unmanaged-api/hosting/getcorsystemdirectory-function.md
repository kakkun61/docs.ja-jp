---
title: GetCORSystemDirectory 関数
ms.date: 03/30/2017
api_name:
- GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORSystemDirectory
helpviewer_keywords:
- GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type:
- apiref
ms.openlocfilehash: 21b01156afceb24ab5c132894fae6922d7b97e59
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733296"
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="7cb2a-102">GetCORSystemDirectory 関数</span><span class="sxs-lookup"><span data-stu-id="7cb2a-102">GetCORSystemDirectory Function</span></span>

<span data-ttu-id="7cb2a-103">プロセスに読み込まれる共通言語ランタイム (CLR) のインストールディレクトリを返します。</span><span class="sxs-lookup"><span data-stu-id="7cb2a-103">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="7cb2a-104">インストールディレクトリは完全に修飾されています。たとえば、"c:\windows\microsoft.net\framework\v1.0.3705" のようになります。</span><span class="sxs-lookup"><span data-stu-id="7cb2a-104">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="7cb2a-105">この関数の使用は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="7cb2a-105">This function is deprecated.</span></span> <span data-ttu-id="7cb2a-106">.NET Framework 4 で提供される [ICLRRuntimeInfo:: GetRuntimeDirectory](iclrruntimeinfo-getruntimedirectory-method.md) メソッドに置き換えられています。</span><span class="sxs-lookup"><span data-stu-id="7cb2a-106">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](iclrruntimeinfo-getruntimedirectory-method.md) method provided in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cb2a-107">構文</span><span class="sxs-lookup"><span data-stu-id="7cb2a-107">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (
    [out] LPWSTR  pbuffer,
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="7cb2a-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7cb2a-108">Parameters</span></span>  

 `pbuffer`  
 <span data-ttu-id="7cb2a-109">入出力プロセスに読み込まれたランタイムのインストールディレクトリの完全修飾名が含まれた文字列をランタイムが返すバッファー。</span><span class="sxs-lookup"><span data-stu-id="7cb2a-109">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="7cb2a-110">ランタイムがまだプロセスに読み込まれていない場合、関数はコンピューターにインストールされている最新バージョンのランタイムの適切なディレクトリ情報を返します。</span><span class="sxs-lookup"><span data-stu-id="7cb2a-110">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="7cb2a-111">からのサイズ (バイト単位) `pbuffer` 。</span><span class="sxs-lookup"><span data-stu-id="7cb2a-111">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="7cb2a-112">入出力で返された文字数 `pbuffer` 。</span><span class="sxs-lookup"><span data-stu-id="7cb2a-112">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7cb2a-113">注釈</span><span class="sxs-lookup"><span data-stu-id="7cb2a-113">Remarks</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="7cb2a-114">CLR のバージョン4を実行しているプロセスでは、この関数を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="7cb2a-114">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="7cb2a-115">コンピューターに以前のバージョンの CLR がインストールされている場合、この関数はそのバージョンのインストールディレクトリを返します。</span><span class="sxs-lookup"><span data-stu-id="7cb2a-115">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cb2a-116">要件</span><span class="sxs-lookup"><span data-stu-id="7cb2a-116">Requirements</span></span>  

 <span data-ttu-id="7cb2a-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7cb2a-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cb2a-118">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="7cb2a-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7cb2a-119">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7cb2a-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7cb2a-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cb2a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cb2a-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="7cb2a-121">See also</span></span>

- [<span data-ttu-id="7cb2a-122">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="7cb2a-122">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
