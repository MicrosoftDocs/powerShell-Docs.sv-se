---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: aacc89001373ecc8ef75e630f965a8d807bd4ac3
ms.sourcegitcommit: 57df49488015e7ac17ff1df402a94441aa6d6064
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/08/2020
ms.locfileid: "93267975"
---
# Read-Host

## SAMMANFATTNING
Läser en rad med ininformation från-konsolen.

## SYNTAX

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## BESKRIVNING

`Read-Host`Cmdlet: en läser en rad med ininformation från-konsolen. Du kan använda den för att uppmana användaren att ange indata. Eftersom du kan spara indata som en säker sträng kan du använda denna cmdlet för att uppmana användarna att ange säkra data, till exempel lösen ord, samt delade data.

## EXEMPEL

### Exempel 1: Spara konsol indata till en variabel

Det här exemplet visar strängen "Ange din ålder:" som en prompt. När ett värde anges och tangenten Enter trycks ned, lagras värdet i `$Age` variabeln.

```powershell
$Age = Read-Host "Please enter your age"
```

### Exempel 2: Spara konsol indata som en säker sträng

I det här exemplet visas strängen "Ange ett lösen ord:" som en prompt. När ett värde anges visas asterisker () i- `*` konsolen i stället för indatamängden. När ENTER-tangenten trycks ned, lagras värdet som ett **SecureString** -objekt i `$pwd_secure_string` variabeln.

```powershell
$pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
```

## PARAMETRAR

### – AsSecureString

Anger att cmdleten visar asterisker ( `*` ) i stället för de tecken som användaren skriver som indata. När du använder den här parametern är utdata från `Read-Host` cmdleten ett **SecureString** -objekt ( **system. Security. SecureString** ).

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

### -Prompt

Anger texten i prompten.
Skriv en sträng.
Om strängen innehåller blank steg omger du den med citat tecken.
PowerShell lägger till ett kolon ( `:` ) för den text som du anger.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### System. String eller system. Security. SecureString

Om parametern **AsSecureString** används `Read-Host` returnerar en **SecureString**. Annars returnerar den en sträng.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Rensa värd](../microsoft.powershell.core/clear-host.md)

[Hämta värd](Get-Host.md)

[Skriv värd](Write-Host.md)

[ConvertFrom – SecureString](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
