---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-pssessionconfiguration?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSSessionConfiguration
ms.openlocfilehash: 8a769959295de0eed7776cc972b007514cfe8734
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268526"
---
# Set-PSSessionConfiguration

## SAMMANFATTNING
Ändrar egenskaperna för en registrerad session-konfiguration.

## SYNTAX

### NameParameterSet (standard)

```
Set-PSSessionConfiguration [-Name] <String> [-ApplicationBase <String>] [-RunAsCredential <PSCredential>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>]
 [-TransportOption <PSTransportOption>] [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### AssemblyNameParameterSet

```
Set-PSSessionConfiguration [-Name] <String> [-AssemblyName] <String> [-ApplicationBase <String>]
 [-ConfigurationTypeName] <String> [-RunAsCredential <PSCredential>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SessionConfigurationFile

```
Set-PSSessionConfiguration [-Name] <String> [-RunAsCredential <PSCredential>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-TransportOption <PSTransportOption>] -Path <String> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESKRIVNING

`Set-PSSessionConfiguration`Cmdleten ändrar egenskaperna för sessionens konfigurationer på den lokala datorn.

Använd parametern **Name** för att identifiera den konfiguration av sessionen som du vill ändra. Använd de andra parametrarna för att ange nya värden för egenskaperna för sessionen. Om du vill ta bort ett egenskaps värde från konfigurationen och använda standardvärdet anger du en tom sträng ("") eller värdet `$Null` för motsvarande parameter.

Från och med PowerShell 3,0 kan du använda en konfigurations fil för sessionen för att definiera en sessions-konfiguration. Den här funktionen ger en enkel och identifierad metod för att ange och ändra egenskaperna för sessioner som använder sessionen. Om du vill ange en konfigurations fil för sessionen använder du parametern **Path** i `Set-PSSessionConfiguration` . Information om konfigurationsfiler för sessioner finns [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).
Information om hur du skapar och ändrar en konfigurations fil för en session finns i `New-PSSessionConfigurationFile` cmdleten.

Sessionsbaserade definierar miljön för fjärrsessioner ( **PSSessions** ) som ansluter till den lokala datorn. Varje **PSSession** använder en konfiguration av sessionen. Konfigurationen av sessionen bestämmer funktionerna i **PSSession** , till exempel de moduler som är tillgängliga i sessionen, vilka cmdlets som tillåts köras, språk läge, kvoter och tids gränser. Säkerhets beskrivningen för konfigurationen av sessionen avgör vem som kan använda sessionen för att ansluta till den lokala datorn. För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).

Använd `Get-PSSessionConfiguration` cmdleten eller WSMan-providern för att se egenskaperna för en sessions konfiguration. Om du vill ha mer information om WSMan-providern skriver du `Get-Help WSMan` .

## EXEMPEL

### Exempel 1: skapa och ändra en konfiguration av sessionen

Det här exemplet visar hur du lägger till och tar bort ett start skript från en konfiguration.

Det första kommandot skapar **AdminShell** -konfigurationen. Det andra kommandot lägger till `AdminConfig.ps1` skriptet i konfigurationen. Ändringen gäller när du startar om **WinRM**.
Det tredje kommandot tar bort `AdminConfig.ps1` skriptet från konfigurationen.

```powershell
Register-PSSessionConfiguration -Name "AdminShell" -AssemblyName "C:\Shells\AdminShell.dll" -ConfigurationTypeName "AdminClass"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript "AdminConfig.ps1"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript $Null
```

### Exempel 2: Visa resultat

Det här exemplet ökar värdet för egenskapen **MaximumReceivedObjectSizeMB** till 20. Det här kommandot kräver också att du startar om **WinRM** -tjänsten. Ändringen gäller inte förrän **WinRM** -tjänsten har startats om.

```powershell
Set-PSSessionConfiguration -Name "IncObj" -MaximumReceivedObjectSizeMB 20
```

```Output
WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin\IncObj\InitializationParameters

ParamName                       ParamValue
---------                       ----------
psmaximumreceivedobjectsizemb   20

"Restart WinRM service"
WinRM service need to be restarted to make the changes effective. Do you want to run the command "restart-service winrm"?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): y
```

### Exempel 3: Visa resultat på olika sätt

I det här exemplet `Set-PSSessionConfiguration` ändrar Start skriptet i **MaintenanceShell** -sessionen till `Maintenance.ps1` . Resultatet visar ändringen och du ombeds att starta om **WinRM** -tjänsten. Svaret är "y" (Ja).

`Get-PSSessionConfiguration` hämtar konfigurationen för **MaintenanceShell** -sessionen. Pipeline-operatorn (|) skickar resultatet från kommandot till `Format-List` , som visar alla egenskaper för konfigurationsobjektet i en lista. Därefter visar vi initierings parametrarna för **MaintenanceShell** -konfigurationen med hjälp av WSMan-providern. `Get-ChildItem` (alias `dir` ) hämtar de underordnade objekten i **InitializationParameters** -noden för **MaintenanceShell** -plugin-programmet. Om du vill ha mer information om WSMan-providern skriver du `Get-Help wsman` .

```powershell
Set-PSSessionConfiguration -Name "MaintenanceShell" -StartupScript "C:\ps-test\Maintenance.ps1"
```

```Output
WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin\MaintenanceShell\InitializationParameters

