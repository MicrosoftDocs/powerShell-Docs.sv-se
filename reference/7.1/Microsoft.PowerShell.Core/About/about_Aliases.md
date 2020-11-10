---
description: Beskriver hur du använder alternativa namn för cmdlets och kommandon i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_aliases?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Aliases
ms.openlocfilehash: 9213bd41af6d5383c7e67d33b8909736a6e380bb
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391297"
---
# <a name="about-aliases"></a>Om alias

## <a name="short-description"></a>KORT BESKRIVNING
Beskriver hur du använder alternativa namn för cmdlets och kommandon i PowerShell.

## <a name="long-description"></a>LÅNG BESKRIVNING

Ett alias är ett alternativt namn eller smek namn för en cmdlet eller ett kommando element, till exempel en funktion, ett skript, en fil eller en körbar fil. Du kan använda aliaset i stället för kommando namnet i PowerShell-kommandon.

Använd New-Alias-cmdleten om du vill skapa ett alias. Följande kommando skapar till exempel "gasen"-alias för `Get-AuthenticodeSignature` cmdleten:

```powershell
New-Alias -Name gas -Value Get-AuthenticodeSignature
```

När du har skapat aliaset för cmdlet-namnet kan du använda aliaset i stället för namnet på cmdleten. Om du till exempel vill hämta Authenticode-signaturen för SqlScript.ps1-filen skriver du:

```powershell
Get-AuthenticodeSignature SqlScript.ps1
```

Eller skriv:

```powershell
gas SqlScript.ps1
```

Om du skapar "Word" som alias för Microsoft Office Word kan du skriva "Word" i stället för följande:

```powershell
"C:\Program Files\Microsoft Office\Office11\Winword.exe"
```

## <a name="built-in-aliases"></a>INBYGGDA ALIAS

PowerShell innehåller en uppsättning inbyggda alias, inklusive "CD" och "chdir" för Set-Location-cmdleten och "LS" och "dir" för Get-ChildItem-cmdleten.

Om du vill hämta alla alias på datorn, inklusive inbyggda alias, skriver du:

```powershell
Get-Alias
```

## <a name="alias-cmdlets"></a>ALIAS-CMDLETAR

PowerShell innehåller följande cmdletar, som är utformade för att fungera med alias:

- `Get-Alias` -Hämtar alla alias i den aktuella sessionen.
- `New-Alias` -Skapar ett nytt alias.
- `Set-Alias` -Skapar eller ändrar ett alias.
- `Export-Alias` -Exporterar ett eller flera alias till en fil.
- `Import-Alias` – Importerar en aliasresurspost till PowerShell.

Om du vill ha detaljerad information om cmdletarna skriver du:

```powershell
Get-Help <cmdlet-Name> -Detailed
```

Skriv till exempel:

```powershell
Get-Help Export-Alias -Detailed
```

## <a name="creating-an-alias"></a>SKAPA ETT ALIAS

Använd New-Alias-cmdleten om du vill skapa ett nytt alias. Om du till exempel vill skapa aliaset "förnamn" för Get-Help skriver du:

```powershell
New-Alias -Name gh -Value Get-Help
```

Du kan använda aliaset i kommandon, precis som du använder det fullständiga cmdlet-namnet, och du kan använda aliaset med parametrarna.

Om du till exempel vill få detaljerad hjälp för Get-WmiObject-cmdlet skriver du:

```powershell
Get-Help Get-WmiObject -Detailed
```

Eller skriv:

```powershell
gh Get-WmiObject -Detailed
```

## <a name="saving-aliases"></a>SPARAR ALIAS

De alias som du skapar sparas bara i den aktuella sessionen. Om du vill använda alias i en annan session lägger du till aliaset i din PowerShell-profil. Du kan också använda Export-Alias cmdlet för att spara alias till en fil.

Om du vill ha mer information skriver du:

```powershell
Get-Help about_Profiles
```

## <a name="getting-aliases"></a>HÄMTAR ALIAS

Om du vill hämta alla alias i den aktuella sessionen, inklusive inbyggda alias, alias i dina PowerShell-profiler och de alias som du har skapat i den aktuella sessionen, skriver du:

```powershell
Get-Alias
```

Om du vill hämta särskilda alias använder du parametern name i Get-Alias-cmdleten. Om du till exempel vill hämta alias som börjar med "p" skriver du:

```powershell
Get-Alias -Name p*
```

Använd definitions parametern för att hämta alias för ett visst objekt. Till exempel för att hämta alias för Get-ChildItem cmdlet-typ:

```powershell
Get-Alias -Definition Get-ChildItem
```

### <a name="get-alias-output"></a>GET-ALIAS FÖR UTDATA

