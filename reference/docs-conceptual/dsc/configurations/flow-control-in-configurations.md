---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, installation
title: Villkorssatser och slingor i konfigurationer
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71942036"
---
# <a name="conditional-statements-and-loops-in-configurations"></a><span data-ttu-id="8d201-103">Villkorssatser och slingor i konfigurationer</span><span class="sxs-lookup"><span data-stu-id="8d201-103">Conditional statements and loops in Configurations</span></span>

<span data-ttu-id="8d201-104">Du kan göra dina [konfigurationer](configurations.md) mer dynamiska med PowerShell-flödes kontroll nyckelord.</span><span class="sxs-lookup"><span data-stu-id="8d201-104">You can make your [Configurations](configurations.md) more dynamic using PowerShell flow-control keywords.</span></span> <span data-ttu-id="8d201-105">I den här artikeln visas hur du kan använda villkors satser och slingor för att göra dina konfigurationer mer dynamiska.</span><span class="sxs-lookup"><span data-stu-id="8d201-105">This article will show you how you can use conditional statements, and loops to make your Configurations more dynamic.</span></span> <span data-ttu-id="8d201-106">Genom att kombinera villkorliga och slingor med [parametrar](add-parameters-to-a-configuration.md) och [konfigurations data](configData.md) kan du öka flexibiliteten och kontrollen när du kompilerar dina konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="8d201-106">Combining conditional and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your Configurations.</span></span>

<span data-ttu-id="8d201-107">Precis som en funktion eller ett skript block kan du använda valfritt PowerShell-språk i en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="8d201-107">Just like a Function or a Script Block, you can use any PowerShell language within a Configuration.</span></span> <span data-ttu-id="8d201-108">De instruktioner du använder utvärderas bara när du anropar konfigurationen för att kompilera en ". MOF"-fil.</span><span class="sxs-lookup"><span data-stu-id="8d201-108">The statements you use will only be evaluated when you call your Configuration to compile a ".mof" file.</span></span> <span data-ttu-id="8d201-109">I exemplen nedan visas enkla scenarier för att demonstrera koncept.</span><span class="sxs-lookup"><span data-stu-id="8d201-109">The examples below show simple scenarios to demonstrate concepts.</span></span> <span data-ttu-id="8d201-110">Villkorliger är slingor som ofta används med parametrar och konfigurations data.</span><span class="sxs-lookup"><span data-stu-id="8d201-110">Conditionals are loops are more often used with parameters and Configuration Data.</span></span>

<span data-ttu-id="8d201-111">I det här enkla exemplet hämtar **tjänst** resurs blocket det aktuella läget för en tjänst vid kompileringen för att generera en ". MOF"-fil som upprätthåller dess aktuella tillstånd.</span><span class="sxs-lookup"><span data-stu-id="8d201-111">In this simple example, the **Service** resource block retrieves the current state of a service at compile time to generate a ".mof" file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="8d201-112">Om du använder dynamiska resurs block blockeras effektiviteten i IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="8d201-112">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="8d201-113">PowerShell-parsern kan inte avgöra om de angivna värdena är acceptabla tills konfigurationen kompileras.</span><span class="sxs-lookup"><span data-stu-id="8d201-113">The PowerShell parser cannot determine if the values specified are acceptable until the Configuration is compiled.</span></span>

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

<span data-ttu-id="8d201-114">Dessutom kan du skapa en **tjänst** block resurs för varje tjänst på den aktuella datorn med hjälp av en `foreach` slinga.</span><span class="sxs-lookup"><span data-stu-id="8d201-114">Additionally, you could create a **Service** block resource for every service on the current machine, using a `foreach` loop.</span></span>

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

<span data-ttu-id="8d201-115">Du kan också bara skapa konfigurationer för datorer som är online genom att använda ett enkelt `if`-uttryck.</span><span class="sxs-lookup"><span data-stu-id="8d201-115">You could also only create configurations for machines that are online, by using a simple `if` statement.</span></span>

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
> <span data-ttu-id="8d201-116">De dynamiska resurs blocken i ovanstående exempel hänvisar till den aktuella datorn.</span><span class="sxs-lookup"><span data-stu-id="8d201-116">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="8d201-117">I den här instansen skulle det vara den dator du redigerar konfigurationen på, inte målnoden.</span><span class="sxs-lookup"><span data-stu-id="8d201-117">In this instance, that would be the machine you are authoring the Configuration on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="8d201-118">Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="8d201-118">Summary</span></span>

<span data-ttu-id="8d201-119">I sammanfattning kan du använda valfritt PowerShell-språk i en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="8d201-119">In summary, you can use any PowerShell language within a Configuration.</span></span>

<span data-ttu-id="8d201-120">Detta inkluderar sådant som:</span><span class="sxs-lookup"><span data-stu-id="8d201-120">This includes things like:</span></span>

- <span data-ttu-id="8d201-121">Anpassade objekt</span><span class="sxs-lookup"><span data-stu-id="8d201-121">Custom Objects</span></span>
- <span data-ttu-id="8d201-122">Hash</span><span class="sxs-lookup"><span data-stu-id="8d201-122">Hashtables</span></span>
- <span data-ttu-id="8d201-123">Sträng manipulering</span><span class="sxs-lookup"><span data-stu-id="8d201-123">String manipulation</span></span>
- <span data-ttu-id="8d201-124">Tjänst</span><span class="sxs-lookup"><span data-stu-id="8d201-124">Remoting</span></span>
- <span data-ttu-id="8d201-125">WMI och CIM</span><span class="sxs-lookup"><span data-stu-id="8d201-125">WMI and CIM</span></span>
- <span data-ttu-id="8d201-126">ActiveDirectory-objekt</span><span class="sxs-lookup"><span data-stu-id="8d201-126">ActiveDirectory objects</span></span>
- <span data-ttu-id="8d201-127">med flera...</span><span class="sxs-lookup"><span data-stu-id="8d201-127">and more...</span></span>

<span data-ttu-id="8d201-128">Alla PowerShell-koder som definierats i en konfiguration utvärderas som en kompileringstid, men du kan också placera kod i skriptet som innehåller konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="8d201-128">Any PowerShell code defined in a Configuration will be evaluated a compile time, but you can also place code in the script containing your Configuration.</span></span> <span data-ttu-id="8d201-129">All kod utanför konfigurations blocket körs när du importerar konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="8d201-129">Any code outside of the Configuration block will be executed when you import your Configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d201-130">Se även</span><span class="sxs-lookup"><span data-stu-id="8d201-130">See also</span></span>

- [<span data-ttu-id="8d201-131">Lägga till parametrar till en konfiguration</span><span class="sxs-lookup"><span data-stu-id="8d201-131">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="8d201-132">Separera konfigurations data från konfigurationer</span><span class="sxs-lookup"><span data-stu-id="8d201-132">Separate Configuration data from Configurations</span></span>](configData.md)