ParamName            ParamValue
---------            ----------
startupscript        c:\ps-test\Mainte...

"Restart WinRM service"
WinRM service need to be restarted to make the changes effective. Do you want to run
the command "restart-service winrm"?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): y

```

```powershell
Get-PSSessionConfiguration MaintenanceShell | Format-List -Property *
```

```Output
xmlns            : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
Name             : MaintenanceShell
Filename         : %windir%\system32\pwrshplugin.dll
SDKVersion       : 1
XmlRenderingType : text
lang             : en-US
PSVersion        : 2.0
startupscript    : c:\ps-test\Maintenance.ps1
ResourceUri      : http://schemas.microsoft.com/powershell/MaintenanceShell
SupportsOptions  : true
ExactMatch       : true
Capability       : {Shell}
Permission       :
```

```powershell
dir WSMan:\localhost\Plugin\MaintenanceShell\InitializationParameters
```

```Output
ParamName     ParamValue
---------     ----------
PSVersion     2.0
startupscript c:\ps-test\Maintenance.ps1
```

## PARAMETRAR

### -AccessMode

Aktiverar och inaktiverar konfigurationen av sessionen och avgör om den kan användas för fjärranslutna eller lokala sessioner på datorn. De acceptabla värdena för den här parametern är:

- Inaktiverat Inaktiverar konfigurationen av sessionen. Den kan inte användas för fjärran sluten eller lokal åtkomst till datorn. Det här värdet anger egenskapen **Enabled** för session-konfigurationen ( `WSMan:\<ComputerName>\PlugIn\<SessionConfigurationName>\Enabled` ) till **false**.
- Inställningar. Lägger till en **Network_Deny_All** post i säkerhets beskrivningen för konfigurationen av sessionen.
  Användare av den lokala datorn kan använda sessionen för att skapa en lokal loopback-session på samma dator, men fjärran vändare nekas åtkomst.
- Fjärrserveradministrationsverktyg. Tar bort **Deny_All** och **Network_Deny_All** poster från säkerhets beskrivarna i konfigurationen av sessionen. Användare av lokala och fjärranslutna datorer kan använda sessionen för att skapa sessioner och köra kommandon på den här datorn.

Standardvärdet är **fjärran sluten**.

Andra cmdletar kan åsidosätta värdet för den här parametern senare. Till exempel `Enable-PSRemoting` möjliggör cmdleten alla sessionsbaserade på datorn och tillåter fjärråtkomst till dem, och `Disable-PSRemoting` cmdleten tillåter endast lokal åtkomst till alla sessionsinställningar på datorn.

Den här parametern introducerades i PowerShell 3,0.

```yaml
Type: System.Management.Automation.Runspaces.PSSessionConfigurationAccessMode
Parameter Sets: (All)
Aliases:
Accepted values: Disabled, Local, Remote

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – ApplicationBase

