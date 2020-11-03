---
description: Windows Management Instrumentation (WMI) använder Common Information Model (CIM) för att representera system, program, nätverk, enheter och andra hanterbara komponenter i det moderna företaget.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wmi?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WMI
ms.openlocfilehash: d24b952ee167e51815d6d9920e95bbc9a6bb9608
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271929"
---
# <a name="about-wmi"></a><span data-ttu-id="c2c40-104">Om WMI</span><span class="sxs-lookup"><span data-stu-id="c2c40-104">About WMI</span></span>

## <a name="short-description"></a><span data-ttu-id="c2c40-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c2c40-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="c2c40-106">Windows Management Instrumentation (WMI) använder Common Information Model (CIM) för att representera system, program, nätverk, enheter och andra hanterbara komponenter i det moderna företaget.</span><span class="sxs-lookup"><span data-stu-id="c2c40-106">Windows Management Instrumentation (WMI) uses the Common Information Model (CIM) to represent systems, applications, networks, devices, and other manageable components of the modern enterprise.</span></span>

## <a name="long-description"></a><span data-ttu-id="c2c40-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c2c40-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="c2c40-108">Windows Management Instrumentation (WMI) är Microsofts implementering av Web-Based Enterprise Management (WBEM), bransch standard.</span><span class="sxs-lookup"><span data-stu-id="c2c40-108">Windows Management Instrumentation (WMI) is Microsoft's implementation of Web-Based Enterprise Management (WBEM), the industry standard.</span></span>

<span data-ttu-id="c2c40-109">Klassisk WMI använder DCOM för att kommunicera med nätverksanslutna enheter för att hantera fjärrsystem.</span><span class="sxs-lookup"><span data-stu-id="c2c40-109">Classic WMI uses DCOM to communicate with networked devices to manage remote systems.</span></span> <span data-ttu-id="c2c40-110">Windows PowerShell 3,0 introducerar en CIM-provider som använder WinRM för att ta bort beroendet av DCOM.</span><span class="sxs-lookup"><span data-stu-id="c2c40-110">Windows PowerShell 3.0 introduces a CIM provider model that uses WinRM to remove the dependency on DCOM.</span></span> <span data-ttu-id="c2c40-111">Den här CIM-providern använder också nya WMI-providers-API: er som gör att utvecklare kan skriva Windows PowerShell-cmdlets i intern kod (C \+ \+ ).</span><span class="sxs-lookup"><span data-stu-id="c2c40-111">This CIM provider model also uses new WMI provider APIs that enable developers to write Windows PowerShell cmdlets in native code (C\+\+).</span></span>

<span data-ttu-id="c2c40-112">Blanda inte WMI-providrar med Windows PowerShell-leverantörer.</span><span class="sxs-lookup"><span data-stu-id="c2c40-112">Do not confuse WMI providers with Windows PowerShell providers.</span></span> <span data-ttu-id="c2c40-113">Många Windows-funktioner har en associerad WMI-provider som visar hanterings funktionerna.</span><span class="sxs-lookup"><span data-stu-id="c2c40-113">Many Windows features have an associated WMI provider that exposes their management capabilities.</span></span> <span data-ttu-id="c2c40-114">Om du vill hämta WMI-providers kör du en WMI-fråga som hämtar instanser av klassen __Provider WMI, till exempel följande fråga.</span><span class="sxs-lookup"><span data-stu-id="c2c40-114">To get WMI providers, run a WMI query that gets instances of the __Provider WMI class, such as the following query.</span></span>

```powershell
Get-WmiObject -Class __Provider
```

## <a name="three-components-of-wmi"></a><span data-ttu-id="c2c40-115">TRE KOMPONENTER I WMI</span><span class="sxs-lookup"><span data-stu-id="c2c40-115">THREE COMPONENTS OF WMI</span></span>

<span data-ttu-id="c2c40-116">Följande tre komponenter i WMI interagerar med Windows PowerShell: namnrymder, providers och klasser.</span><span class="sxs-lookup"><span data-stu-id="c2c40-116">The following three components of WMI interact with Windows PowerShell: Namespaces, Providers, and Classes.</span></span>

