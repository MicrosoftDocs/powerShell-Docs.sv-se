---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
title: Felkorrigeringar i WMF 5.1
ms.openlocfilehash: 137095f50f9f926d3488ff9c1ce8270ddbda63eb
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="bug-fixes-in-wmf-51"></a><span data-ttu-id="e37a3-103">Felkorrigeringar i WMF 5.1#</span><span class="sxs-lookup"><span data-stu-id="e37a3-103">Bug Fixes in WMF 5.1#</span></span>

## <a name="bug-fixes"></a><span data-ttu-id="e37a3-104">Felkorrigeringar</span><span class="sxs-lookup"><span data-stu-id="e37a3-104">Bug fixes</span></span> ##

<span data-ttu-id="e37a3-105">Följande viktiga programfel har åtgärdats i WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="e37a3-105">The following notable bugs are fixed in WMF 5.1:</span></span>

### <a name="module-auto-discovery-fully-honors-envpsmodulepath"></a><span data-ttu-id="e37a3-106">Automatisk identifiering av modulen godkänner fullständigt`$env:PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="e37a3-106">Module auto-discovery fully honors `$env:PSModulePath`</span></span> ###

<span data-ttu-id="e37a3-107">Modulen automatisk identifiering (inläsning moduler automatiskt utan en explicit Import-Module vid anrop av ett kommando) introducerades i WMF 3.</span><span class="sxs-lookup"><span data-stu-id="e37a3-107">Module auto-discovery (loading modules automatically without an explicit Import-Module when calling a command) was introduced in WMF 3.</span></span> <span data-ttu-id="e37a3-108">När införts, PowerShell markerade kommandon i `$PSHome\Modules` innan du använder `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="e37a3-108">When introduced, PowerShell checked for commands in `$PSHome\Modules` before using `$env:PSModulePath`.</span></span>

<span data-ttu-id="e37a3-109">WMF 5.1 ändras detta beteende respektera `$env:PSModulePath` helt.</span><span class="sxs-lookup"><span data-stu-id="e37a3-109">WMF 5.1 changes this behavior to honor `$env:PSModulePath` completely.</span></span> <span data-ttu-id="e37a3-110">Det här tillåter en användare skriven modul som definierar med PowerShell-kommandon (t.ex. `Get-ChildItem`) som automatiskt-hämtas och korrekt åsidosätter ett inbyggt kommando.</span><span class="sxs-lookup"><span data-stu-id="e37a3-110">This allows for a user-authored module that defines commands provided by PowerShell (e.g. `Get-ChildItem`) to be auto-loaded and correctly overriding the built-in command.</span></span>

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a><span data-ttu-id="e37a3-111">Filen inte längre hårdkodar för omdirigering`-Encoding Unicode`</span><span class="sxs-lookup"><span data-stu-id="e37a3-111">File redirection no longer hard-codes `-Encoding Unicode`</span></span> ###

<span data-ttu-id="e37a3-112">I alla tidigare versioner av PowerShell inte var möjligt att styra Filkodning som används av operatorn filen omdirigering, t.ex. `Get-ChildItem > out.txt` eftersom PowerShell lagts `-Encoding Unicode`.</span><span class="sxs-lookup"><span data-stu-id="e37a3-112">In all previous versions of PowerShell, it was impossible to control the file encoding used by the file redirection operator, e.g. `Get-ChildItem > out.txt` because PowerShell added `-Encoding Unicode`.</span></span>

<span data-ttu-id="e37a3-113">Från och med WMF 5.1, du kan nu ändra Filkodning av omdirigering genom att ange `$PSDefaultParameterValues`:</span><span class="sxs-lookup"><span data-stu-id="e37a3-113">Starting with WMF 5.1, you can now change the file encoding of redirection by setting `$PSDefaultParameterValues`:</span></span>

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a><span data-ttu-id="e37a3-114">Fast en regression för åtkomst till medlemmar i`System.Reflection.TypeInfo`</span><span class="sxs-lookup"><span data-stu-id="e37a3-114">Fixed a regression in accessing members of `System.Reflection.TypeInfo`</span></span> ###

<span data-ttu-id="e37a3-115">En regression med WMF 5.0 bröt mot åtkomst till medlemmar i `System.Reflection.RuntimeType`, t.ex. `[int].ImplementedInterfaces`.</span><span class="sxs-lookup"><span data-stu-id="e37a3-115">A regression introduced in WMF 5.0 broke accessing members of `System.Reflection.RuntimeType`, e.g. `[int].ImplementedInterfaces`.</span></span>
<span data-ttu-id="e37a3-116">Det här felet är åtgärdat i WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="e37a3-116">This bug has been fixed in WMF 5.1.</span></span>


### <a name="fixed-some-issues-with-com-objects"></a><span data-ttu-id="e37a3-117">Fasta några problem med COM-objekt</span><span class="sxs-lookup"><span data-stu-id="e37a3-117">Fixed some issues with COM objects</span></span> ###

<span data-ttu-id="e37a3-118">WMF 5.0 introduceras en ny COM-binder för anropa metoder i COM-objekt och inte att komma åt egenskaperna för COM-objekt.</span><span class="sxs-lookup"><span data-stu-id="e37a3-118">WMF 5.0 introduced a new COM binder for invoking methods on COM objects and accessing properties of COM objects.</span></span> <span data-ttu-id="e37a3-119">Den här nya binder bättre prestanda avsevärt men infördes också vissa fel som har åtgärdats i WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="e37a3-119">This new binder improved performance significantly but also introduced some bugs which have been fixed in WMF 5.1.</span></span>

#### <a name="argument-conversions-were-not-always-performed-correctly"></a><span data-ttu-id="e37a3-120">Argumentet konverteringar utfördes inte alltid korrekt</span><span class="sxs-lookup"><span data-stu-id="e37a3-120">Argument conversions were not always performed correctly</span></span> ####

<span data-ttu-id="e37a3-121">I följande exempel:</span><span class="sxs-lookup"><span data-stu-id="e37a3-121">In the following example:</span></span>

```
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

