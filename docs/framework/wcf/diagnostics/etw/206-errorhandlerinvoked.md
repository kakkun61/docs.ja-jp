---
title: 206 - ErrorHandlerInvoked
ms.date: 03/30/2017
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
ms.openlocfilehash: 99415733624752217d32f6f026a419b2b32bfa7b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244614"
---
# <a name="206---errorhandlerinvoked"></a><span data-ttu-id="d8660-102">206 - ErrorHandlerInvoked</span><span class="sxs-lookup"><span data-stu-id="d8660-102">206 - ErrorHandlerInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="d8660-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d8660-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d8660-104">ID</span><span class="sxs-lookup"><span data-stu-id="d8660-104">ID</span></span>|<span data-ttu-id="d8660-105">206</span><span class="sxs-lookup"><span data-stu-id="d8660-105">206</span></span>|  
|<span data-ttu-id="d8660-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="d8660-106">Keywords</span></span>|<span data-ttu-id="d8660-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d8660-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="d8660-108">Level</span><span class="sxs-lookup"><span data-stu-id="d8660-108">Level</span></span>|<span data-ttu-id="d8660-109">情報</span><span class="sxs-lookup"><span data-stu-id="d8660-109">Information</span></span>|  
|<span data-ttu-id="d8660-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="d8660-110">Channel</span></span>|<span data-ttu-id="d8660-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="d8660-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d8660-112">Description</span><span class="sxs-lookup"><span data-stu-id="d8660-112">Description</span></span>  

 <span data-ttu-id="d8660-113">このイベントは、サービス操作中に発生した例外を処理する機会が `ErrorHandler` に与えられた後に、生成されます。</span><span class="sxs-lookup"><span data-stu-id="d8660-113">This event is emitted after an `ErrorHandler` has had an opportunity to handle an exception that occurred in a service operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d8660-114">Message</span><span class="sxs-lookup"><span data-stu-id="d8660-114">Message</span></span>  

 <span data-ttu-id="d8660-115">ディスパッチャーが型 ' %1 ' の ErrorHandler を呼び出しましたが、型 ' %3 ' の例外が発生しました。</span><span class="sxs-lookup"><span data-stu-id="d8660-115">The Dispatcher invoked an ErrorHandler of type '%1' with an exception of type '%3'.</span></span> <span data-ttu-id="d8660-116">ErrorHandled == '%2'。</span><span class="sxs-lookup"><span data-stu-id="d8660-116">ErrorHandled == '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d8660-117">詳細</span><span class="sxs-lookup"><span data-stu-id="d8660-117">Details</span></span>  
  
|<span data-ttu-id="d8660-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="d8660-118">Data Item Name</span></span>|<span data-ttu-id="d8660-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="d8660-119">Data Item Type</span></span>|<span data-ttu-id="d8660-120">説明</span><span class="sxs-lookup"><span data-stu-id="d8660-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d8660-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="d8660-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="d8660-122">呼び出された `ErrorHandler` の型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="d8660-122">The CLR FullName of the type of the invoked `ErrorHandler`.</span></span>|  
|<span data-ttu-id="d8660-123">処理済み</span><span class="sxs-lookup"><span data-stu-id="d8660-123">Handled</span></span>|`xs:unsignedByte`|<span data-ttu-id="d8660-124">エラー ハンドラーがエラーを処理した場合は `true`。それ以外の場合は `false`。</span><span class="sxs-lookup"><span data-stu-id="d8660-124">`true` if the error handler handled the error, otherwise `false`.</span></span>|  
|<span data-ttu-id="d8660-125">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="d8660-125">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="d8660-126">処理対象である例外の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="d8660-126">The CLR FullName of the exception that was being handled.</span></span>|  
|<span data-ttu-id="d8660-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="d8660-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="d8660-128">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="d8660-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="d8660-129">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="d8660-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="d8660-130">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="d8660-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="d8660-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d8660-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="d8660-132">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="d8660-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
