---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/push-location?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Push-Location
ms.openlocfilehash: eaa7622e29680de4228579f8b77a6c829a586bf8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710195"
---
# Push-Location

## SAMMANFATTNING
Lägger till den aktuella platsen överst i en plats stack.

## SYNTAX

### Sökväg (standard)

```
Push-Location [[-Path] <String>] [-PassThru] [-StackName <String>] [<CommonParameters>]
```

### LiteralPath

```
Push-Location [-LiteralPath <String>] [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## BESKRIVNING

`Push-Location`Cmdleten lägger till ("pushs") den aktuella platsen till en plats stack. Om du anger en sökväg, `Push-Location` pushar den aktuella platsen till en plats stack och ändrar sedan den aktuella platsen till den plats som anges i sökvägen. Du kan använda `Pop-Location` cmdleten för att hämta platser från plats stacken.

Som standard push-överför `Push-Location` cmdleten den aktuella platsen till den aktuella plats-stacken, men du kan använda parametern **StackName** för att ange en alternativ plats stack. Om stacken inte finns `Push-Location` skapas den.

Mer information om plats stackar finns i [anteckningarna](#notes).

## EXEMPEL

### Exempel 1

I det här exemplet skickas den aktuella platsen till standard plats stacken och sedan ändras platsen till `C:\Windows` .

```
PS C:\> Push-Location C:\Windows
```

### Exempel 2

Det här exemplet pushrar den aktuella platsen till RegFunction-stacken och ändrar den aktuella platsen till `HKLM:\Software\Policies` platsen.

```
PS C:\> Push-Location HKLM:\Software\Policies -StackName RegFunction
```

Du kan använda plats-cmdletar i valfri PowerShell-enhet (PSDrive).

### Exempel 3

Det här kommandot push-överför den aktuella platsen till standard stacken. Den ändrar inte platsen.

```
PS C:\> Push-Location
```

### Exempel 4 – Skapa och Använd en namngiven stack

De här kommandona visar hur du skapar och använder en namngiven plats stack.

```
PS C:\> Push-Location ~ -StackName Stack2
PS C:\Users\User01> Pop-Location -StackName Stack2
PS C:\>
```

Det första kommandot push-överför den aktuella platsen till en ny stack med namnet Stack2 och ändrar sedan den aktuella platsen till arbets katalogen, som visas i kommandot med tilde ( `~` ), som när det används på ett fil Systems leverantörs enheter motsvarar `$HOME` och `$env:USERPROFILE` .

Om Stack2 inte redan finns i sessionen `Push-Location` skapas den. Det andra kommandot använder `Pop-Location` cmdleten för att plocka den ursprungliga platsen ( `C:\` ) från Stack2-stacken. Om du inte använder parametern **StackName** `Pop-Location` skulle platsen kunna visas från den namnlösa standard stacken.

Mer information om plats stackar finns i [anteckningarna](#notes).

## PARAMETRAR

### -LiteralPath

Anger sökvägen till den nya platsen. Till skillnad från parametern **Path** används värdet för parametern **LiteralPath** exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – PassThru

Skickar ett objekt som representerar platsen för pipelinen. Som standard genererar denna cmdlet inga utdata.

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

Ändrar platsen till den plats som anges av den här sökvägen efter att den lägger till (push-överför) den aktuella platsen överst i stacken. Ange en sökväg till en plats vars provider stöder denna cmdlet. Jokertecken är tillåtna. Parameter namnet är valfritt.

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -StackName

Anger den plats stack som den aktuella platsen ska läggas till i. Ange ett plats stack namn.
Om stacken inte finns `Push-Location` skapas den.

Utan den här parametern `Push-Location` lägger till platsen i den aktuella plats stacken. Som standard är den aktuella plats stacken den namnlösa standard plats stacken som PowerShell skapar.
Om du vill skapa en plats stack för den aktuella plats stacken använder du parametern **StackName** för `Set-Location` cmdleten. Mer information om plats stackar finns i [anteckningarna](#notes).

> [!NOTE]
> `Push-Location` Det går inte att lägga till en plats i den namnlösa standard stacken om den inte är den aktuella plats stacken.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Default stack
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka vidare en sträng som innehåller en sökväg (men inte en literal sökväg) till `Push-Location` .

## UTDATA

### Ingen eller system. Management. Automation. PathInfo

När du använder parametern **Passthru** `Push-Location` genereras ett **system. Management. Automation. PathInfo** -objekt som representerar platsen. Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

PowerShell stöder flera körnings utrymmen per process. Varje körnings utrymme har sin egen _aktuella katalog_.
Detta är inte samma som `[System.Environment]::CurrentDirectory` . Det här problemet kan vara ett problem när du anropar .NET-API: er eller kör ursprungliga program utan att ange explicita katalog Sök vägar.

Även om plats-cmdletarna har angett den aktuella katalogen för hela processen, är du inte beroende av den eftersom en annan körnings utrymme kan ändra den när som helst. Du bör använda plats-cmdletar för att utföra vägbaserade åtgärder med hjälp av den aktuella arbets katalogen som är unik för den aktuella körnings utrymme.

En stack är en sista ingångs punkt som endast det objekt som lagts till senast har åtkomst till.
Du lägger till objekt i en stack i den ordning som du använder dem och hämtar dem sedan för användning i omvänd ordning. Med PowerShell kan du lagra leverantörs platser i plats stackar.

PowerShell skapar en namnlös standard plats stack och du kan skapa flera namngivna plats stackar. Om du inte anger något stack namn använder PowerShell den aktuella plats stacken. Som standard är den namnlösa standard platsen den aktuella plats stacken, men du kan använda `Set-Location` cmdleten för att ändra den aktuella plats stacken.

Om du vill hantera plats stackar använder du cmdletarna för PowerShell-platsen på följande sätt.

- Om du vill lägga till en plats i en plats stack använder du `Push-Location` cmdleten.

- Använd cmdleten för att hämta en plats från en plats stack `Pop-Location` .

- Om du vill visa platserna i den aktuella platsens stack, använder du cmdlet-parametern **stack** `Get-Location` .

- Om du vill visa platserna i en namngiven plats stack använder du parametern **StackName** för `Get-Location` cmdleten.

- Om du vill skapa en ny plats stack använder du parametern StackName för `Push-Location` cmdleten. Om du anger en stack som inte finns `Push-Location` skapar stacken.

- Om du vill skapa en plats stack för den aktuella plats stacken använder du parametern StackName för `Set-Location` cmdleten.

Den namnlösa standard plats stacken är endast tillgänglig när den är den aktuella plats stacken.
Om du skapar en namngiven plats stack för den aktuella plats stacken kan du inte längre använda `Push-Location` `Pop-Location` cmdletarna eller för att lägga till eller hämta objekt från standard stacken eller `Get-Location` använda cmdleten för att Visa platserna i den namnlösa stacken. Om du vill göra den namnlösa stacken till den aktuella stacken använder du parametern **StackName** för `Set-Location` cmdleten med värdet `$null` eller en tom sträng ( `""` ).

Du kan också referera till `Push-Location` med dess inbyggda alias `pushd` . Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).

`Push-Location`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst. Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` . Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## RELATERADE LÄNKAR

[Get-location](Get-Location.md)

[Pop-location](Pop-Location.md)

[Ange plats](Set-Location.md)

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