<span data-ttu-id="e37a3-122">SendKeys-metoden förväntar sig en sträng, men PowerShell konverterades inte char till en sträng, vänta konverteringen till IDispatch::Invoke som använder VariantChangeType för att utföra konvertering, som i det här exemplet resulterade i att skicka tangenterna '1', '7' och '3' i stället av den förväntade Volume.Mute nyckeln.</span><span class="sxs-lookup"><span data-stu-id="e37a3-122">The SendKeys method expects a string, but PowerShell did not convert the char to a string, deferring the conversion to IDispatch::Invoke, which uses VariantChangeType to do the conversion, which in this example resulted in sending the keys '1', '7', and '3' instead of the expected Volume.Mute key.</span></span>

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a><span data-ttu-id="e37a3-123">Enumerable COM-objekt som inte alltid hanteras korrekt</span><span class="sxs-lookup"><span data-stu-id="e37a3-123">Enumerable COM objects not always handled correctly</span></span> ####

<span data-ttu-id="e37a3-124">PowerShell räknar upp normalt de flesta enumerable objekt, men en regression med WMF 5.0 förhindrade uppräkning av COM-objekt som implementerar IEnumerable.</span><span class="sxs-lookup"><span data-stu-id="e37a3-124">PowerShell normally enumerates most enumerable objects, but a regression introduced in WMF 5.0 prevented the enumeration of COM objects that implement IEnumerable.</span></span>  <span data-ttu-id="e37a3-125">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="e37a3-125">For example:</span></span>

