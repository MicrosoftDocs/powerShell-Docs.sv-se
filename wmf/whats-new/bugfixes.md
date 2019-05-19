---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: Felkorrigeringar i WMF 5.1
ms.openlocfilehash: 8edf295eb6304dc04de2fa5d3792b1c2fc4b01f3
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856212"
---
# <a name="bug-fixes-in-wmf-51"></a><span data-ttu-id="7875d-103">Felkorrigeringar i WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="7875d-103">Bug Fixes in WMF 5.1</span></span>

## <a name="bug-fixes"></a><span data-ttu-id="7875d-104">Felkorrigeringar</span><span class="sxs-lookup"><span data-stu-id="7875d-104">Bug fixes</span></span>

<span data-ttu-id="7875d-105">Följande viktiga programfel korrigeras i WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="7875d-105">The following notable bugs are fixed in WMF 5.1:</span></span>

### <a name="module-auto-discovery-fully-honors-psmodulepath"></a><span data-ttu-id="7875d-106">Automatisk identifiering av modulen godkänner fullständigt PSModulePath</span><span class="sxs-lookup"><span data-stu-id="7875d-106">Module auto-discovery fully honors PSModulePath</span></span>

<span data-ttu-id="7875d-107">Modulen automatisk identifiering (läser in moduler automatiskt utan en explicit Import-Module när du anropar ett kommando) introducerades i WMF 3.</span><span class="sxs-lookup"><span data-stu-id="7875d-107">Module auto-discovery (loading modules automatically without an explicit Import-Module when calling a command) was introduced in WMF 3.</span></span> <span data-ttu-id="7875d-108">När introducerade kommer PowerShell kontrolleras för kommandon i `$PSHome\Modules` innan du använder `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="7875d-108">When introduced, PowerShell checked for commands in `$PSHome\Modules` before using `$env:PSModulePath`.</span></span>

<span data-ttu-id="7875d-109">WMF 5.1 ändrar det här beteendet att respektera `$env:PSModulePath` helt.</span><span class="sxs-lookup"><span data-stu-id="7875d-109">WMF 5.1 changes this behavior to honor `$env:PSModulePath` completely.</span></span> <span data-ttu-id="7875d-110">Det möjliggör en användarskapade modul som definierar med PowerShell-kommandon (t.ex. `Get-ChildItem`) automatiskt-läsas och korrekt åsidosätter ett inbyggt kommando.</span><span class="sxs-lookup"><span data-stu-id="7875d-110">This allows for a user-authored module that defines commands provided by PowerShell (e.g. `Get-ChildItem`) to be auto-loaded and correctly overriding the built-in command.</span></span>

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a><span data-ttu-id="7875d-111">Filen omdirigering utan långa hård-koder-kodning Unicode</span><span class="sxs-lookup"><span data-stu-id="7875d-111">File redirection no longer hard-codes -Encoding Unicode</span></span>

<span data-ttu-id="7875d-112">I alla tidigare versioner av PowerShell är det omöjligt att styra Filkodning som används av operatorn för omdirigering av filen.</span><span class="sxs-lookup"><span data-stu-id="7875d-112">In all previous versions of PowerShell, it was impossible to control the file encoding used by the file redirection operator.</span></span>

<span data-ttu-id="7875d-113">Från och med WMF 5.1, du kan nu ändra Filkodning för omdirigering genom att ange `$PSDefaultParameterValues`:</span><span class="sxs-lookup"><span data-stu-id="7875d-113">Starting with WMF 5.1, you can now change the file encoding of redirection by setting `$PSDefaultParameterValues`:</span></span>

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a><span data-ttu-id="7875d-114">Fast en regression i åtkomst till medlemmar i System.Reflection.TypeInfo</span><span class="sxs-lookup"><span data-stu-id="7875d-114">Fixed a regression in accessing members of System.Reflection.TypeInfo</span></span>

<span data-ttu-id="7875d-115">En regression med WMF 5.0 avbrutits åtkomst till medlemmar i `System.Reflection.RuntimeType`, till exempel `[int].ImplementedInterfaces`.</span><span class="sxs-lookup"><span data-stu-id="7875d-115">A regression introduced in WMF 5.0 broke accessing members of `System.Reflection.RuntimeType`, for example, `[int].ImplementedInterfaces`.</span></span> <span data-ttu-id="7875d-116">Det här felet har åtgärdats i WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="7875d-116">This bug has been fixed in WMF 5.1.</span></span>

### <a name="fixed-some-issues-with-com-objects"></a><span data-ttu-id="7875d-117">Fast några problem med COM-objekt</span><span class="sxs-lookup"><span data-stu-id="7875d-117">Fixed some issues with COM objects</span></span>

<span data-ttu-id="7875d-118">WMF 5.0 introducerade en ny COM-binder för anropar metoder på COM-objekt och komma åt egenskaperna för COM-objekt.</span><span class="sxs-lookup"><span data-stu-id="7875d-118">WMF 5.0 introduced a new COM binder for invoking methods on COM objects and accessing properties of COM objects.</span></span> <span data-ttu-id="7875d-119">Den här nya binder förbättrad prestanda avsevärt, men också medfört vissa buggar som fastställts i WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="7875d-119">This new binder improved performance significantly but also introduced some bugs which have been fixed in WMF 5.1.</span></span>

#### <a name="argument-conversions-were-not-always-performed-correctly"></a><span data-ttu-id="7875d-120">Argumentet konverteringar utfördes inte alltid korrekt</span><span class="sxs-lookup"><span data-stu-id="7875d-120">Argument conversions were not always performed correctly</span></span>

<span data-ttu-id="7875d-121">I följande exempel:</span><span class="sxs-lookup"><span data-stu-id="7875d-121">In the following example:</span></span>

```powershell
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

