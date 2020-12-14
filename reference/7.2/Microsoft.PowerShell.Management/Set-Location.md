---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-location?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Location
ms.openlocfilehash: ec6f69d1d4a0b382ceec26b9409d01501edb814f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710399"
---
# Set-Location

## SAMMANFATTNING
Anger den aktuella arbets platsen till en angiven plats.

## SYNTAX

### Sökväg (standard)

```
Set-Location [[-Path] <String>] [-PassThru] [<CommonParameters>]
```

### LiteralPath

```
Set-Location -LiteralPath <String> [-PassThru] [<CommonParameters>]
```

### Stack

```
Set-Location [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## BESKRIVNING

`Set-Location`Cmdleten anger arbets platsen till en angiven plats. Platsen kan vara en katalog, en under katalog, en register plats eller en sökväg till en provider.

PowerShell 6,2 har lagt till stöd för `-` och `+` som värden för parametern **Path** . PowerShell har en historik över de senaste 20 platserna som kan nås med `-` och `+` . Den här listan är oberoende av den plats stack som nås med hjälp av parametern **StackName** .

## EXEMPEL

### Exempel 1: Ange den aktuella platsen

```
PS C:\> Set-Location -Path "HKLM:\"
PS HKLM:\>
```

Det här kommandot anger den aktuella platsen till `HKLM:` enhetens rot.

### Exempel 2: Ange den aktuella platsen och visa platsen

```
PS C:\> Set-Location -Path "Env:\" -PassThru
```

```Output
Path
----
Env:\

PS Env:\>
```

Det här kommandot anger den aktuella platsen till `Env:` enhetens rot. Den använder parametern **Passthru** för att dirigera PowerShell för att returnera ett **PathInfo** -objekt som representerar `Env:\` platsen.

### Exempel 3: Ange platsen till den aktuella platsen i enhet C:

```powershell
PS C:\Windows\> Set-Location HKLM:\
PS HKLM:\> Set-Location C:
PS C:\Windows\>
```

Det första kommandot anger platsen för `HKLM:` enhetens rot i Registry-providern.
Det andra kommandot anger platsen för `C:` enhetens aktuella plats i fil systemets Provider.
När enhets namnet anges i formuläret `<DriveName>:` (utan omvänt snedstreck) anger cmdleten platsen till den aktuella platsen i PSDrive.
För att hämta den aktuella platsen i kommandot PSDrive use `Get-Location -PSDrive <DriveName>` .

### Exempel 4: Ange den aktuella platsen som en namngiven stack

```
PS C:\> Push-Location -Path 'C:\Program Files\PowerShell\' -StackName "Paths"
PS C:\Program Files\PowerShell\> Set-Location -StackName "Paths"
PS C:\Program Files\PowerShell\> Get-Location -Stack
```

```Output
Path
----
C:\
```

Det första kommandot lägger till den aktuella platsen i sökvägar-stacken.
Det andra kommandot gör Sök vägs platsen stack för den aktuella plats stacken.
Det tredje kommandot visar platserna i den aktuella plats stacken.

`*-Location`Cmdletarna använder den aktuella plats stacken om inte en annan plats stack anges i kommandot. Information om plats stackar finns i [anteckningarna](#notes).

### Exempel 5: navigera plats historiken med `+` eller `-`

```
PS C:\> Set-Location -Path $env:SystemRoot
PS C:\Windows> Set-Location -Path Cert:\
PS Cert:\> Set-Location -Path HKLM:\
PS HKLM:\>

# Navigate back through the history using "-"
PS HKLM:\> Set-Location -Path -
PS Cert:\> Set-Location -Path -
PS C:\Windows>