Anger sökvägen till sammansättnings filen ( \* . dll) som anges i värdet för parametern **AssemblyName** .

```yaml
Type: System.String
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AssemblyName

Anger sammansättnings namnet. Denna cmdlet skapar en sessionsnyckel som baseras på en klass som har definierats i en sammansättning.

Ange fil namnet eller den fullständiga sökvägen till en Assembly. dll-fil som definierar en-sessions konfiguration. Om du bara anger fil namnet kan du ange sökvägen i värdet för parametern **ApplicationBase** .

```yaml
Type: System.String
Parameter Sets: AssemblyNameParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConfigurationTypeName

Anger typen av sessionsinformation som definieras i sammansättningen i parametern **AssemblyName** . Den typ som du anger måste implementera klassen **system. Management. Automation. Remoting. PSSessionConfiguration** .

Den här parametern krävs när du anger ett sammansättnings namn.

```yaml
Type: System.String
Parameter Sets: AssemblyNameParameterSet
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Ignorerar alla användar meddelanden och startar om **WinRM** -tjänsten utan att fråga. Att starta om tjänsten gör att konfigurations ändringen träder i kraft.

Om du vill förhindra en omstart och ignorera omstarts meddelandet använder du parametern **NoServiceRestart** .

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

### -MaximumReceivedDataSizePerCommandMB

Anger gränsen för mängden data som kan skickas till den här datorn i ett enda fjärran slutet kommando. Ange data storleken i megabyte (MB). Standardvärdet är 50 MB.

Om en data storleks gräns definieras i den konfigurations typ som anges i parametern **ConfigurationTypeName** används gränsen i konfigurations typen. Värdet för den här parametern ignoreras.

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumReceivedObjectSizeMB

Anger gränserna för mängden data som kan skickas till den här datorn i ett enda objekt.
Ange data storleken i megabyte. Standardvärdet är 10 MB.

Om en gräns för objekt storlek definieras i den konfigurations typ som anges i parametern **ConfigurationTypeName** , används gränsen i konfigurations typen. Värdet för den här parametern ignoreras.

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModulesToImport

Anger moduler och snapin-moduler som importeras automatiskt till sessioner som använder-sessionen. Ange modul och namn på snapin-modulen.

Som standard importeras bara snapin-modulen **Microsoft. PowerShell. Core** till sessioner, men om inte cmdletarna utesluts kan du använda- `Import-Module` och Add-PSSnapin-cmdletarna för att lägga till moduler och snapin-moduler till sessionen.

Modulerna som anges i detta parameter värde importeras i tillägg till moduler som anges i konfigurations filen för sessionen ( `New-PSSessionConfigurationFile` ). Inställningarna i konfigurations filen för sessionen kan dock dölja de kommandon som exporteras av moduler eller hindra användarna från att använda dem.

Modulerna som anges i detta parameter värde ersätter listan över moduler som anges genom att använda **ModulesToImport** -parametern för `Register-PSSessionConfiguration` cmdleten.

Den här parametern introducerades i PowerShell 3,0.

```yaml
Type: System.Object[]
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Anger namnet på den sessionsinformation som du vill ändra.

Du kan inte använda den här parametern för att ändra namnet på konfigurationen av sessionen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoServiceRestart

Startar inte om **WinRM** -tjänsten och inaktiverar uppmaningen att starta om tjänsten.

När du kör `Set-PSSessionConfiguration` uppmanas du som standard att starta om **WinRM** -tjänsten för att den nya konfigurationen ska fungera. Den nya konfigurationen är inte giltig förrän **WinRM** -tjänsten har startats om.