Get-Alias returnerar endast en typ av objekt, ett AliasInfo-objekt (system. Management. Automation. AliasInfo). Namnet på alias som inte innehåller något bindestreck, till exempel "CD", visas i följande format:

```powershell
Get-Alias ac
```

```Output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Alias           ac -> Add-Content
```

Detta gör det mycket snabbt och enkelt att få den information som du behöver.

Formatet för den pilbaserade aliaset används inte för alias som innehåller bindestreck. Detta är sannolikt att föredra ersättnings namn för cmdlets och functions, i stället för vanliga förkortningar eller smek namn, och författaren kanske inte vill att de ska vara så tydliga.

## <a name="alternate-names-for-commands-with-parameters"></a>ALTERNATIVA NAMN FÖR KOMMANDON MED PARAMETRAR

Du kan tilldela ett alias till en cmdlet, ett skript, en funktion eller en körbar fil. Du kan inte tilldela ett alias till ett kommando och dess parametrar. Du kan till exempel tilldela ett alias till `Get-Eventlog` cmdleten, men du kan inte tilldela ett alias till `Get-Eventlog -LogName System` kommandot.

Du kan skapa en funktion som innehåller kommandot. Om du vill skapa en funktion skriver du ordet "function" följt av ett namn för funktionen. Skriv kommandot och omge det med klammerparenteser ( {} ).

Till exempel skapar följande kommando syslog-funktionen. Den här funktionen representerar `Get-Eventlog -LogName System` kommandot:

```powershell
function Get-SystemEventlog {Get-Eventlog -LogName System}
Set-Alias -Name syslog -Value Get-SystemEventlog
```

Nu kan du skriva "syslog" i stället för kommandot. Du kan också skapa alias för den nya funktionen.

Om du vill ha mer information om funktioner skriver du:

```powershell
Get-Help about_Functions
```

## <a name="alias-objects"></a>ALIAS-OBJEKT

PowerShell-alias representeras av objekt som är instanser av klassen system. Management. Automation. AliasInfo. Mer information om den här typen av objekt finns i [AliasInfo-klassen][aliasinfo] i PowerShell SDK.

Hämta aliasen om du vill visa egenskaper och metoder för alias-objekten.
Sedan kan du skicka vidare till Get-Member-cmdlet: en. Till exempel:

```powershell
Get-Alias | Get-Member
```

Om du vill visa värdena för egenskaperna för ett speciellt alias, till exempel `dir` alias, hämtar du aliaset. Sedan går du till den Format-List-cmdleten. Följande kommando hämtar till exempel "dir"-aliaset. Därefter rör kommandot aliaset till Format-List-cmdleten. Sedan använder kommandot egenskaps parametern för Format-List med ett jokertecken ( \* ) för att visa alla egenskaper för `dir` aliaset. Följande kommando utför följande åtgärder:

```powershell
Get-Alias -Name dir | Format-List -Property *
```

## <a name="powershell-alias-provider"></a>PowerShell-ALIASRESURSPOST

PowerShell inkluderar alias-providern. Med hjälp av Ali Aset providern kan du Visa alias i PowerShell som om de fanns på en fil system enhet.

Ali Aset-providern visar aliaset: Drive. För att gå till aliaset: enhet, skriver du:

```powershell
Set-Location Alias:
```

Om du vill visa innehållet i enheten skriver du:

```powershell
Get-ChildItem
```

Om du vill visa innehållet i enheten från en annan PowerShell-enhet börjar du med sökvägen med enhets namnet. Inkludera kolon (:). Till exempel:

```powershell
Get-ChildItem -Path Alias:
```

Om du vill hämta information om ett visst alias, anger du enhets namn och aliasnamn. Eller Skriv ett namn mönster. Om du till exempel vill hämta alla alias som börjar med "p" skriver du:

```powershell
Get-ChildItem -Path Alias:p*
```

Om du vill ha mer information om PowerShell-Aliern skriver du:

```powershell
Get-Help Alias
```

## <a name="see-also"></a>SE ÄVEN

- [Nytt-alias](xref:Microsoft.PowerShell.Utility.New-Alias)
- [Get-alias](xref:Microsoft.PowerShell.Utility.Get-Alias)
- [Set-alias](xref:Microsoft.PowerShell.Utility.Set-Alias)
- [Exportera-alias](xref:Microsoft.PowerShell.Utility.Export-Alias)
- [Importera-alias](xref:Microsoft.PowerShell.Utility.Import-Alias)
- [Get-PSProvider](xref:Microsoft.PowerShell.Management.Get-PSProvider)
- [Get-PSDrive](xref:Microsoft.PowerShell.Management.Get-PSDrive)
- [about_functions](about_functions.md)
- [about_profiles](about_profiles.md)
- [about_providers](about_providers.md)

<!-- External links -->
[aliasinfo]: /dotnet/api/system.management.automation.aliasinfo
