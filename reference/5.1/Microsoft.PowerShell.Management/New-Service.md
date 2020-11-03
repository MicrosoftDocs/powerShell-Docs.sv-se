---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Service
ms.openlocfilehash: 3249ce91a63417f2790997d37e2420c6fcb374d8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265520"
---
# New-Service

## SAMMANFATTNING
Skapar en ny Windows-tjänst.

## SYNTAX

```
New-Service [-Name] <String> [-BinaryPathName] <String> [-DisplayName <String>] [-Description <String>]
 [-StartupType <ServiceStartMode>] [-Credential <PSCredential>] [-DependsOn <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`New-Service`Cmdleten skapar en ny post för en Windows-tjänst i registret och i tjänst databasen. En ny tjänst kräver en körbar fil som körs under tjänsten.

Med parametrarna för denna cmdlet kan du ange visnings namn, beskrivning, start typ och beroenden för tjänsten.

## EXEMPEL

### Exempel 1: skapa en tjänst

```powershell
New-Service -Name "TestService" -BinaryPathName "C:\WINDOWS\System32\svchost.exe -k netsvcs"
```

Det här kommandot skapar en tjänst med namnet TestService.

### Exempel 2: skapa en tjänst som innehåller beskrivning, start typ och visnings namn

```powershell
$params = @{
  Name = "TestService"
  BinaryPathName = "C:\WINDOWS\System32\svchost.exe -k netsvcs"
  DependsOn = "NetLogon"
  DisplayName = "Test Service"
  StartupType = "Manual"
  Description = "This is a test service."
}
New-Service @params
```

Det här kommandot skapar en tjänst med namnet TestService. Den använder parametrarna för `New-Service` för att ange en beskrivning, starttyp och visnings namn för den nya tjänsten.

### Exempel 3: Visa den nya tjänsten

```powershell
Get-CimInstance -ClassName Win32_Service -Filter "Name='testservice'"
```

```Output
ExitCode  : 0
Name      : testservice
ProcessId : 0
StartMode : Auto
State     : Stopped
Status    : OK
```

Det här kommandot används `Get-CimInstance` för att hämta **Win32_Service** -objektet för den nya tjänsten. Det här objektet innehåller start-och tjänst beskrivningen.

### Exempel 4: ta bort en tjänst

```powershell
sc.exe delete TestService
# - or -
(Get-CimInstance -Class Win32_Service -Filter "name='TestService'").delete()
```

I det här exemplet visas två sätt att ta bort TestService-tjänsten. Det första kommandot använder alternativet ta bort `Sc.exe` . Det andra kommandot använder **Delete** -metoden för **Win32_Service** objekt som `Get-CimInstance` returneras.

## PARAMETRAR

### -BinaryPathName

Anger sökvägen till tjänstens körbara fil. Den här parametern är obligatorisk.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Anger kontot som används av tjänsten som [tjänst inloggnings konto](/windows/desktop/ad/about-service-logon-accounts).

Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten. Om du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.

Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).

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

### – DependsOn

Anger namnen på andra tjänster som den nya tjänsten är beroende av. Om du vill ange flera tjänst namn använder du ett kommatecken för att avgränsa namnen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Beskrivning

Anger en beskrivning av tjänsten.

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

Anger ett visnings namn för tjänsten.

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

### -Name

Anger namnet på tjänsten.
Den här parametern är obligatorisk.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ServiceName

Required: True
Position: 0
Default value: None
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
Aliases:
Accepted values: Boot, System, Automatic, Manual, Disabled

Required: False
Position: Named
Default value: Automatic
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Uppmanar dig att bekräfta innan du kör cmdleten.

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

### -WhatIf

Visar vad som skulle hända om cmdleten kördes.
Cmdleten körs inte.

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

### Inget

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### System. ServiceProcess. ServiceController

Denna cmdlet returnerar ett objekt som representerar den nya tjänsten.

## ANTECKNINGAR

Om du vill köra den här cmdleten på Windows Vista och senare versioner av Windows-operativsystemet startar du PowerShell med alternativet Kör som administratör.

Om du vill ta bort en tjänst använder du Sc.exe eller använder `Get-CimInstance` cmdleten för att hämta **Win32_Service** -objektet som representerar tjänsten och använder sedan **Delete** -metoden för att ta bort tjänsten. Objektet som `Get-Service` returnerar har ingen Delete-metod.

## RELATERADE LÄNKAR

[Get-Service](Get-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)
