---
title: Clrver.exe (CLR バージョン ツール)
description: Clrver.exe (CLR バージョン ツール) を確認します。 このツールによって、コンピューターにインストールされている共通言語ランタイム (CLR) のすべてのバージョンが報告されます。
ms.date: 03/30/2017
helpviewer_keywords:
- Clrver.exe
- CLR Version tool
ms.assetid: cbc2ee86-bdc8-4a65-a8f1-ba23bce3a699
ms.openlocfilehash: 3a7a585d990051553aa8fdc0e99b2dc206273cf4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247227"
---
# <a name="clrverexe-clr-version-tool"></a><span data-ttu-id="30fcf-104">Clrver.exe (CLR バージョン ツール)</span><span class="sxs-lookup"><span data-stu-id="30fcf-104">Clrver.exe (CLR Version Tool)</span></span>

<span data-ttu-id="30fcf-105">CLR バージョン ツール (Clrver.exe) は、コンピューターにインストールされている共通言語ランタイム (CLR: Common Language Runtime) のすべてのバージョンを報告します。</span><span class="sxs-lookup"><span data-stu-id="30fcf-105">The CLR Version tool (Clrver.exe) reports all the installed versions of the common language runtime (CLR) on the computer.</span></span>  
  
 <span data-ttu-id="30fcf-106">このツールは、Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="30fcf-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="30fcf-107">このツールを実行するには、Visual Studio 用開発者コマンド プロンプト (または Windows 7 の Visual Studio コマンド プロンプト) を使用します。</span><span class="sxs-lookup"><span data-stu-id="30fcf-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="30fcf-108">詳細については、「[Visual Studio 用開発者コマンド プロンプト](developer-command-prompt-for-vs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30fcf-108">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="30fcf-109">コマンド プロンプトに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="30fcf-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30fcf-110">構文</span><span class="sxs-lookup"><span data-stu-id="30fcf-110">Syntax</span></span>  
  
```console  
clrver [option]  
```  
  
## <a name="options"></a><span data-ttu-id="30fcf-111">Options</span><span class="sxs-lookup"><span data-stu-id="30fcf-111">Options</span></span>  
  
|<span data-ttu-id="30fcf-112">オプション</span><span class="sxs-lookup"><span data-stu-id="30fcf-112">Option</span></span>|<span data-ttu-id="30fcf-113">説明</span><span class="sxs-lookup"><span data-stu-id="30fcf-113">Description</span></span>|  
|------------|-----------------|  
|`-all`|<span data-ttu-id="30fcf-114">CLR を使用しているコンピューター上のすべてのプロセスを表示します。</span><span class="sxs-lookup"><span data-stu-id="30fcf-114">Displays all processes on the computer that are using the CLR.</span></span>|  
|<span data-ttu-id="30fcf-115">*pid*</span><span class="sxs-lookup"><span data-stu-id="30fcf-115">*pid*</span></span>|<span data-ttu-id="30fcf-116">指定したプロセス ID (PID) のプロセスで使用されている CLR のバージョンを表示します。</span><span class="sxs-lookup"><span data-stu-id="30fcf-116">Displays the version(s) of the CLR used by the process that has the specified process ID (PID).</span></span>|  
|`-?`|<span data-ttu-id="30fcf-117">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="30fcf-117">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30fcf-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="30fcf-118">Remarks</span></span>  

 <span data-ttu-id="30fcf-119">オプションを指定せずに Clrver.exe を呼び出した場合、インストールされている CLR のすべてのバージョンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="30fcf-119">If you call Clrver.exe with no options, it displays all installed CLR versions.</span></span> <span data-ttu-id="30fcf-120">別のユーザーの PID を指定する場合、バージョン情報を取得するには、管理アクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="30fcf-120">If you specify a PID for another user, you must have administrative permissions to obtain the version information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30fcf-121">Windows Vista 以降では、ユーザー アカウント制御 (UAC: User Account Control) でユーザーの権限が決定されます。</span><span class="sxs-lookup"><span data-stu-id="30fcf-121">In Windows Vista and later, User Account Control (UAC) determines the privileges of a user.</span></span> <span data-ttu-id="30fcf-122">ユーザーが組み込みの Administrators グループのメンバーである場合、そのユーザーには標準ユーザー アクセス トークンおよび管理者アクセス トークンの 2 つのランタイム アクセス トークンが割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="30fcf-122">If you are a member of the Built-in Administrators group, you are assigned two run-time access tokens: a standard user access token and an administrator access token.</span></span> <span data-ttu-id="30fcf-123">既定では、ユーザーは標準ユーザー ロールに所属します。</span><span class="sxs-lookup"><span data-stu-id="30fcf-123">By default, you are in the standard user role.</span></span> <span data-ttu-id="30fcf-124">管理アクセス許可を必要とするコードを実行するには、最初に、ユーザーの権限を標準ユーザーから管理者に昇格させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="30fcf-124">To execute code that requires administrative permission, you must first elevate your privileges from standard user to administrator.</span></span> <span data-ttu-id="30fcf-125">この操作は、コマンド プロンプトの起動時にコマンド プロンプト アイコンを右クリックし、管理者として実行することを指定して行うことができます。</span><span class="sxs-lookup"><span data-stu-id="30fcf-125">You can do this when you start the command prompt by right-clicking the command prompt icon and indicating that you want to run as an administrator.</span></span>  
  
 <span data-ttu-id="30fcf-126">SYSTEM、LOCAL SERVICE、および NETWORK SERVICE の各プロセスの CLR バージョンを確認しようとすると、PID が存在しないことを示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="30fcf-126">Attempting to determine the CLR version for SYSTEM, LOCAL SERVICE, and NETWORK SERVICE processes results in a message indicating that the PID doesn't exist.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="30fcf-127">使用例</span><span class="sxs-lookup"><span data-stu-id="30fcf-127">Examples</span></span>  

 <span data-ttu-id="30fcf-128">コンピューターにインストールされている CLR のすべてのバージョンを表示するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="30fcf-128">The following command displays all the versions of the CLR installed on the computer.</span></span>  
  
 `clrver`  
  
 <span data-ttu-id="30fcf-129">プロセス 128 で使用されている CLR のバージョンを表示するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="30fcf-129">The following command displays the version of the CLR used by process 128.</span></span>  
  
 `clrver 128`  
  
 <span data-ttu-id="30fcf-130">すべてのマネージド プロセスとそれらのプロセスで使用されている CLR のバージョンを表示するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="30fcf-130">The following command displays all the managed processes and the version of the CLR they are using.</span></span>  
  
 `Clrver -all`  
  
## <a name="see-also"></a><span data-ttu-id="30fcf-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="30fcf-131">See also</span></span>

- [<span data-ttu-id="30fcf-132">ツール</span><span class="sxs-lookup"><span data-stu-id="30fcf-132">Tools</span></span>](index.md)
- [<span data-ttu-id="30fcf-133">Visual Studio 用開発者コマンド プロンプト</span><span class="sxs-lookup"><span data-stu-id="30fcf-133">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
