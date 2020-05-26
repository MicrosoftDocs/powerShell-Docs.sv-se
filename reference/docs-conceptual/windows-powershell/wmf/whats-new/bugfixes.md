---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: Felkorrigeringar i WMF 5.1
ms.openlocfilehash: 8edf295eb6304dc04de2fa5d3792b1c2fc4b01f3
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810647"
---
# <a name="bug-fixes-in-wmf-51"></a><span data-ttu-id="bb6e3-103">Felkorrigeringar i WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="bb6e3-103">Bug Fixes in WMF 5.1</span></span>

## <a name="bug-fixes"></a><span data-ttu-id="bb6e3-104">Felkorrigeringar</span><span class="sxs-lookup"><span data-stu-id="bb6e3-104">Bug fixes</span></span>

<span data-ttu-id="bb6e3-105">Följande viktiga buggar korrigeras i WMF 5,1:</span><span class="sxs-lookup"><span data-stu-id="bb6e3-105">The following notable bugs are fixed in WMF 5.1:</span></span>

### <a name="module-auto-discovery-fully-honors-psmodulepath"></a><span data-ttu-id="bb6e3-106">Automatisk identifiering av modulen PSModulePath</span><span class="sxs-lookup"><span data-stu-id="bb6e3-106">Module auto-discovery fully honors PSModulePath</span></span>

<span data-ttu-id="bb6e3-107">Automatisk identifiering av modul (moduler som läses in automatiskt utan en explicit import-modul vid anrop av ett kommando) introducerades i WMF 3.</span><span class="sxs-lookup"><span data-stu-id="bb6e3-107">Module auto-discovery (loading modules automatically without an explicit Import-Module when calling a command) was introduced in WMF 3.</span></span> <span data-ttu-id="bb6e3-108">När den introducerades kontrollerar PowerShell för kommandon i `$PSHome\Modules` innan du använder `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="bb6e3-108">When introduced, PowerShell checked for commands in `$PSHome\Modules` before using `$env:PSModulePath`.</span></span>

<span data-ttu-id="bb6e3-109">WMF 5,1 ändrar det här beteendet för att respektera `$env:PSModulePath` fullständigt.</span><span class="sxs-lookup"><span data-stu-id="bb6e3-109">WMF 5.1 changes this behavior to honor `$env:PSModulePath` completely.</span></span> <span data-ttu-id="bb6e3-110">Detta gör att en användardefinierad modul som definierar kommandon som tillhandahålls av PowerShell (t. ex. `Get-ChildItem` ) automatiskt läses in och som åsidosätter det inbyggda kommandot.</span><span class="sxs-lookup"><span data-stu-id="bb6e3-110">This allows for a user-authored module that defines commands provided by PowerShell (e.g. `Get-ChildItem`) to be auto-loaded and correctly overriding the built-in command.</span></span>

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a><span data-ttu-id="bb6e3-111">Omdirigering av fil är inte längre hårdkodade Unicode-kodning</span><span class="sxs-lookup"><span data-stu-id="bb6e3-111">File redirection no longer hard-codes -Encoding Unicode</span></span>

<span data-ttu-id="bb6e3-112">I alla tidigare versioner av PowerShell var det omöjligt att kontrol lera fil kodningen som används av operatorn för fil omdirigering.</span><span class="sxs-lookup"><span data-stu-id="bb6e3-112">In all previous versions of PowerShell, it was impossible to control the file encoding used by the file redirection operator.</span></span>

<span data-ttu-id="bb6e3-113">Från och med WMF 5,1 kan du nu ändra fil kodningen för omdirigering genom att ställa in `$PSDefaultParameterValues` :</span><span class="sxs-lookup"><span data-stu-id="bb6e3-113">Starting with WMF 5.1, you can now change the file encoding of redirection by setting `$PSDefaultParameterValues`:</span></span>

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a><span data-ttu-id="bb6e3-114">Fast en regression vid åtkomst till medlemmar i system. Reflection. TypeInfo</span><span class="sxs-lookup"><span data-stu-id="bb6e3-114">Fixed a regression in accessing members of System.Reflection.TypeInfo</span></span>

<span data-ttu-id="bb6e3-115">En regression som introducerades i WMF 5,0 som har till gång till medlemmar i `System.Reflection.RuntimeType` , till exempel `[int].ImplementedInterfaces` .</span><span class="sxs-lookup"><span data-stu-id="bb6e3-115">A regression introduced in WMF 5.0 broke accessing members of `System.Reflection.RuntimeType`, for example, `[int].ImplementedInterfaces`.</span></span> <span data-ttu-id="bb6e3-116">Den här buggen har åtgärd ATS i WMF 5,1.</span><span class="sxs-lookup"><span data-stu-id="bb6e3-116">This bug has been fixed in WMF 5.1.</span></span>

### <a name="fixed-some-issues-with-com-objects"></a><span data-ttu-id="bb6e3-117">Åtgärda problem med COM-objekt</span><span class="sxs-lookup"><span data-stu-id="bb6e3-117">Fixed some issues with COM objects</span></span>

<span data-ttu-id="bb6e3-118">WMF 5,0 introducerade en ny COM-bindning för att anropa metoder på COM-objekt och komma åt egenskaper för COM-objekt.</span><span class="sxs-lookup"><span data-stu-id="bb6e3-118">WMF 5.0 introduced a new COM binder for invoking methods on COM objects and accessing properties of COM objects.</span></span> <span data-ttu-id="bb6e3-119">Detta nya binder förbättrade prestanda avsevärt men introducerade vissa buggar som har åtgärd ATS i WMF 5,1.</span><span class="sxs-lookup"><span data-stu-id="bb6e3-119">This new binder improved performance significantly but also introduced some bugs which have been fixed in WMF 5.1.</span></span>

#### <a name="argument-conversions-were-not-always-performed-correctly"></a><span data-ttu-id="bb6e3-120">Argument konverteringar utfördes inte alltid korrekt</span><span class="sxs-lookup"><span data-stu-id="bb6e3-120">Argument conversions were not always performed correctly</span></span>

<span data-ttu-id="bb6e3-121">Se följande exempel:</span><span class="sxs-lookup"><span data-stu-id="bb6e3-121">In the following example:</span></span>

```powershell
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