```
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

<span data-ttu-id="e37a3-126">I exemplet ovan skrev WMF 5.0 felaktigt i Scripting.Dictionary för pipeline i stället för att räkna upp nyckel/värde-par.</span><span class="sxs-lookup"><span data-stu-id="e37a3-126">In the above example, WMF 5.0 incorrectly wrote the Scripting.Dictionary to the pipeline instead of enumerating the key/value pairs.</span></span>

<span data-ttu-id="e37a3-127">Den här ändringen adresser [utfärda 1752224 på Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224)</span><span class="sxs-lookup"><span data-stu-id="e37a3-127">This change also addresses [issue 1752224 on Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224)</span></span>

### <a name="ordered-was-not-allowed-inside-classes"></a><span data-ttu-id="e37a3-128">`[ordered]`Det var inte tillåtet i klasser</span><span class="sxs-lookup"><span data-stu-id="e37a3-128">`[ordered]` was not allowed inside classes</span></span> ###

<span data-ttu-id="e37a3-129">WMF 5.0 introducerade klasser med verifieringen av typen literaler som används i klasser.</span><span class="sxs-lookup"><span data-stu-id="e37a3-129">WMF 5.0 introduced classes with validation of type literals used in classes.</span></span>  
<span data-ttu-id="e37a3-130">`[ordered]`ser ut som en literal typ men är inte ett TrueType .NET.</span><span class="sxs-lookup"><span data-stu-id="e37a3-130">`[ordered]` looks like a type literal but is not a true .NET type.</span></span> <span data-ttu-id="e37a3-131">WMF 5.0 felaktigt rapporterade ett fel på `[ordered]` inuti en klass:</span><span class="sxs-lookup"><span data-stu-id="e37a3-131">WMF 5.0 incorrectly reported an error on `[ordered]` inside a class:</span></span>

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a><span data-ttu-id="e37a3-132">Hjälp på om med flera versioner fungerar inte</span><span class="sxs-lookup"><span data-stu-id="e37a3-132">Help on About topics with multiple versions does not work</span></span> ###

<span data-ttu-id="e37a3-133">Innan du WMF 5.1, om du har flera versioner av en installerad modul och alla delade ett hjälpavsnitt, till exempel about_PSReadline, `help about_PSReadline` returnerar flera avsnitt med inget enkelt sätt att visa verkliga hjälpen.</span><span class="sxs-lookup"><span data-stu-id="e37a3-133">Before WMF 5.1, if you had multiple versions of a module installed and they all shared a help topic, for example, about_PSReadline, `help about_PSReadline` would return multiple topics with no obvious way to view the real help.</span></span>

<span data-ttu-id="e37a3-134">WMF 5.1 åtgärdar detta genom att gå tillbaka i hjälpen för den senaste versionen av avsnittet.</span><span class="sxs-lookup"><span data-stu-id="e37a3-134">WMF 5.1 fixes this by returning the help for the latest version of the topic.</span></span>

<span data-ttu-id="e37a3-135">`Get-Help`ger inte ett sätt att ange vilken version du vill ha hjälp för.</span><span class="sxs-lookup"><span data-stu-id="e37a3-135">`Get-Help` does not provide a way to specify which version you want help for.</span></span> <span data-ttu-id="e37a3-136">Undvik detta genom att navigera till katalogen moduler och visa hjälp direkt med ett verktyg som favorit redigerare.</span><span class="sxs-lookup"><span data-stu-id="e37a3-136">To work around this, navigate to the modules directory and view the help directly with a tool like your favorite editor.</span></span> 

### <a name="powershellexe-reading-from-stdin-stopped-working"></a><span data-ttu-id="e37a3-137">PowerShell.exe läsning från STDIN slutat att fungera</span><span class="sxs-lookup"><span data-stu-id="e37a3-137">powershell.exe reading from STDIN stopped working</span></span>

<span data-ttu-id="e37a3-138">Kunder använder `powershell -command -` från interna appar att köra PowerShell vidare i skriptet via STDIN tyvärr detta har brutits pga att andra ändringar konsolen värden.</span><span class="sxs-lookup"><span data-stu-id="e37a3-138">Customers use `powershell -command -` from native apps to execute PowerShell passing in the script via STDIN unfortunately this was broken due to other changes it the console host.</span></span>

<span data-ttu-id="e37a3-139">https://windowsserver.uservoice.com/forums/301869-PowerShell/Suggestions/15854689-PowerShell-exe-Command-is-broken-on-Windows-10</span><span class="sxs-lookup"><span data-stu-id="e37a3-139">https://windowsserver.uservoice.com/forums/301869-powershell/suggestions/15854689-powershell-exe-command-is-broken-on-windows-10</span></span>

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a><span data-ttu-id="e37a3-140">PowerShell.exe skapar insamling i CPU-användning vid start</span><span class="sxs-lookup"><span data-stu-id="e37a3-140">powershell.exe creates spike in CPU usage on startup</span></span>

<span data-ttu-id="e37a3-141">PowerShell använder en WMI-fråga för att kontrollera om den startats via en Grupprincip, inte orsakar fördröjning i inloggningen.</span><span class="sxs-lookup"><span data-stu-id="e37a3-141">PowerShell uses a WMI query to check if it was started via Group Policy to avoid causing delay in login.</span></span>
<span data-ttu-id="e37a3-142">WMI-fråga slutar att injicera tzres.mui.dll i varje process på datorn eftersom klassen WMI Win32_Process försöker hämta information om lokala tidszon.</span><span class="sxs-lookup"><span data-stu-id="e37a3-142">The WMI query ends up injecting tzres.mui.dll into every process on the system since the WMI Win32_Process class attempts to retrieve local timezone information.</span></span>
<span data-ttu-id="e37a3-143">Detta resulterar i en stor CPU-topp i wmiprvse (WMI-provider host).</span><span class="sxs-lookup"><span data-stu-id="e37a3-143">This results in a large CPU spike in wmiprvse (the WMI provider host).</span></span>
<span data-ttu-id="e37a3-144">Lösning är att använda Win32 API-anrop för att få samma information i stället för med hjälp av WMI.</span><span class="sxs-lookup"><span data-stu-id="e37a3-144">Fix is to use Win32 API calls to get the same information instead of using WMI.</span></span>

