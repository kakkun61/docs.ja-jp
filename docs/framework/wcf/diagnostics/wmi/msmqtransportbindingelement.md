---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 6590c5188e4e1758987a75fbd007099703ea6bc5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250425"
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="42b28-102">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="42b28-102">MsmqTransportBindingElement</span></span>

<span data-ttu-id="42b28-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="42b28-103">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42b28-104">構文</span><span class="sxs-lookup"><span data-stu-id="42b28-104">Syntax</span></span>  
  
```csharp
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="42b28-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="42b28-105">Methods</span></span>  

 <span data-ttu-id="42b28-106">MsmqTransportBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="42b28-106">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="42b28-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="42b28-107">Properties</span></span>  

 <span data-ttu-id="42b28-108">MsmqTransportBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="42b28-108">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="42b28-109">MaxPoolSize</span><span class="sxs-lookup"><span data-stu-id="42b28-109">MaxPoolSize</span></span>  

 <span data-ttu-id="42b28-110">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="42b28-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="42b28-111">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="42b28-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="42b28-112">内部 MSMQ メッセージ オブジェクトを含むプールの最大サイズです。</span><span class="sxs-lookup"><span data-stu-id="42b28-112">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="42b28-113">QueueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="42b28-113">QueueTransferProtocol</span></span>  

 <span data-ttu-id="42b28-114">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="42b28-114">Data type: string</span></span>  
  
 <span data-ttu-id="42b28-115">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="42b28-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="42b28-116">このバインディングが使用するキューに置かれた通信チャネルのトランスポートを示す列挙値です。</span><span class="sxs-lookup"><span data-stu-id="42b28-116">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="42b28-117">UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="42b28-117">UseActiveDirectory</span></span>  

 <span data-ttu-id="42b28-118">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="42b28-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="42b28-119">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="42b28-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="42b28-120">キューのアドレスを Active Directory を使用して変換する必要があるかどうかを示すブール値を返します。</span><span class="sxs-lookup"><span data-stu-id="42b28-120">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42b28-121">要件</span><span class="sxs-lookup"><span data-stu-id="42b28-121">Requirements</span></span>  
  
|<span data-ttu-id="42b28-122">MOF</span><span class="sxs-lookup"><span data-stu-id="42b28-122">MOF</span></span>|<span data-ttu-id="42b28-123">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="42b28-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="42b28-124">名前空間</span><span class="sxs-lookup"><span data-stu-id="42b28-124">Namespace</span></span>|<span data-ttu-id="42b28-125">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="42b28-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="42b28-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="42b28-126">See also</span></span>

- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