<span data-ttu-id="bb6e3-122">**SendKeys** -metoden förväntar sig en sträng, men PowerShell konverterade inte Char-tecken till en sträng, som Uppskjut konverteringen till **IDispatch:: Invoke**, som använder **VariantChangeType** för att utföra konverteringen.</span><span class="sxs-lookup"><span data-stu-id="bb6e3-122">The **SendKeys** method expects a string, but PowerShell did not convert the char to a string, deferring the conversion to **IDispatch::Invoke**, which uses **VariantChangeType** to do the conversion.</span></span> <span data-ttu-id="bb6e3-123">I det här exemplet har detta resulterat i att skicka nycklarna "1", "7" och "3" i stället för den förväntade **volymen. inaktivera** nyckel.</span><span class="sxs-lookup"><span data-stu-id="bb6e3-123">In this example, this resulted in sending the keys '1', '7', and '3' instead of the expected **Volume.Mute** key.</span></span>

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a><span data-ttu-id="bb6e3-124">Enumerable COM-objekt hanteras inte alltid korrekt</span><span class="sxs-lookup"><span data-stu-id="bb6e3-124">Enumerable COM objects not always handled correctly</span></span>

<span data-ttu-id="bb6e3-125">PowerShell räknar normalt upp de flesta enumerable-objekt, men en regression som introducerades i WMF 5,0 förhindrade uppräkningen av COM-objekt som implementerar IEnumerable.</span><span class="sxs-lookup"><span data-stu-id="bb6e3-125">PowerShell normally enumerates most enumerable objects, but a regression introduced in WMF 5.0 prevented the enumeration of COM objects that implement IEnumerable.</span></span> <span data-ttu-id="bb6e3-126">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="bb6e3-126">For example:</span></span>

