---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 2d6b4e3045bc8cff90576c345d1ccb97b2487426
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225597"
---
# <a name="new-guid"></a><span data-ttu-id="25963-102">New-Guid</span><span class="sxs-lookup"><span data-stu-id="25963-102">New-Guid</span></span>
<span data-ttu-id="25963-103">Ofta skript (eller kanske skriva en DSC-resurs) kan du inte har behov av en unik identifierare.</span><span class="sxs-lookup"><span data-stu-id="25963-103">Often script (or perhaps writing a DSC resource), you have the need for a unique identifier.</span></span> <span data-ttu-id="25963-104">GUID fungerar bra, och det är lätt att anropa .NET Framework Guid-klassen för att generera en, men med en cmdlet gör det lättare att hitta för slutanvändare som inte är redan bekant med .NET Framework-klass:</span><span class="sxs-lookup"><span data-stu-id="25963-104">GUIDs work well, and it is easy to call the .NET Framework Guid class to generate one, but having a cmdlet makes this more discoverable for end users who are not already familiar with the .NET Framework class:</span></span>

<span data-ttu-id="25963-105">PS C:\\ &gt; nytt Guid</span><span class="sxs-lookup"><span data-stu-id="25963-105">PS C:\\&gt; New-Guid</span></span>

<span data-ttu-id="25963-106">GUID</span><span class="sxs-lookup"><span data-stu-id="25963-106">Guid</span></span>

----

<span data-ttu-id="25963-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span><span class="sxs-lookup"><span data-stu-id="25963-107">e19d6ea5-3cc2-4db9-8095-0cdaed5a703d</span></span>