<span data-ttu-id="7875d-122">Den **Skicka tecken** metoden förväntar sig en sträng, men PowerShell inte att konvertera char till en sträng skjuta upp konverteringen till **IDispatch::Invoke**, som använder **VariantChangeType**att utföra konverteringen.</span><span class="sxs-lookup"><span data-stu-id="7875d-122">The **SendKeys** method expects a string, but PowerShell did not convert the char to a string, deferring the conversion to **IDispatch::Invoke**, which uses **VariantChangeType** to do the conversion.</span></span> <span data-ttu-id="7875d-123">I det här exemplet är detta resulterade i att skicka nycklarna '1', '7 ”och” 3 ”i stället för den förväntade **Volume.Mute** nyckel.</span><span class="sxs-lookup"><span data-stu-id="7875d-123">In this example, this resulted in sending the keys '1', '7', and '3' instead of the expected **Volume.Mute** key.</span></span>

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a><span data-ttu-id="7875d-124">Uppräkningsbara COM-objekt som inte alltid hanteras korrekt</span><span class="sxs-lookup"><span data-stu-id="7875d-124">Enumerable COM objects not always handled correctly</span></span>

<span data-ttu-id="7875d-125">PowerShell räknar upp normalt de flesta uppräkningsbara objekt, men en regression med WMF 5.0 förhindrade uppräkning av COM-objekt som implementerar IEnumerable.</span><span class="sxs-lookup"><span data-stu-id="7875d-125">PowerShell normally enumerates most enumerable objects, but a regression introduced in WMF 5.0 prevented the enumeration of COM objects that implement IEnumerable.</span></span> <span data-ttu-id="7875d-126">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="7875d-126">For example:</span></span>

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

<span data-ttu-id="7875d-127">I exemplet ovan WMF 5.0 felaktigt skrev den **Scripting.Dictionary** till pipelinen i stället för att räkna upp nyckel/värde-par.</span><span class="sxs-lookup"><span data-stu-id="7875d-127">In the above example, WMF 5.0 incorrectly wrote the **Scripting.Dictionary** to the pipeline instead of enumerating the key/value pairs.</span></span>

### <a name="ordered-was-not-allowed-inside-classes"></a><span data-ttu-id="7875d-128">[sorterade] inte tilläts inuti klasser</span><span class="sxs-lookup"><span data-stu-id="7875d-128">[ordered] was not allowed inside classes</span></span>

<span data-ttu-id="7875d-129">WMF 5.0 introducerade klasser med verifiering av typen litteraler som används i klasser.</span><span class="sxs-lookup"><span data-stu-id="7875d-129">WMF 5.0 introduced classes with validation of type literals used in classes.</span></span> <span data-ttu-id="7875d-130">`[ordered]` ser ut som en literal typ men är inte av typen SANT .NET.</span><span class="sxs-lookup"><span data-stu-id="7875d-130">`[ordered]` looks like a type literal but is not a true .NET type.</span></span> <span data-ttu-id="7875d-131">WMF 5.0 felaktigt rapporterade ett fel på `[ordered]` inuti en klass:</span><span class="sxs-lookup"><span data-stu-id="7875d-131">WMF 5.0 incorrectly reported an error on `[ordered]` inside a class:</span></span>