Om du vill starta om **WinRM** -tjänsten utan att begära det använder du parametern **Force** . Om du vill starta om **WinRM** -tjänsten manuellt använder du `Restart-Service` cmdleten.

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

### -Path

Anger sökvägen till en sessions konfigurations fil (. PSSC), till exempel en som skapats av `New-PSSessionConfigurationFile` cmdleten. Om du utelämnar sökvägen är standardvärdet den aktuella katalogen.

Information om hur du ändrar en konfigurations fil för en session finns i hjälp avsnittet för `New-PSSessionConfigurationFile` cmdleten.

Den här parametern introducerades i PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: SessionConfigurationFile
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – PSVersion

Anger versionen för PowerShell i sessioner som använder den här sessionen.

Värdet för den här parametern prioriteras över värdet för **PowerShellVersion** -nyckeln i sessionens konfigurations fil.

Den här parametern introducerades i PowerShell 3,0.

```yaml
Type: System.Version
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases: PowerShellVersion

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAsCredential

Anger autentiseringsuppgifter för kommandon i sessionen. Som standard körs kommandona med behörigheterna för den aktuella användaren.

Den här parametern introducerades i PowerShell 3,0.

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

### -SecurityDescriptorSddl

Anger en annan SDDL-sträng (Security Descriptor Definition Language) för konfigurationen.

Den här strängen avgör vilka behörigheter som krävs för att använda den nya konfigurationen av sessionen. Om du vill använda en sessionshantering i en session måste användarna ha minst körnings behörighet (Invoke) för konfigurationen.

Om du vill använda standard säkerhets beskrivningen för konfigurationen anger du en tom sträng ("") eller värdet `$Null` . Standardvärdet är rot-SDDL i filen WSMan: Drive.

Om säkerhets beskrivningen är komplex kan du överväga att använda parametern **ShowSecurityDescriptorUI** i stället för den här. Du kan inte använda båda parametrarna i samma kommando.

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

### -SessionTypeOption

Anger typspecifika alternativ för konfigurationen av sessionen. Ange ett alternativ för sessionsläge, till exempel **PSWorkflowExecutionOption** -objektet som `New-PSWorkflowExecutionOption` cmdleten returnerar.

Alternativen för sessioner som använder sessionen bestäms av värdena för session-alternativen och konfigurations alternativen för sessionen. Om inget annat anges får alternativ som anges i sessionen, till exempel med hjälp av `New-PSSessionOption` cmdleten, företräde framför alternativ som angetts i konfigurationen av sessionen. Värdena för sessionens alternativ får dock inte överskrida de maximala värden som angetts i konfigurationen av sessionen.

Den här parametern introducerades i PowerShell 3,0.

```yaml
Type: System.Management.Automation.PSSessionTypeOption
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ShowSecurityDescriptorUI

Anger att denna cmdlet är en egenskaps sida som hjälper dig att skapa en ny SDDL för konfigurationen av sessionen. Egenskaps sidan visas när du har kört `Set-PSSessionConfiguration` kommandot och startat om **WinRM** -tjänsten.

Kom ihåg att användarna måste ha minst körnings behörighet för att kunna använda sessionen i en session när du anger behörigheter för konfigurationen.

Du kan inte använda parametern **SecurityDescriptorSDDL** och den här parametern i samma kommando.

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

### -StartupScript

Anger start skriptet för konfigurationen. Ange den fullständigt kvalificerade sökvägen till ett PowerShell-skript. Det angivna skriptet körs i den nya sessionen som använder konfigurationen av sessionen.

Om du vill ta bort ett start skript från en sessions konfiguration anger du en tom sträng ("") eller värdet `$Null` .

Du kan använda ett start skript för att ytterligare konfigurera användarsessionen. Om skriptet genererar ett fel, till och med ett icke-avslutande fel, skapas inte sessionen och `New-PSSession` kommandot Miss lyckas.

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

