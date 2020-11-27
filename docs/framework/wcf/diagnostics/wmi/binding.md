---
title: Binding2
ms.date: 03/30/2017
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
ms.openlocfilehash: b72bd3903b7139c4adf2a8bd0ced6c34e7285640
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274297"
---
# <a name="binding"></a><span data-ttu-id="ce585-102">バインド</span><span class="sxs-lookup"><span data-stu-id="ce585-102">Binding</span></span>

<span data-ttu-id="ce585-103">wmi バインディング</span><span class="sxs-lookup"><span data-stu-id="ce585-103">wmi Binding</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce585-104">構文</span><span class="sxs-lookup"><span data-stu-id="ce585-104">Syntax</span></span>  
  
```csharp
class Binding  
{  
  BindingElement BindingElements[];  
  datetime CloseTimeout;  
  string Name;  
  string Namespace;  
  datetime OpenTimeout;  
  datetime ReceiveTimeout;  
  string Scheme;  
  datetime SendTimeout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ce585-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="ce585-105">Methods</span></span>  

 <span data-ttu-id="ce585-106">Binding クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="ce585-106">The Binding class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ce585-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ce585-107">Properties</span></span>  

 <span data-ttu-id="ce585-108">Binding クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="ce585-108">The Binding class has the following properties.</span></span>  
  
### <a name="bindingelements"></a><span data-ttu-id="ce585-109">BindingElements</span><span class="sxs-lookup"><span data-stu-id="ce585-109">BindingElements</span></span>  

 <span data-ttu-id="ce585-110">データ型 : BindingElement 配列</span><span class="sxs-lookup"><span data-stu-id="ce585-110">Data type: BindingElement array</span></span>  
  
 <span data-ttu-id="ce585-111">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ce585-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ce585-112">バインディングによって実装されるバインド要素のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="ce585-112">The collection of binding elements implemented by the binding.</span></span>  
  
### <a name="closetimeout"></a><span data-ttu-id="ce585-113">CloseTimeout</span><span class="sxs-lookup"><span data-stu-id="ce585-113">CloseTimeout</span></span>  

 <span data-ttu-id="ce585-114">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="ce585-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="ce585-115">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ce585-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ce585-116">クローズ操作が完了するまで待機する時間です。</span><span class="sxs-lookup"><span data-stu-id="ce585-116">The interval of time provided for a close operation to complete.</span></span>  
  
### <a name="name"></a><span data-ttu-id="ce585-117">名前</span><span class="sxs-lookup"><span data-stu-id="ce585-117">Name</span></span>  

 <span data-ttu-id="ce585-118">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="ce585-118">Data type: string</span></span>  
  
 <span data-ttu-id="ce585-119">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ce585-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ce585-120">バインディングの名前。</span><span class="sxs-lookup"><span data-stu-id="ce585-120">The name of the binding.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="ce585-121">名前空間</span><span class="sxs-lookup"><span data-stu-id="ce585-121">Namespace</span></span>  

 <span data-ttu-id="ce585-122">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="ce585-122">Data type: string</span></span>  
  
 <span data-ttu-id="ce585-123">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ce585-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ce585-124">バインディングの XML 名前空間。</span><span class="sxs-lookup"><span data-stu-id="ce585-124">The XML namespace of the binding.</span></span>  
  
### <a name="opentimeout"></a><span data-ttu-id="ce585-125">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="ce585-125">OpenTimeout</span></span>  

 <span data-ttu-id="ce585-126">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="ce585-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="ce585-127">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ce585-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ce585-128">オープン操作が完了するまで待機する時間です。</span><span class="sxs-lookup"><span data-stu-id="ce585-128">The interval of time provided for an open operation to complete.</span></span>  
  
### <a name="receivetimeout"></a><span data-ttu-id="ce585-129">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="ce585-129">ReceiveTimeout</span></span>  

 <span data-ttu-id="ce585-130">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="ce585-130">Data type: datetime</span></span>  
  
 <span data-ttu-id="ce585-131">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ce585-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ce585-132">受信操作が完了するまで待機する時間です。</span><span class="sxs-lookup"><span data-stu-id="ce585-132">The interval of time provided for a receive operation to complete.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="ce585-133">Scheme</span><span class="sxs-lookup"><span data-stu-id="ce585-133">Scheme</span></span>  

 <span data-ttu-id="ce585-134">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="ce585-134">Data type: string</span></span>  
  
 <span data-ttu-id="ce585-135">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ce585-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ce585-136">このバインディングに組み込まれているチャネルおよびリスナー ファクトリによって使用される URI トランスポート スキームです。</span><span class="sxs-lookup"><span data-stu-id="ce585-136">The URI transport scheme that is used by the channel and listener factories that are built by the binding.</span></span>  
  
### <a name="sendtimeout"></a><span data-ttu-id="ce585-137">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="ce585-137">SendTimeout</span></span>  

 <span data-ttu-id="ce585-138">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="ce585-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="ce585-139">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ce585-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ce585-140">送信操作が完了するまで待機する時間です。</span><span class="sxs-lookup"><span data-stu-id="ce585-140">The interval of time provided for a send operation to complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce585-141">要件</span><span class="sxs-lookup"><span data-stu-id="ce585-141">Requirements</span></span>  
  
|<span data-ttu-id="ce585-142">MOF</span><span class="sxs-lookup"><span data-stu-id="ce585-142">MOF</span></span>|<span data-ttu-id="ce585-143">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="ce585-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ce585-144">名前空間</span><span class="sxs-lookup"><span data-stu-id="ce585-144">Namespace</span></span>|<span data-ttu-id="ce585-145">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="ce585-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ce585-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="ce585-146">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
