---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 02/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-alias?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Alias
ms.openlocfilehash: e9e80b4bf558dcf1e225868a1138979270ea304f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708362"
---
# Set-Alias

## SAMMANFATTNING
Skapar eller ändrar ett alias för en cmdlet eller något annat kommando i den aktuella PowerShell-sessionen.

## SYNTAX

### Standard (standard)

```
Set-Alias [-Name] <string> [-Value] <string> [-Description <string>] [-Option <ScopedItemOptions>]
 [-PassThru] [-Scope <string>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Set-Alias`Cmdleten skapar eller ändrar ett alias för en cmdlet eller ett kommando, till exempel en funktion, ett skript, en fil eller en annan körbar fil. Ett alias är ett alternativt namn som refererar till en cmdlet eller ett kommando.
Är till exempel `sal` alias för `Set-Alias` cmdleten. Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).

En cmdlet kan ha flera alias, men ett alias kan bara associeras med en cmdlet. Du kan använda `Set-Alias` för att omtilldela ett befintligt alias till en annan cmdlet eller ändra ett Aliass egenskaper, till exempel beskrivningen.

Ett alias som skapas eller ändras av `Set-Alias` är inte permanent och är bara tillgängligt under den aktuella PowerShell-sessionen. När PowerShell-sessionen stängs tas aliaset bort.

## EXEMPEL

### Exempel 1: skapa ett alias för en cmdlet

Det här kommandot skapar ett alias till en cmdlet i den aktuella PowerShell-sessionen.

```
PS> Set-Alias -Name list -Value Get-ChildItem

PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-ChildItem
```

`Set-Alias`Cmdleten skapar ett alias i den aktuella PowerShell-sessionen. Parametern **Name** anger aliasets namn `list` . Parametern **Value** anger den cmdlet som aliaset kör.

Om du vill köra aliaset skriver `list` du på PowerShell-kommandoraden.

### Exempel 2: omtilldela ett befintligt alias till en annan cmdlet

Det här kommandot tilldelar om ett befintligt alias för att köra en annan cmdlet.

```
PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-ChildItem

PS> Set-Alias -Name list -Value Get-Location

PS> Get-Alias -Name list

CommandType     Name
-----------     ----
Alias           list -> Get-Location
```

`Get-Alias`Cmdlet: en använder parametern **Name** för att visa `list` aliaset. `list`Aliaset är associerat med `Get-ChildItem` cmdleten. När `list` aliaset körs visas objekten i den aktuella katalogen.

`Set-Alias`Cmdleten använder **Name** -parametern för att ange `list` alias. Parametern **Value** associerar aliaset med `Get-Location` cmdleten.

`Get-Alias`Cmdlet: en använder parametern **Name** för att visa `list` aliaset. `list`Aliaset är associerat med `Get-Location` cmdleten. När `list` aliaset körs visas den aktuella katalogens plats.

### Exempel 3: skapa och ändra ett skrivskyddat alias

Det här kommandot skapar ett skrivskyddat alias. Alternativet Skriv skydd förhindrar oönskade ändringar i ett alias. Använd parametern **Force** om du vill ändra eller ta bort ett skrivskyddat alias.

```
PS> Set-Alias -Name loc -Value Get-Location -Option ReadOnly -PassThru | Format-List -Property *

DisplayName         : loc -> Get-Location
Definition          : Get-Location
Options             : ReadOnly
Description         :
Name                : loc
CommandType         : Alias

PS> Set-Alias -Name loc -Value Get-Location -Option ReadOnly -Description 'Displays the current directory' -Force -PassThru | Format-List -Property *

DisplayName         : loc -> Get-Location
Definition          : Get-Location
Options             : ReadOnly
Description         : Displays the current directory
Name                : loc
CommandType         : Alias
```

`Set-Alias`Cmdleten skapar ett alias i den aktuella PowerShell-sessionen. Parametern **Name** anger aliasets namn `loc` . Parametern **Value** anger den `Get-Location` cmdlet som aliaset kör. **Alternativ** parametern anger det **skrivskyddade** värdet. Parametern **Passthru** representerar objektet alias och skickar objektet nedåt i pipeline till `Format-List` cmdleten. `Format-List` använder **egenskaps** parametern med en asterisk ( `*` ) så att alla egenskaper visas. I exempel resultatet visas en del av de här egenskaperna.

`loc`Aliaset ändras med addition av två parametrar. **Beskrivning** lägger till text för att förklara aliasets syfte. Parametern **Force** krävs eftersom `loc` aliaset är skrivskyddat. Om **Force** -parametern inte används, Miss lyckas ändringen.

### Exempel 4: skapa ett alias till en körbar fil

I det här exemplet skapas ett alias till en körbar fil på den lokala datorn.

```
PS> Set-Alias -Name np -Value C:\Windows\notepad.exe

PS> Get-Alias -Name np

CommandType     Name
-----------     ----
Alias           np -> notepad.exe
```

`Set-Alias`Cmdleten skapar ett alias i den aktuella PowerShell-sessionen. Parametern **Name** anger aliasets namn `np` . Parametern **Value** anger sökväg och program namn **C:\Windows\notepad.exe**. `Get-Alias`Cmdleten använder parametern **Name** för att visa att `np` aliaset är associerat med **notepad.exe**.

Om du vill köra aliaset skriver du `np` på PowerShell-kommandoraden för att öppna **notepad.exe**.

