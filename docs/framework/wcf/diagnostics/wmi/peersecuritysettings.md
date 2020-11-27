---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: 2de417e4a4f5c6197551c1408da6907e2fa7c635
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269003"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="7709e-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="7709e-102">PeerSecuritySettings</span></span>

<span data-ttu-id="7709e-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="7709e-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7709e-104">構文</span><span class="sxs-lookup"><span data-stu-id="7709e-104">Syntax</span></span>  
  
```csharp
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7709e-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="7709e-105">Methods</span></span>  

 <span data-ttu-id="7709e-106">PeerSecuritySettings クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="7709e-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7709e-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7709e-107">Properties</span></span>  

 <span data-ttu-id="7709e-108">PeerSecuritySettings クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="7709e-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="7709e-109">モード</span><span class="sxs-lookup"><span data-stu-id="7709e-109">Mode</span></span>  

 <span data-ttu-id="7709e-110">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="7709e-110">Data type: string</span></span>  
  
 <span data-ttu-id="7709e-111">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7709e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7709e-112">このバインディングで構成されたエンドポイントによって、メッセージ レベルおよびトランスポート レベルのセキュリティが使用されているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="7709e-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="7709e-113">トランスポート</span><span class="sxs-lookup"><span data-stu-id="7709e-113">Transport</span></span>  

 <span data-ttu-id="7709e-114">データ型 : PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="7709e-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="7709e-115">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="7709e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7709e-116">トランスポートのセキュリティ設定です。</span><span class="sxs-lookup"><span data-stu-id="7709e-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7709e-117">要件</span><span class="sxs-lookup"><span data-stu-id="7709e-117">Requirements</span></span>  
  
|<span data-ttu-id="7709e-118">MOF</span><span class="sxs-lookup"><span data-stu-id="7709e-118">MOF</span></span>|<span data-ttu-id="7709e-119">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="7709e-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7709e-120">名前空間</span><span class="sxs-lookup"><span data-stu-id="7709e-120">Namespace</span></span>|<span data-ttu-id="7709e-121">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="7709e-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7709e-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="7709e-122">See also</span></span>

- <xref:System.ServiceModel.PeerSecuritySettings>
