---
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: 3dcc1f3b27d93d5641a4bb2d8082aa3fa88882dc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274219"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="3b791-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="3b791-102">ChannelPoolSettings</span></span>

<span data-ttu-id="3b791-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="3b791-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b791-104">構文</span><span class="sxs-lookup"><span data-stu-id="3b791-104">Syntax</span></span>  
  
```csharp
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3b791-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="3b791-105">Methods</span></span>  

 <span data-ttu-id="3b791-106">ChannelPoolSettings クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="3b791-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3b791-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="3b791-107">Properties</span></span>  

 <span data-ttu-id="3b791-108">ChannelPoolSettings クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="3b791-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="3b791-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="3b791-109">IdleTimeout</span></span>  

 <span data-ttu-id="3b791-110">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="3b791-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="3b791-111">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3b791-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b791-112">接続が切断されるまでの最大アイドル時間。</span><span class="sxs-lookup"><span data-stu-id="3b791-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="3b791-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="3b791-113">LeaseTimeout</span></span>  

 <span data-ttu-id="3b791-114">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="3b791-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="3b791-115">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3b791-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b791-116">リース操作の完了がタイムアウトするまでの最大時間。</span><span class="sxs-lookup"><span data-stu-id="3b791-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="3b791-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="3b791-117">MaxOutboundChannelsPerEndpoint</span></span>  

 <span data-ttu-id="3b791-118">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="3b791-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="3b791-119">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3b791-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b791-120">各エンドポイントでの送信チャネルの最大数。</span><span class="sxs-lookup"><span data-stu-id="3b791-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b791-121">要件</span><span class="sxs-lookup"><span data-stu-id="3b791-121">Requirements</span></span>  
  
|<span data-ttu-id="3b791-122">MOF</span><span class="sxs-lookup"><span data-stu-id="3b791-122">MOF</span></span>|<span data-ttu-id="3b791-123">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="3b791-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3b791-124">名前空間</span><span class="sxs-lookup"><span data-stu-id="3b791-124">Namespace</span></span>|<span data-ttu-id="3b791-125">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="3b791-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3b791-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="3b791-126">See also</span></span>

- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
