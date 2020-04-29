---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, installation
title: Villkorssatser och slingor i konfigurationer
ms.openlocfilehash: 86f75be4a3d1c1760dd6269335431e8ab9fd8d09
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736904"
---
# <a name="conditional-statements-and-loops-in-a-configuration"></a><span data-ttu-id="bf347-103">Villkors uttryck och slingor i en konfiguration</span><span class="sxs-lookup"><span data-stu-id="bf347-103">Conditional statements and loops in a Configuration</span></span>

<span data-ttu-id="bf347-104">Du kan göra [konfigurationen](configurations.md) mer dynamisk med hjälp av PowerShell Flow-Control-nyckelord.</span><span class="sxs-lookup"><span data-stu-id="bf347-104">You can make your [Configuration](configurations.md) more dynamic by using PowerShell flow-control keywords.</span></span> <span data-ttu-id="bf347-105">Den här artikeln visar hur du kan använda villkors satser och slingor för att göra `Configuration` mer dynamiska.</span><span class="sxs-lookup"><span data-stu-id="bf347-105">This article shows you how you can use conditional statements and loops to make your `Configuration` more dynamic.</span></span> <span data-ttu-id="bf347-106">Genom att kombinera villkorliga uttryck och slingor med [parametrar](add-parameters-to-a-configuration.md) och [konfigurations data](configData.md) kan du öka flexibiliteten och `Configuration`kontrollen när du kompilerar.</span><span class="sxs-lookup"><span data-stu-id="bf347-106">Combining conditional statements and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your `Configuration`.</span></span>

<span data-ttu-id="bf347-107">Precis som en funktion eller ett skript block kan du använda valfri PowerShell-språkfunktion i en `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="bf347-107">Just like a function or a script block, you can use any PowerShell language feature within a `Configuration`.</span></span>
<span data-ttu-id="bf347-108">De instruktioner du använder utvärderas bara när du anropar `Configuration` för att kompilera en `.mof` fil.</span><span class="sxs-lookup"><span data-stu-id="bf347-108">The statements you use will only be evaluated when you call your `Configuration` to compile a `.mof` file.</span></span> <span data-ttu-id="bf347-109">I exemplen nedan visas scenarier för att demonstrera koncept.</span><span class="sxs-lookup"><span data-stu-id="bf347-109">The examples below show scenarios to demonstrate concepts.</span></span> <span data-ttu-id="bf347-110">Villkors uttryck och slingor används oftare med parametrar och konfigurations data.</span><span class="sxs-lookup"><span data-stu-id="bf347-110">Conditional statements and loops are more often used with parameters and configuration Data.</span></span>

<span data-ttu-id="bf347-111">I det här exemplet hämtar **tjänst** resurs blocket det aktuella läget för en tjänst vid kompileringen för att skapa en `.mof` fil som upprätthåller dess aktuella tillstånd.</span><span class="sxs-lookup"><span data-stu-id="bf347-111">In this  example, the **Service** resource block retrieves the current state of a service at compile time to generate a `.mof` file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="bf347-112">Om du använder dynamiska resurs block blockeras effektiviteten i IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="bf347-112">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="bf347-113">PowerShell-parsern kan inte avgöra om de angivna värdena är acceptabla `Configuration` tills kompileraren kompileras.</span><span class="sxs-lookup"><span data-stu-id="bf347-113">The PowerShell parser cannot determine if the values specified are acceptable until the `Configuration` is compiled.</span></span>

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

<span data-ttu-id="bf347-114">Dessutom kan du skapa ett **tjänst** resurs block för varje tjänst på den aktuella datorn med en `foreach` loop.</span><span class="sxs-lookup"><span data-stu-id="bf347-114">Additionally, you could create a **Service** resource block for every service on the current machine using a `foreach` loop.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        foreach ($service in $(Get-Service))
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

<span data-ttu-id="bf347-115">Du kan också skapa en `Configuration` endast för datorer som är online med hjälp av `if` en instruktion.</span><span class="sxs-lookup"><span data-stu-id="bf347-115">You could also create a `Configuration` only for machines that are online by using an `if` statement.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    foreach ($computer in @('Server01', 'Server02', 'Server03'))
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
> <span data-ttu-id="bf347-116">De dynamiska resurs blocken i ovanstående exempel hänvisar till den aktuella datorn.</span><span class="sxs-lookup"><span data-stu-id="bf347-116">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="bf347-117">I den här instansen skulle det vara den dator som du redigerar `Configuration` på, inte målnoden.</span><span class="sxs-lookup"><span data-stu-id="bf347-117">In this instance, that would be the machine you are authoring the `Configuration` on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="bf347-118">Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="bf347-118">Summary</span></span>

<span data-ttu-id="bf347-119">Sammanfattnings vis kan du använda valfri PowerShell-språkfunktion i `Configuration`en.</span><span class="sxs-lookup"><span data-stu-id="bf347-119">In summary, you can use any PowerShell language feature within a `Configuration`.</span></span>

<span data-ttu-id="bf347-120">Detta inkluderar sådant som:</span><span class="sxs-lookup"><span data-stu-id="bf347-120">This includes things like:</span></span>

- <span data-ttu-id="bf347-121">Anpassade objekt</span><span class="sxs-lookup"><span data-stu-id="bf347-121">Custom Objects</span></span>
- <span data-ttu-id="bf347-122">Hash</span><span class="sxs-lookup"><span data-stu-id="bf347-122">Hashtables</span></span>
- <span data-ttu-id="bf347-123">Sträng manipulering</span><span class="sxs-lookup"><span data-stu-id="bf347-123">String manipulation</span></span>
- <span data-ttu-id="bf347-124">Tjänst</span><span class="sxs-lookup"><span data-stu-id="bf347-124">Remoting</span></span>
- <span data-ttu-id="bf347-125">WMI och CIM</span><span class="sxs-lookup"><span data-stu-id="bf347-125">WMI and CIM</span></span>
- <span data-ttu-id="bf347-126">ActiveDirectory-objekt</span><span class="sxs-lookup"><span data-stu-id="bf347-126">ActiveDirectory objects</span></span>
- <span data-ttu-id="bf347-127">med flera...</span><span class="sxs-lookup"><span data-stu-id="bf347-127">and more...</span></span>

<span data-ttu-id="bf347-128">Alla PowerShell-koder som definieras `Configuration` i a utvärderas vid kompilering, men du kan också placera kod i skriptet som innehåller din `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="bf347-128">Any PowerShell code defined in a `Configuration` is evaluated at compile time, but you can also place code in the script containing your `Configuration`.</span></span> <span data-ttu-id="bf347-129">All kod utanför `Configuration` blocket körs när du importerar din `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="bf347-129">Any code outside of the `Configuration` block is executed when you import your `Configuration`.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf347-130">Se även</span><span class="sxs-lookup"><span data-stu-id="bf347-130">See also</span></span>

- [<span data-ttu-id="bf347-131">Lägga till parametrar till en konfiguration</span><span class="sxs-lookup"><span data-stu-id="bf347-131">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="bf347-132">Separera konfigurationsdata från konfigurationer</span><span class="sxs-lookup"><span data-stu-id="bf347-132">Separate Configuration data from Configurations</span></span>](configData.md)
