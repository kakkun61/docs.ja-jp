---
title: ServiceAppDomain
ms.date: 03/30/2017
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
ms.openlocfilehash: 243c9112dd9caf5c92ef77aa0f45b4b1e71a4e9f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273257"
---
# <a name="serviceappdomain"></a><span data-ttu-id="9732d-102">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="9732d-102">ServiceAppDomain</span></span>

<span data-ttu-id="9732d-103">アプリケーション ドメインにサービスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="9732d-103">Maps a service to an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9732d-104">構文</span><span class="sxs-lookup"><span data-stu-id="9732d-104">Syntax</span></span>  
  
```csharp
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="9732d-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="9732d-105">Methods</span></span>  

 <span data-ttu-id="9732d-106">ServiceAppDomain クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="9732d-106">The ServiceAppDomain class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9732d-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="9732d-107">Properties</span></span>  

 <span data-ttu-id="9732d-108">ServiceAppDomain クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="9732d-108">The ServiceAppDomain class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="9732d-109">ref</span><span class="sxs-lookup"><span data-stu-id="9732d-109">ref</span></span>  

 <span data-ttu-id="9732d-110">データ型 : Service</span><span class="sxs-lookup"><span data-stu-id="9732d-110">Data type: Service</span></span>  
<span data-ttu-id="9732d-111">修飾子: キー</span><span class="sxs-lookup"><span data-stu-id="9732d-111">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="9732d-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="9732d-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9732d-113">このアプリケーション ドメインのサービスです。</span><span class="sxs-lookup"><span data-stu-id="9732d-113">The service of this application domain.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="9732d-114">ref</span><span class="sxs-lookup"><span data-stu-id="9732d-114">ref</span></span>  

 <span data-ttu-id="9732d-115">データ型: AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="9732d-115">Data type: AppDomainInfo</span></span>  
<span data-ttu-id="9732d-116">修飾子: キー</span><span class="sxs-lookup"><span data-stu-id="9732d-116">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="9732d-117">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="9732d-117">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9732d-118">アプリケーション ドメインのプロパティが格納されています。</span><span class="sxs-lookup"><span data-stu-id="9732d-118">Contains properties of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9732d-119">要件</span><span class="sxs-lookup"><span data-stu-id="9732d-119">Requirements</span></span>  
  
|<span data-ttu-id="9732d-120">MOF</span><span class="sxs-lookup"><span data-stu-id="9732d-120">MOF</span></span>|<span data-ttu-id="9732d-121">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="9732d-121">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9732d-122">名前空間</span><span class="sxs-lookup"><span data-stu-id="9732d-122">Namespace</span></span>|<span data-ttu-id="9732d-123">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="9732d-123">Defined in root\ServiceModel</span></span>|
