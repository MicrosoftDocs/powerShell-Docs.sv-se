---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Starta Windows PowerShell 2.0-motorn
ms.assetid: edafc2fa-7576-49c2-bbba-9336f4bcfc28
ms.openlocfilehash: f5dd01cd93095fe15cc7e57f97f4b2920e580c22
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086518"
---
# <a name="starting-the-windows-powershell-20-engine"></a>Starta Windows PowerShell 2.0-motorn

Det här avsnittet beskrivs hur du startar Windows PowerShell 2.0-motorn på Windows 8.1, Windows Server 2012 R2, Windows 8 och Windows Server 2012, bland annat Windows PowerShell 2.0-motorn och på andra system på vilka Windows PowerShell 2.0, Windows PowerShell 3.0 och Windows PowerShell 4.0 har installerats.

Windows PowerShell 4.0 och Windows PowerShell 3.0 är avsedda att vara bakåtkompatibla med Windows PowerShell 2.0. Cmdlet: ar, leverantörer, snapin-moduler, moduler och skript som har skrivits för Windows PowerShell 2.0 kör oförändrad i Windows PowerShell 4.0 och Windows PowerShell 3.0. Men på grund av en ändring i principen runtime aktivering i Microsoft .NET Framework 4, även Windows PowerShell-värd program som har skrivits för Windows PowerShell 2.0 och kompileras med Runtime CLR (Common Language) 2.0 kan inte köras utan ändringar i Windows PowerShell 3.0 eller Windows PowerShell 4.0, som kompileras med CLR 4.0. Windows PowerShell 2.0-motorn är avsedd att användas endast när ett befintligt skript eller värdprogrammet kan inte köras eftersom det är inte kompatibel med Windows PowerShell 4.0, Windows PowerShell 3.0 eller Microsoft .NET Framework 4. Sådana fall förväntas vara sällsynt.

Många program som kräver Windows PowerShell 2.0-motorn startas den automatiskt. Dessa anvisningar ingår i ovanliga situationer där du behöver att starta motorn manuellt.

## <a name="installing-and-enabling-required-programs"></a>Installera och aktivera nödvändiga program

Aktivera Windows PowerShell 2.0-motorn och Microsoft .NET Framework 3.5 med Service Pack 1 innan du startar Windows PowerShell 2.0-motorn. Anvisningar finns i [installera Windows PowerShell](../install/Installing-Windows-PowerShell.md).

System har alla de nödvändiga komponenterna på vilka Windows Management Framework 4.0 eller Windows Management Framework 3.0 är installerat. Det krävs ingen ytterligare konfiguration. Information om hur du installerar [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/?LinkID=293881) eller Windows Management Framework 3.0 finns i [installera Windows PowerShell](../install/Installing-Windows-PowerShell.md).

## <a name="how-to-start-the-windows-powershell-20-engine"></a>Så här startar du Windows PowerShell 2.0-motorn

När du startar Windows PowerShell startar den senaste versionen som standard. Starta Windows PowerShell med Windows PowerShell 2.0-motorn med parametern Version av PowerShell.exe. Du kan köra kommandot vid en kommandotolk, inklusive Windows PowerShell och Cmd.exe.

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a>Hur du startar en fjärrsession med Windows PowerShell 2.0-motorn

Skapa en sessionskonfiguration (kallas även en ”slutpunkt”) för att köra Windows PowerShell 2.0-motorn i en fjärrsession på fjärrdatorn som läser in Windows PowerShell 2.0-motorn. Sessionskonfigurationen sparas på fjärrdatorn och kan användas av alla behöriga användare för att skapa sessioner som använder Windows PowerShell 2.0-motorn.

Det här är en avancerad uppgift som vanligtvis utförs av en systemadministratör.

I följande procedur används den **PSVersion** -parametern för den [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) cmdlet för att skapa en sessionskonfiguration som använder Windows PowerShell 2.0-motorn. Du kan också använda den **PowerShellVersion** -parametern för den [New PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866) cmdlet för att skapa en konfigurationsfil för sessionen för en session som läser in Windows PowerShell 2.0-motorn och Du kan använda den **PSVersion** -parametern för den [Set-PSSessionConfiguration](https://technet.microsoft.com/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) parameter för att ändra en sessionskonfiguration om du vill använda Windows PowerShell 2.0-motorn.

Läs mer om sessionen konfigurationsfiler [about_Session_Configuration_Files](https://technet.microsoft.com/library/c7217447-1ebf-477b-a8ef-4dbe9a1473b8). Information om sessionskonfigurationer, inklusive installation och säkerhet finns i [about_Session_Configurations [v4]](https://technet.microsoft.com/library/a2fbe12a-350c-4d04-be50-24102824e3ab).

#### <a name="to-start-a-remote-windows-powershell-20-session"></a>Att starta en fjärrsession med Windows PowerShell 2.0

1. Du kan skapa en sessionskonfiguration som kräver Windows PowerShell 2.0-motorn med den **PSVersion** -parametern för den [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) cmdlet med värdet ”2.0”. Kör kommandot på datorn på ”serversidan” eller mottagande änden av anslutningen.

   Kommandot i följande exempel skapar PS2-sessionskonfiguration på Server01-dator. Om du vill köra det här kommandot, starta Windows PowerShell 4.0 eller Windows PowerShell 3.0 med den **kör som administratör** alternativet.

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

2. Du kan skapa en session på datorn Server01 som använder sessionskonfigurationen PS2 med den **ConfigurationName** -parametern för cmdletar som skapar en fjärrsession som den [New-PSSession](https://technet.microsoft.com/library/76f6628c-054c-4eda-ba7a-a6f28daaa26f) cmdlet.

   När en session som använder sessionskonfigurationen startar Windows PowerShell 2.0-motorn automatiskt att läsas in i sessionen.

   Följande kommando startar en session på datorn Server01 som använder sessionskonfigurationen PS2. Kommandot sparar sessionen i variabeln $s.

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a>Hur du startar ett bakgrundsjobb med Windows PowerShell 2.0-motorn

Starta ett bakgrundsjobb med Windows PowerShell 2.0-motorn med den **PSVersion** -parametern för den [Start-Job](https://technet.microsoft.com/library/2bc04935-0deb-4ec0-b856-d7290cca6442) cmdlet.

Följande kommando startar ett bakgrundsjobb med Windows PowerShell 2.0-motorn

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

Mer information om bakgrundsjobb finns i [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).