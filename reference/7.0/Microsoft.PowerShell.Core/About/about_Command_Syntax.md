---
description: Beskriver de syntax-diagram som används i PowerShell.
Locale: en-US
ms.date: 06/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_command_syntax?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Command_Syntax
ms.openlocfilehash: acdc62590ecd410599bf4a319cd2b46976cda415
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194980"
---
# <a name="about-command-syntax"></a>Om kommandosyntax

## <a name="short-description"></a>KORT BESKRIVNING
Beskriver de syntax-diagram som används i PowerShell.

## <a name="long-description"></a>LÅNG BESKRIVNING

Cmdletarna [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) och [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command) visar syntax-diagram som hjälper dig att skapa kommandon på rätt sätt. I det här avsnittet beskrivs hur du tolkar syntax-diagram.

## <a name="syntax-diagrams"></a>SYNTAX DIAGRAM

Varje stycke i ett kommando för kommandosyntaxen representerar en giltig form av kommandot.

Om du vill skapa ett kommando följer du syntaxen för diagrammet från vänster till höger. Välj bland de valfria parametrarna och ange värden för plats hållarna.

PowerShell använder följande notation för syntax-diagram.

```powershell
<command-name> -<Required Parameter Name> <Required Parameter Value>
[-<Optional Parameter Name> <Optional Parameter Value>]
[-<Optional Switch Parameters>]
[-<Optional Parameter Name>] <Required Parameter Value>
```

Följande är syntaxen för cmdleten [New-alias](xref:Microsoft.PowerShell.Utility.New-Alias) .

```powershell
New-Alias [-Name] <string> [-Value] <string> [-Description <string>]
[-Force] [-Option {None | ReadOnly | Constant | Private | AllScope}]
[-PassThru] [-Scope <string>] [-Confirm] [-WhatIf] [<CommonParameters>]
```

Syntaxen är kapitaliserad för läsbarhet, men PowerShell är Skift läges okänsligt.

Syntax-diagrammet innehåller följande element.

## <a name="command-name"></a>Kommando namn

Kommandon börjar alltid med ett kommando namn, till exempel `New-Alias` . Skriv kommando namnet eller dess alias, t. ex. "GCM" för `Get-Command` .

## <a name="parameters"></a>Parametrar

Parametrarna för ett kommando är alternativ som avgör vad kommandot gör.
Vissa parametrar tar ett "värde" som är indata från användaren till kommandot.

Till exempel `Get-Help` har kommandot en **namn** parameter som gör att du kan ange namnet på det ämne som hjälpen visas för. Ämnes namnet är värdet för parametern **Name** .

I ett PowerShell-kommando börjar parameter namn alltid med ett bindestreck.
Bindestrecket talar om för PowerShell att objektet i kommandot är ett parameter namn.

Om du till exempel vill använda namn parametern för `New-Alias` skriver du följande:

```powershell
-Name
```

Parametrar kan vara obligatoriska eller valfria. Valfria objekt omges av hakparenteser i ett syntax diagram `[ ]` .

Mer information om parametrar finns i [about_Parameters](about_Parameters.md).

## <a name="parameter-values"></a>Parametervärden

Ett parameter värde är den Indatatyp som parametern tar. Eftersom Windows PowerShell baseras på Microsoft .NET Framework representeras parameter värden i syntax-diagrammet av deras .NET-typ.

Till exempel använder name-parametern för `Get-Help` ett "String"-värde, som är en text sträng, till exempel ett enstaka ord eller flera ord som omges av citat tecken.

```powershell
[-Name] <string>
```

.NET-typen för ett parameter värde omges av vinkelparenteser `< >` för att indikera att den är plats hållare för ett värde och inte en literal som du skriver in i ett kommando.

Om du vill använda parametern ersätter du plats hållaren för .NET-typ med ett objekt som har den angivna .NET-typen.

Om du till exempel vill använda **namn** parametern skriver du "-name" följt av en sträng, till exempel följande:

