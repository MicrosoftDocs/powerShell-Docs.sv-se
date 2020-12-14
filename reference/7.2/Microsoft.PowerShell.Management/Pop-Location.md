---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/pop-location?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Pop-Location
ms.openlocfilehash: 8a44849f27de80ece486b573f1adccafab51972a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710201"
---
# Pop-Location

## SAMMANFATTNING
Ändrar den aktuella platsen till den plats som senast flyttades till stacken.

## SYNTAX

```
Pop-Location [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## BESKRIVNING

`Pop-Location`Cmdleten ändrar den aktuella platsen till den plats som senast skickas till stacken med hjälp av `Push-Location` cmdleten. Du kan pop en plats från standard stacken eller från en stack som du skapar med hjälp av ett `Push-Location` kommando.

## EXEMPEL

### Exempel 1: ändra till den senaste platsen

```
PS C:\> Pop-Location
```

Det här kommandot ändrar platsen till den plats som senast lades till i den aktuella stacken.

### Exempel 2: ändra till den senaste platsen i en namngiven stack

```
PS C:\> Pop-Location -StackName "Stack2"
```

Det här kommandot ändrar platsen till den plats som senast lades till i Stack2-platsens stack.

Mer information om plats stackar finns i [anteckningarna](#notes).

### Exempel 3: flytta mellan platser för olika providrar

```
PS C:\> pushd HKLM:\Software\Microsoft\PowerShell
PS HKLM:\Software\Microsoft\PowerShell> pushd Cert:\LocalMachine\TrustedPublisher
PS cert:\LocalMachine\TrustedPublisher> popd
PS HKLM:\Software\Microsoft\PowerShell> popd
PS C:\>
```

Dessa kommandon använder `Push-Location` `Pop-Location` cmdletarna och för att flytta mellan platser som stöds av olika PowerShell-leverantörer. Kommandona använder `pushd` aliaset för `Push-Location` och `popd` aliaset för `Pop-Location` .

Det första kommandot push-överför den aktuella fil system platsen till stacken och flyttas till den HKLM-enhet som stöds av PowerShell-providern.

Det andra kommandot push-överför register platsen till stacken och flyttas till en plats som stöds av PowerShell-certifikat leverantören.

De två sista kommandona pop-bort dessa platser från stacken. Det första `popd` kommandot återgår till register enheten och det andra kommandot återgår till fil system enheten.

## PARAMETRAR

### – PassThru

Skickar ett objekt som representerar platsen för pipelinen. Som standard genererar denna cmdlet inga utdata.

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

### -StackName

Anger den plats stack från vilken platsen visas. Ange ett plats stack namn.

Utan den här parametern får `Pop-Location` pop en plats från den aktuella plats stacken. Som standard är den aktuella plats stacken den namnlösa standard plats stacken som PowerShell skapar. Om du vill skapa en plats stack för den aktuella plats stacken använder du parametern **StackName** för `Set-Location` cmdleten. Mer information om plats stackar finns i [anteckningarna](#notes).

`Pop-Location` Det går inte att popupa en plats från den namnlösa standard stacken om den inte är den aktuella plats stacken.

```yaml
Type: System.String
Parameter Sets: (All)
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

### Inga

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### Ingen, system. Management. Automation. PathInfo

Denna cmdlet skapar ett **system. Management. Automation. PathInfo** -objekt som representerar platsen, om du anger parametern **Passthru** . Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

PowerShell stöder flera körnings utrymmen per process. Varje körnings utrymme har sin egen _aktuella katalog_.
Detta är inte samma som `[System.Environment]::CurrentDirectory` . Det här problemet kan vara ett problem när du anropar .NET-API: er eller kör ursprungliga program utan att ange explicita katalog Sök vägar.

Även om plats-cmdletarna har angett den aktuella katalogen för hela processen, är du inte beroende av den eftersom en annan körnings utrymme kan ändra den när som helst. Du bör använda plats-cmdletar för att utföra vägbaserade åtgärder med hjälp av den aktuella arbets katalogen som är unik för den aktuella körnings utrymme.

En stack är en sista ingångs lista i som endast det objekt som lagts till senast lades till. Du lägger till objekt i en stack i den ordning som du använder dem och hämtar dem sedan för användning i omvänd ordning. Med PowerShell kan du lagra leverantörs platser i plats stackar.

PowerShell skapar en namnlös standard plats stack och du kan skapa flera namngivna plats stackar. Om du inte anger något stack namn använder PowerShell den aktuella plats stacken. Som standard är den namnlösa standard platsen den aktuella plats stacken, men du kan använda `Set-Location` cmdleten för att ändra den aktuella plats stacken.

Om du vill hantera plats stackar använder du PowerShell `*-Location` -cmdletarna enligt följande:

- Om du vill lägga till en plats i en plats stack använder du `Push-Location` cmdleten.

- Använd cmdleten för att hämta en plats från en plats stack `Pop-Location` .

- Om du vill visa platserna i den aktuella platsens stack, använder du cmdlet-parametern **stack** `Get-Location` .

- Om du vill visa platserna i en namngiven plats stack använder du parametern **StackName** för `Get-Location` cmdleten.

- Om du vill skapa en ny plats stack använder du parametern **StackName** för `Push-Location` cmdleten. Om du anger en stack som inte finns `Push-Location` skapar stacken.

- Om du vill skapa en plats stack för den aktuella plats stacken använder du parametern **StackName** för `Set-Location` cmdleten.

Den namnlösa standard plats stacken är endast tillgänglig när den är den aktuella plats stacken.
Om du skapar en namngiven plats stack för den aktuella plats stacken kan du inte längre använda `Push-Location` `Pop-Location` cmdletarna eller för att lägga till eller hämta objekt från standard stacken eller `Get-Location` använda cmdleten för att Visa platserna i den namnlösa stacken. Om du vill göra den namnlösa stacken till den aktuella stacken använder du parametern **StackName** för `Set-Location` cmdleten med värdet `$Null` eller en tom sträng ( `""` ).

Du kan också referera till `Pop-Location` med dess inbyggda alias `popd` . Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).

`Pop-Location` är utformad för att fungera med data som exponeras av vilken provider som helst. Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` . Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## RELATERADE LÄNKAR

[Get-location](Get-Location.md)

[Push-plats](Push-Location.md)

[Ange plats](Set-Location.md)

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
