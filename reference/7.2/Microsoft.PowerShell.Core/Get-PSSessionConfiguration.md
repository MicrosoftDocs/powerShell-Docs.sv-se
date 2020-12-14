---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssessionconfiguration?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSessionConfiguration
ms.openlocfilehash: a5aa70521841b3b05d34623ff92ebbf9e3471fd1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710495"
---
# Get-PSSessionConfiguration

## SAMMANFATTNING
Hämtar de registrerade sessionsbaserade på datorn.

## SYNTAX

```
Get-PSSessionConfiguration [[-Name] <String[]>] [-Force] [<CommonParameters>]
```

## BESKRIVNING

`Get-PSSessionConfiguration`Cmdlet: en hämtar de sessionsinställningar som har registrerats på den lokala datorn. Det här är en avancerad cmdlet som är avsedd att användas av system administratörer för att hantera konfigurationer för anpassade sessioner för sina användare.

Från och med PowerShell 3,0 kan du definiera egenskaperna för en session-konfiguration med hjälp av en PSSC-fil (session Configuration). Med den här funktionen kan du skapa anpassade och begränsade sessioner utan att skriva ett dator program. Mer information om konfigurationsfiler för sessioner finns [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).

Från och med PowerShell 3,0 har nya antecknings egenskaper också lagts till i sessionens konfigurations objekt som `Get-PSSessionConfiguration` returneras. De här egenskaperna gör det enklare för användare och konfiguration av sessioner att granska och jämföra sessionsbaserade.

Använd cmdleten för att skapa och registrera en konfiguration av en session `Register-PSSessionConfiguration` .
För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).

## EXEMPEL

### Exempel 1 – Hämta konfigurationer för sessioner på den lokala datorn

```powershell
Get-PSSessionConfiguration
```

### Exempel 2 – Hämta två standardkonfigurationer för sessioner

Kommandot använder **Name** -parametern för `Get-PSSessionConfiguration` att bara hämta sessionsinställningar med namn som börjar med "Microsoft".

```powershell
Get-PSSessionConfiguration -Name Microsoft*
```

```Output
Name                      PSVersion  StartupScript        Permission
----                      ---------  -------------        ----------
microsoft.powershell      5.1                             BUILTIN\Administrators AccessAll...
microsoft.powershell32    5.1                             BUILTIN\Administrators AccessAll...
```

### Exempel 3 – Hämta egenskaperna och värdena för en konfiguration av sessionen

I det här exemplet visas egenskaper och egenskaps värden för en sessionsfil som skapats med hjälp av en konfigurations fil för sessionen.

```powershell
Get-PSSessionConfiguration -Name Full  | Format-List -Property *
```

```Output
Copyright                     : (c) 2011 User01. All rights reserved.
AliasDefinitions              : {System.Collections.Hashtable}
SessionType                   : Default
CompanyName                   : Unknown
GUID                          : 1e9cb265-dae0-4bd3-89a9-8338a47698a1
Author                        : User01
ExecutionPolicy               : Restricted
SchemaVersion                 : 1.0.0.0
LanguageMode                  : FullLanguage
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/Full
MaxConcurrentCommandsPerShell : 1500
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 10
lang                          : en-US
SupportsOptions               : true
ExactMatch                    : true
configfilepath                : C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
MaxShells                     : 300
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
SDKVersion                    : 1
Name                          : Full
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 25
Enabled                       : True
MaxShellsPerUser              : 30
Permission                    :
```

Exemplet använder `Get-PSSessionConfiguration` cmdleten för att hämta den fullständiga konfigurationen av sessionen. En pipeline-operator skickar fullständig sessionsinformation till `Format-List` cmdleten. **Egenskaps** parametern med värdet `*` (alla) leder `Format-List` för att visa alla egenskaper och värden för objektet i en lista.

Utdata innehåller användbar information, inklusive författaren av sessionens konfiguration, typ av session, språk läge och körnings princip för sessioner som skapas med den här konfigurationen, session kvoter och den fullständiga sökvägen till sessionens konfigurations fil.

Den här vyn av en sessions konfiguration används för sessioner som innehåller en konfigurations fil för sessionen.
Mer information om konfigurationsfiler för sessioner finns [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).

