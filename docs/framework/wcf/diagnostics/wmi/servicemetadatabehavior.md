---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 921a880dad0d77558a70dff8a09f75c25a3cbb8a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262282"
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="7d8a2-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="7d8a2-102">ServiceMetadataBehavior</span></span>

<span data-ttu-id="7d8a2-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="7d8a2-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d8a2-104">構文</span><span class="sxs-lookup"><span data-stu-id="7d8a2-104">Syntax</span></span>  
  
```csharp
class ServiceMetadataBehavior : Behavior  
{  
  string ExternalMetadataLocation;  
  boolean HttpGetEnabled;  
  string HttpGetUrl;  
  boolean HttpsGetEnabled;  
  string HttpsGetUrl;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7d8a2-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="7d8a2-105">Methods</span></span>  

 <span data-ttu-id="7d8a2-106">ServiceMetadataBehavior クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="7d8a2-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7d8a2-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7d8a2-107">Properties</span></span>  

 <span data-ttu-id="7d8a2-108">ServiceMetadataBehavior クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="7d8a2-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="7d8a2-109">ExternalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="7d8a2-109">ExternalMetadataLocation</span></span>  

 <span data-ttu-id="7d8a2-110">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="7d8a2-110">Data type: string</span></span>  
  
 <span data-ttu-id="7d8a2-111">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7d8a2-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7d8a2-112">サービスがメタデータ要求をリダイレクトする場所を設定します。</span><span class="sxs-lookup"><span data-stu-id="7d8a2-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="7d8a2-113">HttpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="7d8a2-113">HttpGetEnabled</span></span>  

 <span data-ttu-id="7d8a2-114">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="7d8a2-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="7d8a2-115">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7d8a2-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7d8a2-116">`HttpGetUrl` 属性によって制御されるアドレスで、サービスが WSDL を公開するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="7d8a2-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="7d8a2-117">HttpGetUrl</span><span class="sxs-lookup"><span data-stu-id="7d8a2-117">HttpGetUrl</span></span>  

 <span data-ttu-id="7d8a2-118">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="7d8a2-118">Data type: string</span></span>  
  
 <span data-ttu-id="7d8a2-119">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7d8a2-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7d8a2-120">HTTP を使用した取得のために、サービス WSDL が公開される場所を設定します。</span><span class="sxs-lookup"><span data-stu-id="7d8a2-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="7d8a2-121">HttpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="7d8a2-121">HttpsGetEnabled</span></span>  

 <span data-ttu-id="7d8a2-122">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="7d8a2-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="7d8a2-123">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7d8a2-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7d8a2-124">`HttpsGetUrl` 属性によって制御されるアドレスで、サービスが HTTPS を介して WSDL を公開するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="7d8a2-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="7d8a2-125">HttpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="7d8a2-125">HttpsGetUrl</span></span>  

 <span data-ttu-id="7d8a2-126">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="7d8a2-126">Data type: string</span></span>  
  
 <span data-ttu-id="7d8a2-127">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7d8a2-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7d8a2-128">HTTPS を使用した取得のために、サービス WSDL が公開される場所を設定します。</span><span class="sxs-lookup"><span data-stu-id="7d8a2-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d8a2-129">要件</span><span class="sxs-lookup"><span data-stu-id="7d8a2-129">Requirements</span></span>  
  
|<span data-ttu-id="7d8a2-130">MOF</span><span class="sxs-lookup"><span data-stu-id="7d8a2-130">MOF</span></span>|<span data-ttu-id="7d8a2-131">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="7d8a2-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7d8a2-132">名前空間</span><span class="sxs-lookup"><span data-stu-id="7d8a2-132">Namespace</span></span>|<span data-ttu-id="7d8a2-133">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="7d8a2-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7d8a2-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="7d8a2-134">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