### Exempel 5: skapa ett alias för ett kommando med parametrar

Det här exemplet visar hur du tilldelar ett alias till ett kommando med parametrar.

Du kan skapa ett alias för en cmdlet, till exempel `Set-Location` . Du kan inte skapa ett alias för ett kommando med parametrar och värden, till exempel `Set-Location -Path C:\Windows\System32` . Skapa ett alias för ett kommando genom att skapa en funktion som innehåller kommandot och sedan skapa ett alias för funktionen. Mer information finns i [about_Functions](../Microsoft.PowerShell.Core/about/about_Functions.md).

```
PS> Function CD32 {Set-Location -Path C:\Windows\System32}

PS> Set-Alias -Name Go -Value CD32
```

En funktion `CD32` som heter skapas. Funktionen använder `Set-Location` cmdleten med parametern **Path** för att ange katalogen, **C:\Windows\System32**.

`Set-Alias`Cmdleten skapar ett alias för funktionen i den aktuella PowerShell-sessionen. Parametern **Name** anger aliasets namn `Go` . Parametern **Value** anger funktionens namn, `CD32` .

Om du vill köra aliaset skriver `Go` du på PowerShell-kommandoraden. `CD32`Funktionen körs och ändras till katalogen **C:\Windows\System32**.

## PARAMETRAR

### -Beskrivning

Anger en beskrivning av aliaset. Du kan ange valfri sträng. Om beskrivningen innehåller blank steg omger du det med enkla citat tecken.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Använd parametern **Force** för att ändra eller ta bort ett alias som har **alternativ** parametern inställd på **skrivskyddad**.

**Force** -parametern kan inte ändra eller ta bort ett alias med **alternativ** parametern inställd på **konstant**.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Anger namnet på ett nytt alias. Ett aliasnamn får innehålla alfanumeriska tecken och bindestreck. Aliasnamn får inte vara numeriska, till exempel 123.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Alternativ

Anger aliasets **alternativ** egenskaps värde. Värden som **ReadOnly** och **konstant** skyddar ett alias från oavsiktliga ändringar. Om du vill se egenskapen **alternativ** för alla alias i sessionen skriver du `Get-Alias | Format-Table -Property Name, Options -Autosize` .

De acceptabla värdena för den här parametern är följande:

- **AllScope** Aliaset kopieras till alla nya omfattningar som skapas.
- **Konstant** Kan inte ändras eller tas bort.
- **Ingen** Anger inga alternativ och är standardvärdet.
- **Privat** Aliaset är endast tillgängligt i det aktuella omfånget.
- **ReadOnly** Kan inte ändras eller tas bort om inte parametern **Force** används.
- **Ospecificerat**

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: AllScope, Constant, None, Private, ReadOnly, Unspecified

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – PassThru

Returnerar ett objekt som representerar aliaset. Använd en format-cmdlet, till exempel `Format-List` för att visa objektet. `Set-Alias`Genererar inga utdata som standard.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Omfattning

Anger omfattningen som detta alias är giltigt i. Standardvärdet är **Local**. Mer information finns i [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).

De acceptabla värdena är följande:

- Global
- Lokal
- Privat
- Numrerade omfattningar
- Skript

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Global, Local, Private, Numbered scopes, Script

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### -Värde

Anger namnet på den cmdlet eller det kommando som aliaset kör. Parametern **Value** är aliasets **definitions** egenskap.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

Uppmanar dig att bekräfta innan du kör cmdleten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Visar vad som skulle hända om cmdleten kördes. Cmdleten körs inte.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inga

`Set-Alias` accepterar inte ininformation från pipelinen.

## UTDATA

### Ingen eller system. Management. Automation. AliasInfo

När du använder parametern **Passthru** `Set-Alias` genereras ett **system. Management. Automation. AliasInfo** -objekt som representerar aliaset. Annars `Set-Alias` genererar inga utdata.

## ANTECKNINGAR

PowerShell innehåller inbyggda alias som är tillgängliga i varje PowerShell-session. `Get-Alias`Cmdleten visar de alias som är tillgängliga i en PowerShell-session.

Om du vill skapa ett alias använder du cmdletarna `Set-Alias` eller `New-Alias` . I PowerShell 6, om du vill ta bort ett alias, använder du `Remove-Alias` cmdleten. `Remove-Item` accepteras för bakåtkompatibilitet, till exempel för skript som skapats med tidigare versioner av PowerShell. Använd ett kommando som `Remove-Item -Path Alias:aliasname` .

Om du vill skapa ett alias som är tillgängligt i varje PowerShell-session lägger du till det i din PowerShell-profil.
Mer information finns i [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).

Ett alias kan sparas och återanvändas i en annan PowerShell-session genom att exportera och importera. Använd om du vill spara ett alias i en fil `Export-Alias` . Använd om du vill lägga till ett sparat alias i en ny PowerShell-session `Import-Alias` .

## RELATERADE LÄNKAR

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Functions](../Microsoft.PowerShell.Core/about/about_Functions.md)

[about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)

[about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)

[Exportera-alias](Export-Alias.md)

[Get-alias](Get-Alias.md)

[Importera-alias](Import-Alias.md)

[Nytt-alias](New-Alias.md)

[Ta bort-alias](Remove-Alias.md)

[Ta bort objekt](../Microsoft.PowerShell.Management/Remove-Item.md)

