---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimsession?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimSession
ms.openlocfilehash: c40367d0458c3670b9d684cd0c3b4b2a3631b3e4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265929"
---
# Get-CimSession

## SAMMANFATTNING
Hämtar CIM-sessionsobjekt från den aktuella sessionen.

## SYNTAX

### ComputerNameSet (standard)

```
Get-CimSession [[-ComputerName] <String[]>] [<CommonParameters>]
```

### SessionIdSet

```
Get-CimSession [-Id] <UInt32[]> [<CommonParameters>]
```

### InstanceIdSet

```
Get-CimSession -InstanceId <Guid[]> [<CommonParameters>]
```

### NameSet

```
Get-CimSession -Name <String[]> [<CommonParameters>]
```

## BESKRIVNING

Som standard hämtar cmdleten alla CIM-sessioner som skapats i den aktuella PowerShell-sessionen. Du kan använda parametrarna för `Get-CimSession` för att hämta de sessioner som är specifika för vissa datorer, eller så kan du identifiera sessioner efter namn eller andra identifierare. `Get-CimSession` hämtar inte CIM-sessioner som skapats i andra PowerShell-sessioner eller som skapades på andra datorer.

Mer information om CIM-sessioner finns [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).

## EXEMPEL

### Exempel 1: Hämta CIM-sessioner från den aktuella PowerShell-sessionen

I det här exemplet skapas CIM [-sessioner med New-CimSession](New-CimSession.md)och sedan hämtas CIM-sessioner med hjälp av `Get-CimSession` .

```powershell
New-CimSession -ComputerName Server01,Server02
Get-CimSession
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : d1413bc3-162a-4cb8-9aec-4d2c61253d59
ComputerName : Server01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### Exempel 2: Hämta CIM-sessionerna till en angiven dator

Det här exemplet hämtar de CIM-sessioner som är anslutna till datorn med namnet **Server02**.

```powershell
Get-CimSession -ComputerName Server02
```

```Output
Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### Exempel 3: Hämta en lista över CIM-sessioner och formatera sedan listan

Det här exemplet hämtar alla CIM-sessioner i den aktuella PowerShell-sessionen och visar en tabell som endast innehåller egenskaperna **computername** och **InstanceID** .

```powershell
Get-CimSession | Format-Table -Property ComputerName,InstanceId
```

```Output
ComputerName InstanceId
------------ ----------
Server01     d1413bc3-162a-4cb8-9aec-4d2c61253d59
Server02     c0095981-52c5-4e7f-a5bb-c4c680541710
```

### Exempel 4: Hämta alla CIM-sessioner som har vissa namn

Det här exemplet hämtar alla CIM-sessioner som har namn som börjar med **Serv**.

```powershell
Get-CimSession -ComputerName Serv*
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : d1413bc-162a-4cb8-9aec-4d2c61253d59
ComputerName : Server01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### Exempel 5: Hämta en angiven CIM-session

Det här exemplet hämtar CIM-sessionen med **ID** 2.

```powershell
Get-CimSession -ID 2
```

```Output
Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

## PARAMETRAR

### -ComputerName

Anger namnet på den dator där CIM-sessioner som är anslutna till ska hämtas. Jokertecken är tillåtna.

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -ID

Anger identifieraren för den CIM-session som ska hämtas. Använd kommatecken för att avgränsa ID: n eller Använd intervall operatorn () för `..` att ange ett intervall med ID: n för flera ID: n. Ett **ID** är ett heltal som unikt identifierar CIM-sessionen inom den aktuella PowerShell-sessionen.

Mer information om operatorn Range finns [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md).

```yaml
Type: System.UInt32[]
Parameter Sets: SessionIdSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

Anger instans-ID för CIM-sessionen som ska hämtas.

**InstanceID** är en globalt unik IDENTIFIERARE (GUID) som unikt identifierar en CIM-session. **InstanceID** är unikt, även om du har flera sessioner som körs i PowerShell.

**InstanceID** lagras i egenskapen **InstanceID** för objektet som representerar en CIM-session.

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Hämtar en eller flera CIM-sessioner som innehåller angivna egna namn. Jokertecken är tillåtna.

```yaml
Type: System.String[]
Parameter Sets: NameSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters
Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

## UTDATA

### Microsoft. Management. Infrastructure. CimSession

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Format-Table](../microsoft.powershell.utility/format-table.md)

[New-CimSession](New-CimSession.md)

[Remove-CimSession](remove-cimsession.md)

[about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)
