---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Service
ms.openlocfilehash: df4fda68508e21700235d2b772c6dd43c8e1fe1e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265377"
---
# Set-Service

## SAMMANFATTNING
Startar, stoppar och pausar en tjänst och ändrar dess egenskaper.

## SYNTAX

### Namn (standard)

```
Set-Service [-ComputerName <String[]>] [-Name] <String> [-DisplayName <String>]
 [-Description <String>] [-StartupType <ServiceStartMode>] [-Status <String>] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### InputObject

```
Set-Service [-ComputerName <String[]>] [-DisplayName <String>] [-Description <String>]
 [-StartupType <ServiceStartMode>] [-Status <String>] [-InputObject <ServiceController>] [-PassThru]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Set-Service`Cmdleten ändrar egenskaperna för en tjänst, till exempel **status** , **Beskrivning** , **DisplayName** och **startuptype tjänst**. `Set-Service` kan starta, stoppa, pausa eller pausa en tjänst. För att identifiera en tjänst anger du dess tjänst namn eller skickar ett tjänst objekt. Eller skicka ett tjänst namn eller tjänst objekt nedåt i pipeline till `Set-Service` .

## EXEMPEL

### Exempel 1: ändra ett visnings namn

I det här exemplet ändras en tjänsts visnings namn. Använd om du vill visa det ursprungliga visnings namnet `Get-Service` .

```powershell
Set-Service -Name LanmanWorkstation -DisplayName "LanMan Workstation"
```

`Set-Service` använder **Name** -parametern för att ange tjänstens namn, **LanmanWorkstation**. Parametern **DisplayName** anger det nya visnings namnet, **LANMAN-arbetsstationen**.

### Exempel 2: ändra start typen för tjänster

Det här exemplet visar hur du ändrar Start typen för en tjänst.

```powershell
Set-Service -Name BITS -StartupType Automatic
Get-Service BITS | Select-Object -Property Name, StartType, Status
```

```Output
Name  StartType   Status
----  ---------   ------
BITS  Automatic  Running
```

`Set-Service` använder **Name** -parametern för att ange tjänstens namn, **bitar**. Parametern **startuptype tjänst** anger att tjänsten ska vara **Automatisk**.

`Get-Service` använder **Name** -parametern för att ange **BITS** -tjänsten och skickar objektet nedåt i pipelinen. `Select-Object` använder **egenskaps** parametern för att visa **BITS** -tjänstens status.

### Exempel 3: ändra beskrivningen av en tjänst

Det här exemplet ändrar beskrivningen av BITS-tjänsten och visar resultatet.

`Get-CimInstance`Cmdleten används eftersom den returnerar ett **Win32_Service** -objekt som innehåller tjänstens **Beskrivning**.

```powershell
Get-CimInstance Win32_Service -Filter 'Name = "BITS"'  | Format-List  Name, Description
```

```Output
Name        : BITS
Description : Transfers files in the background using idle network bandwidth. If the service is
              disabled, then any applications that depend on BITS, such as Windows Update or MSN
              Explorer, will be unable to automatically download programs and other information.
