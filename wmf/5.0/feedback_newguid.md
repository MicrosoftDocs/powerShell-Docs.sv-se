---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
ms.openlocfilehash: 91c115c7f0553cd5edf7fecf04e6a5c71c0a1aa2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="new-guid"></a><span data-ttu-id="f63ab-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="f63ab-102">New-Guid</span></span>
<span data-ttu-id="f63ab-103">Ofta skript (eller kanske skriva en DSC-resurs) kan du inte har behov av en unik identifierare.</span><span class="sxs-lookup"><span data-stu-id="f63ab-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="f63ab-104">GUID fungerar bra, och det är lätt att anropa .NET Framework Guid-klassen för att generera en, men med en cmdlet gör det lättare att hitta för slutanvändare som inte är redan bekant med .NET Framework-klass:</span><span class="sxs-lookup"><span data-stu-id="f63ab-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="f63ab-105">PS C:\\ &gt; nytt Guid</span><span class="sxs-lookup"><span data-stu-id="f63ab-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="f63ab-106">GUID</span><span class="sxs-lookup"><span data-stu-id="f63ab-106">Guid</span></span>

----

<span data-ttu-id="f63ab-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="f63ab-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>