<span data-ttu-id="c2c40-117">WMI-namnområden ordnar WMI-providers och WMI-klasser i grupper av relaterade komponenter.</span><span class="sxs-lookup"><span data-stu-id="c2c40-117">WMI Namespaces organize WMI providers and WMI classes into groups of related components.</span></span> <span data-ttu-id="c2c40-118">På så sätt liknar de .NET Framework namn områden.</span><span class="sxs-lookup"><span data-stu-id="c2c40-118">In this way, they are similar to .NET Framework namespaces.</span></span>
<span data-ttu-id="c2c40-119">Namn områden är inte fysiska platser, men är mer logiska databaser.</span><span class="sxs-lookup"><span data-stu-id="c2c40-119">Namespaces are not physical locations, but are more like logical databases.</span></span>
<span data-ttu-id="c2c40-120">Alla WMI-namnområden är instanser av klassen __Namespace system.</span><span class="sxs-lookup"><span data-stu-id="c2c40-120">All WMI namespaces are instances of the __Namespace system class.</span></span> <span data-ttu-id="c2c40-121">Standard namn området för WMI är rot \/ -cimv2 (sedan Microsoft Windows 2000).</span><span class="sxs-lookup"><span data-stu-id="c2c40-121">The default WMI namespace is Root\/CIMV2 (since Microsoft Windows 2000).</span></span> <span data-ttu-id="c2c40-122">Använd ett kommando med följande format om du vill använda Windows PowerShell för att hämta WMI-namnrymder i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c2c40-122">To use Windows PowerShell to get WMI namespaces in the current session, use a command with the following format.</span></span>

```powershell
Get-WmiObject -Class __Namespace
```

<span data-ttu-id="c2c40-123">Om du vill hämta WMI-namnrymder i andra namn områden använder du parametern namespace för att ändra sökningens plats.</span><span class="sxs-lookup"><span data-stu-id="c2c40-123">To get WMI namespaces in other namespaces, use the Namespace parameter to change the location of the search.</span></span> <span data-ttu-id="c2c40-124">Följande kommando hittar WMI-namnrymder som finns i namn området rot/Cimv2/program.</span><span class="sxs-lookup"><span data-stu-id="c2c40-124">The following command finds WMI namespaces that reside in the Root/Cimv2/Applications namespace.</span></span>

```powershell
Get-WmiObject -Class __Namespace -Namespace root/CIMv2/applications
```

<span data-ttu-id="c2c40-125">WMI-namnrymder är hierarkiska.</span><span class="sxs-lookup"><span data-stu-id="c2c40-125">WMI namespaces are hierarchical.</span></span> <span data-ttu-id="c2c40-126">Därför kräver en rekursiv fråga som börjar vid rot namn rymden att hämta en lista över alla namn områden i ett visst system.</span><span class="sxs-lookup"><span data-stu-id="c2c40-126">Therefore, obtaining a list of all namespaces on a particular system requires performing a recursive query starting at the root namespace.</span></span>

<span data-ttu-id="c2c40-127">WMI-providers visar information om Windows-hanterbara objekt.</span><span class="sxs-lookup"><span data-stu-id="c2c40-127">WMI Providers expose information about Windows manageable objects.</span></span> <span data-ttu-id="c2c40-128">En provider hämtar data från en komponent och skickar dessa data via WMI till ett hanterings program, till exempel Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c2c40-128">A provider retrieves data from a component, and passes that data through WMI to a management application, such as Windows PowerShell.</span></span> <span data-ttu-id="c2c40-129">De flesta WMI-providers är dynamiska leverantörer, vilket innebär att de hämtar data dynamiskt när de begärs via hanterings programmet.</span><span class="sxs-lookup"><span data-stu-id="c2c40-129">Most WMI providers are dynamic providers, which means that they obtain the data dynamically when it is requested through the management application.</span></span>

## <a name="finding-wmi-classes"></a><span data-ttu-id="c2c40-130">HITTA WMI-KLASSER</span><span class="sxs-lookup"><span data-stu-id="c2c40-130">FINDING WMI CLASSES</span></span>

