---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Starta Windows PowerShell 2.0-motorn
ms.openlocfilehash: 824077008d2dcfd707e977d2112f0882d07a8aca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030442"
---
# <a name="starting-the-windows-powershell-20-engine"></a>Starta Windows PowerShell 2.0-motorn

I det här avsnittet beskrivs hur du startar Windows PowerShell 2,0-motorn på Windows 8,1, Windows Server 2012 R2, Windows 8 och Windows Server 2012, inklusive Windows PowerShell 2,0-motorn och på andra datorer där Windows PowerShell 2,0, Windows PowerShell 3,0 och Windows PowerShell 4,0 installeras.

Windows PowerShell 4,0 och Windows PowerShell 3,0 är utformade för att vara bakåtkompatibla med Windows PowerShell 2,0. Cmdlets, providers, snapin-moduler, moduler och skript som skrivits för Windows PowerShell 2,0 körs oförändrade i Windows PowerShell 4,0 och Windows PowerShell 3,0. Men på grund av en ändring i aktiverings principen för körning i Microsoft .NET Framework 4, kan Windows PowerShell-värdar som har skrivits för Windows PowerShell 2,0 och kompilerats med CLR (Common Language Runtime) 2,0 inte köras utan ändringar i Windows PowerShell 3,0 eller Windows PowerShell 4,0, som kompileras med CLR 4,0. Windows PowerShell 2,0-motorn är avsedd att användas endast när ett befintligt skript eller värd program inte kan köras eftersom det är inkompatibelt med Windows PowerShell 4,0, Windows PowerShell 3,0 eller Microsoft .NET Framework 4. Sådana fall förväntas vara ovanliga.

Många program som kräver Windows PowerShell 2,0-motorn startar automatiskt. Dessa instruktioner ingår i de sällsynta situationer där du måste starta motorn manuellt.

## <a name="installing-and-enabling-required-programs"></a>Installera och aktivera nödvändiga program

Innan du startar Windows PowerShell 2,0-motorn aktiverar du Windows PowerShell 2,0-motorn och Microsoft .NET Framework 3,5 med Service Pack 1. Instruktioner finns i [Installera Windows PowerShell](../install/Installing-Windows-PowerShell.md).

System där Windows Management Framework 4,0 eller Windows Management Framework 3,0 har installerats har alla nödvändiga komponenter. Ingen ytterligare konfiguration krävs. Information om hur du installerar [Windows Management framework 4,0](https://go.microsoft.com/fwlink/?LinkID=293881) eller Windows management Framework 3,0 finns i [Installera Windows PowerShell](../install/Installing-Windows-PowerShell.md).

## <a name="how-to-start-the-windows-powershell-20-engine"></a>Starta Windows PowerShell 2,0-motorn

När du startar Windows PowerShell startas den senaste versionen som standard. Starta Windows PowerShell med Windows PowerShell 2,0-motorn med hjälp av versions parametern för PowerShell. exe. Du kan köra kommandot i valfri kommando tolk, inklusive Windows PowerShell och cmd. exe.

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a>Så här startar du en fjärrsession med Windows PowerShell 2,0-motorn

Om du vill köra Windows PowerShell 2,0-motorn i en fjärrsession skapar du en sessionsnyckel (kallas även "slut punkt") på den fjärrdator som läser in Windows PowerShell 2,0-motorn. Konfigurationen av sessionen sparas på fjärrdatorn och kan användas av alla auktoriserade användare för att skapa sessioner som använder Windows PowerShell 2,0-motorn.

Detta är en avancerad uppgift som vanligt vis utförs av en system administratör.

I följande procedur används parametern **PSVersion** i cmdleten [register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) för att skapa en sessionsnyckel som använder Windows PowerShell 2,0-motorn. Du kan också använda parametern **PowerShellVersion** för [New-PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866) -cmdlet: en för att skapa en konfigurations fil för sessionen för en session som läser in Windows PowerShell 2,0-motorn och du kan använda parametern **PSVersion** för parametern [set-PSSessionConfiguration](https://technet.microsoft.com/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) för att ändra en sessions konfiguration till att använda Windows PowerShell 2,0-motorn.

Mer information om konfigurationsfiler för sessioner finns [about_Session_Configuration_Files](https://technet.microsoft.com/library/c7217447-1ebf-477b-a8ef-4dbe9a1473b8). Information om sessionsdata, inklusive konfiguration och säkerhet, finns [about_Session_Configurations [V4]](https://technet.microsoft.com/library/a2fbe12a-350c-4d04-be50-24102824e3ab).

#### <a name="to-start-a-remote-windows-powershell-20-session"></a>Starta en fjärran sluten Windows PowerShell 2,0-session

1. Om du vill skapa en sessionsnyckel som kräver Windows PowerShell 2,0-motorn använder du parametern **PSVersion** i cmdleten [register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) med värdet "2,0". Kör det här kommandot på datorn på "Server sidan" eller ta emot slutet av anslutningen.

   Följande exempel kommando skapar PS2-sessionen på Server01-datorn. Kör det här kommandot genom att starta Windows PowerShell 4,0 eller Windows PowerShell 3,0 med alternativet **Kör som administratör** .

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

2. Om du vill skapa en-session på Server01-datorn som använder PS2-sessionen använder du parametern **ConfigurationName** för cmdlet: ar som skapar en fjärrsession, till exempel cmdleten [New-PSSession](https://technet.microsoft.com/library/76f6628c-054c-4eda-ba7a-a6f28daaa26f) .

   När en session som använder sessionen startar läses Windows PowerShell 2,0-motorn automatiskt in i sessionen.

   Följande kommando startar en-session på Server01-datorn som använder PS2-sessionen. Kommandot sparar sessionen i variabeln $s.

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a>Så här startar du ett bakgrunds jobb med Windows PowerShell 2,0-motorn

Om du vill starta ett bakgrunds jobb med Windows PowerShell 2,0-motorn använder du parametern **PSVersion** i cmdleten [Start-Job](https://technet.microsoft.com/library/2bc04935-0deb-4ec0-b856-d7290cca6442) .

Följande kommando startar ett bakgrunds jobb med Windows PowerShell 2,0-motorn

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

Mer information om bakgrunds jobb finns [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).
