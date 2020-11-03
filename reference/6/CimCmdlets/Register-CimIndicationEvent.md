---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/register-cimindicationevent?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-CimIndicationEvent
ms.openlocfilehash: a5e801c2b41fff618c78b4abcec9d90d09ea2323
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265899"
---
# Register-CimIndicationEvent

## SAMMANFATTNING
Prenumererar på indikationer med hjälp av ett filter uttryck eller ett frågeuttryck.

## SYNTAX

### ClassNameComputerSet (standard)

```
Register-CimIndicationEvent [-Namespace <String>] [-ClassName] <String>
 [-OperationTimeoutSec <UInt32>] [-ComputerName <String>] [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward]
 [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

### ClassNameSessionSet

```
Register-CimIndicationEvent [-Namespace <String>] [-ClassName] <String>
 [-OperationTimeoutSec <UInt32>] -CimSession <CimSession> [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward]
 [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

### QueryExpressionSessionSet

```
Register-CimIndicationEvent [-Namespace <String>] [-Query] <String> [-QueryDialect <String>]
 [-OperationTimeoutSec <UInt32>] -CimSession <CimSession> [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward]
 [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

### QueryExpressionComputerSet

```
Register-CimIndicationEvent [-Namespace <String>] [-Query] <String> [-QueryDialect <String>]
 [-OperationTimeoutSec <UInt32>] [-ComputerName <String>] [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward]
 [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

## BESKRIVNING

`Register-CimIndicationEvent`Cmdleten prenumererar på indikeringar med hjälp av ett indikations klass namn eller ett frågeuttryck. Använd parametern **SourceIdentifier** för att ge prenumerationen ett namn.

Den här cmdleten returnerar ett **EventSubscription** -objekt. Du kan använda det här objektet för att avbryta prenumerationen.

## EXEMPEL

### Exempel 1: registrera händelser som genererats av en klass

Det här exemplet prenumererar på händelser som genererats av klassen som heter **Win32_ProcessStartTrace**. Den här klassen aktiverar en händelse när en process startar.

```powershell
Register-CimIndicationEvent -ClassName 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted"
Get-Event -SourceIdentifier "ProcessStarted"
```

`Get-Event`Cmdlet: en hämtar händelserna med **ProcessStarted** -prenumerationen. Mer information finns i [Get-Event](../Microsoft.PowerShell.Utility/Get-Event.md).

> [!NOTE]
> I det här exemplet måste du köra PowerShell som administratör.

### Exempel 2: registrera händelserna med en fråga

I det här exemplet används en fråga för att prenumerera på en händelse som genereras när instansen för en klass som heter **Win32_LocalTime** ändras.

```powershell
$query = "SELECT * FROM CIM_InstModification WHERE TargetInstance ISA 'Win32_LocalTime'"
Register-CimIndicationEvent -Query $query -SourceIdentifier "Timer"
```

### Exempel 3: kör ett skript när händelsen anländer

Det här exemplet visar hur du använder en åtgärd som svar på en händelse. Variabeln `$action` innehåller skript blocket för **åtgärden** , som använder `$event` variabeln för att komma åt händelsen som tas emot från CIM.

```powershell
$action = {
  $name = $event.SourceEventArgs.NewEvent.ProcessName
  $id = $event.SourceEventArgs.NewEvent.ProcessId
  Write-Host -Object "New Process Started : Name = $name
 ID = $id"
}
Register-CimIndicationEvent -ClassName 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted" -Action $action
```

Mer information finns i [Win32_ProcessStartTrace](/previous-versions/windows/desktop/krnlprov/win32-processstarttrace).

### Exempel 4: registrera händelser på en fjärrdator

Det här exemplet prenumererar på händelser på en fjärrdator med namnet **Server01**. Händelser som tas emot från CIM-servern lagras i händelse kön i den aktuella PowerShell-sessionen och kör sedan en lokal `Get-Event` för att hämta händelserna.

```powershell
Register-CimIndicationEvent -ClassName 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted" -ComputerName Server01
Get-Event -SourceIdentifier "ProcessStarted"
```

## PARAMETRAR

### -Åtgärd

Anger de kommandon som hanterar händelserna. De kommandon som anges av den här parametern körs när en händelse höjs, i stället för att skicka händelsen till händelse kön. Omge kommandoen med klammerparenteser ( `{}` ) för att skapa ett skript block.

Det skript block som anges med **åtgärden** kan omfatta `$Event` `$EventSubscriber` variablerna,, `$Sender` , och för `$SourceEventArgs` `$SourceArgs` Automatiska variabler, som innehåller information om händelsen till **Åtgärds** skript blocket. Mer information finns i [om automatiska variabler](../microsoft.powershell.core/about/about_automatic_variables.md).

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – CimSession

Kör kommandot med den angivna CIM-sessionen. Ange en variabel som innehåller CIM-sessionen, eller ett kommando som skapar eller hämtar CIM-sessionen, t. ex `New-CimSession` . eller- `Get-CimSession` cmdletar. Mer information finns i [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).

```yaml
Type: Microsoft.Management.Infrastructure.CimSession
Parameter Sets: ClassNameSessionSet, QueryExpressionSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ClassName

Anger den indikations klass som du prenumererar på. Du kan använda TABB-slutförande för att bläddra i listan över klasser, eftersom PowerShell hämtar en lista över klasser från den lokala WMI-servern för att tillhandahålla en lista över klass namn.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Anger namnet på den dator som du vill köra CIM-åtgärden på. Du kan ange ett fullständigt kvalificerat domän namn (FQDN), ett NetBIOS-namn eller en IP-adress.

Om du anger den här parametern skapar cmdleten en tillfällig session till den angivna datorn med hjälp av WsMan-protokollet. Om du inte anger den här parametern utför cmdleten åtgärden på det lokala systemet med hjälp av Component Object Model (COM).

Om flera åtgärder utförs på samma dator ansluter du med en CIM-session för bättre prestanda.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, QueryExpressionComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Forward

Anger att händelser för prenumerationen vidarebefordras till sessionen på den lokala datorn. Använd den här parametern när du registrerar händelser på en fjärrdator eller i en fjärran sluten session.

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

### -MaxTriggerCount

Parameter för att ange att prenumeranten ska avregistreras automatiskt när de har Aktiver ATS för angivna tider. Om värdet är lika med eller mindre än noll, finns det ingen gräns för hur många gånger händelsen kan utlösas utan att avregistreras.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MessageData

Anger eventuella ytterligare data som ska associeras med den här händelse prenumerationen. Värdet för den här parametern visas i egenskapen **MessageData** för alla händelser som är associerade med den här prenumerationen.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Namnrymd

Anger namn området för CIM-åtgärden. Standard namn området är **rot-/cimv2**. Du kan använda TABB-slutförande för att bläddra i listan över namn områden, eftersom PowerShell hämtar en lista över namn områden från den lokala WMI-servern för att tillhandahålla listan över namn områden.

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

### -OperationTimeoutSec

Anger hur lång tid cmdleten väntar på ett svar från datorn. Som standard är värdet för den här parametern 0, vilket innebär att cmdleten använder standardvärdet för timeout för servern.

Om **OperationTimeoutSec** -parametern har angetts till ett värde som är lägre än det stabila anslutnings försöket på 3 minuter, går det inte att återställa nätverks fel som sist mer än värdet för parametern **OperationTimeoutSec** , eftersom åtgärden på servern överskrider innan klienten kan återansluta.

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Fråga

Anger en fråga som ska köras på CIM-servern. Om det angivna värdet innehåller dubbla citat tecken `"` , enkla citat tecken `'` eller ett omvänt snedstreck `\` måste du kringgå dessa tecken genom att prefixet med omvänt snedstreck. Om värdet som anges använder WQL-operatorn som operator måste du undanta följande tecken genom att omge dem med hakparenteser `[]` : procent `%` , under streck `_` eller inledande hak paren tes `[` .

```yaml
Type: System.String
Parameter Sets: QueryExpressionSessionSet, QueryExpressionComputerSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -QueryDialect

Anger frågespråket som används för **Frågeparametern** . De acceptabla värdena för den här parametern är: **WQL** eller **CQL**. Standardvärdet är **WQL**.

```yaml
Type: System.String
Parameter Sets: QueryExpressionSessionSet, QueryExpressionComputerSet
Aliases:

Required: False
Position: Named
Default value: WQL
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier

Anger ett namn för prenumerationen. Det namn som du anger måste vara unikt i den aktuella sessionen. Standardvärdet är ett GUID som PowerShell tilldelar. Det här värdet visas i värdet för **SourceIdentifier** -egenskapen för Subscriber-objektet och för alla händelse objekt som är associerade med den här prenumerationen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SupportEvent

Anger att händelse prenumerationen är dold. Använd den här parametern när den aktuella prenumerationen är en del av en mer komplex metod för registrering av händelser och den bör inte identifieras separat.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Denna cmdlet accepterar inga inobjekt.

## UTDATA

### System. Object

Den här cmdleten matar ut ett **EventSubscription** -objekt.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Hämta händelse](../microsoft.powershell.utility/get-event.md)

[Ta bort händelse](../microsoft.powershell.utility/remove-event.md)

[Avregistrera-händelse](../microsoft.powershell.utility/unregister-event.md)

[Skriv värd](../microsoft.powershell.utility/write-host.md)

[Get-CimSession](Get-CimSession.md)

[New-CimSession](New-CimSession.md)
