---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 08f431c27cd0ee769518b5246af2fa95aa499d54
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="new-temporaryfile"></a><span data-ttu-id="0d0a1-102">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="0d0a1-102">New-TemporaryFile</span></span>
<span data-ttu-id="0d0a1-103">Ibland måste du skapa en temporär fil i ett skript.</span><span class="sxs-lookup"><span data-stu-id="0d0a1-103">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="0d0a1-104">Du kan göra detta med den **ny TemporaryFile** cmdlet:</span><span class="sxs-lookup"><span data-stu-id="0d0a1-104">You can easily do this with the **New-TemporaryFile** cmdlet:</span></span>

<span data-ttu-id="0d0a1-105">PS C:\\ &gt; $tempFile = New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="0d0a1-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span></span>

<span data-ttu-id="0d0a1-106">PS C:\\ &gt; $tempFile.FullName</span><span class="sxs-lookup"><span data-stu-id="0d0a1-106">PS C:\\&gt; $tempFile.FullName</span></span>

<span data-ttu-id="0d0a1-107">C:\\användare\\slee\\AppData\\lokala\\Temp\\tmp375.tmp</span><span class="sxs-lookup"><span data-stu-id="0d0a1-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span></span>
