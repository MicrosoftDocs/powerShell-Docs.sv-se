---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-location?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Location
ms.openlocfilehash: 06b1596366c9c9e20857b55aa9a17342bab07028
ms.sourcegitcommit: fe1e20f8523e3663d68546093aaf3670182337b8
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/14/2020
ms.locfileid: "93269199"
---
# Set-Location

## SAMMANFATTNING
Anger den aktuella arbets platsen till en angiven plats.

## SYNTAX

### Sökväg (standard)

```
Set-Location [[-Path] <String>] [-PassThru] [-UseTransaction] [<CommonParameters>]
```

### LiteralPath

```
Set-Location -LiteralPath <String> [-PassThru] [-UseTransaction] [<CommonParameters>]
```

### Stack

```
Set-Location [-PassThru] [-StackName <String>] [-UseTransaction] [<CommonParameters>]
```

## BESKRIVNING

`Set-Location`Cmdleten anger arbets platsen till en angiven plats. Platsen kan vara en katalog, en under katalog, en register plats eller en sökväg till en provider.

Du kan också använda parametern **StackName** för att skapa en namngiven plats stack den aktuella plats stacken. Mer information om plats stackar finns i anteckningarna.

## EXEMPEL

### Exempel 1: Ange den aktuella platsen

```powershell
PS C:\> Set-Location -Path "HKLM:\"
```

```output
PS HKLM:\>
```

Det här kommandot anger den aktuella platsen till `HKLM:` enhetens rot.

### Exempel 2: Ange den aktuella platsen och visa platsen

```powershell
PS C:\> Set-Location -Path "Env:\" -PassThru
```

```output
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

```powershell
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

## PARAMETRAR

### -LiteralPath

Anger sökvägen till platsen. Värdet för parametern **LiteralPath** används exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

Enkla citat tecken anger att Windows PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath

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

`*-Location`Cmdletarna fungerar på den aktuella stacken om du inte använder parametern **StackName** för att ange en annan stack.

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

### – UseTransaction

Inkluderar kommandot i den aktiva transaktionen.
Den här parametern är bara giltig medan en transaktion pågår.
Mer information finns i about_Transactions.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
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
