---
title: メタデータ エンドポイントを公開する
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 5be27a72c87d95e36a5b283e7930ba0a5191a5a1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249762"
---
# <a name="publishing-metadata-endpoints"></a><span data-ttu-id="7e3cb-102">メタデータ エンドポイントを公開する</span><span class="sxs-lookup"><span data-stu-id="7e3cb-102">Publishing Metadata Endpoints</span></span>

<span data-ttu-id="7e3cb-103">Windows Communication Foundation (WCF) サービスは、1つまたは複数のメタデータエンドポイントを公開することによってメタデータを公開します。</span><span class="sxs-lookup"><span data-stu-id="7e3cb-103">Windows Communication Foundation (WCF) services publish metadata by publishing one or more metadata endpoints.</span></span> <span data-ttu-id="7e3cb-104">サービス メタデータを公開すると、そのメタデータで WS-MetadataExchange (MEX) や HTTP/GET 要求などの標準化プロトコルを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="7e3cb-104">Publishing service metadata makes the metadata available using standardized protocols, such as WS-MetadataExchange (MEX) and HTTP/GET requests.</span></span> <span data-ttu-id="7e3cb-105">メタデータのエンドポイントは、アドレス、バインディング、およびコントラクトを持つ他のサービス エンドポイントに似ており、構成またはコードを使用してサービス ホストに追加できます。</span><span class="sxs-lookup"><span data-stu-id="7e3cb-105">Metadata endpoints are similar to other service endpoints in that they have an address, a binding, and a contract, and they can be added to a service host through configuration or in code.</span></span> <span data-ttu-id="7e3cb-106">メタデータ エンドポイントの公開を有効にするには、<xref:System.ServiceModel.Description.ServiceMetadataBehavior> サービス動作をサービスに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e3cb-106">To enable publishing metadata endpoints, you must add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> service behavior to the service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7e3cb-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="7e3cb-107">In This Section</span></span>  

 [<span data-ttu-id="7e3cb-108">方法: 構成ファイルを使用してサービスのメタデータを公開する</span><span class="sxs-lookup"><span data-stu-id="7e3cb-108">How to: Publish Metadata for a Service Using a Configuration File</span></span>](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 <span data-ttu-id="7e3cb-109">クライアントがクエリ文字列を使用して WS-MetadataExchange または HTTP/GET 要求を使用してメタデータを取得できるように、メタデータを公開するように WCF サービスを構成する方法を示し `?wsdl` ます。</span><span class="sxs-lookup"><span data-stu-id="7e3cb-109">Demonstrates how to configure a WCF service to publish metadata so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
 [<span data-ttu-id="7e3cb-110">方法: コードを使用してサービスのメタデータを公開する</span><span class="sxs-lookup"><span data-stu-id="7e3cb-110">How to: Publish Metadata for a Service Using Code</span></span>](./feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 <span data-ttu-id="7e3cb-111">WCF サービスのメタデータ公開をコードで有効にし、クライアントがクエリ文字列を使用して WS-MetadataExchange または HTTP/GET 要求を使用してメタデータを取得できるようにする方法を示し `?wsdl` ます。</span><span class="sxs-lookup"><span data-stu-id="7e3cb-111">Demonstrates how to enable metadata publishing for a WCF service in code so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e3cb-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="7e3cb-112">See also</span></span>

- [<span data-ttu-id="7e3cb-113">メタデータの公開</span><span class="sxs-lookup"><span data-stu-id="7e3cb-113">Publishing Metadata</span></span>](./feature-details/publishing-metadata.md)
