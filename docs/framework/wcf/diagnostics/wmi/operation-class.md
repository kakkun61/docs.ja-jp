---
title: Operation class
ms.date: 03/30/2017
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
ms.openlocfilehash: 6b47d933dc84813532398830c92c95210208a709
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269159"
---
# <a name="operation-class"></a><span data-ttu-id="c4161-102">Operation class</span><span class="sxs-lookup"><span data-stu-id="c4161-102">Operation class</span></span>

<span data-ttu-id="c4161-103">操作</span><span class="sxs-lookup"><span data-stu-id="c4161-103">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4161-104">構文</span><span class="sxs-lookup"><span data-stu-id="c4161-104">Syntax</span></span>  
  
```csharp
class Operation  
{  
  string Action;  
  boolean AsyncPattern;  
  Behavior Behaviors[];  
  boolean IsCallback;  
  boolean IsInitiating;  
  boolean IsOneWay;  
  boolean IsTerminating;  
  string MethodSignature;  
  string Name;  
  string ParameterTypes[];  
  string ReplyAction;  
  string ReturnType;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c4161-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="c4161-105">Methods</span></span>  

 <span data-ttu-id="c4161-106">Operation クラスで定義されているメソッドはありせん。</span><span class="sxs-lookup"><span data-stu-id="c4161-106">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c4161-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c4161-107">Properties</span></span>  

 <span data-ttu-id="c4161-108">Operation クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="c4161-108">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="c4161-109">アクション</span><span class="sxs-lookup"><span data-stu-id="c4161-109">Action</span></span>  

 <span data-ttu-id="c4161-110">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="c4161-110">Data type: string</span></span>  
  
 <span data-ttu-id="c4161-111">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c4161-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4161-112">要求メッセージの WS-Addressing 操作。</span><span class="sxs-lookup"><span data-stu-id="c4161-112">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="c4161-113">AsyncPattern</span><span class="sxs-lookup"><span data-stu-id="c4161-113">AsyncPattern</span></span>  

 <span data-ttu-id="c4161-114">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="c4161-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="c4161-115">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c4161-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4161-116">`Begin`サービスコントラクトで [開始/終了山かっこ] と `End` [開始/終了山かっこ] の組み合わせを使用して、操作が非同期的に実装されることを示します。</span><span class="sxs-lookup"><span data-stu-id="c4161-116">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="c4161-117">動作</span><span class="sxs-lookup"><span data-stu-id="c4161-117">Behaviors</span></span>  

 <span data-ttu-id="c4161-118">データ型 : Behavior array</span><span class="sxs-lookup"><span data-stu-id="c4161-118">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="c4161-119">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c4161-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4161-120">この操作に関連付けられている動作。</span><span class="sxs-lookup"><span data-stu-id="c4161-120">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="c4161-121">IsCallback</span><span class="sxs-lookup"><span data-stu-id="c4161-121">IsCallback</span></span>  

 <span data-ttu-id="c4161-122">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="c4161-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="c4161-123">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c4161-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4161-124">この操作がコールバック操作の場合、True。</span><span class="sxs-lookup"><span data-stu-id="c4161-124">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="c4161-125">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="c4161-125">IsInitiating</span></span>  

 <span data-ttu-id="c4161-126">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="c4161-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="c4161-127">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c4161-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4161-128">メソッドが、サーバーでセッションを開始できる操作を実装するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c4161-128">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="c4161-129">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="c4161-129">IsOneWay</span></span>  

 <span data-ttu-id="c4161-130">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="c4161-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="c4161-131">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c4161-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4161-132">操作が応答メッセージを返すかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c4161-132">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="c4161-133">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="c4161-133">IsTerminating</span></span>  

 <span data-ttu-id="c4161-134">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="c4161-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="c4161-135">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c4161-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4161-136">操作が応答メッセージを返すかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c4161-136">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="c4161-137">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="c4161-137">MethodSignature</span></span>  

 <span data-ttu-id="c4161-138">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="c4161-138">Data type: string</span></span>  
  
 <span data-ttu-id="c4161-139">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c4161-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4161-140">操作のメソッド署名。</span><span class="sxs-lookup"><span data-stu-id="c4161-140">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="c4161-141">名前</span><span class="sxs-lookup"><span data-stu-id="c4161-141">Name</span></span>  

 <span data-ttu-id="c4161-142">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="c4161-142">Data type: string</span></span>  
  
 <span data-ttu-id="c4161-143">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c4161-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4161-144">操作の名前。</span><span class="sxs-lookup"><span data-stu-id="c4161-144">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="c4161-145">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="c4161-145">ParameterTypes</span></span>  

 <span data-ttu-id="c4161-146">データ型 : string array</span><span class="sxs-lookup"><span data-stu-id="c4161-146">Data type: string array</span></span>  
  
 <span data-ttu-id="c4161-147">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c4161-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4161-148">操作のパラメーターの型。</span><span class="sxs-lookup"><span data-stu-id="c4161-148">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="c4161-149">ReplyAction</span><span class="sxs-lookup"><span data-stu-id="c4161-149">ReplyAction</span></span>  

 <span data-ttu-id="c4161-150">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="c4161-150">Data type: string</span></span>  
  
 <span data-ttu-id="c4161-151">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c4161-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4161-152">操作の応答メッセージの SOAP アクションの値。</span><span class="sxs-lookup"><span data-stu-id="c4161-152">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="c4161-153">ReturnType</span><span class="sxs-lookup"><span data-stu-id="c4161-153">ReturnType</span></span>  

 <span data-ttu-id="c4161-154">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="c4161-154">Data type: string</span></span>  
  
 <span data-ttu-id="c4161-155">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c4161-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4161-156">操作の戻り値の型。</span><span class="sxs-lookup"><span data-stu-id="c4161-156">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4161-157">要件</span><span class="sxs-lookup"><span data-stu-id="c4161-157">Requirements</span></span>  
  
|<span data-ttu-id="c4161-158">MOF</span><span class="sxs-lookup"><span data-stu-id="c4161-158">MOF</span></span>|<span data-ttu-id="c4161-159">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="c4161-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c4161-160">名前空間</span><span class="sxs-lookup"><span data-stu-id="c4161-160">Namespace</span></span>|<span data-ttu-id="c4161-161">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="c4161-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c4161-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4161-162">See also</span></span>

- <xref:System.ServiceModel.Description.OperationDescription>
