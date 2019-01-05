---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-Loggresurs
ms.openlocfilehash: 1f94a2d847a4ef63f81e2fb83d1a0f76f5677b09
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048682"
---
# <a name="dsc-log-resource"></a><span data-ttu-id="27d80-103">DSC-Loggresurs</span><span class="sxs-lookup"><span data-stu-id="27d80-103">DSC Log Resource</span></span>

> <span data-ttu-id="27d80-104">_Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="27d80-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="27d80-105">Den __Log__ resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att skriva meddelanden till Microsoft-Windows-Desired State Configuration / analytiska händelseloggen.</span><span class="sxs-lookup"><span data-stu-id="27d80-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> <span data-ttu-id="27d80-106">Endast de operativa loggarna för DSC är aktiverade som standard.</span><span class="sxs-lookup"><span data-stu-id="27d80-106">By default only the Operational logs for DSC are enabled.</span></span> <span data-ttu-id="27d80-107">Innan den analytiska loggen kommer att vara tillgängliga eller synliga, måste vara aktiverat.</span><span class="sxs-lookup"><span data-stu-id="27d80-107">Before the Analytic log will be available or visible, it must be enabled.</span></span> <span data-ttu-id="27d80-108">Mer information finns i [där är DSC-händelseloggar?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span><span class="sxs-lookup"><span data-stu-id="27d80-108">For more information, see [Where are DSC Event Logs?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span></span>

## <a name="properties"></a><span data-ttu-id="27d80-109">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="27d80-109">Properties</span></span>

| <span data-ttu-id="27d80-110">Egenskap</span><span class="sxs-lookup"><span data-stu-id="27d80-110">Property</span></span> | <span data-ttu-id="27d80-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="27d80-111">Description</span></span> |
| --- | --- |
| <span data-ttu-id="27d80-112">Meddelande</span><span class="sxs-lookup"><span data-stu-id="27d80-112">Message</span></span>| <span data-ttu-id="27d80-113">Anger vilket meddelande som du vill skriva till händelseloggen Microsoft-Windows-Desired tillstånd Configuration/analytiska.</span><span class="sxs-lookup"><span data-stu-id="27d80-113">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>|
| <span data-ttu-id="27d80-114">DependsOn</span><span class="sxs-lookup"><span data-stu-id="27d80-114">DependsOn</span></span> | <span data-ttu-id="27d80-115">Anger att konfigurationen av en annan resurs måste köras innan den här loggmeddelande skrivs.</span><span class="sxs-lookup"><span data-stu-id="27d80-115">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="27d80-116">Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för den här egenskapen är `DependsOn = '[ResourceType]ResourceName'`.</span><span class="sxs-lookup"><span data-stu-id="27d80-116">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = '[ResourceType]ResourceName'`.</span></span>|

## <a name="example"></a><span data-ttu-id="27d80-117">Exempel</span><span class="sxs-lookup"><span data-stu-id="27d80-117">Example</span></span>

<span data-ttu-id="27d80-118">I följande exempel visar hur du inkludera ett meddelande i händelseloggen Microsoft-Windows-Desired tillstånd Configuration/analytiska.</span><span class="sxs-lookup"><span data-stu-id="27d80-118">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> [!NOTE]
> <span data-ttu-id="27d80-119">Om du kör [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) med den här resursen har konfigurerats, returnerar den alltid **$false**.</span><span class="sxs-lookup"><span data-stu-id="27d80-119">If you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

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
