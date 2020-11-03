---
description: Beskriver funktionerna i Windows PowerShell för PowerShell 7.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_powershell_compatibility?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_PowerShell_Compatibility
ms.openlocfilehash: 522c9d2169e49584915450813ad28dfc5e0d5ca2
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270135"
---
# <a name="about-windows-powershell-compatibility"></a>Om Windows PowerShell-kompatibilitet

## <a name="short-description"></a>KORT BESKRIVNING

Beskriver funktionerna i Windows PowerShell för PowerShell 7.

## <a name="long-description"></a>LÅNG BESKRIVNING

Om module-manifestet inte anger att modulen är kompatibel med PowerShell Core läses modulerna i `%windir%\system32\WindowsPowerShell\v1.0\Modules` mappen in i en Windows powershell 5,1-process med Windows PowerShell-kompatibilitet.

### <a name="using-the-compatibility-feature"></a>Använda funktionen kompatibilitet

När den första modulen importeras med funktionen Windows PowerShell-kompatibilitet, skapar PowerShell en fjärrsession med namnet `WinPSCompatSession` som körs i en bakgrunds process i Windows powershell 5,1. Den här processen skapas när funktionen kompatibilitet importerar den första modulen. Processen stängs när den sista modulen tas bort (med `Remove-Module` ) eller när PowerShell-processen avslutas.

Modulerna som läses in i `WinPSCompatSession` sessionen används via implicit fjärr kommunikation och återspeglas i den aktuella PowerShell-sessionen. Detta är samma transport metod som används för PowerShell-jobb.

När en modul importeras till `WinPSCompatSession` sessionen genererar implicit fjärr kommunikation en proxy-modul i användarens `$env:Temp` katalog och importerar denna proxy-modul till den aktuella PowerShell-sessionen. Detta gör att PowerShell kan identifiera att modulen har lästs in med Windows PowerShell-kompatibilitet.

När sessionen har skapats kan den användas för åtgärder som inte fungerar korrekt på avserialiserade objekt. Hela pipelinen körs i Windows PowerShell och endast det slutliga resultatet returneras. Ett exempel:

```powershell
$s = Get-PSSession -Name WinPSCompatSession
Invoke-Command -Session $s -ScriptBlock {
  "Running in Windows PowerShell version $($PSVersionTable.PSVersion)"
}
```

Funktionen kompatibilitet kan anropas på två sätt:

- Uttryckligen genom att importera en modul med parametern **UseWindowsPowerShell**

   ```powershell
   Import-Module -Name ScheduledTasks -UseWindowsPowerShell
   ```

- Implicit genom att importera en Windows PowerShell-modul efter Modulnamn, sökväg eller automatisk inläsning via kommando identifiering.

   ```powershell
   Import-Module -Name ServerManager
   Get-AppLockerPolicy -Local
   ```

   Om den inte redan har lästs in läses AppLocker-modulen in när du kör  `Get-AppLockerPolicy` .

Windows PowerShell-kompatibilitet inläsning av moduler som anges i `WindowsPowerShellCompatibilityModuleDenyList` inställningen i PowerShell-konfigurationsfilen.

Standardvärdet för den här inställningen är:

```json
"WindowsPowerShellCompatibilityModuleDenyList":  [
   "PSScheduledJob","BestPractices","UpdateServices"
]
```

### <a name="managing-implicit-module-loading"></a>Hantera inläsning av implicit modul

Använd inställningen i en PowerShell-konfigurationsfil om du vill inaktivera funktionen för kompatibilitet med Windows PowerShell för implicit import `DisableImplicitWinCompat` . Den här inställningen kan läggas till i `powershell.config.json` filen. Mer information finns i [about_powershell_config](about_powershell_config.md).

Det här exemplet visar hur du skapar en konfigurations fil som inaktiverar funktionen för implicit modul-inläsning av Windows PowerShell-kompatibilitet.

```powershell
$ConfigPath = "$PSHOME\DisableWinCompat.powershell.config.json"
$ConfigJSON = ConvertTo-Json -InputObject @{
  "DisableImplicitWinCompat" = $true
  "Microsoft.PowerShell:ExecutionPolicy" = "RemoteSigned"
}
$ConfigJSON | Out-File -Force $ConfigPath
pwsh -settingsFile $ConfigPath
```

Mer information om modulens kompatibilitet finns i [PowerShell 7-modulen Compatibility](https://aka.ms/PSModuleCompat) List.

### <a name="managing-cmdlet-clobbering"></a>Clobbering för att hantera cmdlet

Funktionen Windows PowerShell-kompatibilitet använder implicit fjärr kommunikation för att läsa in moduler i kompatibilitetsläge. Resultatet är att kommandon som exporteras av modulen prioriteras framför kommandon i samma namn i den aktuella PowerShell 7-sessionen. I PowerShell 7.0.0-versionen inkluderade de viktigaste modulerna som medföljer PowerShell.

I PowerShell 7,1 ändrades beteendet så att följande grundläggande PowerShell-moduler inte är clobbered:

- Microsoft. PowerShell. ConsoleHost
- Microsoft. PowerShell. Diagnostics
- Microsoft. PowerShell. Host
- Microsoft. PowerShell. Management
- Microsoft. PowerShell. Security
- Microsoft.PowerShell.Utility
- Microsoft. WSMan. Management

PowerShell 7,1 har också lagt till möjligheten att lista ytterligare moduler som inte ska vara clobbered i kompatibilitetsläge.

Du kan lägga till `WindowsPowerShellCompatibilityNoClobberModuleList` inställningen i PowerShell-konfigurationsfilen. Värdet för den här inställningen är en kommaavgränsad lista med modulnamn. Standardvärdet för den här inställningen är:

```json
"WindowsPowerShellCompatibilityNoClobberModuleList": [ ]
```

## <a name="limitations"></a>Begränsningar

Funktionen Windows PowerShell-kompatibilitet:

1. Fungerar endast lokalt på Windows-datorer
1. Kräver att Windows PowerShell 5,1
1. Körs på serialiserade cmdlet-parametrar och retur värden, inte på Live-objekt
1. Alla moduler som importer ATS till Windows PowerShell-fjärrsessionen delar samma körnings utrymme.

## <a name="keywords"></a>Nyckelord

about_Windows_PowerShell_Compatibility

## <a name="see-also"></a>Se även

[about_Modules](about_Modules.md)

[Importera-modul](xref:Microsoft.PowerShell.Core.Import-Module)

