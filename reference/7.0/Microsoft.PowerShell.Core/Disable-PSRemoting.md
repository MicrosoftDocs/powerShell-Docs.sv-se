---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-psremoting?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSRemoting
ms.openlocfilehash: f4fe65ec687ca39c1356dd5c9a590899c8b3789c
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94346011"
---
# Disable-PSRemoting

## SAMMANFATTNING
Förhindrar att PowerShell-slutpunkter tar emot fjärr anslutningar.

## SYNTAX

```
Disable-PSRemoting [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Disable-PSRemoting`Cmdleten blockerar fjärråtkomst till alla PowerShell version 6 och större konfigurationer för sessionens slut punkt på den lokala datorn. Konfigurationen för Windows PowerShell-slutpunkter påverkas inte. Om du vill inaktivera slut punkts konfiguration för Windows PowerShell kör du kommandot inifrån `Disable-PSRemoting` en Windows PowerShell-session.

Använd cmdleten för att återaktivera fjärråtkomst till alla PowerShell version 6 och fler konfigurationer för sessionens slut punkt `Enable-PSRemoting` . Om du vill återaktivera fjärråtkomst till alla Windows PowerShell-sessionens slut punkts konfiguration, kör du i `Enable-PSRemoting` en Windows PowerShell-session.

> [!NOTE]
> Om du vill inaktivera all PowerShell-fjärråtkomst till en lokal Windows-dator måste du köra det här kommandot både från en i PowerShell version 6 eller en senare session och inifrån en Windows PowerShell-session. Windows PowerShell installeras som standard på alla Windows-datorer.

Om du vill inaktivera och återaktivera fjärråtkomst till en speciell sessions slut punkts konfiguration använder du `Enable-PSSessionConfiguration` `Disable-PSSessionConfiguration` cmdletarna och. Om du vill ange specifika åtkomst konfigurationer för enskilda slut punkter använder du `Set-PSSessionConfiguration` cmdleten tillsammans med parametern **AccessMode** . För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).

> [!NOTE]
> Trots att `Disable-PSRemoting` du har kört kan du fortfarande göra loopback-anslutningar på den lokala datorn. En loopback-anslutning är en PowerShell-fjärrsession som kommer från och ansluter till samma lokala dator. Fjärrsessioner från externa källor förblir blockerade. För loopback-anslutningar måste du använda implicita autentiseringsuppgifter tillsammans med parametern **EnableNetworkAccess** . Mer information om loopback-anslutningar finns i [New-PSSession](New-PSSession.md).

Den här cmdleten är endast tillgänglig på Windows-plattformen. Den är inte tillgänglig på Linux-eller macOS-versioner av PowerShell. Starta PowerShell med alternativet **Kör som administratör** för att köra denna cmdlet.

## EXEMPEL

### Exempel 1: förhindra fjärråtkomst till alla PowerShell-sessionsbaserade konfigurationer

Det här exemplet förhindrar fjärråtkomst till alla PowerShell-sessionens slut punkts konfiguration på datorn.

```powershell
Disable-PSRemoting
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### Exempel 2: förhindra fjärråtkomst till alla PowerShell-sessionsbaserade utan bekräftelse meddelande

Det här exemplet förhindrar fjärråtkomst till alla PowerShell-sessionens slut punkts konfiguration på datorn utan att du behöver ange något.

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### Exempel 3: effekterna av att köra denna cmdlet

I det här exemplet visas effekterna av att använda `Disable-PSRemoting` cmdleten. Starta PowerShell med alternativet **Kör som administratör** för att köra den här kommando sekvensen.

När du har inaktiverat sessionerna `New-PSSession` försöker cmdleten skapa en fjärrsession till den lokala datorn (kallas även "loopback"). Eftersom fjärråtkomst är inaktive rad på den lokala datorn Miss lyckas kommandot.

```powershell
Disable-PSRemoting -Force
New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error
 message : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (System.Management.A\u2026tion.RemoteRunspace:RemoteRunspace)
 [New-PSSession], PSRemotingTransportException
+ FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed
```

### Exempel 4: effekterna av att köra denna cmdlet och Enable-PSRemoting

I det här exemplet visas effekterna av sessionens konfigurationer av med hjälp av `Disable-PSRemoting` `Enable-PSRemoting` cmdletarna och.

`Disable-PSRemoting` används för att inaktivera fjärråtkomst till alla PowerShell-sessioner för slut punkts konfiguration. Parametern **Force** förhindrar alla användar meddelanden. `Get-PSSessionConfiguration` `Format-Table` Cmdletarna och visar sessionens konfigurationer på datorn.

Utdata visar att alla fjärran vändare med en nätverks-token nekas åtkomst till slut punkts konfigurationerna. Gruppen Administratörer på den lokala datorn får åtkomst till slut punkts konfigurationerna så länge de ansluter lokalt (kallas även loopback) och använder implicita autentiseringsuppgifter.

```powershell
Disable-PSRemoting -force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Enable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
PowerShell.6.2.0   NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...

Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
PowerShell.6.2.0   NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed ...
```

`Enable-PSRemoting`Cmdleten återaktiverar fjärråtkomst till alla PowerShell-sessionens slut punkts konfiguration på datorn. **Force** -parametern utelämnar alla användar meddelanden och startar om WinRM-tjänsten utan att fråga. De nya utdata visar att **AccessDenied** säkerhets beskrivningar har tagits bort från alla sessionsinställningar.

### Exempel 5: loopback-anslutningar med inaktiverade sessioner med slut punkts konfiguration

Det här exemplet visar hur slut punkts konfigurationen är inaktive rad och hur du gör en lyckad loopback-anslutning till en inaktive rad slut punkt. `Disable-PSRemoting` inaktiverar alla slut punkts konfigurationer för PowerShell-sessioner.

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

```powershell
New-PSSession -ComputerName localhost -ConfigurationName powershell.6 -Credential (Get-Credential)
```

```Output
PowerShell credential request
Enter your credentials.
User: UserName
Password for user UserName: ************

New-PSSession: [localhost] Connecting to remote server localhost failed with the following error message
 : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
```

```powershell
New-PSSession -ComputerName localhost -ConfigurationName powershell.6 -EnableNetworkAccess
```

```Output
 Id Name       Transport ComputerName  ComputerType   State   ConfigurationName   Availability
 -- ----       --------- ------------  ------------   -----   -----------------   ------------
 1  Runspace1  WSMan     localhost     RemoteMachine  Opened  powershell.6           Available
```

Den första användningen av `New-PSSession` försök att skapa en fjärrsession till den lokala datorn. Parametern **ConfigurationName** används för att ange en inaktive rad PowerShell-slutpunkt. Autentiseringsuppgifter skickas explicit till kommandot via parametern för **autentiseringsuppgifter** . Den här typen av anslutning går igenom nätverks stacken och är inte en loopback. Det innebär att anslutnings försöket till den inaktiverade slut punkten Miss lyckas med fel meddelandet **åtkomst nekas** .

Den andra användningen av `New-PSSession` försöker också att skapa en fjärrsession till den lokala datorn.
I det här fallet lyckas det eftersom det är en loopback-anslutning som kringgår nätverks stacken.

En loopback-anslutning skapas när följande villkor uppfylls:

- Dator namnet som ska anslutas till är localhost.
- Inga autentiseringsuppgifter har skickats. Den aktuella inloggade användaren (implicita autentiseringsuppgifter) används för anslutningen.
- Växel parametern **EnableNetworkAccess** används.

Mer information om loopback-anslutningar finns i [New-PSSession](New-PSSession.md) Document.

### Exempel 6: inaktivera alla konfigurationer för PowerShell-fjärrkörning av slut punkter

Det här exemplet visar hur körning av `Disable-PSRemoting` kommandot inte påverkar konfigurationen av Windows PowerShell-slutpunkter. `Get-PSSessionConfiguration` Kör i Windows PowerShell visar alla slut punkts konfigurationer. Vi ser att konfigurationerna för Windows PowerShell-slutpunkten inte är inaktiverade.

```powershell
Disable-PSRemoting -Force
powershell.exe -command 'Get-PSSessionConfiguration'
```

```Output
WARNING: PowerShell remoting has been disabled only for PowerShell 6+ configurations and does not affect
 Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect all PowerShell
 remoting configurations.

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name          : microsoft.powershell
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote
                Management Users AccessAllowed

Name          : microsoft.powershell.workflow
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : microsoft.powershell32
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote
                Management Users AccessAllowed

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

