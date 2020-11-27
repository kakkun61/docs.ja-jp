---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
ms.openlocfilehash: c618b5b41790b04a84b4c50fe47baa2c0cb05ab2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274102"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="e2993-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="e2993-102">SymmetricSecurityBindingElement</span></span>

<span data-ttu-id="e2993-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="e2993-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2993-104">構文</span><span class="sxs-lookup"><span data-stu-id="e2993-104">Syntax</span></span>  
  
```csharp
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e2993-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="e2993-105">Methods</span></span>  

 <span data-ttu-id="e2993-106">SymmetricSecurityBindingElement クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="e2993-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e2993-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2993-107">Properties</span></span>  

 <span data-ttu-id="e2993-108">SymmetricSecurityBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="e2993-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="e2993-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="e2993-109">MessageProtectionOrder</span></span>  

 <span data-ttu-id="e2993-110">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="e2993-110">Data type: string</span></span>  
  
 <span data-ttu-id="e2993-111">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="e2993-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e2993-112">このバインディングのメッセージの暗号化と署名の命令。</span><span class="sxs-lookup"><span data-stu-id="e2993-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="e2993-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="e2993-113">RequireSignatureConfirmation</span></span>  

 <span data-ttu-id="e2993-114">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="e2993-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="e2993-115">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="e2993-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e2993-116">バインディングで署名の確認が必要かどうか。</span><span class="sxs-lookup"><span data-stu-id="e2993-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2993-117">要件</span><span class="sxs-lookup"><span data-stu-id="e2993-117">Requirements</span></span>  
  
|<span data-ttu-id="e2993-118">MOF</span><span class="sxs-lookup"><span data-stu-id="e2993-118">MOF</span></span>|<span data-ttu-id="e2993-119">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="e2993-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e2993-120">名前空間</span><span class="sxs-lookup"><span data-stu-id="e2993-120">Namespace</span></span>|<span data-ttu-id="e2993-121">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="e2993-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e2993-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="e2993-122">See also</span></span>

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
