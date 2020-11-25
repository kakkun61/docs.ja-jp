---
title: ResolveTypeLib メソッド
ms.date: 03/30/2017
api_name:
- ResolveTypeLib
api_location:
- tlbref.dll
f1_keywords:
- ResolveTypeLib
helpviewer_keywords:
- ITypeLibResolver::ResolveTypeLib method [.NET Framework]
- ResolveTypeLib method [.NET Framework]
ms.assetid: 95d2aa0d-8eeb-4a9f-a216-5249f7e2c167
topic_type:
- apiref
ms.openlocfilehash: 84eea78b9c2e73e24238a5ecbc9442f3d63dbd4e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719789"
---
# <a name="resolvetypelib-method"></a><span data-ttu-id="3fca1-102">ResolveTypeLib メソッド</span><span class="sxs-lookup"><span data-stu-id="3fca1-102">ResolveTypeLib Method</span></span>

<span data-ttu-id="3fca1-103">完全修飾パスを返すことにより、タイプライブラリの簡易名を解決します。</span><span class="sxs-lookup"><span data-stu-id="3fca1-103">Resolves the simple name of a type library by returning its fully qualified path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fca1-104">構文</span><span class="sxs-lookup"><span data-stu-id="3fca1-104">Syntax</span></span>  
  
```cpp  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fca1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3fca1-105">Parameters</span></span>  

 `bstrSimpleName`  
 <span data-ttu-id="3fca1-106">からタイプライブラリの簡易名を格納している [BSTR](/previous-versions/windows/desktop/automat/bstr) 。</span><span class="sxs-lookup"><span data-stu-id="3fca1-106">[in] A [BSTR](/previous-versions/windows/desktop/automat/bstr) that contains the simple name of the type library.</span></span>  
  
 `tlbid`  
 <span data-ttu-id="3fca1-107">からレジストリのタイプライブラリに割り当てられている GUID。</span><span class="sxs-lookup"><span data-stu-id="3fca1-107">[in] The GUID assigned to the type library in the registry.</span></span>  
  
 `lcid`  
 <span data-ttu-id="3fca1-108">からタイプライブラリのローカライズ ID。</span><span class="sxs-lookup"><span data-stu-id="3fca1-108">[in] The localization ID of the type library.</span></span>  
  
 `wMajorVersion`  
 <span data-ttu-id="3fca1-109">からタイプライブラリのメジャーバージョン番号。</span><span class="sxs-lookup"><span data-stu-id="3fca1-109">[in] The major version number of the type library.</span></span> <span data-ttu-id="3fca1-110">たとえば、バージョン *x.y* の場合、メジャーバージョン番号は *x* になります。</span><span class="sxs-lookup"><span data-stu-id="3fca1-110">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `wMinorVersion`  
 <span data-ttu-id="3fca1-111">からタイプライブラリのマイナーバージョン番号。</span><span class="sxs-lookup"><span data-stu-id="3fca1-111">[in] The minor version number of the type library.</span></span> <span data-ttu-id="3fca1-112">たとえば、バージョン *x.y* の場合、マイナーバージョン番号は *y* になります。</span><span class="sxs-lookup"><span data-stu-id="3fca1-112">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
 `syskind`  
 <span data-ttu-id="3fca1-113">からオペレーティング環境を識別する [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) フラグ。</span><span class="sxs-lookup"><span data-stu-id="3fca1-113">[in] A [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) flag that identifies the operating environment.</span></span> <span data-ttu-id="3fca1-114">共通値は SYS_WIN32 と SYS_WIN64 です。</span><span class="sxs-lookup"><span data-stu-id="3fca1-114">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pbstrResolvedTlbName`  
 <span data-ttu-id="3fca1-115">入出力パラメーターで指定されたタイプライブラリの完全パスを格納する [BSTR](/previous-versions/windows/desktop/automat/bstr) へのポインター `bstrSimpleName` 。</span><span class="sxs-lookup"><span data-stu-id="3fca1-115">[out] A pointer to a [BSTR](/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fca1-116">注釈</span><span class="sxs-lookup"><span data-stu-id="3fca1-116">Remarks</span></span>  

 <span data-ttu-id="3fca1-117">`ResolveTypeLib`メソッドは[Tlbexp.exe (タイプライブラリエクスポーター)](../../tools/tlbexp-exe-type-library-exporter.md)の処理中に[LoadTypeLibWithResolver 関数](loadtypelibwithresolver-function.md)によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3fca1-117">The `ResolveTypeLib` method is called by the [LoadTypeLibWithResolver function](loadtypelibwithresolver-function.md) during [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md) processing.</span></span>  
  
 <span data-ttu-id="3fca1-118">このインターフェイスのカスタム実装では、パラメーターに指定されたタイプライブラリの完全パスを含む [BSTR](/previous-versions/windows/desktop/automat/bstr) を返す必要があり `bstrSimpleName` ます。</span><span class="sxs-lookup"><span data-stu-id="3fca1-118">Custom implementations of this interface must return a [BSTR](/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fca1-119">要件</span><span class="sxs-lookup"><span data-stu-id="3fca1-119">Requirements</span></span>  

 <span data-ttu-id="3fca1-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3fca1-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fca1-121">**ヘッダー:** Tlf .idl, Tl. h</span><span class="sxs-lookup"><span data-stu-id="3fca1-121">**Header:** TlbRef.idl, TlbRef.h</span></span>  
  
 <span data-ttu-id="3fca1-122">**ライブラリ:** Tlf .lib</span><span class="sxs-lookup"><span data-stu-id="3fca1-122">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="3fca1-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fca1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fca1-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="3fca1-124">See also</span></span>

- [<span data-ttu-id="3fca1-125">Tlbexp ヘルパー関数</span><span class="sxs-lookup"><span data-stu-id="3fca1-125">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="3fca1-126">LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="3fca1-126">LoadTypeLibEx</span></span>](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
