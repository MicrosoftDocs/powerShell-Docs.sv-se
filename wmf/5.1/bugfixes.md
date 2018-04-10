---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
title: Felkorrigeringar i WMF 5.1
ms.openlocfilehash: dfd9ead447edfe9b7bdae23be14785df4b182bbc
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="bug-fixes-in-wmf-51"></a>Felkorrigeringar i WMF 5.1#

## <a name="bug-fixes"></a>Felkorrigeringar ##

Följande viktiga programfel har åtgärdats i WMF 5.1:

### <a name="module-auto-discovery-fully-honors-envpsmodulepath"></a>Automatisk identifiering av modulen godkänner fullständigt `$env:PSModulePath` ###

Modulen automatisk identifiering (inläsning moduler automatiskt utan en explicit Import-Module vid anrop av ett kommando) introducerades i WMF 3.
När införts, PowerShell markerade kommandon i `$PSHome\Modules` innan du använder `$env:PSModulePath`.

WMF 5.1 ändras detta beteende respektera `$env:PSModulePath` helt.
Det här tillåter en användare skriven modul som definierar med PowerShell-kommandon (t.ex. `Get-ChildItem`) som automatiskt-hämtas och korrekt åsidosätter ett inbyggt kommando.

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a>Filen inte längre hårdkodar för omdirigering `-Encoding Unicode` ###

I alla tidigare versioner av PowerShell inte var möjligt att styra Filkodning som används av operatorn filen omdirigering, t.ex. `Get-ChildItem > out.txt` eftersom PowerShell lagts `-Encoding Unicode`.

Från och med WMF 5.1, du kan nu ändra Filkodning av omdirigering genom att ange `$PSDefaultParameterValues`:

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a>Fast en regression för åtkomst till medlemmar i `System.Reflection.TypeInfo` ###

En regression med WMF 5.0 bröt mot åtkomst till medlemmar i `System.Reflection.RuntimeType`, t.ex. `[int].ImplementedInterfaces`.
Det här felet är åtgärdat i WMF 5.1.


### <a name="fixed-some-issues-with-com-objects"></a>Fasta några problem med COM-objekt ###

WMF 5.0 introduceras en ny COM-binder för anropa metoder i COM-objekt och inte att komma åt egenskaperna för COM-objekt.
Den här nya binder bättre prestanda avsevärt men infördes också vissa fel som har åtgärdats i WMF 5.1.

#### <a name="argument-conversions-were-not-always-performed-correctly"></a>Argumentet konverteringar utfördes inte alltid korrekt ####

I följande exempel:

```
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

SendKeys-metoden förväntar sig en sträng, men PowerShell konverterades inte char till en sträng, vänta konverteringen till IDispatch::Invoke som använder VariantChangeType för att utföra konvertering, som i det här exemplet resulterade i att skicka tangenterna '1', '7' och '3' i stället av den förväntade Volume.Mute nyckeln.

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a>Enumerable COM-objekt som inte alltid hanteras korrekt ####

PowerShell räknar upp normalt de flesta enumerable objekt, men en regression med WMF 5.0 förhindrade uppräkning av COM-objekt som implementerar IEnumerable.  Till exempel:

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

I exemplet ovan skrev WMF 5.0 felaktigt i Scripting.Dictionary för pipeline i stället för att räkna upp nyckel/värde-par.

Den här ändringen adresser [utfärda 1752224 på Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224)

### <a name="ordered-was-not-allowed-inside-classes"></a>`[ordered]` Det var inte tillåtet i klasser ###

WMF 5.0 introducerade klasser med verifieringen av typen literaler som används i klasser.
`[ordered]` ser ut som en literal typ men är inte ett TrueType .NET.
WMF 5.0 felaktigt rapporterade ett fel på `[ordered]` inuti en klass:

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a>Hjälp på om med flera versioner fungerar inte ###

Innan du WMF 5.1, om du har flera versioner av en installerad modul och alla delade ett hjälpavsnitt, till exempel about_PSReadline, `help about_PSReadline` returnerar flera avsnitt med inget enkelt sätt att visa verkliga hjälpen.

WMF 5.1 åtgärdar detta genom att gå tillbaka i hjälpen för den senaste versionen av avsnittet.

`Get-Help` ger inte ett sätt att ange vilken version du vill ha hjälp för.
Undvik detta genom att navigera till katalogen moduler och visa hjälp direkt med ett verktyg som favorit redigerare.

### <a name="powershellexe-reading-from-stdin-stopped-working"></a>PowerShell.exe läsning från STDIN slutat att fungera

Kunder använder `powershell -command -` från interna appar att köra PowerShell vidare i skriptet via STDIN tyvärr detta har brutits pga att andra ändringar konsolen värden.

https://windowsserver.uservoice.com/forums/301869-powershell/suggestions/15854689-powershell-exe-command-is-broken-on-windows-10

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a>PowerShell.exe skapar insamling i CPU-användning vid start

PowerShell använder en WMI-fråga för att kontrollera om den startats via en Grupprincip, inte orsakar fördröjning i inloggningen.
WMI-fråga slutar att injicera tzres.mui.dll i varje process på datorn eftersom klassen WMI Win32_Process försöker hämta information om lokala tidszon.
Detta resulterar i en stor CPU-topp i wmiprvse (WMI-provider host).
Lösning är att använda Win32 API-anrop för att få samma information i stället för med hjälp av WMI.