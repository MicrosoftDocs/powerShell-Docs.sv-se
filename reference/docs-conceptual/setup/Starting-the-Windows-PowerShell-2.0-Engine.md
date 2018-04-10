---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Starta Windows PowerShell 2.0-motorn
ms.assetid: edafc2fa-7576-49c2-bbba-9336f4bcfc28
ms.openlocfilehash: 585e1003554362d11fe99414bd3e80c497799a88
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="starting-the-windows-powershell-20-engine"></a>Starta Windows PowerShell 2.0-motorn

Det här avsnittet beskrivs hur du startar Windows PowerShell 2.0-motorn på Windows 8.1, Windows Server 2012 R2, Windows 8 och Windows Server 2012, bland annat Windows PowerShell 2.0-motorn och på andra datorer på vilka Windows PowerShell 2.0, Windows PowerShell 3.0 och Windows PowerShell 4.0 är installerat.

Windows PowerShell 4.0 och Windows PowerShell 3.0 är avsedda att vara bakåtkompatibla med Windows PowerShell 2.0. Cmdlets, providers, snapin-moduler, moduler och skript som är skrivna för Windows PowerShell 2.0 kör oförändrad i Windows PowerShell 4.0 och Windows PowerShell 3.0. Men på grund av en ändring i principen runtime aktivering i Microsoft .NET Framework 4 även Windows PowerShell värd för program som har skrivits för Windows PowerShell 2.0 och kompileras med Runtime CLR (Common Language) 2.0 kan inte köras utan ändringar i Windows PowerShell 3.0 eller Windows PowerShell 4.0, som kompileras med CLR-4.0. Windows PowerShell 2.0-motorn är avsedd att användas endast när ett befintligt skript eller värdprogrammet kan inte köras eftersom den inte är kompatibel med Windows PowerShell 4.0, Windows PowerShell 3.0 eller Microsoft .NET Framework 4. Sådana fall förväntas vara sällsynt.

Många program som kräver Windows PowerShell 2.0-motorn startas den automatiskt. Dessa instruktioner ingår i ovanliga situationer där du behöver starta motorn manuellt.

## <a name="installing-and-enabling-required-programs"></a>Installera och aktivera program som behövs

Aktivera Windows PowerShell 2.0-motorn och Microsoft .NET Framework 3.5 med Service Pack 1 innan du startar Windows PowerShell 2.0-motorn. Instruktioner finns i [installera Windows PowerShell](Installing-Windows-PowerShell.md).

System där [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) eller Windows Management Framework 3.0 är installerat har alla nödvändiga komponenter. Det krävs ingen ytterligare konfiguration. Information om hur du installerar [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) eller Windows Management Framework 3.0 finns [installera Windows PowerShell](Installing-Windows-PowerShell.md).

## <a name="how-to-start-the-windows-powershell-20-engine"></a>Så här startar du Windows PowerShell 2.0-motorn

Som standard när du startar Windows PowerShell startar den senaste versionen. Om du vill starta Windows PowerShell med Windows PowerShell 2.0-motorn, använder du parametern Version av PowerShell.exe. Du kan köra kommandot i en kommandotolk, inklusive Windows PowerShell och Cmd.exe.

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a>Hur du startar en fjärrsession med Windows PowerShell 2.0-motorn

Skapa en sessionskonfiguration (även kallat en ”slutpunkt”) för att köra Windows PowerShell 2.0-motorn i en fjärrsession på fjärrdatorn som läser in Windows PowerShell 2.0-motorn. Sessionskonfigurationen sparas på fjärrdatorn och kan användas av alla behöriga användare för att skapa sessioner som använder Windows PowerShell 2.0-motorn.

Detta är en avancerad uppgift som vanligtvis utförs av en systemadministratör.

I följande procedur används den **PSVersion** parameter för den [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) för att skapa en sessionskonfiguration som använder Windows PowerShell 2.0-motorn. Du kan också använda den **PowerShellVersion** parameter för den [ny PSSessionConfigurationFile](https://technet.microsoft.com/en-us/library/5f3e3633-6e90-479c-aea9-ba45a1954866) för att skapa en konfigurationsfil för sessionen för en session som läser in Windows PowerShell 2.0-motorn och Du kan använda den **PSVersion** parameter för den [Set-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) parametern för att ändra en sessionskonfiguration om du vill använda Windows PowerShell 2.0-motorn.

Mer information om sessionen konfigurationsfiler finns [about_Session_Configuration_Files](https://technet.microsoft.com/en-us/library/c7217447-1ebf-477b-a8ef-4dbe9a1473b8). Information om sessionskonfigurationer, inklusive installation och säkerhet, se [about_Session_Configurations [v4]](https://technet.microsoft.com/en-us/library/a2fbe12a-350c-4d04-be50-24102824e3ab).

#### <a name="to-start-a-remote-windows-powershell-20-session"></a>Att starta en fjärrsession i Windows PowerShell 2.0

1. Så här skapar du en sessionskonfiguration som kräver Windows PowerShell 2.0-motorn på **PSVersion** parameter för den [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) cmdlet med värdet ”2.0”. Kör kommandot på datorn i ”serversidan” eller mottagande slutet av anslutningen.

   Följande exempelkommando skapar PS2-sessionskonfiguration på Server01-datorn. Om du vill köra det här kommandot, starta Windows PowerShell 4.0 eller Windows PowerShell 3.0 med den **kör som administratör** alternativet.

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

2. Använd för att skapa en session på datorn Server01 som använder sessionskonfigurationen PS2 den **ConfigurationName** parametern för cmdletar som skapar en fjärrsession som den [New-PSSession](https://technet.microsoft.com/en-us/library/76f6628c-054c-4eda-ba7a-a6f28daaa26f) cmdlet.

   När en session som använder sessionskonfigurationen startar laddas automatiskt Windows PowerShell 2.0-motorn i sessionen.

   Följande kommando startar en session på datorn Server01 som använder sessionskonfigurationen PS2. Kommandot sparar sessionen i variabeln $s.

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a>Starta ett bakgrundsjobb med Windows PowerShell 2.0-motorn

Starta ett bakgrundsjobb med Windows PowerShell 2.0 motorn med den **PSVersion** parameter för den [Start-Job](https://technet.microsoft.com/en-us/library/2bc04935-0deb-4ec0-b856-d7290cca6442) cmdlet.

Följande kommando startar bakgrunden med Windows PowerShell 2.0-motorn

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

Mer information om bakgrundsjobb finns [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).