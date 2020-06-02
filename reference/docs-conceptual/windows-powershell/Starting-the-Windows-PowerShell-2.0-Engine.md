---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Använda Windows PowerShell 2,0-motorn
ms.openlocfilehash: e00fb71c7fc32f5b48bc17ef5b25f910a846c893
ms.sourcegitcommit: 1748b2bdfae81d98097962c6c25c25df4bced1d8
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/01/2020
ms.locfileid: "84262621"
---
# <a name="using-the-windows-powershell-20-engine"></a>Använda Windows PowerShell 2,0-motorn

Windows PowerShell är utformat för att vara bakåtkompatibelt med tidigare versioner. Cmdlets, providers, snapin-moduler, moduler och skript som skrivits för Windows PowerShell 2,0 körs oförändrade i nyare versioner av Windows PowerShell. Microsoft .NET Framework 4 ändrade dock aktiverings principen för körning.
Windows PowerShell-värdprogram som skrivits för Windows PowerShell 2,0 och kompileras med CLR (Common Language Runtime) 2,0 kan inte köras utan ändringar i nya versioner Windows PowerShell som kompileras med CLR 4,0 (eller högre).

Windows PowerShell 2,0-motorn är avsedd att användas endast när ett befintligt skript eller värd program inte kan köras eftersom det är inkompatibelt med Windows PowerShell 5,1. Exempel på detta är äldre versioner av Exchange eller SQL Server moduler. Sådana fall förväntas vara ovanliga.

Många program som kräver Windows PowerShell 2,0-motorn startar automatiskt. Dessa instruktioner ingår i de sällsynta situationer där du måste starta motorn manuellt.

## <a name="deprecation-and-security-concerns"></a>Utfasnings-och säkerhets problem

Windows PowerShell 2,0 föråldrades i augusti 2017. Mer information finns i [meddelandet][] på PowerShell-bloggen.

Windows PowerShell 2,0 saknar en betydande mängd härdnings-och säkerhetsfunktioner som har lagts till i version 3, 4 och 5. Vi rekommenderar starkt att användarna inte använder den om de kan hjälpa dem. Mer information finns i [jämförelse av gränssnitts-och skript språk säkerhet][] och [PowerShell ♥ blått-teamet][blueteam].

## <a name="installing-and-enabling-required-programs"></a>Installera och aktivera nödvändiga program

Innan du startar Windows PowerShell 2,0-motorn aktiverar du Windows PowerShell 2,0-motorn och Microsoft .NET Framework 3,5 med Service Pack 1. Instruktioner finns i [Installera Windows PowerShell][].

System där Windows Management Framework 3,0 eller senare har installerats har alla nödvändiga komponenter. Ingen ytterligare konfiguration krävs. Information om hur du installerar Windows Management Framework finns i [Installera och konfigurera WMF][].

## <a name="how-to-start-the-windows-powershell-20-engine"></a>Starta Windows PowerShell 2,0-motorn

När du startar Windows PowerShell startas den senaste versionen som standard. Starta Windows PowerShell med Windows PowerShell 2,0-motorn med hjälp av parametern version i `PowerShell.exe` . Du kan köra kommandot i valfri kommando tolk, inklusive Windows PowerShell och cmd. exe.

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a>Så här startar du en fjärrsession med Windows PowerShell 2,0-motorn

Om du vill köra Windows PowerShell 2,0-motorn i en fjärran sluten session skapar du en sessionsnyckel (kallas även _slut punkt_) på den fjärrdator som läser in Windows PowerShell 2,0-motorn. Konfigurationen av sessionen sparas på fjärrdatorn och kan användas av alla auktoriserade användare för att skapa sessioner som använder Windows PowerShell 2,0-motorn.

Detta är en avancerad uppgift som vanligt vis utförs av en system administratör.

I följande procedur används parametern **PSVersion** i cmdleten [register-PSSessionConfiguration][] för att skapa en sessionsnyckel som använder Windows PowerShell 2,0-motorn. Du kan också använda parametern **PowerShellVersion** för [New-PSSessionConfigurationFile][] -cmdlet: en för att skapa en konfigurations fil för sessionen för en session som läser in Windows PowerShell 2,0-motorn och du kan använda parametern **PSVersion** för parametern [set-PSSessionConfiguration][] för att ändra en sessions konfiguration till att använda Windows PowerShell 2,0-motorn.

Mer information om konfigurationsfiler för sessioner finns [about_Session_Configuration_Files][].
Information om sessionsdata, inklusive konfiguration och säkerhet, finns [about_Session_Configurations][].

### <a name="to-start-a-remote-windows-powershell-20-session"></a>Starta en fjärran sluten Windows PowerShell 2,0-session

1. Om du vill skapa en sessionsnyckel som kräver Windows PowerShell 2,0-motorn använder du parametern **PSVersion** för `Register-PSSessionConfiguration` cmdleten med värdet `2.0` .
   Kör det här kommandot på datorn på "Server sidan" eller ta emot slutet av anslutningen.

   Följande exempel kommando skapar PS2-sessionen på Server01-datorn. Starta Windows PowerShell med alternativet **Kör som administratör** för att köra det här kommandot.

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

1. Om du vill skapa en session på Server01-datorn som använder PS2-sessionen använder du parametern **ConfigurationName** för cmdlet: ar som skapar en fjärrsession, till exempel cmdleten "New-PSSession".

   När en session som använder sessionen startar läses Windows PowerShell 2,0-motorn automatiskt in i sessionen.

   Följande kommando startar en-session på Server01-datorn som använder PS2-sessionen. Kommandot sparar sessionen i `$s` variabeln.

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a>Så här startar du ett bakgrunds jobb med Windows PowerShell 2,0-motorn

Om du vill starta ett bakgrunds jobb med Windows PowerShell 2,0-motorn använder du parametern **PSVersion** i cmdleten [Start-Job][] .

Följande kommando startar ett bakgrunds jobb med Windows PowerShell 2,0-motorn

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

Mer information om bakgrunds jobb finns [about_Jobs][].

<!-- link references -->
[känna]: https://devblogs.microsoft.com/powershell/windows-powershell-2-0-deprecation/
[Jämförelse mellan gränssnitts-och skript språk säkerhet]: https://devblogs.microsoft.com/powershell/a-comparison-of-shell-and-scripting-language-security/
[blueteam]: https://devblogs.microsoft.com/powershell/powershell-the-blue-team/
[Installera Windows PowerShell]: install/Installing-Windows-PowerShell.md
[Installera och konfigurera WMF]: wmf/setup/install-configure.md
[Registrera – PSSessionConfiguration]: /powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration
[New-PSSessionConfigurationFile]: /powershell/module/Microsoft.PowerShell.Core/New-PSSessionConfiguration
[Set-PSSessionConfiguration]: /powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration
[about_Session_Configuration_Files]: /powershell/module/Microsoft.PowerShell.Core/about/about_Session_Configuration_Files
[about_Session_Configurations]: /powershell/module/Microsoft.PowerShell.Core/about/about_Session_Configurations
[Start – jobb]: /powershell/module/microsoft.powershell.core/start-job
[about_Jobs]: /powershell/module/microsoft.powershell.core/about/about_jobs
