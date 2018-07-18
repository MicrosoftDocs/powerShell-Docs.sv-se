---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-Loggresurs
ms.openlocfilehash: fade94efd8133ae0172737e4bb1aed89fc0f97d9
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093484"
---
# <a name="dsc-log-resource"></a><span data-ttu-id="724c1-103">DSC-Loggresurs</span><span class="sxs-lookup"><span data-stu-id="724c1-103">DSC Log Resource</span></span>

> <span data-ttu-id="724c1-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="724c1-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="724c1-105">Den __Log__ resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att skriva meddelanden till Microsoft-Windows-Desired State Configuration / analytiska händelseloggen.</span><span class="sxs-lookup"><span data-stu-id="724c1-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> <span data-ttu-id="724c1-106">Endast de operativa loggarna för DSC är aktiverade som standard.</span><span class="sxs-lookup"><span data-stu-id="724c1-106">By default only the Operational logs for DSC are enabled.</span></span> <span data-ttu-id="724c1-107">Innan den analytiska loggen kommer att vara tillgängliga eller synliga, måste vara aktiverat.</span><span class="sxs-lookup"><span data-stu-id="724c1-107">Before the Analytic log will be available or visible, it must be enabled.</span></span> <span data-ttu-id="724c1-108">Mer information finns i [där är DSC-händelseloggar?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs).</span><span class="sxs-lookup"><span data-stu-id="724c1-108">For more information, see [Where are DSC Event Logs?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs).</span></span>

## <a name="properties"></a><span data-ttu-id="724c1-109">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="724c1-109">Properties</span></span>

|  <span data-ttu-id="724c1-110">Egenskap</span><span class="sxs-lookup"><span data-stu-id="724c1-110">Property</span></span>  |  <span data-ttu-id="724c1-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="724c1-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="724c1-112">Meddelande</span><span class="sxs-lookup"><span data-stu-id="724c1-112">Message</span></span>| <span data-ttu-id="724c1-113">Anger vilket meddelande som du vill skriva till händelseloggen Microsoft-Windows-Desired tillstånd Configuration/analytiska.</span><span class="sxs-lookup"><span data-stu-id="724c1-113">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>|
| <span data-ttu-id="724c1-114">DependsOn</span><span class="sxs-lookup"><span data-stu-id="724c1-114">DependsOn</span></span> | <span data-ttu-id="724c1-115">Anger att konfigurationen av en annan resurs måste köras innan den här loggmeddelande skrivs.</span><span class="sxs-lookup"><span data-stu-id="724c1-115">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="724c1-116">Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är __ResourceName__ och är av typen __ResourceType__, syntaxen för den här egenskapen är `DependsOn = '[ResourceType]ResourceName'`.</span><span class="sxs-lookup"><span data-stu-id="724c1-116">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = '[ResourceType]ResourceName'`.</span></span>|

## <a name="example"></a><span data-ttu-id="724c1-117">Exempel</span><span class="sxs-lookup"><span data-stu-id="724c1-117">Example</span></span>

<span data-ttu-id="724c1-118">I följande exempel visar hur du inkludera ett meddelande i händelseloggen Microsoft-Windows-Desired tillstånd Configuration/analytiska.</span><span class="sxs-lookup"><span data-stu-id="724c1-118">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> [!NOTE]
> <span data-ttu-id="724c1-119">Om du kör [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) med den här resursen har konfigurerats, returnerar den alltid **$false**.</span><span class="sxs-lookup"><span data-stu-id="724c1-119">If you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Log LogExample
        {
            Message = 'This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log.'
        }
    }
}
```