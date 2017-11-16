---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: 90e0ab3579e1840598cc3050c27db0b73ba6f69d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="new-temporaryfile"></a><span data-ttu-id="efabe-102">Ny TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="efabe-102">New-TemporaryFile</span></span>
<span data-ttu-id="efabe-103">Ibland måste du skapa en temporär fil i ett skript.</span><span class="sxs-lookup"><span data-stu-id="efabe-103">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="efabe-104">Du kan göra detta med den **ny TemporaryFile** cmdlet:</span><span class="sxs-lookup"><span data-stu-id="efabe-104">You can easily do this with the **New-TemporaryFile** cmdlet:</span></span>

<span data-ttu-id="efabe-105">PS C:\\ &gt; $tempFile = New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="efabe-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span></span>

<span data-ttu-id="efabe-106">PS C:\\ &gt; $tempFile.FullName</span><span class="sxs-lookup"><span data-stu-id="efabe-106">PS C:\\&gt; $tempFile.FullName</span></span>

<span data-ttu-id="efabe-107">C:\\användare\\slee\\AppData\\lokala\\Temp\\tmp375.tmp</span><span class="sxs-lookup"><span data-stu-id="efabe-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span></span>

