---
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: 6e20556541b1aa48e7dfc6a8cde97e1bc477457e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273946"
---
# <a name="servicetoendpointassociation"></a><span data-ttu-id="007d0-102">ServiceToEndpointAssociation</span><span class="sxs-lookup"><span data-stu-id="007d0-102">ServiceToEndpointAssociation</span></span>

<span data-ttu-id="007d0-103">エンドポイントにサービスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="007d0-103">Maps a service to an endpoint.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="007d0-104">構文</span><span class="sxs-lookup"><span data-stu-id="007d0-104">Syntax</span></span>  
  
```csharp
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="007d0-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="007d0-105">Methods</span></span>  

 <span data-ttu-id="007d0-106">ServiceToEndpointAssociation クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="007d0-106">The ServiceToEndpointAssociation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="007d0-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="007d0-107">Properties</span></span>  

 <span data-ttu-id="007d0-108">ServiceToEndpointAssociation クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="007d0-108">The ServiceToEndpointAssociation class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="007d0-109">ref</span><span class="sxs-lookup"><span data-stu-id="007d0-109">ref</span></span>  

 <span data-ttu-id="007d0-110">データ型 : Service</span><span class="sxs-lookup"><span data-stu-id="007d0-110">Data type: Service</span></span>  
  
 <span data-ttu-id="007d0-111">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="007d0-111">Access type: Read-only</span></span>  
<span data-ttu-id="007d0-112">修飾子: キー</span><span class="sxs-lookup"><span data-stu-id="007d0-112">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="007d0-113">エンドポイントに関連付けられるサービス。</span><span class="sxs-lookup"><span data-stu-id="007d0-113">The service associated with the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="007d0-114">ref</span><span class="sxs-lookup"><span data-stu-id="007d0-114">ref</span></span>  

 <span data-ttu-id="007d0-115">データ型 : Endpoint</span><span class="sxs-lookup"><span data-stu-id="007d0-115">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="007d0-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="007d0-116">Access type: Read-only</span></span>  
<span data-ttu-id="007d0-117">修飾子: キー</span><span class="sxs-lookup"><span data-stu-id="007d0-117">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="007d0-118">サービスに関連付けられるエンドポイント。</span><span class="sxs-lookup"><span data-stu-id="007d0-118">The endpoint associated with the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="007d0-119">要件</span><span class="sxs-lookup"><span data-stu-id="007d0-119">Requirements</span></span>  
  
|<span data-ttu-id="007d0-120">MOF</span><span class="sxs-lookup"><span data-stu-id="007d0-120">MOF</span></span>|<span data-ttu-id="007d0-121">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="007d0-121">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="007d0-122">名前空間</span><span class="sxs-lookup"><span data-stu-id="007d0-122">Namespace</span></span>|<span data-ttu-id="007d0-123">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="007d0-123">Defined in root\ServiceModel</span></span>|