# Navigate using the Set-Location alias "cd" and the implicit positional Path parameter
PS C:\Windows> cd -
PS C:\> cd +
PS C:\Windows> cd +
PS Cert:\>
```

Med hjälp av aliaset `cd -` eller `cd +` är ett enkelt sätt att navigera genom plats historiken i terminalen. Mer information om hur du navigerar med `-` / `+` finns i parametern **Path** .

## PARAMETRAR

### -LiteralPath

Anger sökvägen till platsen. Värdet för parametern **LiteralPath** används exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – PassThru

Returnerar ett **PathInfo** -objekt som representerar platsen. Som standard genererar denna cmdlet inga utdata.

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

### -Path

Ange sökvägen till en ny arbets plats. Om ingen sökväg anges används `Set-Location` den aktuella användarens hem katalog som standard. När jokertecken används, väljer cmdleten den första sökvägen som matchar mönstret jokertecken.

PowerShell behåller en historik över de senaste 20 platserna som du har angett. Om värdet för parametern **Path** är ett `-` blank steg, kommer den nya arbets platsen att vara den tidigare arbets platsen i historiken (om den finns). På samma sätt `+` kommer den nya arbets platsen att vara nästa arbets plats i historiken (om det finns), om värdet är ett blank steg. Detta påminner om att använda `Pop-Location` och `Push-Location` förutom att historiken är en lista, inte en stack, och spåras implicit, inte manuellt kontrollerad. Det finns för närvarande inget sätt att visa historik listan.

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -StackName

Anger det befintliga plats stack namnet som den här cmdleten gör den aktuella plats stacken. Ange ett plats stack namn. Om du vill ange den namnlösa standard plats stacken skriver `$null` eller en tom sträng ( `""` ).

`*-Location`Cmdletarna fungerar på den aktuella stacken om du inte använder parametern **StackName** för att ange en annan stack. Mer information om plats stackar finns i [anteckningarna](#notes).

```yaml
Type: System.String
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka vidare en sträng som innehåller en sökväg, men inte en literal sökväg, till denna cmdlet.

## UTDATA

### Ingen, system. Management. Automation. PathInfo, system. Management. Automation. PathInfoStack

Denna cmdlet genererar inga utdata om du inte anger parametern **Passthru** . Om du använder **Passthru** med **Path** eller **LiteralPath** genereras ett **PathInfo** -objekt som representerar den nya platsen. Om du använder **Passthru** med **StackName** genereras ett **PathInfoStack** -objekt som representerar den nya stack kontexten.

## ANTECKNINGAR

PowerShell stöder flera körnings utrymmen per process. Varje körnings utrymme har sin egen _aktuella katalog_.
Detta är inte samma som `[System.Environment]::CurrentDirectory` . Det här problemet kan vara ett problem när du anropar .NET-API: er eller kör ursprungliga program utan att ange explicita katalog Sök vägar.

Även om plats-cmdletarna har angett den aktuella katalogen för hela processen, är du inte beroende av den eftersom en annan körnings utrymme kan ändra den när som helst. Du bör använda plats-cmdletar för att utföra vägbaserade åtgärder med hjälp av den aktuella arbets katalogen som är unik för den aktuella körnings utrymme.

`Set-Location`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst. Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` . Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/about/about_Providers.md).

En stack är en sista ingångs lista i som endast det objekt som lagts till senast lades till. Du lägger till objekt i en stack i den ordning som du använder dem och hämtar dem sedan för användning i omvänd ordning. Med PowerShell kan du lagra leverantörs platser i plats stackar. PowerShell skapar en namnlös standard plats stack. Du kan skapa flera namngivna plats grupper. Om du inte anger något stack namn använder PowerShell den aktuella plats stacken. Som standard är den namnlösa standard platsen den aktuella plats stacken, men du kan använda `Set-Location` cmdleten för att ändra den aktuella plats stacken.

Om du vill hantera plats stackar använder du `*-Location` cmdletarna på följande sätt:

- Om du vill lägga till en plats i en plats stack använder du `Push-Location` cmdleten.

- Använd cmdleten för att hämta en plats från en plats stack `Pop-Location` .

- Om du vill visa platserna i den aktuella platsens stack, använder du cmdlet-parametern **stack** `Get-Location` . Om du vill visa platserna i en namngiven plats stack använder du parametern **StackName** i `Get-Location` .

- Om du vill skapa en ny plats stack använder du parametern **StackName** i `Push-Location` . Om du anger en stack som inte finns `Push-Location` skapar stacken.

- Om du vill skapa en plats stack för den aktuella plats stacken använder du parametern **StackName** i `Set-Location` .

Den namnlösa standard plats stacken är endast tillgänglig när den är den aktuella plats stacken.
Om du skapar en namngiven plats stack för den aktuella plats stacken kan du inte längre använda `Push-Location` `Pop-Location` cmdletarna eller för att lägga till eller hämta objekt från standard stacken eller `Get-Location` använda cmdleten för att Visa platserna i den namnlösa stacken. Om du vill göra den namnlösa stacken till den aktuella stacken använder du parametern **StackName** för `Set-Location` cmdleten med värdet `$null` eller en tom sträng ( `""` ).

## RELATERADE LÄNKAR

[Get-location](Get-Location.md)

[Pop-location](Pop-Location.md)

[Push-plats](Push-Location.md)

