---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-psremoting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSRemoting
ms.openlocfilehash: 3a281786f99b2a46d0aeb9785480f02b35b2b433
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263667"
---
# Disable-PSRemoting

## SAMMANFATTNING
Förhindrar att PowerShell-slutpunkter tar emot fjärr anslutningar.

## SYNTAX

```
Disable-PSRemoting [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Disable-PSRemoting`Cmdleten blockerar fjärråtkomst till alla Windows PowerShell-sessionens slut punkts konfiguration på den lokala datorn. Detta inkluderar alla slut punkter som skapats av PowerShell 6 eller senare.

Använd cmdleten för att återaktivera fjärråtkomst till alla sessioner `Enable-PSRemoting` . Detta inkluderar alla slut punkter som skapats av PowerShell 6 eller senare. Använd parametern **AccessMode** för cmdleten om du vill aktivera fjärråtkomst till valda sessionsbaserade konfigurationer `Set-PSSessionConfiguration` .
Du kan också använda `Enable-PSSessionConfiguration` `Disable-PSSessionConfiguration` cmdletarna och för att aktivera och inaktivera sessionsinställningar för alla användare. För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).

> [!NOTE]
> Trots att `Disable-PSRemoting` du har kört kan du fortfarande göra loopback-anslutningar på den lokala datorn. En loopback-anslutning är en PowerShell-fjärrsession som kommer från och ansluter till samma lokala dator. Fjärrsessioner från externa källor förblir blockerade. För loopback-anslutningar måste du använda implicita autentiseringsuppgifter tillsammans med parametern **EnableNetworkAccess** . Mer information om loopback-anslutningar finns i [New-PSSession](New-PSSession.md).

Om du vill köra den här cmdleten startar du Windows PowerShell med alternativet **Kör som administratör** .

## EXEMPEL

### Exempel 1: förhindra fjärråtkomst till alla konfigurationer av sessioner

Det här exemplet förhindrar fjärråtkomst till alla PowerShell-sessionens slut punkts konfiguration på datorn.

```powershell
Disable-PSRemoting
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these
 steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.
```

### Exempel 2: förhindra fjärråtkomst till alla datorkonfigurationer utan bekräftelse meddelande

Det här exemplet förhindrar fjärråtkomst till alla PowerShell-sessionens slut punkts konfiguration på datorn utan att du behöver ange något.

```powershell
Disable-PSRemoting -Force
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these
 steps:
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
New-PSSession -ComputerName localhost
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
Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell32        NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
WithProfile                   NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed

Name                          Permission
----                          ----------
microsoft.powershell          BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow BUILTIN\Administrators AccessAllowed
microsoft.powershell32        BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       BUILTIN\Administrators AccessAllowed
WithProfile                   BUILTIN\Administrators AccessAllowed
```

`Enable-PSRemoting`Cmdleten återaktiverar fjärråtkomst till alla PowerShell-sessionens slut punkts konfiguration på datorn. **Force** -parametern utelämnar alla användar meddelanden och startar om WinRM-tjänsten utan att fråga. De nya utdata visar att **AccessDenied** säkerhets beskrivningar har tagits bort från alla sessionsinställningar.

### Exempel 5: loopback-anslutningar med inaktiverade sessioner med slut punkts konfiguration

Det här exemplet visar hur slut punkts konfigurationen är inaktive rad och hur du gör en lyckad loopback-anslutning till en inaktive rad slut punkt. `Disable-PSRemoting` inaktiverar alla slut punkts konfigurationer för PowerShell-sessioner.

```powershell
Disable-PSRemoting -Force
New-PSSession -ComputerName localhost
```

```Output
WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

New-PSSession : [localhost] Connecting to remote server localhost failed with the following error message : Access is
denied. For more information, see the about_Remote_Troubleshooting Help topic.
At line:1 char:1
+ New-PSSession -ComputerName localhost
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [New-PSSession], PSRemotin
   gTransportException
    + FullyQualifiedErrorId : AccessDenied,PSSessionOpenFailed

```

```powershell
New-PSSession -ComputerName localhost -EnableNetworkAccess
```

```Output
 Id Name       Transport ComputerName  ComputerType   State   ConfigurationName   Availability
 -- ----       --------- ------------  ------------   -----   -----------------   ------------
 1  Runspace1  WSMan     localhost     RemoteMachine  Opened  powershell.6           Available
```

Den första användningen av `New-PSSession` försök att skapa en fjärrsession till den lokala datorn. Den här typen av anslutning går igenom nätverks stacken och är inte en loopback. Det innebär att anslutnings försöket till den inaktiverade slut punkten Miss lyckas med fel meddelandet **åtkomst nekas** .

Den andra användningen av `New-PSSession` försöker också att skapa en fjärrsession till den lokala datorn.
I det här fallet lyckas det eftersom det är en loopback-anslutning som kringgår nätverks stacken.

En loopback-anslutning skapas när följande villkor uppfylls:

- Dator namnet som ska anslutas till är localhost.
- Inga autentiseringsuppgifter har skickats. Den aktuella inloggade användaren (implicita autentiseringsuppgifter) används för anslutningen.
- Växel parametern **EnableNetworkAccess** används.

