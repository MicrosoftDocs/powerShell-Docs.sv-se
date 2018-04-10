---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Komma igång med PowerShell önskad Tillståndskonfiguration
ms.openlocfilehash: b5aff5008db5a5e45b77d8094b0e48ad98dc63fa
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="getting-started-with-powershell-desired-state-configuration"></a><span data-ttu-id="535b9-103">Komma igång med PowerShell önskad Tillståndskonfiguration</span><span class="sxs-lookup"><span data-stu-id="535b9-103">Getting Started with PowerShell Desired State Configuration</span></span> #

<span data-ttu-id="535b9-104">Den här guiden beskriver hur du börjar skapa PowerShell Desired State Configuration-dokument och koppla dem till datorer.</span><span class="sxs-lookup"><span data-stu-id="535b9-104">This guide describes how to begin creating PowerShell Desired State Configuration documents and apply them to machines.</span></span> <span data-ttu-id="535b9-105">Den förutsätter grundläggande kunskaper med PowerShell-cmdlet: ar, moduler och funktioner.</span><span class="sxs-lookup"><span data-stu-id="535b9-105">It assumes basic familiarity with PowerShell cmdlets, modules, and functions.</span></span>


## <a name="create-a-configuration"></a><span data-ttu-id="535b9-106">Skapa en konfiguration</span><span class="sxs-lookup"><span data-stu-id="535b9-106">Create a Configuration</span></span> ##

