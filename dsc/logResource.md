---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC-loggen resurs
ms.openlocfilehash: 3bc4bf38b376cc62e42107eee1024eaabc93485a
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-log-resource"></a><span data-ttu-id="00141-103">DSC-loggen resurs</span><span class="sxs-lookup"><span data-stu-id="00141-103">DSC Log Resource</span></span> 

> <span data-ttu-id="00141-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="00141-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="00141-105">Den __loggen__ resurs i Windows PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att skriva meddelanden till händelseloggen för Microsoft-Windows-önskade tillstånd Configuration/analys.</span><span class="sxs-lookup"><span data-stu-id="00141-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

<span data-ttu-id="00141-106">Obs: Som standard de operativa loggarna för DSC är aktiverade.</span><span class="sxs-lookup"><span data-stu-id="00141-106">NOTE: By default only the Operational logs for DSC are enabled.</span></span>
<span data-ttu-id="00141-107">Analytiska loggen ska vara tillgängliga eller synliga, måste vara aktiverat.</span><span class="sxs-lookup"><span data-stu-id="00141-107">Before the Analytic log will be available or visible, it must be enabled.</span></span>
<span data-ttu-id="00141-108">Se följande artikel.</span><span class="sxs-lookup"><span data-stu-id="00141-108">See the following article.</span></span>

[<span data-ttu-id="00141-109">Var finns DSC-händelseloggar?</span><span class="sxs-lookup"><span data-stu-id="00141-109">Where are DSC Event Logs?</span></span>](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)

## <a name="properties"></a><span data-ttu-id="00141-110">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="00141-110">Properties</span></span>
|  <span data-ttu-id="00141-111">Egenskap</span><span class="sxs-lookup"><span data-stu-id="00141-111">Property</span></span>  |  <span data-ttu-id="00141-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="00141-112">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="00141-113">Meddelande</span><span class="sxs-lookup"><span data-stu-id="00141-113">Message</span></span>| <span data-ttu-id="00141-114">Anger meddelandet som du vill skriva till händelseloggen Microsoft-Windows-Desired tillstånd Configuration/analys.</span><span class="sxs-lookup"><span data-stu-id="00141-114">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>| 
| <span data-ttu-id="00141-115">dependsOn</span><span class="sxs-lookup"><span data-stu-id="00141-115">DependsOn</span></span> | <span data-ttu-id="00141-116">Anger att konfigurationen av en annan resurs måste köras innan det här loggmeddelandet hämtar skrivs.</span><span class="sxs-lookup"><span data-stu-id="00141-116">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="00141-117">Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="00141-117">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="00141-118">Exempel</span><span class="sxs-lookup"><span data-stu-id="00141-118">Example</span></span>

<span data-ttu-id="00141-119">I följande exempel visas hur du lägger till ett meddelande i händelseloggen Microsoft-Windows-Desired tillstånd Configuration/analys.</span><span class="sxs-lookup"><span data-stu-id="00141-119">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> <span data-ttu-id="00141-120">**Obs**: Om du kör [Test DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) med den här resursen har konfigurerats, returneras alltid **$false**.</span><span class="sxs-lookup"><span data-stu-id="00141-120">**Note**: if you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

```powershell 
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost

    {
        Log LogExample
        {
            Message = "This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log."
        }
    }
}
```