### -ThreadOptions

Anger inställningen för tråd alternativ i konfigurationen. Den här inställningen definierar hur trådar skapas och används när ett kommando körs i sessionen. De acceptabla värdena för den här parametern är:

- Default
- ReuseThread
- UseCurrentThread
- UseNewThread

Standardvärdet är **UseCurrentThread**.

Mer information finns i [PSThreadOptions-uppräkning](/dotnet/api/system.management.automation.runspaces.psthreadoptions).

```yaml
Type: System.Management.Automation.Runspaces.PSThreadOptions
Parameter Sets: (All)
Aliases:
Accepted values: Default, UseNewThread, ReuseThread, UseCurrentThread

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TransportOption

Anger transport alternativ för konfigurationen av sessionen. Ange ett transport alternativ objekt, till exempel **WSManConfigurationOption** -objektet som `New-PSTransportOption` cmdleten returnerar.

Alternativen för sessioner som använder sessionen bestäms av värdena för session-alternativen och konfigurations alternativen för sessionen. Om inget annat anges får alternativ som anges i sessionen, till exempel med hjälp av `New-PSSessionOption` cmdleten, företräde framför alternativ som angetts i konfigurationen av sessionen. Värdena för sessionens alternativ får dock inte överskrida de maximala värden som angetts i konfigurationen av sessionen.

Den här parametern introducerades i PowerShell 3,0.

```yaml
Type: System.Management.Automation.PSTransportOption
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSharedProcess

Använd bara en process som värd för alla sessioner som startas av samma användare och Använd samma sessions konfiguration. Som standard finns varje session i en egen process.

Den här parametern introducerades i PowerShell 3,0.

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

### Microsoft. WSMan. Management. WSManConfigLeafElement

## ANTECKNINGAR

Starta PowerShell med alternativet Kör som administratör för att köra denna cmdlet.

`Set-PSSessionConfiguration`Cmdleten ändrar inte konfigurations namnet och **WSMan** -providern stöder inte `Rename-Item` cmdleten. Om du vill ändra namnet på en sessions konfiguration använder du `Unregister-PSSessionConfiguration` cmdleten för att ta bort konfigurationen och använder sedan `Register-PSSessionConfiguration` cmdleten för att skapa och registrera en ny konfiguration av sessionen.

Du kan använda `Set-PSSessionConfiguration` cmdleten för att ändra standard konfigurationerna för Microsoft. PowerShell och Microsoft. PowerShell32. De är inte skyddade. Om du vill återgå till den ursprungliga versionen av en standardsession, använder du `Unregister-PSSessionConfiguration` cmdleten för att ta bort standardsessionens konfiguration och använder sedan `Enable-PSRemoting` cmdlet: en för att återställa den.

Egenskaperna för ett konfigurations objekt för en session varierar beroende på vilka alternativ som har angetts för konfigurationen av sessionen och värdena för dessa alternativ. Dessutom har sessionsinställningar som använder en konfigurations fil för sessionen ytterligare egenskaper.

Du kan använda kommandona i WSMan: Drive för att ändra egenskaperna för sessionens konfigurationer.
Du kan dock inte använda WSMan:-enheten i PowerShell 2,0 för att ändra konfigurations egenskaper för sessionen som introduceras i PowerShell 3,0, till exempel **OutputBufferingMode**. Windows PowerShell 2,0-kommandon genererar inte ett fel, men de är inaktiva. Om du vill ändra de egenskaper som introduceras i PowerShell 3,0 använder du kommandot WSMan: Drive i PowerShell 3,0.

## RELATERADE LÄNKAR

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Aktivera – PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[New-PSSessionOption](New-PSSessionOption.md)

[New-PSTransportOption](New-PSTransportOption.md)

[Registrera – PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Avregistrera-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan-Provider](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