```powershell
-Name MyAlias
```

## <a name="parameters-with-no-values"></a>Parametrar utan värden

Vissa parametrar accepterar inte indatatyper, så de har inte något parameter värde.
Parametrar utan värden kallas "växla parametrar" eftersom de fungerar som på/av växlar. Du inkluderar dem (på) eller utelämnar dem (av) från ett kommando.

Om du vill använda en växlings parameter skriver du bara parameter namnet och föregås av ett bindestreck.

Om du till exempel vill använda parametern **whatIf** för `New-Alias` cmdleten skriver du följande:

```powershell
-WhatIf
```

## <a name="parameter-sets"></a>Parameter uppsättningar

Parametrarna för ett kommando visas i parameter uppsättningar. Parameter uppsättningar ser ut som stycken i ett syntax-diagram.

`New-Alias`Cmdleten har en parameter uppsättning, men många cmdlets har flera parameter uppsättningar. Några av cmdlet-parametrarna är unika för en parameter uppsättning och andra visas i flera parameter uppsättningar. Varje parameter uppsättning representerar formatet för ett giltigt kommando. En parameter uppsättning inkluderar bara parametrar som kan användas tillsammans i ett kommando. Om det inte går att använda parametrar i samma kommando, visas de i separata parameter uppsättningar.

Till exempel har cmdleten [Get-slumpmässig](xref:Microsoft.PowerShell.Utility.Get-Random) följande parameter uppsättningar:

```powershell
Get-Random [[-Maximum] <Object>] [-Minimum <Object>] [-SetSeed <int>]
[<CommonParameters>]

Get-Random [-InputObject] <Object[]> [-Count <int>] [-SetSeed <int>]
[<CommonParameters>]
```

Den första parameter uppsättningen, som returnerar ett slumptal, har de **lägsta** och **högsta** parametrarna. Den andra parameter uppsättningen, som returnerar ett slumpmässigt valt objekt från en uppsättning objekt, innehåller parametrarna **InputObject** och **Count** . Båda parameter uppsättningarna har parametern **SetSeed** och de gemensamma parametrarna.

Dessa parameter uppsättningar visar att du kan använda parametrarna **InputObject** och **Count** i samma kommando, men du kan inte använda parametrarna **maximum** och **Count** i samma kommando.

Du anger vilken parameter uppsättning du vill använda med hjälp av parametrarna i den parameter uppsättningen.

Varje cmdlet har dock även en standard parameter uppsättning. Standard parameter uppsättningen används när du inte anger parametrar som är unika för en parameter uppsättning. Om du till exempel använder `Get-Random` utan parametrar förutsätter Windows PowerShell att du använder den **numeriska** parameter uppsättningen och returnerar ett slumpmässigt nummer.

I varje parameter uppsättning visas parametrarna i positions ordning. Ordningen på parametrarna i ett kommando fråga endast när du utelämnar valfria parameter namn. När parameter namn utelämnas tilldelar PowerShell värden till parametrar efter position och typ. Mer information om parameter placering finns i `about_Parameters` .

## <a name="symbols-in-syntax-diagrams"></a>Symboler i syntax diagram

I syntax-diagrammet visas kommando namn, kommando parametrar och parameter värden. Den använder också symboler för att visa hur du skapar ett giltigt kommando.

I syntax diagrammen används följande symboler:

- Ett bindestreck `-` anger ett parameter namn. I ett kommando skriver du bindestrecket omedelbart före parameter namnet utan några mellanliggande blank steg, som du ser i syntax-diagrammet.

  Om du till exempel vill använda **namn** parametern för `New-Alias` skriver du:

  ```powershell
  -Name
  ```

- Vinkelparenteser `<>` visar platshållartext. Du anger inte vinkelparenteser eller platshållartexten i ett kommando. I stället ersätter du det med det objekt som beskrivs.

  Vinkelparenteser används för att identifiera .NET-typen för värdet som en parameter tar. Om du till exempel vill använda parametern **Name** för `New-Alias` cmdlet: en, ersätter du `<string>` med en sträng, som är ett enstaka ord eller en grupp med ord som omges av citat tecken.

