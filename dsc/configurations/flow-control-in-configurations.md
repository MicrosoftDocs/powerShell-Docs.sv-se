---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, installation
title: Villkorssatser och slingor i konfigurationer
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080143"
---
# <a name="conditional-statements-and-loops-in-configurations"></a><span data-ttu-id="b5c00-103">Villkorssatser och slingor i konfigurationer</span><span class="sxs-lookup"><span data-stu-id="b5c00-103">Conditional statements and loops in Configurations</span></span>

<span data-ttu-id="b5c00-104">Du kan göra din [konfigurationer](configurations.md) mer dynamiskt med hjälp av PowerShell flödesreglering nyckelord.</span><span class="sxs-lookup"><span data-stu-id="b5c00-104">You can make your [Configurations](configurations.md) more dynamic using PowerShell flow-control keywords.</span></span> <span data-ttu-id="b5c00-105">Den här artikeln visar hur du kan använda villkorssatser och slingor du gör dina konfigurationer mer dynamiskt.</span><span class="sxs-lookup"><span data-stu-id="b5c00-105">This article will show you how you can use conditional statements, and loops to make your Configurations more dynamic.</span></span> <span data-ttu-id="b5c00-106">Kombinera villkorlig och slingor med [parametrar](add-parameters-to-a-configuration.md) och [konfigurationsdata](configData.md) kan du större flexibilitet och kontroll vid kompilering dina konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="b5c00-106">Combining conditional and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your Configurations.</span></span>

<span data-ttu-id="b5c00-107">Du kan använda alla PowerShell-språket i en konfiguration för precis som en funktion eller ett skriptblock.</span><span class="sxs-lookup"><span data-stu-id="b5c00-107">Just like a Function or a Script Block, you can use any PowerShell language within a Configuration.</span></span> <span data-ttu-id="b5c00-108">De instruktioner som du använder utvärderas bara när du anropar din konfiguration och kompilera en ”.mof”-fil.</span><span class="sxs-lookup"><span data-stu-id="b5c00-108">The statements you use will only be evaluated when you call your Configuration to compile a ".mof" file.</span></span> <span data-ttu-id="b5c00-109">Exemplen nedan visar grundläggande scenarier för att demonstrera begreppen.</span><span class="sxs-lookup"><span data-stu-id="b5c00-109">The examples below show simple scenarios to demonstrate concepts.</span></span> <span data-ttu-id="b5c00-110">Conditions är slingor används oftare med parametrar och konfigurationsdata.</span><span class="sxs-lookup"><span data-stu-id="b5c00-110">Conditionals are loops are more often used with parameters and Configuration Data.</span></span>

<span data-ttu-id="b5c00-111">I den här enkla exemplet skickar den **Service** resource block hämtar det aktuella tillståndet för en tjänst vid kompilering att generera en ”.mof”-fil som underhåller det aktuella tillståndet.</span><span class="sxs-lookup"><span data-stu-id="b5c00-111">In this simple example, the **Service** resource block retrieves the current state of a service at compile time to generate a ".mof" file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="b5c00-112">Med hjälp av dynamisk resurs block kommer åsidosätter effektiviteten i Intellisense.</span><span class="sxs-lookup"><span data-stu-id="b5c00-112">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="b5c00-113">PowerShell-parser kan inte fastställa om värdena som har angetts accepteras tills konfigurationen har kompilerats.</span><span class="sxs-lookup"><span data-stu-id="b5c00-113">The PowerShell parser cannot determine if the values specified are acceptable until the Configuration is compiled.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Service Spooler
        {
            Name = "Spooler"
            State = $(Get-Service -Name 'spooler').Status
            StartType = $(Get-Service -Name 'spooler').StartType
        }
    }
}
```

<span data-ttu-id="b5c00-114">Du kan även skapa en **Service** blockera resurs för varje tjänst på den aktuella datorn med hjälp av en `foreach` loop.</span><span class="sxs-lookup"><span data-stu-id="b5c00-114">Additionally, you could create a **Service** block resource for every service on the current machine, using a `foreach` loop.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Foreach ($service in $(Get-Service))
        {
            Service $service.Name
            {
                Name = $service.Name
                State = $service.Status
                StartType = $service.StartType
            }
        }
    }
}
```