### Exempel 4 – ett annat sätt att titta på sessionens konfigurationer

I det här exemplet används `Get-ChildItem` cmdleten (alias `dir` ) i WSMan: Provider-enheten för att titta på innehållet i plugin-noden. Detta är ett annat sätt att titta på sessionens konfigurationer på datorn.

```powershell
dir wsman:\localhost\plugin
```

```Output
Type            Keys                                Name
----            ----                                ----
Container       {Name=Event Forwarding Plugin}      Event Forwarding Plugin
Container       {Name=Full}                         Full
Container       {Name=microsoft.powershell}         microsoft.powershell
Container       {Name=microsoft.powershell.workf... microsoft.powershell.workflow
Container       {Name=microsoft.powershell32}       microsoft.powershell32
Container       {Name=microsoft.ServerManager}      microsoft.ServerManager
Container       {Name=WMI Provider}                 WMI Provider
```

**Plugin** -noden innehåller **ContainerElement** -objekt (Microsoft. WSMan. Management. WSManConfigContainerElement) som representerar registrerade PowerShell-sessionsbaserade konfigurationer, tillsammans med andra plugin-program för WS-Management.

### Exempel 6 – Visa sessionsinställningar på en fjärrdator

I det här exemplet visas hur du använder WSMan-providern för att Visa sessionsinställningar på en fjärrdator. Den här metoden ger inte så mycket information som ett `Get-PSSessionConfiguration` kommando, men användaren behöver inte vara medlem i gruppen Administratörer för att köra denna cmdlet.

```powershell
Connect-WSMan -ComputerName Server01
dir WSMan:\Server01\Plugin
```

```Output
   WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type            Keys                                Name
----            ----                                ----
Container       {Name=Empty}                        Empty
Container       {Name=Event Forwarding Plugin}      Event Forwarding Plugin
Container       {Name=Full}                         Full
Container       {Name=microsoft.powershell}         microsoft.powershell
Container       {Name=microsoft.powershell.workf... microsoft.powershell.workflow
Container       {Name=microsoft.powershell32}       microsoft.powershell32
Container       {Name=microsoft.ServerManager}      microsoft.ServerManager
Container       {Name=NoLanguage}                   NoLanguage
Container       {Name=RestrictedLang}               RestrictedLang
Container       {Name=RRS}                          RRS
Container       {Name=SEL Plugin}                   SEL Plugin
Container       {Name=WithProfile}                  WithProfile
Container       {Name=WMI Provider}                 WMI Provider
```

`Connect-WSMan`Cmdleten ansluter till WinRM-tjänsten på fjärrdatorn Server01. `Get-ChildItem`Cmdleten (alias `dir` ) för WSMan: Drive hämtar objekten i **Server01\Plugin** -sökvägen. Utdata visar objekten i plugin-katalogen på Server01-datorn. Objekten inkluderar sessionsinställningar, som är en typ av WSMan-plugin-program, tillsammans med andra typer av plugin-program på datorn.

### Exempel 7 – Hämta detaljerade sessionsinställningar från en fjärrdator

Det här exemplet visar hur du kör ett `Get-PSSessionConfiguration` kommando på en fjärrdator. Kommandot kräver att CredSSP-delegering aktive ras i klient inställningarna på den lokala datorn och i tjänst inställningarna på fjärrdatorn.

Om du vill köra kommandona i det här exemplet måste du vara medlem i gruppen Administratörer på den lokala datorn och fjärrdatorn och du måste starta PowerShell med alternativet **Kör som administratör** .

```powershell
Enable-WSManCredSSP -Delegate Server02
Connect-WSMan Server02
Set-Item WSMan:\Server02*\Service\Auth\CredSSP -Value $true
Invoke-Command -ScriptBlock {Get-PSSessionConfiguration} -ComputerName Server02 -Authentication CredSSP -Credential Domain01\Admin01
```

```Output
Name                      PSVersion  StartupScript        Permission                          PSComputerName
----                      ---------  -------------        ----------                          --------------
microsoft.powershell      5.1                             BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
microsoft.powershell32    5.1                             BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
MyX86Shell                5.1        c:\test\x86Shell.ps1 BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
```