```powershell
powershell.exe -command 'Disable-PSRemoting -Force'
powershell.exe -command 'Get-PSSessionConfiguration'
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting or
Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to members of the
Administrators group on the computer.

Name          : microsoft.powershell
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : microsoft.powershell.workflow
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management
                Users AccessAllowed

Name          : microsoft.powershell32
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators
                AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

Om du vill inaktivera de här slut punkts konfigurationerna `Disable-PSRemoting` måste kommandot köras inifrån en Windows PowerShell-session. Nu kan du `Get-PSSessionConfiguration` köra från Windows PowerShell och se att alla Endpoint-konfigurationer är inaktiverade.

### Exempel 7: förhindra fjärråtkomst till sessionsinställningar som har anpassade säkerhets beskrivningar

Det här exemplet visar att- `Disable-PSRemoting` cmdleten inaktiverar fjärråtkomst till alla sessionsinställningar som innehåller konfigurationer med anpassade säkerhets beskrivningar.

`Register-PSSessionConfiguration`skapar en **Test** testsessions-konfiguration. Parametern **sökväg** anger en konfigurations fil för sessionen som anpassar sessionen. Parametern **ShowSecurityDescriptorUI** visar en dialog ruta som anger behörigheter för konfigurationen av sessionen. I dialog rutan behörigheter skapar vi anpassade fullständiga åtkomst behörigheter för den angivna användaren.

`Get-PSSessionConfiguration` `Format-Table` Cmdletarna och visar sessionens konfigurationer och deras egenskaper. Utdata visar att **testsessionens** konfiguration tillåter interaktiv åtkomst och särskilda behörigheter för den angivna användaren.

`Disable-PSRemoting` inaktiverar fjärråtkomst till alla konfigurationer för sessioner.

```powershell
Register-PSSessionConfiguration -Name Test -FilePath .\TestEndpoint.pssc -ShowSecurityDescriptorUI -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap

Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Wrap
New-PSSession -ComputerName localhost -ConfigurationName Test
```

```Output
Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   BUILTIN\Remote Management Users AccessAllowed
PowerShell.6.2.0   NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   BUILTIN\Remote Management Users AccessAllowed
Test               NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                   User01 AccessAllowed

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name               Permission
----               ----------
PowerShell.6       NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
PowerShell.6.2.0   NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
Test               NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed,
                   BUILTIN\Administrators AccessAllowed, User01 AccessAllowed

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error message
 : Access is denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost -ConfigurationName Test
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (System.Management.A\u2026tion.RemoteRunspace:RemoteRunspace)
 [New-PSSession], PSRemotingTransportException
+ FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed
```

Nu `Get-PSSessionConfiguration` visar-och `Format-Table` -cmdletarna att en **AccessDenied** säkerhets beskrivning för alla nätverks användare läggs till i alla konfigurationer för sessioner, **Test** inklusive konfigurationen för testsession. Även om de andra säkerhets beskrivarna inte ändras har säkerhets beskrivningen "network_deny_all" företräde. Detta illustreras med det försök att använda `New-PSSession` för att ansluta till **Test** konfigurationen av Testsessionen.

### Exempel 8: återaktivera fjärråtkomst till valda sessionsbaserade

Det här exemplet visar hur du återaktiverar fjärråtkomst enbart till valda sessionsinställningar. När du har inaktiverat alla sessionsinställningar, återaktivera vi en speciell session.

`Set-PSSessionConfiguration`Cmdleten används för att ändra konfigurationen för **PowerShell. 6** -sessionen. Parametern **AccessMode** med värdet **fjärran sluten** för fjärråtkomst återaktiverar fjärråtkomst till konfigurationen.

```powershell
Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Set-PSSessionConfiguration -Name PowerShell.6 -AccessMode Remote -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name                 Permission
----                 ----------
PowerShell.6         NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...
PowerShell.6.2.0     NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...

Name                 Permission
----                 ----------
PowerShell.6         NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\ ...
PowerShell.6.2.0     NT AUTHORITY\NETWORK AccessDenied, NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Adm ...
```

## PARAMETRAR

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

### -Force

Tvingar kommandot att köras utan att fråga användaren om bekräftelse.

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

Det går inte att skicka några objekt till denna cmdlet.

## UTDATA

### Inget

Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

Den här cmdleten är endast tillgänglig på Windows-plattformar.

- Om du inaktiverar-sessionsinställningar återställs inte alla ändringar som har gjorts av `Enable-PSRemoting` `Enable-PSSessionConfiguration` cmdletarna eller. Du kan behöva ångra följande ändringar manuellt.

  1. Stoppa och inaktivera WinRM-tjänsten.
  2. Ta bort den lyssnare som accepterar begär Anden på alla IP-adresser.
  3. Inaktivera brand Väggs undantag för WS-Management kommunikation.
  4. Återställ värdet för LocalAccountTokenFilterPolicy till 0, vilket begränsar fjärråtkomst till medlemmar i gruppen Administratörer på datorn.

- En sessions slut punkts konfiguration är en grupp inställningar som definierar miljön för en session.
  Varje session som ansluter till datorn måste använda en av sessionens slut punkts konfigurationer som är registrerade på datorn. Genom att neka fjärråtkomst till alla konfigurationer för sessionens slut punkt hindrar du effektivt att fjärranslutna användare upprättar sessioner som ansluter till datorn.

## RELATERADE LÄNKAR

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSRemoting](Enable-PSRemoting.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSession](New-PSSession.md)

[Registrera – PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Avregistrera-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan-Provider](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)
