---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/13/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerrestorepoint?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerRestorePoint
ms.openlocfilehash: 73819aafee9ed1911354daf9af23eedff0a3e14c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266169"
---
# Get-ComputerRestorePoint

## SAMMANFATTNING
Hämtar återställnings punkterna på den lokala datorn.

## SYNTAX

### ID (standard)

```
Get-ComputerRestorePoint [[-RestorePoint] <Int32[]>] [<CommonParameters>]
```

### LastStatus

```
Get-ComputerRestorePoint -LastStatus [<CommonParameters>]
```

## BESKRIVNING

`Get-ComputerRestorePoint`Cmdlet: en hämtar system återställnings punkter för den lokala datorn. Och kan visa status för det senaste försöket att återställa datorn.

Du kan använda informationen från `Get-ComputerRestorePoint` för att välja en återställnings punkt. Du kan till exempel använda ett ordnings nummer för att identifiera en återställnings punkt för `Restore-Computer` cmdleten.

System återställnings punkter och `Get-ComputerRestorePoint` cmdlet stöds endast på klient operativ system som Windows 10, Windows 7, Windows Vista och Windows XP.

## EXEMPEL

### Exempel 1: Hämta alla system återställnings punkter

I det här exemplet `Get-ComputerRestorePoint` hämtar alla system återställnings punkter för den lokala datorn.

```powershell
Get-ComputerRestorePoint
```

```Output
CreationTime           Description                    SequenceNumber    EventType         RestorePointType
------------           -----------                    --------------    ---------         ----------------
7/30/2019 09:17:24     Windows Update                 4                 BEGIN_SYSTEM_C... 17
8/5/2019  08:15:37     Installed PowerShell 7-prev... 5                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
8/7/2019  12:56:45     Installed PowerShell 6-x64     6                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
```

### Exempel 2: hämta vissa ordnings nummer

Det här exemplet hämtar system återställnings punkter för vissa sekvensnummer.

```powershell
Get-ComputerRestorePoint -RestorePoint 4, 5
```

```Output
CreationTime           Description                    SequenceNumber    EventType         RestorePointType
------------           -----------                    --------------    ---------         ----------------
7/30/2019 09:17:24     Windows Update                 4                 BEGIN_SYSTEM_C... 17
8/5/2019  08:15:37     Installed PowerShell 7-prev... 5                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
```

`Get-ComputerRestorePoint` använder parametern **RestorePoint** för att ange en kommaavgränsad matris med sekvensnummer.

### Exempel 3: Visa status för en system återställning

I det här exemplet visas statusen för den senaste system återställningen på den lokala datorn.

```powershell
Get-ComputerRestorePoint -LastStatus
```

```Output
The last attempt to restore the computer failed.
```

`Get-ComputerRestorePoint` använder parametern **LastStatus** för att visa resultatet av den senaste system återställningen.

### Exempel 4: Använd ett uttryck för att konvertera CreationTime

`Get-ComputerRestorePoint` matar ut **CreationTime** som en Windows Management INSTRUMENTATION (WMI)-datum-och tids sträng.

I det här exemplet lagrar en variabel ett uttryck som konverterar **CreationTime** -strängen till ett **datetime** -objekt. Om du vill visa **CreationTime** -strängar innan de konverteras, använder du ett kommando som `((Get-ComputerRestorePoint).CreationTime)` . Mer information om WMI-datum och tids sträng finns [CIM_DATETIME](/windows/win32/wmisdk/cim-datetime).

```powershell
$date = @{Label="Date"; Expression={$_.ConvertToDateTime($_.CreationTime)}}
Get-ComputerRestorePoint | Select-Object -Property SequenceNumber, $date, Description
```

```Output
SequenceNumber   Date                 Description
--------------   ----                 -----------
             4   7/30/2019 09:17:24   Windows Update
             5   8/5/2019  08:15:37   Installed PowerShell 7-preview-x64
             6   8/7/2019  12:56:45   Installed PowerShell 6-x64
```

`$date`Variabeln lagrar en hash-tabell med uttrycket som använder metoden **ConvertToDateTime** . Uttrycket konverterar **CreationTime** -egenskapens värde från en WMI-sträng till ett **datetime** -objekt.

`Get-ComputerRestorePoint` skickar system återställnings punkts objekt nedåt i pipelinen. `Select-Object` använder **egenskaps** parametern för att ange vilka egenskaper som ska visas. För varje objekt i pipelinen konverterar uttrycket i `$date` **CreationTime** och matar ut resultatet i egenskapen **date** .

### Exempel 5: Använd en egenskap för att hämta ett sekvensnummer

Det här exemplet hämtar ett sekvensnummer med hjälp av egenskapen **SequenceNumber** och ett mat ris index. Utdata innehåller bara sekvensnumret.

```powershell
((Get-ComputerRestorePoint).SequenceNumber)[-1]
```

```Output
6
```

`Get-ComputerRestorePoint` använder egenskapen **SequenceNumber** med ett mat ris index. Mat ris indexet för `-1` hämtar det senaste sekvensnumret i matrisen.

## PARAMETRAR

### -LastStatus

Anger att `Get-ComputerRestorePoint` hämtar status för den senaste system återställnings åtgärden.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LastStatus
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -RestorePoint

Anger system återställnings punkternas ordnings nummer. Du kan ange antingen ett enda sekvensnummer eller en kommaavgränsad matris med sekvensnummer.

Om parametern **RestorePoint** inte anges `Get-ComputerRestorePoint` returnerar alla system återställnings punkter för den lokala datorn.

```yaml
Type: System.Int32[]
Parameter Sets: ID
Aliases:

Required: False
Position: 0
Default value: All restore points
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Du kan inte skicka objekt nedåt i pipelinen till `Get-ComputerRestorePoint` .

## UTDATA

### System. Management. ManagementObject # root\default\SystemRestore eller string

`Get-ComputerRestorePoint` Returnerar ett **SystemRestore** -objekt, som är en instans av **SystemRestore** -klassen (Windows Management Instrumentation).

När du använder parametern **LastStatus** `Get-ComputerRestorePoint` returneras en sträng.

## ANTECKNINGAR

Om du vill köra ett `Get-ComputerRestorePoint` kommando i Windows Vista och senare versioner av Windows öppnar du PowerShell med alternativet **Kör som administratör** .

`Get-ComputerRestorePoint` använder WMI- **SystemRestore** -klassen.

## RELATERADE LÄNKAR

[about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[about_Arrays](../Microsoft.PowerShell.Core/About/about_Arrays.md)

[Checkpoint-Computer](Checkpoint-Computer.md)

[Disable-ComputerRestore](Disable-ComputerRestore.md)

[Aktivera – ComputerRestore](Enable-ComputerRestore.md)

[Starta om datorn](Restart-Computer.md)

[Återställa-dator](Restore-Computer.md)

[SystemRestore](/windows/win32/sr/systemrestore)
