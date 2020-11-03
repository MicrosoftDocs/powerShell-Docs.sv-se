---
description: Beskriver hur PowerShell avgör vilket kommando som ska köras.
keywords: powershell,cmdlet
ms.date: 02/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_command_precedence?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Command_Precedence
ms.openlocfilehash: f777d8b627288dff37a166f6819d36d10ed5db37
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270849"
---
# <a name="about-command-precedence"></a>Om kommando prioritet

## <a name="short-description"></a>Kort beskrivning
Beskriver hur PowerShell avgör vilket kommando som ska köras.

## <a name="long-description"></a>Lång beskrivning

Kommando prioriteten beskriver hur PowerShell avgör vilket kommando som ska köras när en session innehåller fler än ett kommando med samma namn. Kommandon i en session kan döljas eller ersättas av kommandon med samma namn. Den här artikeln visar hur du kör dolda kommandon och hur du undviker kommando namns konflikter.

## <a name="command-precedence"></a>Kommando prioritet

När en PowerShell-session innehåller fler än ett kommando som har samma namn, avgör PowerShell vilket kommando som ska köras med hjälp av följande regler.

Om du anger sökvägen till ett kommando kör PowerShell kommandot på den plats som anges i sökvägen.

Följande kommando kör till exempel FindDocs.ps1-skriptet i katalogen "C: \\ TechDocs":

```
C:\TechDocs\FindDocs.ps1
```

Som en säkerhetsfunktion kör PowerShell inte körbara (interna) kommandon, inklusive PowerShell-skript, om inte kommandot finns i en sökväg som anges i miljövariabeln PATH `$env:path` eller om du inte anger sökvägen till skript filen.

