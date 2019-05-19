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
# <a name="bug-fixes-in-wmf-51"></a>Felkorrigeringar i WMF 5.1

## <a name="bug-fixes"></a>Felkorrigeringar

Följande viktiga programfel korrigeras i WMF 5.1:

### <a name="module-auto-discovery-fully-honors-psmodulepath"></a>Automatisk identifiering av modulen godkänner fullständigt PSModulePath

Modulen automatisk identifiering (läser in moduler automatiskt utan en explicit Import-Module när du anropar ett kommando) introducerades i WMF 3. När introducerade kommer PowerShell kontrolleras för kommandon i `$PSHome\Modules` innan du använder `$env:PSModulePath`.

WMF 5.1 ändrar det här beteendet att respektera `$env:PSModulePath` helt. Det möjliggör en användarskapade modul som definierar med PowerShell-kommandon (t.ex. `Get-ChildItem`) automatiskt-läsas och korrekt åsidosätter ett inbyggt kommando.

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a>Filen omdirigering utan långa hård-koder-kodning Unicode

I alla tidigare versioner av PowerShell är det omöjligt att styra Filkodning som används av operatorn för omdirigering av filen.

Från och med WMF 5.1, du kan nu ändra Filkodning för omdirigering genom att ange `$PSDefaultParameterValues`:

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a>Fast en regression i åtkomst till medlemmar i System.Reflection.TypeInfo

En regression med WMF 5.0 avbrutits åtkomst till medlemmar i `System.Reflection.RuntimeType`, till exempel `[int].ImplementedInterfaces`. Det här felet har åtgärdats i WMF 5.1.

### <a name="fixed-some-issues-with-com-objects"></a>Fast några problem med COM-objekt

WMF 5.0 introducerade en ny COM-binder för anropar metoder på COM-objekt och komma åt egenskaperna för COM-objekt. Den här nya binder förbättrad prestanda avsevärt, men också medfört vissa buggar som fastställts i WMF 5.1.

#### <a name="argument-conversions-were-not-always-performed-correctly"></a>Argumentet konverteringar utfördes inte alltid korrekt

I följande exempel:

```powershell
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

Den **Skicka tecken** metoden förväntar sig en sträng, men PowerShell inte att konvertera char till en sträng skjuta upp konverteringen till **IDispatch::Invoke**, som använder **VariantChangeType**att utföra konverteringen. I det här exemplet är detta resulterade i att skicka nycklarna '1', '7 ”och” 3 ”i stället för den förväntade **Volume.Mute** nyckel.

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a>Uppräkningsbara COM-objekt som inte alltid hanteras korrekt

PowerShell räknar upp normalt de flesta uppräkningsbara objekt, men en regression med WMF 5.0 förhindrade uppräkning av COM-objekt som implementerar IEnumerable. Till exempel:

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

I exemplet ovan WMF 5.0 felaktigt skrev den **Scripting.Dictionary** till pipelinen i stället för att räkna upp nyckel/värde-par.

### <a name="ordered-was-not-allowed-inside-classes"></a>[sorterade] inte tilläts inuti klasser

WMF 5.0 introducerade klasser med verifiering av typen litteraler som används i klasser. `[ordered]` ser ut som en literal typ men är inte av typen SANT .NET. WMF 5.0 felaktigt rapporterade ett fel på `[ordered]` inuti en klass:

```powershell
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```

### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a>Hjälp om ämnen med flera versioner fungerar inte

Innan du WMF 5.1, om du hade flera versioner av en installerad modul och alla delade ett hjälpavsnitt, till exempel about_PSReadline, `help about_PSReadline` kommer att returnera flera avsnitt med inget enkelt sätt att visa den verkliga hjälpen.

WMF 5.1 åtgärdar detta genom att returnera hjälpen för den senaste versionen av avsnittet.

`Get-Help` ger inte möjligt att ange vilken version du vill ha hjälp för. Undvik detta genom att gå till moduler-katalog och visa hjälp direkt med ett verktyg som redigeringsprogram du föredrar.

### <a name="powershellexe-reading-from-stdin-stopped-working"></a>PowerShell.exe läsning från STDIN slutar fungera

Kunder använder `powershell -command -` från inbyggda appar för att köra PowerShell skicka i skriptet via STDIN tyvärr detta har fördelat andra ändringar i konsolvärden.

Detta har åtgärdats för version 5.1 i Windows 10 Anniversary Update.

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a>PowerShell.exe skapar topp i CPU-användning vid start

PowerShell använder en WMI-fråga för att kontrollera om det har börjat via en grupprincip inte orsakar fördröjning när du loggar in. WMI-frågan slutar Infoga tzres.mui.dll i varje process på systemet sedan WMI **Win32_Process** klass försöker hämta lokala tidszonen. Detta resulterar i en stor CPU-topp i **wmiprvse** (WMI-provider host). Korrigeringen är att använda Win32 API-anrop för att få samma information i stället för med hjälp av WMI.
