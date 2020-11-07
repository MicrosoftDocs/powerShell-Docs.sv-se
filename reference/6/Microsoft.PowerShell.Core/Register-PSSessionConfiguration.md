---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/register-pssessionconfiguration?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PSSessionConfiguration
ms.openlocfilehash: 6417881880cb7f317e7a42d6749b8b7f2cb712fb
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94345484"
---
# Register-PSSessionConfiguration

## SAMMANFATTNING
Skapar och registrerar en ny konfiguration av sessionen.

## SYNTAX

### NameParameterSet (standard)

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-SessionType <PSSessionType>]
 [-Name] <String> [-ApplicationBase <String>] [-RunAsCredential <PSCredential>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>]
 [-TransportOption <PSTransportOption>] [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### AssemblyNameParameterSet

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String> [-AssemblyName] <String>
 [-ApplicationBase <String>] [-ConfigurationTypeName] <String> [-RunAsCredential <PSCredential>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>]
 [-TransportOption <PSTransportOption>] [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SessionConfigurationFile

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String>
 [-RunAsCredential <PSCredential>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-TransportOption <PSTransportOption>] -Path <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Register-PSSessionConfiguration`Cmdleten skapar och registrerar en ny sessionshantering på den lokala datorn. Det här är en avancerad cmdlet som du kan använda för att skapa anpassade sessioner för fjärran vändare.

Varje PowerShell-session ( **PSSession** ) använder en sessionshantering, även kallad en slut punkt.
När användarna skapar en-session som ansluter till datorn kan de välja en sessionsnyckel eller använda den standardsessions-konfiguration som registreras när du aktiverar PowerShell-fjärrkommunikation.
Användare kan också ange variabeln $PSSessionConfigurationName, som anger en standard konfiguration för fjärrsessioner som skapas i den aktuella sessionen.

Konfigurationen av sessionen definierar miljön för fjärrsessionen. Konfigurationen kan avgöra vilka kommandon och språk element som är tillgängliga i sessionen, och det kan innehålla inställningar som skyddar datorn, till exempel sådana som begränsar mängden data som sessionen kan ta emot via fjärr anslutning i ett enda objekt eller kommando. Säkerhets beskrivningen för konfigurationen av sessionen avgör vilka användare som har behörighet att använda sessionen.

Du kan definiera komponenterna i konfigurationen genom att använda en sammansättning som implementerar en ny konfigurations klass och genom att använda ett skript som körs i sessionen. Från och med PowerShell 3,0 kan du också använda en konfigurations fil för sessionen för att definiera konfigurationen för sessionen.

Information om sessionsdata finns [about_Session_Configurations](About/about_Session_Configurations.md).
Information om konfigurationsfiler för sessioner finns [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).

## EXEMPEL

### Exempel 1: registrera en konfiguration för NewShell-sessionen

I det här exemplet registrerar vi konfigurationen för **NewShell** -sessionen. Parametrarna **AssemblyName** och **ApplicationBase** anger platsen för **MyShell.dll** -filen, som anger de cmdlets och providers i konfigurationen för sessionen. Parametern **ConfigurationTypeName** anger vilken konfigurations klass som ska användas från sammansättningen.

```powershell
$sessionConfiguration = @{
    Name='NewShell'
    ApplicationBase='c:\MyShells\'
    AssemblyName='MyShell.dll'
    ConfigurationTypeName='MyClass'
}
Register-PSSessionConfiguration @sessionConfiguration
```

Om du vill använda den här konfigurationen skriver du `New-PSSession -ConfigurationName newshell` .

### Exempel 2: registrera en konfiguration för MaintenanceShell-sessioner

Det här exemplet registrerar konfigurationen för **MaintenanceShell** på den lokala datorn. Parametern **StartupScript** anger `Maintenance.ps1` skriptet.

```powershell
Register-PSSessionConfiguration -Name MaintenanceShell -StartupScript C:\ps-test\Maintenance.ps1
```

När en användare använder ett `New-PSSession` kommando och väljer **MaintenanceShell** -konfigurationen `Maintenance.ps1` körs skriptet i den nya sessionen. Skriptet kan konfigurera sessionen. Detta inkluderar att importera moduler och att ställa in körnings principen för sessionen. Om skriptet genererar eventuella fel, inklusive icke-avslutande fel, `New-PSSession` Miss lyckas kommandot.

### Exempel 3: registrera en konfiguration av sessionen

Det här exemplet registrerar konfigurationen för **AdminShell** -sessionen.

`$sessionParams`Variabeln är en hash som innehåller alla parameter värden. Denna hash skickas till cmdleten med PowerShell-ihopbuntning. `Register-PSSessionConfiguration`Kommandot använder parametern **SecurityDescritorSDDL** för att ange SDDL i värdet för `$sddl` variabeln och parametern **MaximumReceivedObjectSizeMB** för att öka storleks gränsen för objekt. Den använder också parametern **StartupScript** för att ange ett skript som konfigurerar sessionen.

```powershell
$sddl = "O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;FA;SA;GWGX;;WD)"
$sessionParams = @{
    Name="AdminShell"
    SecurityDescriptorSDDL=$sddl
    MaximumReceivedObjectSizeMB=20
    StartupScript="C:\scripts\AdminShell.ps1"
}
Register-PSSessionConfiguration @sessionParams
```

### Exempel 4: returnera ett konfigurations container element

Det här exemplet visar hur du registrerar **MaintenanceShell** -konfigurationen.
`Register-PSSessionConfiguration` Returnerar ett **WSManConfigContainerElement** -objekt som lagras i `$s` variabeln. `Format-List` visar alla egenskaper för det returnerade objektet. Egenskapen **PSPath** visar att objektet lagras i en katalog för WSMan: Drive. `Get-ChildItem` (alias `dir` ) visar objekten i `WSMan:\LocalHost\PlugIn` sökvägen. Detta omfattar den nya **MaintenanceShell** -konfigurationen och de två standardkonfigurationer som ingår i PowerShell.

```powershell
$s = Register-PSSessionConfiguration -Name MaintenanceShell -StartupScript C:\ps-test\Maintenance.ps1
$s | Format-List -Property *
dir WSMan:\LocalHost\Plugin
```

```Output
PSPath            : Microsoft.WSMan.Management\WSMan::localhost\Plugin\MaintenanceShell
PSParentPath      : Microsoft.WSMan.Management\WSMan::localhost\Plugin
PSChildName       : MaintenanceShell
PSDrive           : WSMan
PSProvider        : Microsoft.WSMan.Management\WSMan
PSIsContainer     : True
Keys              : {Name=MaintenanceShell}
Name              : MaintenanceShell
TypeNameOfElement : Container

Name                      Type                 Keys
----                      ----                 ----
MaintenanceShell          Container            {Name=MaintenanceShell}
microsoft.powershell      Container            {Name=microsoft.powershell}
microsoft.powershell32    Container            {Name=microsoft.powershell32}
```

### Exempel 5: registrera en sessions konfiguration med ett start skript

I det här exemplet skapar och registrerar du konfigurationen för **WithProfile** -sessionen. Parametern **StartupScript** styr PowerShell för att köra det angivna skriptet för alla sessioner som använder sessionen.

```powershell
Register-PSSessionConfiguration -Name WithProfile -StartupScript Add-Profile.ps1
```

Skriptet innehåller ett enda kommando som använder punkt-källa för att köra användarens **CurrentUserAllHosts** -profil i det aktuella omfånget för sessionen.

Mer information om profiler finns [about_Profiles](./About/about_Profiles.md). Mer information om punkt källor finns [about_Scopes](./About/about_Scopes.md).

## PARAMETRAR

### -AccessMode

Aktiverar och inaktiverar konfigurationen av sessionen och avgör om den kan användas för fjärranslutna eller lokala sessioner på datorn. De acceptabla värdena för den här parametern är:

- Inaktiverat Inaktiverar konfigurationen av sessionen. Den kan inte användas för fjärran sluten eller lokal åtkomst till datorn.
- Inställningar. Tillåter användare av den lokala datorn att använda-sessionen för att skapa en lokal loopback-session på samma dator, men nekar åtkomst till fjärran vändare.
- Fjärrserveradministrationsverktyg. Tillåter lokala och fjärranslutna användare att använda sessionen för att skapa sessioner och köra kommandon på den här datorn.

Standardvärdet är fjärran sluten.

Andra cmdletar kan åsidosätta värdet för den här parametern senare. Till exempel `Enable-PSRemoting` tillåter cmdleten fjärråtkomst till alla sessioner, `Enable-PSSessionConfiguration` cmdlet: en aktiverar sessionsbaserade och `Disable-PSRemoting` cmdleten förhindrar fjärråtkomst till alla konfigurationer i sessionen.

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

Anger sökvägen till sammansättnings filen ( \* . dll) som anges i värdet för parametern **AssemblyName** . Använd den här parametern när värdet för parametern **AssemblyName** inte innehåller någon sökväg. Standardvärdet är den aktuella katalogen.

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

Anger namnet på en sammansättnings fil ( \* . dll) där konfigurations typen definieras. Du kan ange sökvägen till. dll i den här parametern eller i värdet för parametern **ApplicationBase** .

Den här parametern krävs när du anger parametern **ConfigurationTypeName** .

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

Anger det fullständigt kvalificerade namnet på den Microsoft .NET Framework-typ som används för den här konfigurationen. Den typ som du anger måste implementera klassen **system. Management. Automation. Remoting. PSSessionConfiguration** .

Om du vill ange sammansättnings filen ( \* . dll) som implementerar konfigurations typen anger du parametrarna **AssemblyName** och **ApplicationBase** .

Genom att skapa en typ kan du kontrol lera fler aspekter av konfigurationen av sessionen, till exempel exponera eller dölja vissa parametrar av cmdletar, eller ange data storlek och storleks gränser för objekt som användarna inte kan åsidosätta.

Om du utelämnar den här parametern används **DefaultRemotePowerShellConfiguration** -klassen för konfigurationen av sessionen.

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

Ignorerar alla användarens prompter och startar om **WinRM** -tjänsten utan att fråga. Att starta om tjänsten gör att konfigurations ändringen träder i kraft.

Om du vill förhindra en omstart och ignorera omstarts meddelandet anger du parametern **NoServiceRestart** .

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

Anger en gräns för mängden data som kan skickas till den här datorn i ett enda fjärran slutet kommando. Ange data storleken i megabyte (MB). Standardvärdet är 50 MB.

Om en data storleks gräns definieras i den konfigurations typ som anges i parametern **ConfigurationTypeName** , används gränsen i konfigurations typen och värdet för den här parametern ignoreras.

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

Anger en gräns för mängden data som kan skickas till den här datorn i ett enda objekt.
Ange data storleken i megabyte. Standardvärdet är 10 MB.

Om en gräns för objekt storlek definieras i den konfigurations typ som anges i parametern **ConfigurationTypeName** , används gränsen i konfigurations typen och värdet för den här parametern ignoreras.

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModulesToImport

Anger de moduler som importeras automatiskt till sessioner som använder sessionen.

Som standard importeras endast **Microsoft. PowerShell. Core** till sessioner. Om inte cmdletarna är uteslutna kan du använda `Import-Module` för att lägga till moduler i sessionen.

Modulerna som anges i det här parametervärdet importeras i tillägg till moduler som anges av parametern **SessionType** och de som anges i **ModulesToImport** -nyckeln i sessionens konfigurations fil ( `New-PSSessionConfigurationFile` ). Inställningarna i konfigurations filen för sessionen kan dock dölja de kommandon som exporteras av moduler eller hindra användarna från att använda dem.

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

Anger ett namn för konfigurationen av sessionen. Den här parametern är obligatorisk.

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

När du kör ett `Register-PSSessionConfiguration` kommando uppmanas du som standard att starta om **WinRM** -tjänsten för att göra den nya konfigurationen effektiv. Den nya konfigurationen är inte giltig förrän **WinRM** -tjänsten har startats om.

Om du vill starta om **WinRM** -tjänsten utan att begära det anger du parametern **Force** . Om du vill starta om **WinRM** -tjänsten manuellt använder du `Restart-Service` cmdleten.

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

Anger sökvägen och fil namnet för en sessions konfigurations fil (. PSSC), till exempel en som skapats av `New-PSSessionConfigurationFile` . Om du utelämnar sökvägen är standardvärdet den aktuella katalogen.

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

### -ProcessorArchitecture

Fastställer om en 32-eller 64-bitars version av PowerShell-processen startas i sessioner som använder den här konfigurationen. De acceptabla värdena för den här parametern är: x86 (32-bitars) och AMD64 (64-bit). Standardvärdet bestäms av processor arkitekturen på den dator som är värd för konfigurationen av sessionen.

Du kan använda den här parametern för att skapa en 32-bitars session på en 64-bitars dator. Försök att skapa en 64-bitars process på en 32-bitars dator Miss lyckas.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PA
Accepted values: x86, amd64

Required: False
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

Anger en SDDL-sträng (Security Descriptor Definition Language) för konfigurationen.

Den här strängen avgör vilka behörigheter som krävs för att använda den nya konfigurationen av sessionen. Om du vill använda en sessionshantering i en session måste användarna ha minst körnings behörighet (Invoke) för konfigurationen.

Om säkerhets beskrivningen är komplex kan du överväga att använda parametern **ShowSecurityDescriptorUI** i stället för den här parametern. Du kan inte använda båda parametrarna i samma kommando.

Om du utelämnar den här parametern används rot-SDDL för **WinRM** -tjänsten för den här konfigurationen.
Om du vill visa eller ändra rot-SDDL använder du WSMan-providern. Till exempel `Get-Item wsman:\localhost\service\rootSDDL`. Om du vill ha mer information om WSMan-providern skriver du `Get-Help wsman` .

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

### -SessionType

Anger vilken typ av session som skapas med hjälp av konfigurationen av sessionen. De acceptabla värdena för den här parametern är:

- Saknas. Inga moduler läggs till i sessionen som standard. Använd parametrarna för denna cmdlet för att lägga till moduler, funktioner, skript och andra funktioner i sessionen.
- Standard. Lägger till Microsoft. PowerShell. core i sessionen. Den här modulen innehåller den `Import-Module` cmdlet som användare kan använda för att importera andra moduler såvida du inte uttryckligen förhindrar cmdlet: en.
- RestrictedRemoteServer. Innehåller endast följande cmdlet:,,,,, `Exit-PSSession` `Get-Command` `Get-FormatData` `Get-Help` `Measure-Object` `Out-Default` och `Select-Object` . Använd ett skript eller en sammansättning eller nycklar i konfigurations filen för sessionen för att lägga till moduler, funktioner, skript och andra funktioner i sessionen.

Standardvärdet är default.

Värdet för den här parametern prioriteras över värdet för **SessionType** -nyckeln i sessionens konfigurations fil.

Den här parametern introducerades i PowerShell 3,0.

```yaml
Type: System.Management.Automation.Runspaces.PSSessionType
Parameter Sets: NameParameterSet
Aliases:
Accepted values: DefaultRemoteShell, Workflow

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

Anger att denna cmdlet visar en egenskaps sida som hjälper dig att skapa SDDL för konfigurationen av sessionen. Egenskaps sidan visas när du har angett `Register-PSSessionConfiguration` kommandot och sedan startar om **WinRM** -tjänsten.

När du anger behörigheterna för konfigurationen måste du komma ihåg att användarna måste ha minst kör (Invoke)-behörighet för att kunna använda sessionen i en session.

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

Anger den fullständigt kvalificerade sökvägen för ett PowerShell-skript. Det angivna skriptet körs i den nya sessionen som använder konfigurationen av sessionen.

Du kan också använda skriptet för att konfigurera sessionen. Om skriptet genererar ett fel, till och med ett icke-avslutande fel, skapas inte sessionen och `New-PSSession` kommandot Miss lyckas.

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

Anger hur trådar skapas och används när ett kommando körs i sessionen. De acceptabla värdena för den här parametern är:

- Standard
- ReuseThread
- UseCurrentThread
- UseNewThread

Standardvärdet är **UseCurrentThread**.

Mer information finns i [PSThreadOptions-uppräkning](/dotnet/api/system.management.automation.runspaces.psthreadoptions?view=powershellsdk-1.1.0).

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

Anger transport alternativet.

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

Visar vad som skulle hända om cmdleten kördes. Cmdleten körs inte.

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

### Microsoft. WSMan. Management. WSManConfigContainerElement

## ANTECKNINGAR

Den här cmdleten är endast tillgänglig på Windows-plattformar.

Om du vill köra denna cmdlet måste du starta PowerShell med alternativet **Kör som administratör** .

Den här cmdleten genererar XML som representerar en plugin-konfiguration för webb tjänster för hantering (WS-Management) och skickar XML till WS-Management, som registrerar plugin-programmet på den lokala datorn ( `New-Item wsman:\localhost\plugin` ).

Egenskaperna för ett konfigurations objekt för en session varierar beroende på vilka alternativ som har angetts för konfigurationen av sessionen och värdena för dessa alternativ. Dessutom har sessionsinställningar som använder en konfigurations fil för sessionen ytterligare egenskaper.

## RELATERADE LÄNKAR

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Aktivera – PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Avregistrera-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan-Provider](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
