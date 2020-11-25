---
title: ValidatorFlags 列挙型
ms.date: 03/30/2017
api_name:
- ValidatorFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ValidatorFlags
helpviewer_keywords:
- ValidatorFlags enumeration [.NET Framework hosting]
ms.assetid: a3f5c266-3fcc-4ad1-aaf5-4cdbe26304ad
topic_type:
- apiref
ms.openlocfilehash: 92c430cdb8b46cf75dde9a8395ce713116dc05a5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732861"
---
# <a name="validatorflags-enumeration"></a><span data-ttu-id="6695d-102">ValidatorFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="6695d-102">ValidatorFlags Enumeration</span></span>

<span data-ttu-id="6695d-103">[ICLRValidator:: Validate](iclrvalidator-validate-method.md)メソッドの呼び出しで実行する必要がある検証の種類を示す値を格納します。</span><span class="sxs-lookup"><span data-stu-id="6695d-103">Contains values that indicate the type of validation that should be performed in a call to the [ICLRValidator::Validate](iclrvalidator-validate-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6695d-104">構文</span><span class="sxs-lookup"><span data-stu-id="6695d-104">Syntax</span></span>  
  
```cpp  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a><span data-ttu-id="6695d-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="6695d-105">Members</span></span>  
  
|<span data-ttu-id="6695d-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="6695d-106">Member</span></span>|<span data-ttu-id="6695d-107">説明</span><span class="sxs-lookup"><span data-stu-id="6695d-107">Description</span></span>|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|<span data-ttu-id="6695d-108">実行可能ファイル内の Microsoft 中間言語 (MSIL) のみを検証するように指定します。</span><span class="sxs-lookup"><span data-stu-id="6695d-108">Specifies that only the Microsoft intermediate language (MSIL) in the executable file should be validated.</span></span>|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|<span data-ttu-id="6695d-109">実行可能ファイルの形式だけを検証することを指定します。</span><span class="sxs-lookup"><span data-stu-id="6695d-109">Specifies that only the format of the executable file should be validated.</span></span>|  
|`VALIDATOR_EXTRA_VERBOSE`|<span data-ttu-id="6695d-110">すべての種類の検証を実行してレポートすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="6695d-110">Specifies that all types of validation should be performed and reported on.</span></span>|  
|`VALIDATOR_NOCHECK_PEFORMAT`|<span data-ttu-id="6695d-111">実行可能ファイルの形式を検証しないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="6695d-111">Specifies that the format of the executable file should not be validated.</span></span>|  
|`VALIDATOR_SHOW_SOURCE_LINES`|<span data-ttu-id="6695d-112">検証エラーメッセージに検証エラーを発生させるソースコード行を含めるように指定します。</span><span class="sxs-lookup"><span data-stu-id="6695d-112">Specifies that validation error messages should include the lines of source code that raise validation errors.</span></span> <span data-ttu-id="6695d-113">このフィールド値は .NET Framework バージョン2.0 では無効です。</span><span class="sxs-lookup"><span data-stu-id="6695d-113">This field value is not valid in the .NET Framework version 2.0.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6695d-114">要件</span><span class="sxs-lookup"><span data-stu-id="6695d-114">Requirements</span></span>  

 <span data-ttu-id="6695d-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6695d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6695d-116">**ヘッダー:** IValidator、IValidator</span><span class="sxs-lookup"><span data-stu-id="6695d-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="6695d-117">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6695d-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6695d-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6695d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6695d-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="6695d-119">See also</span></span>

- [<span data-ttu-id="6695d-120">ICLRErrorReportingManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6695d-120">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="6695d-121">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="6695d-121">Hosting Enumerations</span></span>](hosting-enumerations.md)
