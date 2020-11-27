---
title: MsmqBindingElementBase
ms.date: 03/30/2017
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
ms.openlocfilehash: 48d26bfa9074fd605e3545579f0bdc2744dfc7d8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267860"
---
# <a name="msmqbindingelementbase"></a><span data-ttu-id="3e110-102">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="3e110-102">MsmqBindingElementBase</span></span>

<span data-ttu-id="3e110-103">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="3e110-103">MsmqBindingElementBase</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e110-104">構文</span><span class="sxs-lookup"><span data-stu-id="3e110-104">Syntax</span></span>  
  
```csharp  
class MsmqBindingElementBase : TransportBindingElement  
{  
  string CustomDeadLetterQueue;  
  string DeadLetterQueue;  
  boolean Durable;  
  boolean ExactlyOnce;  
  sint32 MaxRetryCycles;  
  string ReceiveErrorHandling;  
  sint32 ReceiveRetryCount;  
  datetime RetryCycleDelay;  
  datetime TimeToLive;  
  boolean UseMsmqTracing;  
  boolean UseSourceJournal;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3e110-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="3e110-105">Methods</span></span>  

 <span data-ttu-id="3e110-106">MsmqBindingElementBase クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="3e110-106">The MsmqBindingElementBase class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3e110-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="3e110-107">Properties</span></span>  

 <span data-ttu-id="3e110-108">MsmqBindingElementBase クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="3e110-108">The MsmqBindingElementBase class has the following properties:</span></span>  
  
### <a name="customdeadletterqueue"></a><span data-ttu-id="3e110-109">CustomDeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="3e110-109">CustomDeadLetterQueue</span></span>  

 <span data-ttu-id="3e110-110">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="3e110-110">Data type: string</span></span>  
  
 <span data-ttu-id="3e110-111">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3e110-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3e110-112">アプリケーションごとの配信不能キューの場所が含まれている URI です。ここには、期限切れのメッセージや、転送または配信に失敗したメッセージが配置されます。</span><span class="sxs-lookup"><span data-stu-id="3e110-112">A URI that contains the location of the dead letter queue for each application, where messages that have expired or that have failed transfer or delivery are placed.</span></span>  
  
### <a name="deadletterqueue"></a><span data-ttu-id="3e110-113">DeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="3e110-113">DeadLetterQueue</span></span>  

 <span data-ttu-id="3e110-114">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="3e110-114">Data type: string</span></span>  
  
 <span data-ttu-id="3e110-115">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3e110-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3e110-116">使用する配信不能キューの型を示す列挙型の値です。</span><span class="sxs-lookup"><span data-stu-id="3e110-116">An enumeration value that indicates the type of dead letter queue to use.</span></span>  
  
### <a name="durable"></a><span data-ttu-id="3e110-117">Durable</span><span class="sxs-lookup"><span data-stu-id="3e110-117">Durable</span></span>  

 <span data-ttu-id="3e110-118">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="3e110-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="3e110-119">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3e110-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3e110-120">このバインディングによって処理されるメッセージが永続的なものか不安定なものかを示す値です。</span><span class="sxs-lookup"><span data-stu-id="3e110-120">A value that indicates whether the messages processed by this binding are durable or volatile.</span></span>  
  
### <a name="exactlyonce"></a><span data-ttu-id="3e110-121">ExactlyOnce</span><span class="sxs-lookup"><span data-stu-id="3e110-121">ExactlyOnce</span></span>  

 <span data-ttu-id="3e110-122">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="3e110-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="3e110-123">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3e110-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3e110-124">このバインディングで処理されるメッセージが正確に 1 回だけ受信されるかどうかを示すブール値です。</span><span class="sxs-lookup"><span data-stu-id="3e110-124">A Boolean value that indicates whether messages processed by this binding are received exactly once.</span></span>  
  
### <a name="maxretrycycles"></a><span data-ttu-id="3e110-125">MaxRetryCycles</span><span class="sxs-lookup"><span data-stu-id="3e110-125">MaxRetryCycles</span></span>  

 <span data-ttu-id="3e110-126">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="3e110-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="3e110-127">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3e110-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3e110-128">受信アプリケーションにメッセージを配信する再試行サイクルの最大数です。</span><span class="sxs-lookup"><span data-stu-id="3e110-128">The maximum number of retry cycles to attempt delivery of messages to the receiving application.</span></span>  
  
### <a name="receiveerrorhandling"></a><span data-ttu-id="3e110-129">ReceiveErrorHandling</span><span class="sxs-lookup"><span data-stu-id="3e110-129">ReceiveErrorHandling</span></span>  

 <span data-ttu-id="3e110-130">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="3e110-130">Data type: string</span></span>  
  
 <span data-ttu-id="3e110-131">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3e110-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3e110-132">有害メッセージの処理の設定です。</span><span class="sxs-lookup"><span data-stu-id="3e110-132">The settings for poison message handling.</span></span>  
  
### <a name="receiveretrycount"></a><span data-ttu-id="3e110-133">ReceiveRetryCount</span><span class="sxs-lookup"><span data-stu-id="3e110-133">ReceiveRetryCount</span></span>  

 <span data-ttu-id="3e110-134">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="3e110-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="3e110-135">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3e110-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3e110-136">アプリケーション キューから読み取られるメッセージの即時再試行の最大回数です。</span><span class="sxs-lookup"><span data-stu-id="3e110-136">The maximum number of immediate retry attempts on a message that is read from the application queue.</span></span>  
  
### <a name="retrycycledelay"></a><span data-ttu-id="3e110-137">RetryCycleDelay</span><span class="sxs-lookup"><span data-stu-id="3e110-137">RetryCycleDelay</span></span>  

 <span data-ttu-id="3e110-138">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="3e110-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="3e110-139">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3e110-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3e110-140">すぐに配信できなかったメッセージを配信しようとするときの、再試行サイクルの時間遅延を示す値です。</span><span class="sxs-lookup"><span data-stu-id="3e110-140">A value that indicates the time delay between retry cycles when attempting to deliver a message that could not be delivered immediately.</span></span>  
  
### <a name="timetolive"></a><span data-ttu-id="3e110-141">TimeToLive</span><span class="sxs-lookup"><span data-stu-id="3e110-141">TimeToLive</span></span>  

 <span data-ttu-id="3e110-142">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="3e110-142">Data type: datetime</span></span>  
  
 <span data-ttu-id="3e110-143">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3e110-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3e110-144">このバインディングで処理されるメッセージの期限が切れるまで、メッセージをキュー内で保持する時間です。</span><span class="sxs-lookup"><span data-stu-id="3e110-144">The interval of time that indicates how long the messages processed by this binding can be in the queue before they expire.</span></span>  
  
### <a name="usemsmqtracing"></a><span data-ttu-id="3e110-145">UseMsmqTracing</span><span class="sxs-lookup"><span data-stu-id="3e110-145">UseMsmqTracing</span></span>  

 <span data-ttu-id="3e110-146">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="3e110-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="3e110-147">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3e110-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3e110-148">このバインディングにより処理されるメッセージをトレースするかどうかを示すブール値です。</span><span class="sxs-lookup"><span data-stu-id="3e110-148">A Boolean value that indicates whether messages processed by this binding should be traced.</span></span>  
  
### <a name="usesourcejournal"></a><span data-ttu-id="3e110-149">UseSourceJournal</span><span class="sxs-lookup"><span data-stu-id="3e110-149">UseSourceJournal</span></span>  

 <span data-ttu-id="3e110-150">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="3e110-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="3e110-151">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="3e110-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3e110-152">このバインディングにより処理されるメッセージのコピーをソース ジャーナル キューに保存するかどうかを示すブール値です。</span><span class="sxs-lookup"><span data-stu-id="3e110-152">A Boolean value that indicates whether copies of messages processed by this binding should be stored in the source journal queue.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e110-153">要件</span><span class="sxs-lookup"><span data-stu-id="3e110-153">Requirements</span></span>  
  
|<span data-ttu-id="3e110-154">MOF</span><span class="sxs-lookup"><span data-stu-id="3e110-154">MOF</span></span>|<span data-ttu-id="3e110-155">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="3e110-155">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3e110-156">名前空間</span><span class="sxs-lookup"><span data-stu-id="3e110-156">Namespace</span></span>|<span data-ttu-id="3e110-157">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="3e110-157">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3e110-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e110-158">See also</span></span>

- <xref:System.ServiceModel.NetMsmqBinding>
- <xref:System.ServiceModel.MsmqBindingBase>
