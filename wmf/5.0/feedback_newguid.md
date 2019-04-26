---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 90fd26f9f27d2398da839b309c17b921bb3b8521
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085338"
---
# <a name="new-guid"></a><span data-ttu-id="3580c-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="3580c-102">New-Guid</span></span>
<span data-ttu-id="3580c-103">Ofta skript (eller kanske skriva en DSC-resurs) du har behov av en unik identifierare.</span><span class="sxs-lookup"><span data-stu-id="3580c-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="3580c-104">GUID fungerar bra, och det är enkelt att anropa .NET Framework Guid-klassen för att generera en, men med en cmdlet gör det enklare för slutanvändare som inte är redan bekant med .NET Framework-klassen:</span><span class="sxs-lookup"><span data-stu-id="3580c-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="3580c-105">PS C:\\&gt; New-Guid</span><span class="sxs-lookup"><span data-stu-id="3580c-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="3580c-106">Guid</span><span class="sxs-lookup"><span data-stu-id="3580c-106">Guid</span></span>

----

<span data-ttu-id="3580c-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="3580c-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>