```powershell
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```

### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a><span data-ttu-id="7875d-132">Hjälp om ämnen med flera versioner fungerar inte</span><span class="sxs-lookup"><span data-stu-id="7875d-132">Help on About topics with multiple versions does not work</span></span>

<span data-ttu-id="7875d-133">Innan du WMF 5.1, om du hade flera versioner av en installerad modul och alla delade ett hjälpavsnitt, till exempel about_PSReadline, `help about_PSReadline` kommer att returnera flera avsnitt med inget enkelt sätt att visa den verkliga hjälpen.</span><span class="sxs-lookup"><span data-stu-id="7875d-133">Before WMF 5.1, if you had multiple versions of a module installed and they all shared a help topic, for example, about_PSReadline, `help about_PSReadline` would return multiple topics with no obvious way to view the real help.</span></span>

<span data-ttu-id="7875d-134">WMF 5.1 åtgärdar detta genom att returnera hjälpen för den senaste versionen av avsnittet.</span><span class="sxs-lookup"><span data-stu-id="7875d-134">WMF 5.1 fixes this by returning the help for the latest version of the topic.</span></span>

<span data-ttu-id="7875d-135">`Get-Help` ger inte möjligt att ange vilken version du vill ha hjälp för.</span><span class="sxs-lookup"><span data-stu-id="7875d-135">`Get-Help` does not provide a way to specify which version you want help for.</span></span> <span data-ttu-id="7875d-136">Undvik detta genom att gå till moduler-katalog och visa hjälp direkt med ett verktyg som redigeringsprogram du föredrar.</span><span class="sxs-lookup"><span data-stu-id="7875d-136">To work around this, navigate to the modules directory and view the help directly with a tool like your favorite editor.</span></span>

### <a name="powershellexe-reading-from-stdin-stopped-working"></a><span data-ttu-id="7875d-137">PowerShell.exe läsning från STDIN slutar fungera</span><span class="sxs-lookup"><span data-stu-id="7875d-137">powershell.exe reading from STDIN stopped working</span></span>

<span data-ttu-id="7875d-138">Kunder använder `powershell -command -` från inbyggda appar för att köra PowerShell skicka i skriptet via STDIN tyvärr detta har fördelat andra ändringar i konsolvärden.</span><span class="sxs-lookup"><span data-stu-id="7875d-138">Customers use `powershell -command -` from native apps to execute PowerShell passing in the script via STDIN unfortunately this was broken by other changes in the console host.</span></span>

<span data-ttu-id="7875d-139">Detta har åtgärdats för version 5.1 i Windows 10 Anniversary Update.</span><span class="sxs-lookup"><span data-stu-id="7875d-139">This is fixed for version 5.1 in the Windows 10 Anniversary Update.</span></span>

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a><span data-ttu-id="7875d-140">PowerShell.exe skapar topp i CPU-användning vid start</span><span class="sxs-lookup"><span data-stu-id="7875d-140">powershell.exe creates spike in CPU usage on startup</span></span>

<span data-ttu-id="7875d-141">PowerShell använder en WMI-fråga för att kontrollera om det har börjat via en grupprincip inte orsakar fördröjning när du loggar in.</span><span class="sxs-lookup"><span data-stu-id="7875d-141">PowerShell uses a WMI query to check if it was started via Group Policy to avoid causing delay in login.</span></span> <span data-ttu-id="7875d-142">WMI-frågan slutar Infoga tzres.mui.dll i varje process på systemet sedan WMI **Win32_Process** klass försöker hämta lokala tidszonen.</span><span class="sxs-lookup"><span data-stu-id="7875d-142">The WMI query ends up injecting tzres.mui.dll into every process on the system since the WMI **Win32_Process** class attempts to retrieve local timezone information.</span></span> <span data-ttu-id="7875d-143">Detta resulterar i en stor CPU-topp i **wmiprvse** (WMI-provider host).</span><span class="sxs-lookup"><span data-stu-id="7875d-143">This results in a large CPU spike in **wmiprvse** (the WMI provider host).</span></span> <span data-ttu-id="7875d-144">Korrigeringen är att använda Win32 API-anrop för att få samma information i stället för med hjälp av WMI.</span><span class="sxs-lookup"><span data-stu-id="7875d-144">Fix is to use Win32 API calls to get the same information instead of using WMI.</span></span>
