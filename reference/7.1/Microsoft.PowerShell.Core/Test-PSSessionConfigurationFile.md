---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-PSSessionConfigurationFile
ms.openlocfilehash: 625611246ea5a07fba16ecb86a2c8c48345d9ea5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264092"
---
# Test-PSSessionConfigurationFile

## SAMMANFATTNING
Verifierar nycklar och värden i en sessions konfigurations fil.

## SYNTAX

```
Test-PSSessionConfigurationFile [-Path] <String> [<CommonParameters>]
```

## BESKRIVNING

Den här cmdleten verifierar att en konfigurations fil för sessionen innehåller giltiga nycklar och att värdena är av rätt typ. För uppräknade värden verifierar cmdleten att de angivna värdena är giltiga.

Cmdleten returnerar `$True` om filen klarar alla tester och `$False` om den inte gör det. Använd **verbose** -parametern för att hitta eventuella fel.

`Test-PSSessionConfigurationFile` verifierar konfigurations filerna för sessionen, till exempel de som skapats av `New-PSSessionConfigurationFile` cmdleten. Information om sessionsdata finns [about_Session_Configurations](About/about_Session_Configurations.md). Information om konfigurationsfiler för sessioner finns [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).

Denna cmdlet introducerades i PowerShell 3,0.

## EXEMPEL

### Exempel 1: testa en sessions konfigurations fil

```powershell
Test-PSSessionConfigurationFile -Path "FullLanguage.pssc"
```

```Output
True
```

### Exempel 2: testa sessionens konfigurations fil för en sessions konfiguration

I det här exemplet testar vi konfigurations filen som används i konfigurationen för den **begränsade** sessionen.
Värdet för parametern **Path** är resultatet av `Get-PSSessionConfiguration` kommandot som hämtar konfigurationen för den **begränsade** sessionen. Sökvägen till sessionens konfigurations fil lagras i värdet för **ConfigFilePath** -egenskapen i konfigurationen för sessionen.

```powershell
Test-PSSessionConfigurationFile -Path (Get-PSSessionConfiguration -Name Restricted).ConfigFilePath
```

### Exempel 3: testa alla konfigurationsfiler för sessioner

Funktionen i det här exemplet testar alla konfigurationsfiler för sessionen på den lokala datorn. Funktionen använder `Get-PSSessionConfiguration` cmdleten för att hämta alla konfigurationer av sessioner. Koden inuti `ForEach-Object` slingan visar fil Sök vägen och testar var och en av sessionens konfigurationer.

```powershell
function Test-AllConfigFiles
{
    Get-PSSessionConfiguration | ForEach-Object {
        if ($_.ConfigFilePath) {
            $_.ConfigFilePath
            Test-PSSessionConfigurationFile -Verbose -Path $_.ConfigFilePath
        }
    }
}
Test-AllConfigFiles
```

```Output
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Empty_6fd77bf6-e084-4372-bd8a-af3e207354d3.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc
VERBOSE: The member 'AliasDefinitions' must contain the required key 'Description'. Add the require key
to the fileC:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc.
False
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\RestrictedLang_b6bd9474-0a6c-4e06-8722-c2c95bb10d3e.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\RRS_3fb29420-2c87-46e5-a402-e21436331efc.pssc
True
```

Egenskapen **ConfigFilePath** för en session-konfiguration innehåller sökvägen till den session konfigurations fil som används i sessionen, om det finns några.

Om värdet för egenskapen **ConfigFilePath** är ifyllt (är sant), hämtar kommandot (skriver ut) värdet för egenskapen **ConfigFilePath** . Sedan använder den `Test-PSSessionConfigurationFile` cmdlet: en för att testa filen i **ConfigFilePath** -värdet. Den **utförliga** parametern returnerar fil felet när det inte går att köra filen.

## PARAMETRAR

### -Path

Anger sökväg och fil namn för en sessions konfigurations fil (. PSSC). Om du utelämnar sökvägen är standardvärdet den aktuella mappen. Jokertecken stöds, men de måste matcha en enda fil. Du kan också skicka en sökväg till en sessions konfigurations fil `Test-PSSessionConfigurationFile` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka en sökväg till en fil Sök väg för sessionen `Test-PSSessionConfigurationFile` .

## UTDATA

### System. Boolean

## ANTECKNINGAR

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

[WSMan-Provider](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)