`Enable-WSManCredSSP`Cmdlet: en aktiverar **CredSSP** -delegering på Server01, den lokala datorn. `Connect-WSMan`Cmdleten ansluter till Server02-datorn. Den här åtgärden lägger till en nod för Server02 till enheten WSMan: på den lokala datorn, så att du kan visa och ändra WS-Management inställningar på Server02-datorn. `Set-Item`Cmdleten ändrar värdet för **CredSSP** -objektet i noden tjänst på den Server02 datorn till **True**. Detta konfigurerar tjänst inställningarna på fjärrdatorn. `Invoke-Command`Cmdleten kör `Get-PSSessionConfiguration` kommandot på Server02-datorn. Kommandot använder parametern **Credential** och använder parametern **Authentication** med värdet **CredSSP**. Utdata visar sessionens konfigurationer på Server02-fjärrdatorn.

### Exempel 8 – Hämta resurs-URI för en konfiguration av sessionen

Det här exemplet är användbart för att ange värdet för `$PSSessionConfigurationName` variabeln Preference, som tar en resurs-URI.

```powershell
(Get-PSSessionConfiguration -Name CustomShell).resourceURI
```

```Output
http://schemas.microsoft.com/powershell/microsoft.CustomShell
```

`$PSSessionConfigurationName`Variabeln anger standard konfigurationen som används när du skapar en session. Den här variabeln anges på den lokala datorn, men den anger en konfiguration på fjärrdatorn. Mer information om `$PSSessionConfiguration` variabeln finns i [about_Preference_Variables](About/about_Preference_Variables.md).

## PARAMETRAR

### -Force

Inaktiverar uppmaningen att starta om WinRM-tjänsten om tjänsten inte redan körs.

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

### -Name

Hämtar endast sessionsdata med angivet namn eller namn mönster. Ange ett eller flera konfigurations namn för sessionen. Jokertecken är tillåtna.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: All session configurations on the local computer
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](./About/about_CommonParameters.md).

## INDATA

### Inga

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### Microsoft. PowerShell. commands. PSSessionConfigurationCommands # PSSessionConfiguration

## ANTECKNINGAR

- Starta PowerShell med alternativet **Kör som administratör** för att köra denna cmdlet.

- Om du vill visa sessionsinställningar på datorn måste du vara medlem i gruppen Administratörer på datorn.

- Om du vill köra ett `Get-PSSessionConfiguration` kommando på en fjärrdator måste autentiseringen Credential Security Service Provider (CredSSP) vara aktive rad i klient inställningarna på den lokala datorn (med hjälp av `Enable-WSManCredSSP` cmdleten) och i tjänst inställningarna på fjärrdatorn. Du måste också använda **CredSSP** -värdet för parametern **Authentication** när du etablerar fjärrsessionen. Annars nekas åtkomst.

- Antecknings egenskaperna för det objekt som `Get-PSSessionConfiguration` returneras visas bara för objektet när de har ett värde. Endast sessionsinställningar som skapats med hjälp av en konfigurations fil för sessionen har alla definierade egenskaper.

- Egenskaperna för ett konfigurations objekt för en session varierar beroende på vilka alternativ som har angetts för konfigurationen av sessionen och värdena för dessa alternativ. Dessutom har sessionsinställningar som använder en konfigurations fil för sessionen ytterligare egenskaper.

- Du kan använda kommandona i WSMan: Drive för att ändra egenskaperna för sessionens konfigurationer.
  Du kan dock inte använda WSMan:-enheten i PowerShell 2,0 för att ändra konfigurations egenskaper för sessionen som introduceras i PowerShell 3,0, till exempel **OutputBufferingMode**. PowerShell 2,0-kommandon genererar inte ett fel, men de är ineffektiva. Om du vill ändra de egenskaper som introduceras i PowerShell 3,0 använder du kommandot WSMan: Drive i PowerShell 3,0.

## RELATERADE LÄNKAR

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Aktivera – PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[New-PSSessionOption](New-PSSessionOption.md)

[Registrera – PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Avregistrera-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan-Provider](../microsoft.wsman.management/about/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)