```

```powershell
Set-Service -Name BITS -Description "Transfers files in the background using idle network bandwidth."
Get-CimInstance Win32_Service -Filter 'Name = "BITS"' | Format-List  Name, Description
```

```Output
Name        : BITS
Description : Transfers files in the background using idle network bandwidth.
```

`Get-CimInstance` skickar objektet nedåt i pipeline till `Format-List` och visar tjänstens namn och beskrivning. I jämförelse syfte körs kommandot före och efter att beskrivningen har uppdaterats.

`Set-Service` använder **Name** -parametern för att ange **BITS** -tjänsten. Parametern **Description** anger den uppdaterade texten för beskrivningen av tjänsterna.

### Exempel 4: starta en tjänst

I det här exemplet startas en tjänst.

```powershell
Set-Service -Name WinRM -Status Running -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinRM              Windows Remote Management (WS-Manag...
```

`Set-Service` använder parametern **Name** för att ange tjänsten, **WinRM**. **Status** parametern använder det värde som **körs** för att starta tjänsten. **Passthru** -parametern matar ut ett **ServiceController** -objekt som visar resultatet.

### Exempel 5: inaktivera en tjänst

I det här exemplet används pipelinen för att pausa tjänsten.

```powershell
Get-Service -Name Schedule | Set-Service -Status Paused
```

`Get-Service` använder **Name** -parametern för att ange **schema** tjänsten och skickar objektet nedåt i pipelinen. `Set-Service` använder **status** parametern för att ange att tjänsten ska **pausas**.

### Exempel 6: stoppa en tjänst

I det här exemplet används en variabel för att stoppa en tjänst.

```powershell
$S = Get-Service -Name Schedule
Set-Service -InputObject $S -Status Stopped
```

`Get-Service` använder **Name** -parametern för att ange tjänsten, **schema**. Objektet lagras i variabeln `$S` . `Set-Service` använder parametern **InputObject** och anger objektet som lagras `$S` . **Status** parametern anger att tjänsten har **stoppats**.

## PARAMETRAR

### -ComputerName

Anger en eller flera datorer. För fjärrdatorer anger du NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn. Om parametern **computername** inte anges körs kommandot på den lokala datorn.

Den här parametern är inte beroende av PowerShell-fjärrkommunikation. Du kan använda parametern **computername** även om datorn inte är konfigurerad för att köra fjärrkommandon.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: cn

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

Du uppmanas att bekräfta innan du kör `Set-Service` .

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

### -Beskrivning

Anger en ny Beskrivning av tjänsten.

Tjänst beskrivningen visas i **dator hantering, tjänster**. **Beskrivningen** är inte en egenskap för `Get-Service` **ServiceController** -objektet. Om du vill se tjänst beskrivningen använder du `Get-CimInstance` som returnerar ett **Win32_Service** -objekt som representerar tjänsten.

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

### -DisplayName

Anger ett nytt visnings namn för tjänsten.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: DN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger ett **ServiceController** -objekt som representerar den tjänst som ska ändras. Ange en variabel som innehåller objektet eller Skriv ett kommando eller uttryck som hämtar objektet, till exempel ett `Get-Service` kommando. Du kan använda pipelinen för att skicka ett tjänst objekt till `Set-Service` .

```yaml
Type: System.ServiceProcess.ServiceController
Parameter Sets: InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Anger tjänst namnet på den tjänst som ska ändras. Jokertecken är inte tillåtna. Du kan använda pipelinen för att skicka ett tjänst namn till `Set-Service` .

```yaml
Type: System.String
Parameter Sets: Name
Aliases: ServiceName, SN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### – PassThru

Returnerar ett **ServiceController** -objekt som representerar de tjänster som har ändrats. Som standard `Set-Service` genererar inga utdata.

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

### – Startuptype tjänst

Anger tjänstens starttyp. De acceptabla värdena för den här parametern är:

- **Automatiskt** – tjänsten startas eller startades av operativ systemet vid system start.
  Om en automatiskt startad tjänst är beroende av en manuellt startad tjänst startas automatiskt den manuellt startade tjänsten automatiskt vid system start.
- **Disabled** – tjänsten är inaktive rad och kan inte startas av en användare eller ett program.
- **Manuell** – tjänsten startas endast manuellt, av en användare, med hjälp av tjänst hanteraren eller av ett program.
- **Boot** -anger att tjänsten är en enhets driv rutin som startas av system inläsaren. Det här värdet är endast giltigt för enhets driv rutiner.
- **System** -anger att tjänsten är en enhets driv rutin som startas av funktionen ' IOInitSystem () '. Det här värdet är endast giltigt för enhets driv rutiner.

 Standardvärdet är **Automatisk**.

```yaml
Type: System.ServiceProcess.ServiceStartMode
Parameter Sets: (All)
Aliases: StartMode, SM, ST
Accepted values: Boot, System, Automatic, Manual, Disabled

Required: False
Position: Named
Default value: Automatic
Accept pipeline input: False
Accept wildcard characters: False
```

### -Status

Anger tjänstens status.

De acceptabla värdena för den här parametern är följande:

- **Pausat**. Pausar tjänsten.
- **Körs**. Startar tjänsten.
- **Stoppades**. Stoppar tjänsten.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Paused, Running, Stopped

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Visar vad som händer om `Set-Service` körs. Cmdleten körs inte.

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

### System. ServiceProcess. ServiceController, system. String

Du kan använda pipelinen för att skicka ett tjänst objekt eller en sträng som innehåller ett tjänst namn till `Set-Service` .

## UTDATA

### System. ServiceProcess. ServiceController

Som standard `Set-Service` returnerar inte några objekt. Använd parametern **Passthru** för att mata ut ett **ServiceController** -objekt.

## ANTECKNINGAR

`Set-Service` kräver förhöjd behörighet. Använd alternativet **Kör som administratör** .

`Set-Service` Det går bara att kontrol lera tjänster när den aktuella användaren har behörighet att hantera tjänster. Om ett kommando inte fungerar som det ska kanske du inte har de behörigheter som krävs.

Använd om du vill hitta tjänstens namn eller visnings namn för tjänsten `Get-Service` . Tjänst namnen finns i kolumnen **namn** och visnings namnen är i kolumnen **DisplayName** .

## RELATERADE LÄNKAR

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)
