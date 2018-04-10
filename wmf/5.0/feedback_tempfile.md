---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
ms.openlocfilehash: ada4fcc0beb3eb74b099f221762341abbf2c3b4c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="new-temporaryfile"></a><span data-ttu-id="e9032-102">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="e9032-102">New-TemporaryFile</span></span>
<span data-ttu-id="e9032-103">Ibland måste du skapa en temporär fil i ett skript.</span><span class="sxs-lookup"><span data-stu-id="e9032-103">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="e9032-104">Du kan göra detta med den **ny TemporaryFile** cmdlet:</span><span class="sxs-lookup"><span data-stu-id="e9032-104">You can easily do this with the **New-TemporaryFile** cmdlet:</span></span>

<span data-ttu-id="e9032-105">PS C:\\ &gt; $tempFile = New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="e9032-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span></span>

<span data-ttu-id="e9032-106">PS C:\\ &gt; $tempFile.FullName</span><span class="sxs-lookup"><span data-stu-id="e9032-106">PS C:\\&gt; $tempFile.FullName</span></span>

<span data-ttu-id="e9032-107">C:\\användare\\slee\\AppData\\lokala\\Temp\\tmp375.tmp</span><span class="sxs-lookup"><span data-stu-id="e9032-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span></span>