<span data-ttu-id="b5c00-115">Du kan också bara skapa konfigurationer för datorer som är online, med hjälp av en enkel `if` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="b5c00-115">You could also only create configurations for machines that are online, by using a simple `if` statement.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    Foreach ($computer in @('Server01', 'Server02', 'Server03'))
    {
        if (Test-Connection -ComputerName $computer)
        {
            Node $computer
            {
                Service "Spooler"
                {
                    Name = "Spooler"
                    State = "Started"
                }
            }
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="b5c00-116">Dynamisk resursen blockerar i ovanstående exempel referensen till den aktuella datorn.</span><span class="sxs-lookup"><span data-stu-id="b5c00-116">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="b5c00-117">I den här instansen, som är den dator som du använder konfigurationen på, inte target noden.</span><span class="sxs-lookup"><span data-stu-id="b5c00-117">In this instance, that would be the machine you are authoring the Configuration on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="b5c00-118">Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="b5c00-118">Summary</span></span>

<span data-ttu-id="b5c00-119">Sammanfattningsvis ska använda du alla PowerShell-språket i en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="b5c00-119">In summary, you can use any PowerShell language within a Configuration.</span></span>

<span data-ttu-id="b5c00-120">Detta inkluderar:</span><span class="sxs-lookup"><span data-stu-id="b5c00-120">This includes things like:</span></span>

- <span data-ttu-id="b5c00-121">Anpassade objekt</span><span class="sxs-lookup"><span data-stu-id="b5c00-121">Custom Objects</span></span>
- <span data-ttu-id="b5c00-122">Hash-tabeller</span><span class="sxs-lookup"><span data-stu-id="b5c00-122">Hashtables</span></span>
- <span data-ttu-id="b5c00-123">Manipulering av sträng</span><span class="sxs-lookup"><span data-stu-id="b5c00-123">String manipulation</span></span>
- <span data-ttu-id="b5c00-124">Fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="b5c00-124">Remoting</span></span>
- <span data-ttu-id="b5c00-125">WMI- och CIM</span><span class="sxs-lookup"><span data-stu-id="b5c00-125">WMI and CIM</span></span>
- <span data-ttu-id="b5c00-126">ActiveDirectory-objekt</span><span class="sxs-lookup"><span data-stu-id="b5c00-126">ActiveDirectory objects</span></span>
- <span data-ttu-id="b5c00-127">med mera...</span><span class="sxs-lookup"><span data-stu-id="b5c00-127">and more...</span></span>

<span data-ttu-id="b5c00-128">Alla PowerShell-kod som definierats i en konfiguration kommer att utvärderas en kompilering, men du kan också placera kod i skriptet som innehåller din konfiguration.</span><span class="sxs-lookup"><span data-stu-id="b5c00-128">Any PowerShell code defined in a Configuration will be evaluated a compile time, but you can also place code in the script containing your Configuration.</span></span> <span data-ttu-id="b5c00-129">Någon kod utanför Configuration blocket körs när du importerar din konfiguration.</span><span class="sxs-lookup"><span data-stu-id="b5c00-129">Any code outside of the Configuration block will be executed when you import your Configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5c00-130">Se även</span><span class="sxs-lookup"><span data-stu-id="b5c00-130">See also</span></span>

- [<span data-ttu-id="b5c00-131">Lägg till parametrar till en konfiguration</span><span class="sxs-lookup"><span data-stu-id="b5c00-131">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="b5c00-132">Separera konfigurationsdata från konfigurationer</span><span class="sxs-lookup"><span data-stu-id="b5c00-132">Separate Configuration data from Configurations</span></span>](configData.md)
