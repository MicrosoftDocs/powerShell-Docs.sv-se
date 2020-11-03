---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-error?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Error
ms.openlocfilehash: ad9e3daa7d67fc2bec6fa19a873573ce33dc609d
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2020
ms.locfileid: "93272804"
---
# Write-Error

## SAMMANFATTNING
Skriver ett objekt till fel strömmen.

## SYNTAX

### Noexception (standard)

```
Write-Error [-Message] <String> [-Category <ErrorCategory>] [-ErrorId <String>] [-TargetObject <Object>]
 [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### WithException

```
Write-Error -Exception <Exception> [[-Message] <String>] [-Category <ErrorCategory>] [-ErrorId <String>]
 [-TargetObject <Object>] [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### ErrorRecord

```
Write-Error -ErrorRecord <ErrorRecord> [-RecommendedAction <String>] [-CategoryActivity <String>]
 [-CategoryReason <String>] [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

## BESKRIVNING

`Write-Error`Cmdleten deklarerar ett icke-avslutande fel. Som standard skickas fel i fel strömmen till värd programmet som ska visas, tillsammans med utdata.

Om du vill skriva ett icke-avslutande fel, ange en fel meddelande sträng, ett **ErrorRecord** -objekt eller ett **undantags** objekt. Använd de andra parametrarna för `Write-Error` för att fylla i fel posten.

Icke-avslutande fel skriver ett fel till fel strömmen, men de stoppar inte kommando bearbetningen.
Om ett icke-avslutande fel har deklarerats för ett objekt i en samling ingångs objekt fortsätter kommandot att bearbeta de andra objekten i samlingen.

Om du vill deklarera ett avslutande fel använder du `Throw` nyckelordet.
Mer information finns i [about_Throw](../Microsoft.PowerShell.Core/About/about_Throw.md).

## EXEMPEL

### Exempel 1: Skriv ett fel för RegistryKey-objektet

```powershell
Get-ChildItem | ForEach-Object {
    if ($_.GetType().ToString() -eq "Microsoft.Win32.RegistryKey")
    {
        Write-Error "Invalid object" -ErrorId B1 -TargetObject $_
    }
    else
    {
        $_
    }
}
```

Det här kommandot deklarerar ett icke-avslutande fel när `Get-ChildItem` cmdleten returnerar ett `Microsoft.Win32.RegistryKey` objekt, t. ex. objekten i- `HKLM:` eller- `HKCU:` enheterna i PowerShell-huvudprovidern.

### Exempel 2: Skriv ett fel meddelande till konsolen

```powershell
Write-Error "Access denied."
```

Det här kommandot deklarerar ett icke-avslutande fel och skriver "åtkomst nekad"-fel. Kommandot använder **meddelande** parametern för att ange meddelandet, men utelämnar det valfria namnet för **meddelande** parametern.

### Exempel 3: Skriv ett fel till konsolen och ange kategorin

```powershell
Write-Error -Message "Error: Too many input values." -Category InvalidArgument
```

Det här kommandot deklarerar ett icke-avslutande fel och anger en fel kategori.

### Exempel 4: Skriv ett fel med ett undantags objekt

```powershell
$E = [System.Exception]@{Source="Get-ParameterNames.ps1";HelpLink="https://go.microsoft.com/fwlink/?LinkID=113425"}
Write-Error -Exception $E -Message "Files not found. The $Files location does not contain any XML files."
```

Det här kommandot använder ett **undantags** objekt för att deklarera ett icke-avslutande fel.

Det första kommandot använder en hash-tabell för att skapa objektet **system. Exception** . Det sparar undantags objekt i `$E` variabeln. Du kan använda en hash-tabell för att skapa ett objekt av en typ som har en null-konstruktor.

Det andra kommandot använder `Write-Error` cmdleten för att deklarera ett icke-avslutande fel. Värdet för parametern **Exception** är **undantags** objekt i `$E` variabeln.

## PARAMETRAR

### – Kategori

Anger fel kategori. Standardvärdet är **NotSpecified**. De acceptabla värdena för den här parametern är:

- NotSpecified
- OpenError
- CloseError
- DeviceError
- DeadlockDetected
- InvalidArgument
- InvalidData
- InvalidOperation
- InvalidResult
- InvalidType
- MetadataError
- NotImplemented
- NotInstalled
- ObjectNotFound
- OperationStopped
- OperationTimeout
- SyntaxError
- ParserError
- PermissionDenied
- ResourceBusy
- ResourceExists
- ResourceUnavailable
- ReadError
- WriteError
- FromStdErr
- SecurityError
- ProtocolError
- ConnectionError
- AuthenticationError
- LimitsExceeded
- QuotaExceeded
- NotEnabled

Information om fel kategorierna finns i ErrorCategory- [uppräkning](https://go.microsoft.com/fwlink/?LinkId=143600).

```yaml
Type: System.Management.Automation.ErrorCategory
Parameter Sets: NoException, WithException
Aliases:
Accepted values: NotSpecified, OpenError, CloseError, DeviceError, DeadlockDetected, InvalidArgument, InvalidData, InvalidOperation, InvalidResult, InvalidType, MetadataError, NotImplemented, NotInstalled, ObjectNotFound, OperationStopped, OperationTimeout, SyntaxError, ParserError, PermissionDenied, ResourceBusy, ResourceExists, ResourceUnavailable, ReadError, WriteError, FromStdErr, SecurityError, ProtocolError, ConnectionError, AuthenticationError, LimitsExceeded, QuotaExceeded, NotEnabled

Required: False
Position: Named
Default value: NotSpecified
Accept pipeline input: False
Accept wildcard characters: False
```

### -CategoryActivity

Anger den åtgärd som orsakade felet.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Activity

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CategoryReason

Anger hur eller varför aktiviteten orsakade felet.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Reason

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CategoryTargetName

Anger namnet på det objekt som bearbetades när felet uppstod.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: TargetName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CategoryTargetType

Anger vilken typ av objekt som bearbetades när felet inträffade.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: TargetType

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ErrorId

Anger en ID-sträng för att identifiera felet. Strängen ska vara unik för felet.

```yaml
Type: System.String
Parameter Sets: NoException, WithException
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ErrorRecord

Anger ett fel post objekt som representerar felet. Använd egenskaperna för objektet för att beskriva felet.

Om du vill skapa ett fel post objekt använder du `New-Object` cmdleten eller hämtar ett fel post objekt från matrisen i den `$Error` automatiska variabeln.

```yaml
Type: System.Management.Automation.ErrorRecord
Parameter Sets: ErrorRecord
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Undantag

Anger ett undantags objekt som representerar felet. Använd egenskaperna för objektet för att beskriva felet.

Om du vill skapa ett undantags objekt använder du en hash-tabell eller använder `New-Object` cmdleten.

```yaml
Type: System.Exception
Parameter Sets: WithException
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Meddelande

Anger meddelande texten för felet. Om texten innehåller blank steg eller specialtecken, omger du den med citat tecken. Du kan också skicka en meddelande sträng till `Write-Error` .

```yaml
Type: System.String
Parameter Sets: NoException, WithException
Aliases: Msg

Required: True (NoException), False (WithException)
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -RecommendedAction

Anger den åtgärd som användaren bör vidta för att lösa eller förhindra felet.

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

### – TargetObject

Anger det objekt som bearbetades när felet inträffade. Ange objektet, en variabel som innehåller objektet eller ett kommando som hämtar objektet.

```yaml
Type: System.Object
Parameter Sets: NoException, WithException
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka vidare en sträng som innehåller ett fel meddelande till `Write-Error` .

## UTDATA

### Fel objekt

`Write-Error` skriver endast till fel strömmen. Det returnerar inga objekt.

## ANTECKNINGAR

`Write-Error` ändrar inte värdet för den `$?` automatiska variabeln, och därför signalerar det inte ett avslutande fel villkor. Om du vill signalera ett avslutande fel använder du metoden [$PSCmdlet. WriteError ()](/dotnet/api/system.management.automation.cmdlet.writeerror) .

## RELATERADE LÄNKAR

[about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md)

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Skriv-debug](Write-Debug.md)

[Skriv värd](Write-Host.md)

[Skriva-utdata](Write-Output.md)

[Skriv förlopp](Write-Progress.md)

[Skriv-verbose](Write-Verbose.md)

[Skriv varning](Write-Warning.md)
