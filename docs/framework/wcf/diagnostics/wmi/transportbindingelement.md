---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: 45bfcd069391156bc85cc4c26f2b172770197a9e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96234844"
---
# <a name="transportbindingelement"></a><span data-ttu-id="9ddf4-102">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9ddf4-102">TransportBindingElement</span></span>

<span data-ttu-id="9ddf4-103">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9ddf4-103">TransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ddf4-104">構文</span><span class="sxs-lookup"><span data-stu-id="9ddf4-104">Syntax</span></span>  
  
```csharp
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="9ddf4-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="9ddf4-105">Methods</span></span>  

 <span data-ttu-id="9ddf4-106">TransportBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="9ddf4-106">The TransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9ddf4-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="9ddf4-107">Properties</span></span>  

 <span data-ttu-id="9ddf4-108">TransportBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="9ddf4-108">The TransportBindingElement class has the following properties:</span></span>  
  
### <a name="manualaddressing"></a><span data-ttu-id="9ddf4-109">ManualAddressing</span><span class="sxs-lookup"><span data-stu-id="9ddf4-109">ManualAddressing</span></span>  

 <span data-ttu-id="9ddf4-110">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="9ddf4-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="9ddf4-111">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="9ddf4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9ddf4-112">メッセージのアドレス指定をユーザーが制御するかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="9ddf4-112">A boolean value that specifies whether the user wants to take control of message addressing.</span></span>  
  
### <a name="maxbufferpoolsize"></a><span data-ttu-id="9ddf4-113">MaxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="9ddf4-113">MaxBufferPoolSize</span></span>  

 <span data-ttu-id="9ddf4-114">データ型 : sint64</span><span class="sxs-lookup"><span data-stu-id="9ddf4-114">Data type: sint64</span></span>  
  
 <span data-ttu-id="9ddf4-115">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="9ddf4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9ddf4-116">バインディングに使用するバッファー プールの最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="9ddf4-116">The maximum buffer pool size for the binding.</span></span>  
  
### <a name="maxreceivedmessagesize"></a><span data-ttu-id="9ddf4-117">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="9ddf4-117">MaxReceivedMessageSize</span></span>  

 <span data-ttu-id="9ddf4-118">データ型 : sint64</span><span class="sxs-lookup"><span data-stu-id="9ddf4-118">Data type: sint64</span></span>  
  
 <span data-ttu-id="9ddf4-119">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="9ddf4-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9ddf4-120">このバインディングで処理されるメッセージの最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="9ddf4-120">The maximum size for a message that is processed by this binding.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="9ddf4-121">Scheme</span><span class="sxs-lookup"><span data-stu-id="9ddf4-121">Scheme</span></span>  

 <span data-ttu-id="9ddf4-122">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="9ddf4-122">Data type: string</span></span>  
  
 <span data-ttu-id="9ddf4-123">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="9ddf4-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9ddf4-124">トランスポートの URI スキーム。</span><span class="sxs-lookup"><span data-stu-id="9ddf4-124">The URI scheme for the transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ddf4-125">要件</span><span class="sxs-lookup"><span data-stu-id="9ddf4-125">Requirements</span></span>  
  
|<span data-ttu-id="9ddf4-126">MOF</span><span class="sxs-lookup"><span data-stu-id="9ddf4-126">MOF</span></span>|<span data-ttu-id="9ddf4-127">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="9ddf4-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9ddf4-128">名前空間</span><span class="sxs-lookup"><span data-stu-id="9ddf4-128">Namespace</span></span>|<span data-ttu-id="9ddf4-129">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="9ddf4-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9ddf4-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ddf4-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TransportBindingElement>
