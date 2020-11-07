---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-hotfix?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-HotFix
ms.openlocfilehash: cb0fb1a6d7de033438c3165d44d5b8f8c03ba9a4
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94343002"
---
# Get-HotFix

## SAMMANFATTNING
Hämtar snabb korrigeringarna som installeras på lokala eller fjärranslutna datorer.

## SYNTAX

### Standard (standard)

```
Get-HotFix [[-Id] <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
[<CommonParameters>]
```

### Description

```
Get-HotFix [-Description <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
[<CommonParameters>]
```

## BESKRIVNING

`Get-Hotfix`Cmdlet: en hämtar snabb korrigeringar eller uppdateringar som är installerade på den lokala datorn eller angivna fjärrdatorer. Uppdateringarna kan installeras av Windows Update, Microsoft Update, Windows Server Update Services eller installeras manuellt.

## EXEMPEL

### Exempel 1: Hämta alla snabb korrigeringar på den lokala datorn

`Get-Hotfix`Cmdlet: en hämtar alla snabb korrigeringar som är installerade på den lokala datorn.

```powershell
Get-HotFix
```

```output
Source         Description      HotFixID      InstalledBy          InstalledOn
------         -----------      --------      -----------          -----------
Server01       Update           KB4495590     NT AUTHORITY\SYSTEM  5/16/2019 00:00:00
Server01       Security Update  KB4470788     NT AUTHORITY\SYSTEM  1/22/2019 00:00:00
Server01       Update           KB4480056     NT AUTHORITY\SYSTEM  1/24/2019 00:00:00
```

### Exempel 2: Hämta snabb korrigeringar från flera datorer som filtrerats med en sträng

`Get-Hotfix`Kommandot använder parametrar för att hämta snabb korrigeringar som är installerade på fjärrdatorer. Resultaten filtreras efter en angiven beskrivnings sträng.

```
PS> Get-HotFix -Description Security* -ComputerName Server01, Server02 -Credential Domain01\admin01
```

`Get-Hotfix` filtrerar utdata med **beskrivnings** parametern och sträng **säkerheten** som innehåller jokertecknet asterisk ( `*` ). Parametern **computername** innehåller en kommaavgränsad sträng med fjärrdatornamn. Parametern **Credential** anger ett användar konto som har behörighet att komma åt fjärrdatorerna och köra kommandon.

### Exempel 3: kontrol lera om en uppdatering har installerats och skriv dator namn till en fil

Kommandona i det här exemplet verifierar om en viss uppdatering har installerats. Om uppdateringen inte är installerad skrivs dator namnet till en textfil.

```
PS> $A = Get-Content -Path ./Servers.txt
PS> $A | ForEach-Object { if (!(Get-HotFix -Id KB957095 -ComputerName $_))
         { Add-Content $_ -Path ./Missing-KB957095.txt }}
```

`$A`Variabeln innehåller dator namn som hämtades `Get-Content` från en textfil. De objekt som `$A` finns i skickas pipelinen till `ForEach-Object` . En `if` instruktion använder `Get-Hotfix` cmdleten med **ID-** parametern och ett särskilt ID-nummer för varje dator namn. Om en dator inte har angivet snabb korrigerings-ID installerat, `Add-Content` skriver cmdleten dator namnet till en fil.

### Exempel 4: hämta den senaste snabb korrigeringen på den lokala datorn

Det här exemplet hämtar den senaste snabb korrigeringen som är installerad på en dator.

```powershell
(Get-HotFix | Sort-Object -Property InstalledOn)[-1]
```

`Get-Hotfix` skickar objekten nedåt i pipelinen till `Sort-Object` cmdleten. `Sort-Object` sorterar objekt efter stigande ordning och använder **egenskaps** parametern för att utvärdera varje **InstalledOn** datum. Mat ris notationen `[-1]` väljer den senaste installerade snabb korrigeringen.

## PARAMETRAR

### -ComputerName

Anger en fjärrdator. Ange NetBIOS-namnet, en Internet Protocol IP-adress eller ett fullständigt kvalificerat domän namn (FQDN) för en fjärran sluten dator.

När parametern **computername** inte anges körs den `Get-Hotfix` på den lokala datorn.

Parametern **computername** är inte beroende av Windows PowerShell-fjärrkommunikation. Om datorn inte är konfigurerad för att köra fjärrkommandon använder du parametern **computername** .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __Server, IPAddress

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

Anger ett användar konto som har behörighet att komma åt datorn och köra kommandon. Standardvärdet är den aktuella användaren

Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten. Om du anger ett användar namn uppmanas du att ange lösen ordet.

Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Beskrivning

`Get-HotFix` använder **Description** -parametern för att ange snabb korrigerings typer. Jokertecken är tillåtna.

```yaml
Type: System.String[]
Parameter Sets: Description
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ID

Filtrerar `Get-HotFix` resultaten för vissa snabb korrigerings-ID: n. Jokertecken accepteras inte.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: HFID

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Sträng

Du kan skicka ett eller flera dator namn för att få snabb korrigering.

## UTDATA

### System. Management. ManagementObject # root\CIMV2\ Win32_QuickFixEngineering

`Get-HotFix` returnerar objekt som representerar snabb korrigeringarna på datorn.

## ANTECKNINGAR

Den här cmdleten är endast tillgänglig på Windows-plattformar.

**Win32_QuickFixEngineering** [WMI-klassen](/windows/desktop/WmiSdk/retrieving-a-class) representerar en mindre systemomfattande uppdatering, vanligt vis kallat snabb korrigerings teknik (QFE), som tillämpas på det aktuella operativ systemet. Den här klassen returnerar endast uppdateringar som tillhandahålls av Component Based Servicing (CBS). De här uppdateringarna visas inte i registret. Uppdateringar som tillhandahålls av Microsoft Windows Installer (MSI) eller [Windows updates](https://update.microsoft.com) platsen returneras inte av **Win32_QuickFixEngineering**. Mer information finns i [Win32_QuickFixEngineering-klass](/windows/desktop/CIMWin32Prov/win32-quickfixengineering).

`Get-HotFix`Utdata kan variera mellan olika operativ system.

## RELATERADE LÄNKAR

[about_Arrays](../Microsoft.PowerShell.Core/About/about_Arrays.md)

[Lägg till innehåll](Add-Content.md)

[Get-ComputerRestorePoint](Get-ComputerRestorePoint.md)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

[Win32_QuickFixEngineering klass](/windows/desktop/CIMWin32Prov/win32-quickfixengineering)
