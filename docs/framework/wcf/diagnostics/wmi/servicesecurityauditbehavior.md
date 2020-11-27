---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
ms.openlocfilehash: 9da8f77ee8ea5dc8b22ac5c0cb5113e906c5dc78
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262269"
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="1e920-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="1e920-102">ServiceSecurityAuditBehavior</span></span>

<span data-ttu-id="1e920-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="1e920-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e920-104">構文</span><span class="sxs-lookup"><span data-stu-id="1e920-104">Syntax</span></span>  
  
```csharp  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="1e920-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="1e920-105">Methods</span></span>  

 <span data-ttu-id="1e920-106">ServiceSecurityAuditBehavior クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="1e920-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1e920-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="1e920-107">Properties</span></span>  

 <span data-ttu-id="1e920-108">ServiceSecurityAuditBehavior クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="1e920-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="1e920-109">AuditLogLocation</span><span class="sxs-lookup"><span data-stu-id="1e920-109">AuditLogLocation</span></span>  

 <span data-ttu-id="1e920-110">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="1e920-110">Data type: string</span></span>  
  
 <span data-ttu-id="1e920-111">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="1e920-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1e920-112">監査ログの場所。</span><span class="sxs-lookup"><span data-stu-id="1e920-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="1e920-113">MessageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="1e920-113">MessageAuthenticationAuditLevel</span></span>  

 <span data-ttu-id="1e920-114">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="1e920-114">Data type: string</span></span>  
  
 <span data-ttu-id="1e920-115">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="1e920-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1e920-116">監査イベントをログに記録するために使用されるメッセージ認証レベルの種類。</span><span class="sxs-lookup"><span data-stu-id="1e920-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="1e920-117">ServiceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="1e920-117">ServiceAuthorizationAuditLevel</span></span>  

 <span data-ttu-id="1e920-118">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="1e920-118">Data type: string</span></span>  
  
 <span data-ttu-id="1e920-119">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="1e920-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1e920-120">監査ログに記録される承認イベントの種類。</span><span class="sxs-lookup"><span data-stu-id="1e920-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="1e920-121">SuppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="1e920-121">SuppressAuditFailure</span></span>  

 <span data-ttu-id="1e920-122">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="1e920-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="1e920-123">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="1e920-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1e920-124">監査ログへの書き込みエラーを非表示にする動作を指定するブール型の値。</span><span class="sxs-lookup"><span data-stu-id="1e920-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e920-125">要件</span><span class="sxs-lookup"><span data-stu-id="1e920-125">Requirements</span></span>  
  
|<span data-ttu-id="1e920-126">MOF</span><span class="sxs-lookup"><span data-stu-id="1e920-126">MOF</span></span>|<span data-ttu-id="1e920-127">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="1e920-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1e920-128">名前空間</span><span class="sxs-lookup"><span data-stu-id="1e920-128">Namespace</span></span>|<span data-ttu-id="1e920-129">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="1e920-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1e920-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="1e920-130">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
