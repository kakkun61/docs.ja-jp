---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: 806066a8845068413d2a52c78878f76b5f5fa34f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250373"
---
# <a name="onewaybindingelement"></a><span data-ttu-id="6d252-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="6d252-102">OneWayBindingElement</span></span>

<span data-ttu-id="6d252-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="6d252-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d252-104">構文</span><span class="sxs-lookup"><span data-stu-id="6d252-104">Syntax</span></span>  
  
```csharp
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6d252-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="6d252-105">Methods</span></span>  

 <span data-ttu-id="6d252-106">OneWayBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="6d252-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6d252-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="6d252-107">Properties</span></span>  

 <span data-ttu-id="6d252-108">OneWayBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="6d252-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="6d252-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="6d252-109">ChannelPoolSettings</span></span>  

 <span data-ttu-id="6d252-110">データ型 : ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="6d252-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="6d252-111">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6d252-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d252-112">チャネル プールの設定。</span><span class="sxs-lookup"><span data-stu-id="6d252-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="6d252-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="6d252-113">MaxAcceptedChannels</span></span>  

 <span data-ttu-id="6d252-114">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="6d252-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="6d252-115">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6d252-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d252-116">許可されるチャネルの最大数。</span><span class="sxs-lookup"><span data-stu-id="6d252-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="6d252-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="6d252-117">PacketRoutable</span></span>  

 <span data-ttu-id="6d252-118">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="6d252-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="6d252-119">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6d252-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d252-120">パケットがルーティング可能かどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="6d252-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d252-121">要件</span><span class="sxs-lookup"><span data-stu-id="6d252-121">Requirements</span></span>  
  
|<span data-ttu-id="6d252-122">MOF</span><span class="sxs-lookup"><span data-stu-id="6d252-122">MOF</span></span>|<span data-ttu-id="6d252-123">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="6d252-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6d252-124">名前空間</span><span class="sxs-lookup"><span data-stu-id="6d252-124">Namespace</span></span>|<span data-ttu-id="6d252-125">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="6d252-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6d252-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d252-126">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
