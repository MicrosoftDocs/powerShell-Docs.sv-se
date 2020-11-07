---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-service?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Service
ms.openlocfilehash: c6aa8a16bd5ccbeb00252b872e997018b1997181
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94346708"
---
# Set-Service

## SAMMANFATTNING
Startar, stoppar och pausar en tjänst och ändrar dess egenskaper.

## SYNTAX

### Namn (standard)

```
Set-Service [-Name] <String> [-DisplayName <String>] [-Credential <PSCredential>]
 [-Description <String>] [-StartupType <ServiceStartupType>] [-Status <String>]
 [-SecurityDescriptorSddl <String>] [-Force] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObject

```
Set-Service [-InputObject] <ServiceController> [-DisplayName <String>] [-Credential <PSCredential>]
 [-Description <String>] [-StartupType <ServiceStartupType>] [-SecurityDescriptorSddl <String>]
 [-Status <String>] [-Force] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
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

### Exempel 7: stoppa en tjänst på ett fjärrsystem

I det här exemplet stoppas en tjänst på en fjärran sluten dator.
Mer information finns i [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).

```powershell
$Cred = Get-Credential
$S = Get-Service -Name Schedule
Invoke-Command -ComputerName server01.contoso.com -Credential $Cred -ScriptBlock {
  Set-Service -InputObject $S -Status Stopped
}
```

`Get-Credential` efterfrågar ett användar namn och lösen ord och lagrar autentiseringsuppgifterna i `$Cred` variabeln. `Get-Service` använder **Name** -parametern för att ange tjänsten **Schedule** . Objektet lagras i variabeln `$S` .

`Invoke-Command` använder parametern **computername** för att ange en fjärrdator. Parametern **Credential** använder `$Cred` variabeln för att logga in på datorn. **Script block** -anrop `Set-Service` . Parametern **InputObject** anger det tjänst objekt som lagras `$S` . **Status** parametern anger att tjänsten har **stoppats**.

### Exempel 8: ändra autentiseringsuppgifter för en tjänst

Det här exemplet ändrar de autentiseringsuppgifter som används för att hantera en tjänst.

```powershell
$credential = Get-Credential
Set-Service -Name Schedule -Credential $credential
```

`Get-Credential` efterfrågar ett användar namn och lösen ord och lagrar autentiseringsuppgifterna i `$credential` variabeln. `Set-Service` använder **Name** -parametern för att ange tjänsten **Schedule** . Parametern **Credential** använder `$credential` variabeln och uppdaterar tjänsten **schema** .

### Exempel 9: ändra adtagent för en tjänst

Det här exemplet ändrar en tjänsts **adtagent**.

```powershell
$SDDL = "D:(A;;CCLCSWRPWPDTLOCRRC;;;SY)(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;BA)(A;;CCLCSWLOCRRC;;;SU)"
Set-Service -Name "BITS" -SecurityDescriptorSddl $SDDL
```

**Adtagent** lagras i `$SDDL` variabeln. `Set-Service` använder **Name** -parametern för att ange **BITS** -tjänsten. Parametern **SecurityDescriptorSddl** använder `$SDDL` för att ändra **adtagent** för **BITS** -tjänsten.

## PARAMETRAR

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

### -Credential

Anger kontot som används av tjänsten som [tjänst inloggnings konto](/windows/desktop/ad/about-service-logon-accounts).

Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten. Om du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.

Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).

Den här parametern introducerades i PowerShell 6,0.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
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

### -Force

Anger tjänstens stopp läge. Den här parametern fungerar bara när `-Status Stopped` används. Om aktive rad stoppas `Set-Service` de beroende tjänsterna innan mål tjänsten stoppas. Som standard höjs undantag när andra tjänster som körs är beroende av mål tjänsten.

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

### – InputObject

Anger ett **ServiceController** -objekt som representerar den tjänst som ska ändras. Ange en variabel som innehåller objektet eller Skriv ett kommando eller uttryck som hämtar objektet, till exempel ett `Get-Service` kommando. Du kan använda pipelinen för att skicka ett tjänst objekt till `Set-Service` .

```yaml
Type: System.ServiceProcess.ServiceController
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
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

Anger tjänstens start läge.

De acceptabla värdena för den här parametern är följande:

- **Automatiskt** – tjänsten startas eller startades av operativ systemet vid system start.
  Om en automatiskt startad tjänst är beroende av en manuellt startad tjänst startas automatiskt den manuellt startade tjänsten automatiskt vid system start.
- **AutomaticDelayedStart** – startar strax efter att systemet har startat.
- **Disabled** – tjänsten är inaktive rad och kan inte startas av en användare eller ett program.
- **InvalidValue** – har ingen inverkan. Cmdleten returnerar inte ett fel, men Startuptype tjänst för tjänsten har inte ändrats.
- **Manuell** – tjänsten startas endast manuellt, av en användare, med hjälp av tjänst hanteraren eller av ett program.

```yaml
Type: Microsoft.PowerShell.Commands.ServiceStartupType
Parameter Sets: (All)
Aliases: StartMode, SM, ST, StartType
Accepted values: Automatic, AutomaticDelayedStart, Disabled, InvalidValue, Manual

Required: False
Position: Named
Default value: None
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

### -SecurityDescriptorSddl

Anger **adtagent** för tjänsten i **SDDL** -format.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: sd

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

Den här cmdleten är endast tillgänglig på Windows-plattformar.

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

[Remove-service](Remove-Service.md)