```powershell
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

<span data-ttu-id="bb6e3-127">I exemplet ovan skrev WMF 5,0 felaktigt **skript. ord listan** till pipelinen i stället för att räkna upp nyckel/värde-par.</span><span class="sxs-lookup"><span data-stu-id="bb6e3-127">In the above example, WMF 5.0 incorrectly wrote the **Scripting.Dictionary** to the pipeline instead of enumerating the key/value pairs.</span></span>

### <a name="ordered-was-not-allowed-inside-classes"></a><span data-ttu-id="bb6e3-128">[ordnat] tilläts inte i klasser</span><span class="sxs-lookup"><span data-stu-id="bb6e3-128">[ordered] was not allowed inside classes</span></span>

<span data-ttu-id="bb6e3-129">WMF 5,0 introducerade klasser med verifiering av typ strängar som används i klasser.</span><span class="sxs-lookup"><span data-stu-id="bb6e3-129">WMF 5.0 introduced classes with validation of type literals used in classes.</span></span> <span data-ttu-id="bb6e3-130">`[ordered]`det ser ut som en typ sträng men är inte en äkta .NET-typ.</span><span class="sxs-lookup"><span data-stu-id="bb6e3-130">`[ordered]` looks like a type literal but is not a true .NET type.</span></span> <span data-ttu-id="bb6e3-131">WMF 5,0 rapporterade felaktigt ett fel i `[ordered]` en klass:</span><span class="sxs-lookup"><span data-stu-id="bb6e3-131">WMF 5.0 incorrectly reported an error on `[ordered]` inside a class:</span></span>

```powershell
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```

### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a><span data-ttu-id="bb6e3-132">Hjälp om ämnen med flera versioner fungerar inte</span><span class="sxs-lookup"><span data-stu-id="bb6e3-132">Help on About topics with multiple versions does not work</span></span>

<span data-ttu-id="bb6e3-133">Innan WMF 5,1, om du hade flera versioner av en modul installerad och alla delade ett hjälp avsnitt, till exempel about_PSReadline, `help about_PSReadline` skulle returnera flera ämnen utan ett uppenbart sätt att visa den riktiga hjälpen.</span><span class="sxs-lookup"><span data-stu-id="bb6e3-133">Before WMF 5.1, if you had multiple versions of a module installed and they all shared a help topic, for example, about_PSReadline, `help about_PSReadline` would return multiple topics with no obvious way to view the real help.</span></span>

<span data-ttu-id="bb6e3-134">WMF 5,1 åtgärdar detta genom att returnera hjälpen för den senaste versionen av ämnet.</span><span class="sxs-lookup"><span data-stu-id="bb6e3-134">WMF 5.1 fixes this by returning the help for the latest version of the topic.</span></span>

<span data-ttu-id="bb6e3-135">`Get-Help`innehåller inget sätt att ange vilken version du vill ha hjälp med.</span><span class="sxs-lookup"><span data-stu-id="bb6e3-135">`Get-Help` does not provide a way to specify which version you want help for.</span></span> <span data-ttu-id="bb6e3-136">Undvik detta genom att navigera till katalogen moduler och visa hjälpen direkt med ett verktyg som din favorit redigerare.</span><span class="sxs-lookup"><span data-stu-id="bb6e3-136">To work around this, navigate to the modules directory and view the help directly with a tool like your favorite editor.</span></span>

### <a name="powershellexe-reading-from-stdin-stopped-working"></a><span data-ttu-id="bb6e3-137">läsning av PowerShell. exe från STDIN slutade fungera</span><span class="sxs-lookup"><span data-stu-id="bb6e3-137">powershell.exe reading from STDIN stopped working</span></span>

<span data-ttu-id="bb6e3-138">Kunder använder `powershell -command -` sig av inbyggda appar för att köra PowerShell genom att skicka skriptet via STDIN. det här har tyvärr avbrutits av andra ändringar i konsol värden.</span><span class="sxs-lookup"><span data-stu-id="bb6e3-138">Customers use `powershell -command -` from native apps to execute PowerShell passing in the script via STDIN unfortunately this was broken by other changes in the console host.</span></span>

<span data-ttu-id="bb6e3-139">Detta är åtgärdat för version 5,1 i uppdaterings uppdateringen för Windows 10.</span><span class="sxs-lookup"><span data-stu-id="bb6e3-139">This is fixed for version 5.1 in the Windows 10 Anniversary Update.</span></span>

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a><span data-ttu-id="bb6e3-140">PowerShell. exe skapar insamling i CPU-användning vid start</span><span class="sxs-lookup"><span data-stu-id="bb6e3-140">powershell.exe creates spike in CPU usage on startup</span></span>

<span data-ttu-id="bb6e3-141">PowerShell använder en WMI-fråga för att kontrol lera om den har startats via grupprincip för att undvika fördröjning i inloggningen.</span><span class="sxs-lookup"><span data-stu-id="bb6e3-141">PowerShell uses a WMI query to check if it was started via Group Policy to avoid causing delay in login.</span></span> <span data-ttu-id="bb6e3-142">WMI-frågan avslutar inmatningen av tzres. mui. dll i varje process på systemet sedan WMI-klassen **Win32_Process** försöker hämta information om lokal tidszon.</span><span class="sxs-lookup"><span data-stu-id="bb6e3-142">The WMI query ends up injecting tzres.mui.dll into every process on the system since the WMI **Win32_Process** class attempts to retrieve local timezone information.</span></span> <span data-ttu-id="bb6e3-143">Detta resulterar i en stor processor ökning i **Wmiprvse** (WMI-providerns värd).</span><span class="sxs-lookup"><span data-stu-id="bb6e3-143">This results in a large CPU spike in **wmiprvse** (the WMI provider host).</span></span> <span data-ttu-id="bb6e3-144">Korrigera är att använda Win32 API-anrop för att hämta samma information i stället för att använda WMI.</span><span class="sxs-lookup"><span data-stu-id="bb6e3-144">Fix is to use Win32 API calls to get the same information instead of using WMI.</span></span>
