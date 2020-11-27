---
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 8422e1adf9a8914b631431eba5c9c0ed058cd0f3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258024"
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="82432-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="82432-102">NamedPipeConnectionPoolSettings</span></span>

<span data-ttu-id="82432-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="82432-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82432-104">構文</span><span class="sxs-lookup"><span data-stu-id="82432-104">Syntax</span></span>  
  
```csharp
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="82432-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="82432-105">Methods</span></span>  

 <span data-ttu-id="82432-106">NamedPipeConnectionPoolSettings クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="82432-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="82432-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="82432-107">Properties</span></span>  

 <span data-ttu-id="82432-108">NamedPipeConnectionPoolSettings クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="82432-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="82432-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="82432-109">GroupName</span></span>  

 <span data-ttu-id="82432-110">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="82432-110">Data type: string</span></span>  
  
 <span data-ttu-id="82432-111">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="82432-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="82432-112">バインド要素により使用される接続プールのグループ名。</span><span class="sxs-lookup"><span data-stu-id="82432-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="82432-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="82432-113">IdleTimeout</span></span>  

 <span data-ttu-id="82432-114">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="82432-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="82432-115">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="82432-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="82432-116">接続が切断されるまでの最大アイドル時間。</span><span class="sxs-lookup"><span data-stu-id="82432-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="82432-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="82432-117">MaxOutboundConnectionsPerEndpoint</span></span>  

 <span data-ttu-id="82432-118">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="82432-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="82432-119">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="82432-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="82432-120">クライアント上の各エンドポイントでの発信接続の最大数。</span><span class="sxs-lookup"><span data-stu-id="82432-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82432-121">要件</span><span class="sxs-lookup"><span data-stu-id="82432-121">Requirements</span></span>  
  
|<span data-ttu-id="82432-122">MOF</span><span class="sxs-lookup"><span data-stu-id="82432-122">MOF</span></span>|<span data-ttu-id="82432-123">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="82432-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="82432-124">名前空間</span><span class="sxs-lookup"><span data-stu-id="82432-124">Namespace</span></span>|<span data-ttu-id="82432-125">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="82432-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="82432-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="82432-126">See also</span></span>

- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