- Hakparenteser `[ ]` indikerar valfria objekt. En parameter och dess värde kan vara valfritt, eller så kan namnet på en obligatorisk parameter vara valfritt.

  Exempel: **beskrivnings** parametern för `New-Alias` och dess värde omges av hakparenteser eftersom de båda är valfria.

  ```powershell
  [-Description <string>]
  ```

  Hakparenteserna visar också att värdet för namn parametern `<string>` är obligatoriskt, men parameter namnet, "name", är valfritt.

  ```powershell
  [-Name] <string>
  ```

- En höger-och vänsterparentes `[]` som läggs till i en .net-typ indikerar att parametern kan acceptera ett eller flera värden av den typen. Ange värdena i en kommaavgränsad lista.

  Till exempel tar cmdleten **Name** -parametern `New-Alias` bara en sträng, men **namn** parametern för [Get-process](xref:Microsoft.PowerShell.Management.Get-Process) kan ta en eller flera strängar.

  ```powershell
  New-Alias [-Name] <string>

  New-Alias -Name MyAlias
  ```

  ```powershell
  Get-Process [-Name] <string[]>

  Get-Process -Name Explorer, Winlogon, Services
  ```

- Klammerparenteser `{}` anger en "uppräkning", som är en uppsättning giltiga värden för en parameter.

  Värdena i klamrarna separeras med lodräta staplar `|` . Staplarna visar ett "exklusivt OR"-alternativ, vilket innebär att du bara kan välja ett värde från den uppsättning värden som visas innanför klammerparenteserna.

  Syntaxen för `New-Alias` cmdleten innehåller till exempel följande värde uppräkning för **alternativ** parametern:

  ```powershell
  -Option {None | ReadOnly | Constant | Private | AllScope}
  ```

  Klamrarna och de lodräta staplarna visar att du kan välja något av de angivna värdena för **alternativ** parametern, till exempel "ReadOnly" eller "AllScope".

  ```powershell
  -Option ReadOnly
  ```

## <a name="optional-items"></a>Valfria objekt

Hakparenteser `[]` omger valfria objekt. I `New-Alias` beskrivningen för cmdlet-syntaxen är till exempel parametern **omfattning** valfri. Detta anges i syntaxen med hakparenteserna Runt parameter namnet och typen:

```powershell
[-Scope <string>]
```

Följande exempel är korrekt användning av `New-Alias` cmdleten:

```powershell
New-Alias -Name utd -Value Update-TypeData
New-Alias -Name utd -Value Update-TypeData -Scope Global
```

Ett parameter namn kan vara valfritt även om värdet för den parametern är obligatoriskt. Detta anges i syntaxen med hakparenteserna Runt parameter namnet men inte parameter typen, som i det här exemplet från `New-Alias` cmdlet:

```powershell
[-Name] <string> [-Value] <string>
```

Följande kommandon använder `New-Alias` cmdleten korrekt. Kommandona ger samma resultat.

```powershell
New-Alias -Name utd -Value Update-TypeData
New-Alias -Name utd Update-TypeData
New-Alias utd -Value Update-TypeData
New-Alias utd Update-TypeData
```

Om parameter namnet inte ingår i instruktionen som skrivet försöker Windows PowerShell använda positionen för argumenten för att tilldela värdena till parametrar.

Följande exempel är inte klart:

```powershell
New-Alias utd
```

Denna cmdlet kräver värden för både **namn** -och **värde** parametrarna.

I syntaxen används hakparenteser även för namngivning och databyte till .NET Framework typer. I det här sammanhanget anger hakparenteser inte ett element är valfritt.

## <a name="see-also"></a>SE ÄVEN

- [about_Parameters](about_Parameters.md)
- [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command)
- [Get – hjälp](xref:Microsoft.PowerShell.Core.Get-Help)
