---
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
ms.openlocfilehash: 00485ff80a0064e700d99203de3aa581d3761f30
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255729"
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="e742a-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="e742a-102">AsymmetricSecurityBindingElement</span></span>

<span data-ttu-id="e742a-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="e742a-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e742a-104">構文</span><span class="sxs-lookup"><span data-stu-id="e742a-104">Syntax</span></span>  
  
```csharp
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e742a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="e742a-105">Methods</span></span>  

 <span data-ttu-id="e742a-106">AsymmetricSecurityBindingElement クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="e742a-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e742a-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e742a-107">Properties</span></span>  

 <span data-ttu-id="e742a-108">AsymmetricSecurityBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="e742a-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="e742a-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="e742a-109">MessageProtectionOrder</span></span>  

 <span data-ttu-id="e742a-110">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="e742a-110">Data type: string</span></span>  
  
 <span data-ttu-id="e742a-111">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="e742a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e742a-112">このバインディングのメッセージの暗号化と署名の命令。</span><span class="sxs-lookup"><span data-stu-id="e742a-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="e742a-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="e742a-113">RequireSignatureConfirmation</span></span>  

 <span data-ttu-id="e742a-114">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="e742a-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="e742a-115">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="e742a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e742a-116">バインディングで署名の確認が必要かどうか。</span><span class="sxs-lookup"><span data-stu-id="e742a-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e742a-117">要件</span><span class="sxs-lookup"><span data-stu-id="e742a-117">Requirements</span></span>  
  
|<span data-ttu-id="e742a-118">MOF</span><span class="sxs-lookup"><span data-stu-id="e742a-118">MOF</span></span>|<span data-ttu-id="e742a-119">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="e742a-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e742a-120">名前空間</span><span class="sxs-lookup"><span data-stu-id="e742a-120">Namespace</span></span>|<span data-ttu-id="e742a-121">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="e742a-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e742a-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="e742a-122">See also</span></span>

- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
