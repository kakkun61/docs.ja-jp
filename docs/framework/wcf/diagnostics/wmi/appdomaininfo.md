---
title: AppDomainInfo
ms.date: 03/30/2017
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
ms.openlocfilehash: c5c44f4d8f6d93443802d5e1950c4d850976c5b6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96291129"
---
# <a name="appdomaininfo"></a><span data-ttu-id="6c358-102">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="6c358-102">AppDomainInfo</span></span>

<span data-ttu-id="6c358-103">アプリケーション ドメイン情報</span><span class="sxs-lookup"><span data-stu-id="6c358-103">Application domain information</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c358-104">構文</span><span class="sxs-lookup"><span data-stu-id="6c358-104">Syntax</span></span>  
  
```csharp
class AppDomainInfo  
{  
  sint32 AppDomainId;  
  boolean IsDefault;  
  boolean LogMalformedMessages;  
  boolean LogMessagesAtServiceLevel;  
  boolean LogMessagesAtTransportLevel;  
  TraceListener MessageLoggingTraceListeners[];  
  string Name;  
  string PerformanceCounters;  
  sint32 ProcessId;  
  string ServiceConfigPath;  
  string TraceLevel;  
  TraceListener wmiTraceListeners[];  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6c358-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="6c358-105">Methods</span></span>  

 <span data-ttu-id="6c358-106">AppDomainInfo クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="6c358-106">The AppDomainInfo class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6c358-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="6c358-107">Properties</span></span>  

 <span data-ttu-id="6c358-108">AppDomainInfo クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="6c358-108">The AppDomainInfo class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="6c358-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="6c358-109">AppDomainId</span></span>  

 <span data-ttu-id="6c358-110">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="6c358-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="6c358-111">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6c358-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6c358-112">AppDomain の ID です。</span><span class="sxs-lookup"><span data-stu-id="6c358-112">The Id of the appdomain.</span></span>  
  
### <a name="isdefault"></a><span data-ttu-id="6c358-113">IsDefault</span><span class="sxs-lookup"><span data-stu-id="6c358-113">IsDefault</span></span>  

 <span data-ttu-id="6c358-114">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="6c358-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="6c358-115">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6c358-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6c358-116">AppDomain が既定の AppDomain かどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="6c358-116">Indicates whether the appdomain is the default appdomain.</span></span>  
  
### <a name="logmalformedmessages"></a><span data-ttu-id="6c358-117">LogMalformedMessages</span><span class="sxs-lookup"><span data-stu-id="6c358-117">LogMalformedMessages</span></span>  

 <span data-ttu-id="6c358-118">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="6c358-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="6c358-119">アクセスの種類 : 読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="6c358-119">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="6c358-120">非整形式メッセージをログに記録するかどうかを指定する値です。</span><span class="sxs-lookup"><span data-stu-id="6c358-120">A value that specifies whether malformed messages are logged.</span></span>  
  
### <a name="logmessagesatservicelevel"></a><span data-ttu-id="6c358-121">LogMessagesAtServiceLevel</span><span class="sxs-lookup"><span data-stu-id="6c358-121">LogMessagesAtServiceLevel</span></span>  

 <span data-ttu-id="6c358-122">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="6c358-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="6c358-123">アクセスの種類 : 読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="6c358-123">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="6c358-124">メッセージをサービス レベルでトレースするかどうかを指定する値です (暗号化およびトランスポート関連の変換前)。</span><span class="sxs-lookup"><span data-stu-id="6c358-124">A value that specifies whether messages are traced at the service level (before encryption and transport-related transforms).</span></span>  
  
### <a name="logmessagesattransportlevel"></a><span data-ttu-id="6c358-125">LogMessagesAtTransportLevel</span><span class="sxs-lookup"><span data-stu-id="6c358-125">LogMessagesAtTransportLevel</span></span>  

 <span data-ttu-id="6c358-126">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="6c358-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="6c358-127">アクセスの種類 : 読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="6c358-127">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="6c358-128">メッセージをトランスポート レベルでトレースするかどうかを指定する値です。</span><span class="sxs-lookup"><span data-stu-id="6c358-128">A value that specifies whether messages are traced at the transport level.</span></span>  
  
### <a name="messageloggingtracelisteners"></a><span data-ttu-id="6c358-129">MessageLoggingTraceListeners</span><span class="sxs-lookup"><span data-stu-id="6c358-129">MessageLoggingTraceListeners</span></span>  

 <span data-ttu-id="6c358-130">データ型 : TraceListener 配列</span><span class="sxs-lookup"><span data-stu-id="6c358-130">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="6c358-131">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6c358-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6c358-132">System.Wmi.MessageLogging トレース ソースをリッスンするコレクション トレース リスナーです。</span><span class="sxs-lookup"><span data-stu-id="6c358-132">The collection trace listeners that listen to the System.Wmi.MessageLogging trace source.</span></span>  
  
### <a name="name"></a><span data-ttu-id="6c358-133">名前</span><span class="sxs-lookup"><span data-stu-id="6c358-133">Name</span></span>  

 <span data-ttu-id="6c358-134">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="6c358-134">Data type: string</span></span>  
  
 <span data-ttu-id="6c358-135">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6c358-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6c358-136">AppDomain の名前です。</span><span class="sxs-lookup"><span data-stu-id="6c358-136">The name of the appdomain.</span></span>  
  
### <a name="performancecounters"></a><span data-ttu-id="6c358-137">PerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="6c358-137">PerformanceCounters</span></span>  

 <span data-ttu-id="6c358-138">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="6c358-138">Data type: string</span></span>  
  
 <span data-ttu-id="6c358-139">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6c358-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6c358-140">AppDomain におけるアクティブなパフォーマンス カウンターのスコープです。</span><span class="sxs-lookup"><span data-stu-id="6c358-140">The scope of active performance counters in the appdomain.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="6c358-141">ProcessId</span><span class="sxs-lookup"><span data-stu-id="6c358-141">ProcessId</span></span>  

 <span data-ttu-id="6c358-142">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="6c358-142">Data type: sint32</span></span>  
  
 <span data-ttu-id="6c358-143">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6c358-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6c358-144">プロセス ID です。</span><span class="sxs-lookup"><span data-stu-id="6c358-144">The process Id.</span></span>  
  
### <a name="serviceconfigpath"></a><span data-ttu-id="6c358-145">ServiceConfigPath</span><span class="sxs-lookup"><span data-stu-id="6c358-145">ServiceConfigPath</span></span>  

 <span data-ttu-id="6c358-146">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="6c358-146">Data type: string</span></span>  
  
 <span data-ttu-id="6c358-147">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6c358-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6c358-148">サービスの構成へのパスです。</span><span class="sxs-lookup"><span data-stu-id="6c358-148">The path to the configuration of the service.</span></span>  
  
### <a name="tracelevel"></a><span data-ttu-id="6c358-149">TraceLevel</span><span class="sxs-lookup"><span data-stu-id="6c358-149">TraceLevel</span></span>  

 <span data-ttu-id="6c358-150">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="6c358-150">Data type: string</span></span>  
  
 <span data-ttu-id="6c358-151">アクセスの種類 : 読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="6c358-151">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="6c358-152">System.Wmi トレース ソースのトレース レベル。</span><span class="sxs-lookup"><span data-stu-id="6c358-152">The trace level of the System.Wmi trace source.</span></span>  
  
### <a name="servicemodeltracelisteners"></a><span data-ttu-id="6c358-153">ServiceModelTraceListeners</span><span class="sxs-lookup"><span data-stu-id="6c358-153">ServiceModelTraceListeners</span></span>  

 <span data-ttu-id="6c358-154">データ型 : TraceListener 配列</span><span class="sxs-lookup"><span data-stu-id="6c358-154">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="6c358-155">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="6c358-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6c358-156">System.ServiceModel トレース ソースのリスナーのコレクション。</span><span class="sxs-lookup"><span data-stu-id="6c358-156">A collection of listeners from the System.ServiceModel trace source.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c358-157">要件</span><span class="sxs-lookup"><span data-stu-id="6c358-157">Requirements</span></span>  
  
|<span data-ttu-id="6c358-158">MOF</span><span class="sxs-lookup"><span data-stu-id="6c358-158">MOF</span></span>|<span data-ttu-id="6c358-159">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="6c358-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6c358-160">名前空間</span><span class="sxs-lookup"><span data-stu-id="6c358-160">Namespace</span></span>|<span data-ttu-id="6c358-161">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="6c358-161">Defined in root\ServiceModel</span></span>|