<span data-ttu-id="535b9-107">[**Konfigurationer** ](https://msdn.microsoft.com/powershell/dsc/configurations) är dokument som beskriver en miljö.</span><span class="sxs-lookup"><span data-stu-id="535b9-107">[**Configurations**](https://msdn.microsoft.com/powershell/dsc/configurations) are documents that describe an environment.</span></span> <span data-ttu-id="535b9-108">Miljöer består av ”**noder**”, som ofta är virtuella eller fysiska datorer.</span><span class="sxs-lookup"><span data-stu-id="535b9-108">Environments consist of "**nodes**", which are commonly virtual or physical machines.</span></span>

<span data-ttu-id="535b9-109">Konfigurationer kan finnas i olika former.</span><span class="sxs-lookup"><span data-stu-id="535b9-109">Configurations can come in a variety of forms.</span></span> <span data-ttu-id="535b9-110">Det enklaste sättet att skapa en ny konfiguration är att skapa en .ps1-fil för (PowerShell-skript).</span><span class="sxs-lookup"><span data-stu-id="535b9-110">The easiest way to create a new configuration is to create a .ps1 (PowerShell script) file.</span></span> <span data-ttu-id="535b9-111">Gör du genom att öppna redigeringsprogram val.</span><span class="sxs-lookup"><span data-stu-id="535b9-111">To do this, open your editor of choice.</span></span> <span data-ttu-id="535b9-112">PowerShell ISE är ett bra alternativ, eftersom den förstår DSC internt.</span><span class="sxs-lookup"><span data-stu-id="535b9-112">The PowerShell ISE is a good choice, since it understands DSC natively.</span></span> <span data-ttu-id="535b9-113">Spara följande som en PS1:</span><span class="sxs-lookup"><span data-stu-id="535b9-113">Save the following as a PS1:</span></span>

```powershell
configuration MyFirstConfiguration
{
    Import-DscResource -Name WindowsFeature

    Node localhost
    {
        WindowsFeature IIS
        {
            Name = "IIS"

        }

    }

}
```
## <a name="parts-of-a-configuration"></a><span data-ttu-id="535b9-114">Delar av en konfiguration</span><span class="sxs-lookup"><span data-stu-id="535b9-114">Parts of a Configuration</span></span> ##
<span data-ttu-id="535b9-115">**Konfigurationen** är ett nyckelord som har lagts till i PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="535b9-115">**Configuration** is a keyword that has been added to PowerShell 4.0.</span></span> <span data-ttu-id="535b9-116">Det innebär en särskild typ av PowerShell-funktion som används av Desired State Configuration.</span><span class="sxs-lookup"><span data-stu-id="535b9-116">It signifies a special kind of PowerShell function used by Desired State Configuration.</span></span> <span data-ttu-id="535b9-117">I det här exemplet heter funktionen myFirstConfiguration.</span><span class="sxs-lookup"><span data-stu-id="535b9-117">In this example, the function is named myFirstConfiguration.</span></span>

<span data-ttu-id="535b9-118">Nästa rad är en import-sats, som liknar importera en modul.</span><span class="sxs-lookup"><span data-stu-id="535b9-118">The next line is an import statement, similar to importing a module.</span></span> <span data-ttu-id="535b9-119">Den kommer att diskuteras senare.</span><span class="sxs-lookup"><span data-stu-id="535b9-119">It will be discussed later on.</span></span>

<span data-ttu-id="535b9-120">”Noden” definierar namnet på den här konfigurationen fungerar på den dator.</span><span class="sxs-lookup"><span data-stu-id="535b9-120">"Node" defines the machine name this configuration will act on.</span></span> <span data-ttu-id="535b9-121">Även om den här konfigurationen redigeras lokalt, kan konfigurationer nå ut till fjärranslutna noder och konfigurera dem.</span><span class="sxs-lookup"><span data-stu-id="535b9-121">Although this configuration is edited locally, configurations can reach out to remote nodes and configure them.</span></span>

<span data-ttu-id="535b9-122">Noder kan vara datornamn eller IP-adresser.</span><span class="sxs-lookup"><span data-stu-id="535b9-122">Nodes can be machine names or IP addresses.</span></span> <span data-ttu-id="535b9-123">Du kan ha flera noder i ett enda dokument.</span><span class="sxs-lookup"><span data-stu-id="535b9-123">You can have multiple nodes in a single configuration document.</span></span> <span data-ttu-id="535b9-124">Med hjälp av [konfigurationsdata](https://msdn.microsoft.com/powershell/dsc/configdata), du kan också ha samma konfiguration som gäller för flera noder.</span><span class="sxs-lookup"><span data-stu-id="535b9-124">Using [configuration data](https://msdn.microsoft.com/powershell/dsc/configdata), you can also have the same configuration apply to multiple nodes.</span></span> <span data-ttu-id="535b9-125">I det här fallet är noden ”localhost” - vilket innebär att den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="535b9-125">In this case, the node is "localhost" - which means the local computer.</span></span>

<span data-ttu-id="535b9-126">Nästa objekt är en [ **resurs**](https://msdn.microsoft.com/powershell/dsc/resources).</span><span class="sxs-lookup"><span data-stu-id="535b9-126">The next item is a [**resource**](https://msdn.microsoft.com/powershell/dsc/resources).</span></span> <span data-ttu-id="535b9-127">Resurser är byggblocken i konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="535b9-127">Resources are building blocks of configurations.</span></span> <span data-ttu-id="535b9-128">Varje resurs är en modul som definierar logik för implementering av en enda aspekt för en dator.</span><span class="sxs-lookup"><span data-stu-id="535b9-128">Each resource is a module that defines the implementation logic of a single aspect of a machine.</span></span> <span data-ttu-id="535b9-129">Du kan visa alla resurser på din dator genom att köra **Get-DscResource** i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="535b9-129">You can view every resource on your machine by running **Get-DscResource** in PowerShell.</span></span> <span data-ttu-id="535b9-130">Resurser måste finnas på den lokala datorn och det importeras innan de kan användas i en konfiguration med **importera DscResource** som finns på den andra raden i den här konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="535b9-130">Resources must be present on the local machine and imported before they can be used in a configuration with **Import-DscResource** which is on the second line of this configuration.</span></span>

<span data-ttu-id="535b9-131">**Anta en konfiguration**</span><span class="sxs-lookup"><span data-stu-id="535b9-131">**Enacting a Configuration**</span></span>

<span data-ttu-id="535b9-132">Om skriptet ovan sparas och kör, kommer du gav inga utdata.</span><span class="sxs-lookup"><span data-stu-id="535b9-132">If the script above is saved and run, no output will be produced.</span></span> <span data-ttu-id="535b9-133">Detta är eftersom en konfiguration är bara en funktion och skriptet ovan har definierats funktionen men ännu inte köra den.</span><span class="sxs-lookup"><span data-stu-id="535b9-133">This is because a configuration is just a function, and the script above has defined the function but not yet run it.</span></span> <span data-ttu-id="535b9-134">När funktionen har definierats, måste det anropas:</span><span class="sxs-lookup"><span data-stu-id="535b9-134">After the function is defined, it must be invoked:</span></span>
```powershell
myFirstConfiguration
```

<span data-ttu-id="535b9-135">När den exekveras, configuration funktioner Validera konfigurationen är giltig.</span><span class="sxs-lookup"><span data-stu-id="535b9-135">When executed, configuration functions validate the configuration is valid.</span></span> <span data-ttu-id="535b9-136">Det bör ha inga syntaxfel, resurser bör ha alla obligatoriska parametrar som definierats och alla resurser som ska importeras innan körningen.</span><span class="sxs-lookup"><span data-stu-id="535b9-136">It should have no syntax errors, resources should have all mandatory parameters defined, and all resources should be imported before execution.</span></span>

<span data-ttu-id="535b9-137">När konfigurationen körs skapas en mapp med namnet på den konfiguration som innehåller en **. MOF-filen** för varje nod i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="535b9-137">Once the configuration is executed, it creates a folder with the name of the configuration containing a **.MOF file** for every node in the configuration.</span></span> <span data-ttu-id="535b9-138">Den. MOF-filen är en standardbaserad hantering-format som används av PowerShell DSC för att kommunicera över nätverket.</span><span class="sxs-lookup"><span data-stu-id="535b9-138">The .MOF file is a standards-based management format which is used by PowerShell DSC to communicate over the network.</span></span>

<span data-ttu-id="535b9-139">Att införa konfigurationen:</span><span class="sxs-lookup"><span data-stu-id="535b9-139">To enact the configuration:</span></span>
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration
```
<span data-ttu-id="535b9-140">Detta skapar ett PowerShell-jobb som når till noderna i konfigurationen och konfigurerar dem.</span><span class="sxs-lookup"><span data-stu-id="535b9-140">This creates a PowerShell job that reaches out to the nodes in the configuration and configures them.</span></span> <span data-ttu-id="535b9-141">Om du vill se resultatet av jobbet, använder du-vänta.</span><span class="sxs-lookup"><span data-stu-id="535b9-141">To see the output of the job, use -Wait.</span></span>
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration -Wait
```