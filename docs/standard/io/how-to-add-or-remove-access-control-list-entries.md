---
title: '方法: アクセス制御リスト エントリを追加または削除する (.NET Framework のみ)'
ms.date: 01/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ACEs [.NET Framework]
- ACLs [.NET Framework]
- access control entries [.NET Framework]
- I/O [.NET Framework], access control list entries
- access control lists [.NET Framework]
ms.assetid: 53758b39-bd9b-4640-bb04-cad5ed8d0abf
ms.openlocfilehash: ff5a09207b3a1d810f9611dd6bb8cfd206adf1e8
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/02/2020
ms.locfileid: "93187971"
---
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a><span data-ttu-id="afb9a-102">方法: アクセス制御リスト エントリを追加または削除する (.NET Framework のみ)</span><span class="sxs-lookup"><span data-stu-id="afb9a-102">How to: Add or remove Access Control List entries (.NET Framework only)</span></span>

<span data-ttu-id="afb9a-103">ファイルまたはディレクトリでアクセス制御リスト (ACL) エントリを追加したり、削除したりするには、<xref:System.Security.AccessControl.FileSecurity> または <xref:System.Security.AccessControl.DirectorySecurity> オブジェクトをファイルまたはディレクトリから取得します。</span><span class="sxs-lookup"><span data-stu-id="afb9a-103">To add or remove Access Control List (ACL) entries to or from a file or directory, get the <xref:System.Security.AccessControl.FileSecurity> or <xref:System.Security.AccessControl.DirectorySecurity> object from the file or directory.</span></span> <span data-ttu-id="afb9a-104">オブジェクトを変更し、ファイルまたはディレクトリに戻します。</span><span class="sxs-lookup"><span data-stu-id="afb9a-104">Modify the object, and then apply it back to the file or directory.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a><span data-ttu-id="afb9a-105">ACL エントリをファイルに追加するか、ファイルから削除する</span><span class="sxs-lookup"><span data-stu-id="afb9a-105">Add or remove an ACL entry from a file</span></span>  
  
1. <span data-ttu-id="afb9a-106"><xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> メソッドを呼び出して、ファイルの現在の ACL エントリを含む <xref:System.Security.AccessControl.FileSecurity> オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="afb9a-106">Call the <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.FileSecurity> object that contains the current ACL entries of a file.</span></span>  
  
2. <span data-ttu-id="afb9a-107">手順 1. から返された <xref:System.Security.AccessControl.FileSecurity> オブジェクトで ACL エントリの追加または削除を行います。</span><span class="sxs-lookup"><span data-stu-id="afb9a-107">Add or remove ACL entries from the <xref:System.Security.AccessControl.FileSecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="afb9a-108">変更を適用するには、<xref:System.Security.AccessControl.FileSecurity> オブジェクトを <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="afb9a-108">To apply the changes, pass the <xref:System.Security.AccessControl.FileSecurity> object to the <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a><span data-ttu-id="afb9a-109">ACL エントリをディレクトリに追加するか、ディレクトリから削除する</span><span class="sxs-lookup"><span data-stu-id="afb9a-109">Add or remove an ACL entry from a directory</span></span>  
  
1. <span data-ttu-id="afb9a-110"><xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> メソッドを呼び出して、ディレクトリの現在の ACL エントリを含む <xref:System.Security.AccessControl.DirectorySecurity> オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="afb9a-110">Call the <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.DirectorySecurity> object that contains the current ACL entries of a directory.</span></span>  
  
2. <span data-ttu-id="afb9a-111">手順 1. から返された <xref:System.Security.AccessControl.DirectorySecurity> オブジェクトで ACL エントリの追加または削除を行います。</span><span class="sxs-lookup"><span data-stu-id="afb9a-111">Add or remove ACL entries from the <xref:System.Security.AccessControl.DirectorySecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="afb9a-112">変更を適用するには、<xref:System.Security.AccessControl.DirectorySecurity> オブジェクトを <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="afb9a-112">To apply the changes, pass the <xref:System.Security.AccessControl.DirectorySecurity> object to the <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afb9a-113">例</span><span class="sxs-lookup"><span data-stu-id="afb9a-113">Example</span></span>  
 <span data-ttu-id="afb9a-114">この例を実行するには、有効なユーザーまたはグループ アカウントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="afb9a-114">You must use a valid user or group account to run this example.</span></span> <span data-ttu-id="afb9a-115">この例は <xref:System.IO.File> オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="afb9a-115">The example uses a <xref:System.IO.File> object.</span></span> <span data-ttu-id="afb9a-116"><xref:System.IO.FileInfo>、<xref:System.IO.Directory>、<xref:System.IO.DirectoryInfo> クラスに対して同じ手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="afb9a-116">Use the same procedure for the <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, and <xref:System.IO.DirectoryInfo> classes.</span></span>

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