Mer information om loopback-anslutningar finns i [New-PSSession](New-PSSession.md) Document.

### Exempel 6: förhindra fjärråtkomst till sessionsinställningar som har anpassade säkerhets beskrivningar

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
Name                          Permission
----                          ----------
microsoft.powershell          BUILTIN\Administrators AccessAllowed
Test                          NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
DOMAIN01\User01 AccessAllowed

WARNING: Disabling the session configurations does not undo all the changes made by the Enable-PSRemoting
 or Enable-PSSessionConfiguration cmdlet. You might have to manually undo the changes by following these steps:
    1. Stop and disable the WinRM service.
    2. Delete the listener that accepts requests on any IP address.
    3. Disable the firewall exceptions for WS-Management communications.
    4. Restore the value of the LocalAccountTokenFilterPolicy to 0, which restricts remote access to
       members of the Administrators group on the computer.

Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
Test                          NT AUTHORITY\NETWORK AccessDenied, NTAUTHORITY\INTERACTIVE AccessAllowed,
BUILTIN\Administrators AccessAllowed, DOMAIN01\User01 AccessAllowed


[Server01] Connecting to remote server failed with the following error message : Access is denied. For more information, see the about_Rem
ote_Troubleshooting Help topic.
+ CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
+ FullyQualifiedErrorId : PSSessionOpenFailed
```

Nu `Get-PSSessionConfiguration` visar-och `Format-Table` -cmdletarna att en **AccessDenied** säkerhets beskrivning för alla nätverks användare läggs till i alla konfigurationer för sessioner, **Test** inklusive konfigurationen för testsession. Även om de andra säkerhets beskrivarna inte ändras har säkerhets beskrivningen "network_deny_all" företräde. Detta illustreras med det försök att använda `New-PSSession` för att ansluta till **Test** konfigurationen av Testsessionen.

### Exempel 7: återaktivera fjärråtkomst till valda sessionsbaserade

Det här exemplet visar hur du återaktiverar fjärråtkomst enbart till valda sessionsinställningar. När du har inaktiverat alla sessionsinställningar, återaktivera vi en speciell session.

`Set-PSSessionConfiguration`Cmdleten används för att ändra **Microsoft.** Konfiguration av servermanager-session. Parametern **AccessMode** med värdet **fjärran sluten** för fjärråtkomst återaktiverar fjärråtkomst till konfigurationen.

```powershell
Disable-PSRemoting -Force
Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Set-PSSessionConfiguration -Name Microsoft.ServerManager -AccessMode Remote -Force
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

Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell32        NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
WithProfile                   NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed

Name                          Permission
----                          ----------
microsoft.powershell          NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell.workflow NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell32        NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.ServerManager       BUILTIN\Administrators AccessAllowed
WithProfile                   NT AUTHORITY\NETWORK AccessDenied, BUILTIN\Administrators AccessAllowed
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

- Om du inaktiverar-sessionsinställningar återställs inte alla ändringar som har gjorts av `Enable-PSRemoting` `Enable-PSSessionConfiguration` cmdletarna eller. Du kan behöva ångra följande ändringar manuellt.

  1. Stoppa och inaktivera WinRM-tjänsten.
  2. Ta bort den lyssnare som accepterar begär Anden på alla IP-adresser.
  3. Inaktivera brand Väggs undantag för WS-Management kommunikation.
  4. Återställ värdet för LocalAccountTokenFilterPolicy till 0, vilket begränsar fjärråtkomst till medlemmar i gruppen Administratörer på datorn.

  En sessions konfiguration är en grupp med inställningar som definierar miljön för en session. Varje session som ansluter till datorn måste använda en av de sessionsbaserade som har registrerats på datorn. Genom att neka fjärråtkomst till alla sessioner förhindrar du att fjärranslutna användare upprättar sessioner som ansluter till datorn.

  I Windows PowerShell 2,0 `Disable-PSRemoting` lägger till en Deny_All post i säkerhets beskrivarna för alla konfigurationer av sessioner. Den här inställningen förhindrar att alla användare skapar användar hanterade sessioner till den lokala datorn. I Windows PowerShell 3,0 `Disable-PSRemoting` lägger till en Network_Deny_All post i säkerhets beskrivarna för alla konfigurationer av sessioner. Den här inställningen förhindrar användare på andra datorer från att skapa användar hanterade sessioner på den lokala datorn, men tillåter användare av den lokala datorn att skapa användar hanterade loopback-sessioner.

  I Windows PowerShell 2,0 `Disable-PSRemoting` är motsvarigheten till `Disable-PSSessionConfiguration -Name *` . I Windows PowerShell 3,0 och senare versioner `Disable-PSRemoting` är motsvarigheten till `Set-PSSessionConfiguration -Name \<Configuration name\> -AccessMode Local`

## RELATERADE LÄNKAR

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSRemoting](Enable-PSRemoting.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSession](New-PSSession.md)

[Registrera – PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Avregistrera-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan-Provider](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)