Om du vill köra ett skript som finns i den aktuella katalogen anger du den fullständiga sökvägen eller anger en punkt `.\` som representerar den aktuella katalogen.

Om du till exempel vill köra FindDocs.ps1-filen i den aktuella katalogen skriver du:

```
.\FindDocs.ps1
```

### <a name="using-wildcards-in-execution"></a>Använda jokertecken i körningen

Du kan använda jokertecken i kommando körningen. Användning av jokertecken kallas även *globbing*.

PowerShell kör en fil som har en matchning med jokertecken, före en literal matchning.

Överväg till exempel en katalog med följande filer:

```
Get-ChildItem C:\temp\test


    Directory: C:\temp\test


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        5/20/2019   2:29 PM             28 a.ps1
-a----        5/20/2019   2:29 PM             28 [a1].ps1
```

Båda skriptfilerna har samma innehåll: `$MyInvocation.MyCommand.Path` .
Det här kommandot visar namnet på det skript som anropas.

När du kör körs `[a1].ps1` filen `a.ps1` även om filen `[a1].ps1` är en litteral matchning.

```powershell
C:\temp\test\[a1].ps1
```

```Output
C:\temp\test\a.ps1
```

Nu ska vi ta bort `a.ps1` filen och försöka köra den igen.

```powershell
Remove-Item C:\temp\test\a.ps1
C:\temp\test\[a1].ps1
```

```Output
C:\temp\test\[a1].ps1
```

Du kan se från utdata som `[a1].ps1` kör den här gången eftersom litteral matchning är den enda fil matchningen för mönster i jokertecken.

Mer information om hur PowerShell använder jokertecken finns [about_Wildcards](about_Wildcards.md).

> [!NOTE]
> Om du vill begränsa sökningen till en relativ sökväg måste du ge prefixet skriptet namnet med `.\` sökvägen. Detta begränsar Sök funktionen för kommandon till filer i den relativa sökvägen. Utan det här prefixet kan andra PowerShell-syntaxen stå i konflikt och det finns några garantier som filen kan hittas.

Om du inte anger en sökväg, använder PowerShell följande prioritetsordning när den kör kommandon för alla objekt som lästs in i den aktuella sessionen:

  1. Alias
  2. Funktion
  3. Cmdlet
  4. Externa körbara filer (program och icke-PowerShell-skript)

Om du skriver "Help" letar PowerShell därför först efter ett alias med namnet `help` , sedan en funktion med namnet `Help` och slutligen en cmdlet med namnet `Help` . Den kör det första `help` objektet som hittas.

Om sessionen t. ex. innehåller en cmdlet och en funktion, både namngivna `Get-Map` , och när du skriver `Get-Map` , kör PowerShell funktionen.

> [!NOTE]
> Detta gäller endast för inlästa kommandon. Om det finns en `build` körbar fil och ett alias `build` för en funktion med namnet i `Invoke-Build` en modul som inte har lästs in i den aktuella sessionen, kör PowerShell den `build` körbara filen i stället. Modulerna läses inte in automatiskt om den externa körbara filen hittas i det här fallet. Det är bara när ingen extern körbar fil hittas som ett alias, en funktion eller en cmdlet med det namnet anropas, vilket utlöser automatisk inläsning av sin modul.

När sessionen innehåller objekt av samma typ som har samma namn, kör PowerShell det nya objektet.

Om du till exempel importerar en annan `Get-Date` cmdlet från en modul, `Get-Date` kör PowerShell den importerade versionen över den ursprungliga.

## <a name="hidden-and-replaced-items"></a>Dolda och ersatta objekt

Som ett resultat av dessa regler kan objekt ersättas eller döljas av objekt med samma namn.

Objekten är "dolda" eller "skuggade" om du fortfarande har åtkomst till det ursprungliga objektet, till exempel genom att kvalificera objekt namnet med en modul eller ett namn på snapin-modulen.

Om du till exempel importerar en funktion som har samma namn som en cmdlet i sessionen är cmdleten dold (men inte ersatt) eftersom den har importer ATS från en snapin-modul eller modul.

Objekt är "ersatta" eller "överskrivna" om du inte längre kan komma åt det ursprungliga objektet.

Om du till exempel importerar en variabel som har samma namn som en variabel i sessionen, ersätts den ursprungliga variabeln och är inte längre tillgänglig.
Du kan inte kvalificera en variabel med ett modulnamn.

Om du skriver en funktion på kommando raden och sedan importerar en funktion med samma namn, ersätts den ursprungliga funktionen och är inte längre tillgänglig.

### <a name="finding-hidden-commands"></a>Hitta dolda kommandon

Parametern **all** för cmdleten [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command) hämtar alla kommandon med det angivna namnet, även om de är dolda eller ersatta. Från och med PowerShell 3,0 hämtar som standard `Get-Command` bara de kommandon som körs när du skriver kommandots namn.

I följande exempel innehåller sessionen en `Get-Date` funktion och en [Get-date-](xref:Microsoft.PowerShell.Utility.Get-Date) cmdlet.

Följande kommando hämtar det `Get-Date` kommando som körs när du skriver `Get-Date` .

```powershell
Get-Command Get-Date
```

```output
CommandType     Name                      ModuleName
-----------     ----                      ----------
Function        Get-Date
```

Följande kommando använder parametern **all** för att hämta alla `Get-Date` kommandon.

```powershell
Get-Command Get-Date -All
```

```output
CommandType     Name                      ModuleName
-----------     ----                      ----------
Function        Get-Date
Cmdlet          Get-Date                  Microsoft.PowerShell.Utility
```

### <a name="running-hidden-commands"></a>Köra dolda kommandon

Du kan köra vissa kommandon genom att ange objekt egenskaper som särskiljer kommandot från andra kommandon som kan ha samma namn. Du kan använda den här metoden för att köra ett kommando, men det är särskilt användbart för att köra dolda kommandon.

#### <a name="qualified-names"></a>Kvalificerade namn

Med hjälp av det module-kvalificerade namnet för en cmdlet kan du köra kommandon som är dolda med ett objekt med samma namn. Du kan till exempel köra `Get-Date` cmdleten genom att kvalificera den med dess Modulnamn **Microsoft. PowerShell. Utility**.

Använd den här bästa metoden när du skriver skript som du vill distribuera. Du kan inte förutse vilka kommandon som kan finnas i sessionen där skriptet körs.

```powershell
New-Alias -Name "Get-Date" -Value "Get-ChildItem"
Microsoft.PowerShell.Utility\Get-Date
```

```output
Tuesday, September 4, 2018 8:17:25 AM
```

Om du vill köra ett `New-Map` kommando som har lagts till av `MapFunctions` modulen använder du dess kvalificerade namn:

```powershell
MapFunctions\New-Map
```

Om du vill hitta modulen som ett kommando har importer ATS från använder du egenskapen **Modulnamn** för kommandon.

```
(Get-Command <command-name>).ModuleName
```

Om du till exempel vill hitta källan till `Get-Date` cmdleten skriver du:

```powershell
(Get-Command Get-Date).ModuleName
```

```output
Microsoft.PowerShell.Utility
```

> [!NOTE]
> Du kan inte kvalificera variabler eller alias.

#### <a name="call-operator"></a>Anrops operator

Du kan också använda `Call` operatorn `&` för att köra dolda kommandon genom att kombinera den med ett anrop till [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) (aliaset är "dir") `Get-Command` eller [Get-module](xref:Microsoft.PowerShell.Core.Get-Module).

Anrops operatorn kör strängar och skript block i ett underordnat omfång. Mer information finns i [about_Operators](about_Operators.md).

Om du till exempel har en funktion med namnet `Map` som är dold av ett alias som heter `Map` , använder du följande kommando för att köra funktionen.

```powershell
&(Get-Command -Name Map -CommandType Function)
```

eller

```powershell
&(dir Function:\map)
```

Du kan också spara ditt dolda kommando i en variabel för att göra det enklare att köra det.

Följande kommando sparar till exempel `Map` funktionen i `$myMap` variabeln och använder sedan `Call` operatorn för att köra den.

```powershell
$myMap = (Get-Command -Name map -CommandType function)
&($myMap)
```

### <a name="replaced-items"></a>Ersatta objekt

Ett "ersatt" objekt är ett som du inte längre kan komma åt. Du kan ersätta objekt genom att importera objekt av samma namn från en modul eller snapin-modul.

Om du till exempel skriver en `Get-Map` funktion i sessionen och du importerar en funktion som kallas `Get-Map` , ersätter den den ursprungliga funktionen. Det går inte att hämta det i den aktuella sessionen.

Det går inte att dölja variabler och alias eftersom du inte kan använda en anrops operator eller ett kvalificerat namn för att köra dem. När du importerar variabler och alias från en modul eller snapin-modul ersätter de variabler i sessionen med samma namn.

### <a name="avoiding-name-conflicts"></a>Undvika namn konflikter

Det bästa sättet att hantera kommando namns konflikter är att förhindra dem. Använd ett unikt namn när du namnger kommandona. Du kan till exempel lägga till dina initialer eller företagets namn akronym till substantiven i dina kommandon.

När du importerar kommandon till din session från en PowerShell-modul eller från en annan session, använder du dessutom `Prefix` parametern för [modulen importera](xref:Microsoft.PowerShell.Core.Import-Module) eller

[Import-PSSession-](xref:Microsoft.PowerShell.Utility.Import-PSSession) cmdlet: en för att lägga till ett prefix till substantiven i namn på kommandon.

Följande kommando undviker till exempel en konflikt med de `Get-Date` och- `Set-Date` cmdletar som medföljer PowerShell när du importerar `DateFunctions` modulen.

```powershell
Import-Module -Name DateFunctions -Prefix ZZ
```

Mer information finns i `Import-Module` och `Import-PSSession` nedan.

## <a name="see-also"></a>Se även

- [about_Path_Syntax](about_Path_Syntax.md)
- [about_Aliases](about_Aliases.md)
- [about_Functions](about_Functions.md)
- [Alias-Provider](../../Microsoft.PowerShell.Core/About/about_Alias_Provider.md)
- [Funktion-Provider](../../Microsoft.PowerShell.Core/About/about_Function_Provider.md)
- [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command)
- [Importera-modul](xref:Microsoft.PowerShell.Core.Import-Module)
- [Importera – PSSession](xref:Microsoft.PowerShell.Utility.Import-PSSession)