<span data-ttu-id="c2c40-131">I en standard installation av Windows 8 finns det fler än 1 100 WMI-klasser i rot- \/ Cimv2.</span><span class="sxs-lookup"><span data-stu-id="c2c40-131">In a default installation of Windows 8, there are more than 1,100 WMI classes in Root\/Cimv2.</span></span> <span data-ttu-id="c2c40-132">Med den här många WMI-klasser identifierar utmaningarna vilken WMI-klass som ska användas för att utföra en speciell uppgift.</span><span class="sxs-lookup"><span data-stu-id="c2c40-132">With this many WMI classes, the challenge becomes identifying the appropriate WMI class to use to perform a specific task.</span></span> <span data-ttu-id="c2c40-133">Windows PowerShell 3,0 erbjuder två sätt att hitta WMI-klasser som är relaterade till ett speciellt ämne.</span><span class="sxs-lookup"><span data-stu-id="c2c40-133">Windows PowerShell 3.0 provides two ways to find WMI classes that are related to a specific topic.</span></span>

<span data-ttu-id="c2c40-134">Om du till exempel vill hitta WMI-klasser i rot \\ cimv2 WMI-namnrymd som är relaterade till diskar, kan du använda en fråga som den som visas här.</span><span class="sxs-lookup"><span data-stu-id="c2c40-134">For example,to find WMI classes in the root\\CIMV2 WMI namespace that are related to disks, you can use a query such as the one shown here.</span></span>

```powershell
Get-WmiObject -List *disk*
```

<span data-ttu-id="c2c40-135">Om du vill hitta WMI-klasser som är relaterade till minne kan du använda en fråga som den som visas här.</span><span class="sxs-lookup"><span data-stu-id="c2c40-135">To find WMI classes that are related to memory, you might use a query such as the one shown here.</span></span>

```powershell
Get-WmiObject -List *memory*
```

<span data-ttu-id="c2c40-136">CIM-cmdletarna ger också möjlighet att identifiera WMI-klasser.</span><span class="sxs-lookup"><span data-stu-id="c2c40-136">The CIM cmdlets also provide the ability to discover WMI classes.</span></span> <span data-ttu-id="c2c40-137">Använd Get-CIMClass-cmdleten för att göra detta.</span><span class="sxs-lookup"><span data-stu-id="c2c40-137">To do this, use the Get-CIMClass cmdlet.</span></span> <span data-ttu-id="c2c40-138">Kommandot som visas här listar WMI-klasser relaterade till video.</span><span class="sxs-lookup"><span data-stu-id="c2c40-138">The command shown here lists WMI classes related to video.</span></span>

```powershell
Get-CimClass *video*
```

<span data-ttu-id="c2c40-139">När du anpassar WMI-namnrymder och använder med hjälp av tabb-expansion kan du enkelt identifiera namn områden för underordnade WMI.</span><span class="sxs-lookup"><span data-stu-id="c2c40-139">Tab expansion works when changing WMI namespaces, and therefore use of tab expansion makes sub-WMI namespaces easily discoverable.</span></span> <span data-ttu-id="c2c40-140">I följande exempel visar Get-CimClass-cmdleten WMI-klasser relaterade till energi inställningar.</span><span class="sxs-lookup"><span data-stu-id="c2c40-140">In the following example, the Get-CimClass cmdlet lists WMI classes related to power settings.</span></span>
<span data-ttu-id="c2c40-141">För att hitta den, anger du `root/CIMV2/` namn området och trycker sedan på tabbtangenten flera gånger tills Power namespace visas.</span><span class="sxs-lookup"><span data-stu-id="c2c40-141">To find it, type the `root/CIMV2/` namespace and then press the Tab key several times until the power namespace appears.</span></span> <span data-ttu-id="c2c40-142">Här är kommandot:</span><span class="sxs-lookup"><span data-stu-id="c2c40-142">Here is the command:</span></span>

```powershell
Get-CimClass *power* -Namespace root/cimv2/power
```
