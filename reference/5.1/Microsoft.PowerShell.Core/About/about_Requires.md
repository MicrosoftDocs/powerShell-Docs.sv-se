---
description: Förhindrar att ett skript körs utan de element som krävs.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_requires?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Requires
ms.openlocfilehash: d499499c58f22bff10d712d33fc3a021e4fa6bbb
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271460"
---
# <a name="about-requires"></a>Om kräver

## <a name="short-description"></a>Kort beskrivning
Förhindrar att ett skript körs utan de element som krävs.

## <a name="long-description"></a>Lång beskrivning

`#Requires`Instruktionen förhindrar att ett skript körs om inte PowerShell-versionen, modulerna (och versionen) eller snapin-modulerna (och versionen) och versions krav uppfylls. Om kraven inte uppfylls, kör inte PowerShell skriptet.

### <a name="syntax"></a>Syntax

```
#Requires -Assembly { <Path to .dll> | <.NET assembly specification> }
#Requires -Version <N>[.<n>]
#Requires -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -Modules { <Module-Name> | <Hashtable> }
#Requires -PSEdition <PSEdition-Name>
#Requires -ShellId <ShellId> -PSSnapin <PSSnapin-Name> [-Version <N>[.<n>]]
#Requires -RunAsAdministrator
```

Mer information om syntaxen finns i [ScriptRequirements](/dotnet/api/system.management.automation.language.scriptrequirements).

### <a name="rules-for-use"></a>Regler för användning

Ett skript kan innehålla mer än en `#Requires` instruktion. `#Requires`Uttrycken kan visas på alla rader i ett skript.

Att placera en `#Requires` instruktion inuti en funktion begränsar inte dess omfång. Alla `#Requires` instruktioner tillämpas alltid globalt och måste vara uppfyllda innan skriptet kan köras.

> [!WARNING]
> Även om en `#Requires` instruktion kan visas på en rad i ett skript, påverkar dess placering i ett skript inte sekvensen för dess program. Det globala tillstånd som `#Requires` instruktionen visar måste vara uppfyllt innan skript körningen.

Exempel:

```powershell
Get-Module AzureRM.Netcore | Remove-Module
#Requires -Modules AzureRM.Netcore
```

Du kanske tror att ovanstående kod inte ska köras eftersom modulen som krävs togs bort före `#Requires` instruktionen. Men `#Requires` läget var uppfyllt innan skriptet kan köras. Den första raden i skriptet har ogiltig status.

### <a name="parameters"></a>Parametrar

#### <a name="-assembly-assembly-path--net-assembly-specification"></a>– Sammansättning \<Assembly path> |\<.NET assembly specification>

Anger sökvägen till sammansättnings-DLL-filen eller ett .NET-sammansättnings namn. **Sammansättnings** parametern introducerades i PowerShell 5,0. Mer information om .NET-sammansättningar finns i [sammansättnings namn](/dotnet/standard/assembly/names).

Ett exempel:

```
#Requires -Assembly path\to\foo.dll
```

```
#Requires -Assembly "System.Management.Automation, Version=3.0.0.0,
  Culture=neutral, PublicKeyToken=31bf3856ad364e35"
```

#### <a name="-version-nn"></a>-Version \<N\> [. \<n\> ]

Anger den lägsta version av PowerShell som skriptet kräver. Ange ett högre versions nummer och ett valfritt lägre versions nummer.

Ett exempel:

```powershell
#Requires -Version 5.1
```

#### <a name="-pssnapin-pssnapin-name--version-nn"></a>-PSSnapin \<PSSnapin-Name\> [-version \<N\> [. \<n\> ]]

Anger en PowerShell-snapin-modul som skriptet kräver. Ange namnet på snapin-modulen och ett valfritt versions nummer.

Ett exempel:

```powershell
#Requires -PSSnapin DiskSnapin -Version 1.2
```

#### <a name="-modules-module-name--hashtable"></a>– Moduler \<Module-Name\> |\<Hashtable\>

Anger PowerShell-moduler som skriptet kräver. Ange modulens namn och ett valfritt versions nummer.

Om de moduler som krävs inte finns i den aktuella sessionen importeras de av PowerShell.
Om modulerna inte kan importeras, genererar PowerShell ett avslutande fel.

Ange modulnamnet ( \<String\> ) eller en hash-tabell för varje modul. Värdet kan vara en kombination av strängar och hash-tabeller. Hash-tabellen har följande nycklar.

- `ModuleName` - **Krävs** Anger namnet på modulen.
- `GUID` - **Valfritt** Anger modulens GUID.
- Du **måste** också ange en av de tre nycklarna nedan. Nycklarna kan inte användas tillsammans.
  - `ModuleVersion` -Anger en minsta godtagbar version av modulen.
  - `RequiredVersion` -Anger en exakt, obligatorisk version av modulen.
  - `MaximumVersion` -Anger den högsta godkända versionen av modulen.

> [!NOTE]
> `RequiredVersion` lades till i Windows PowerShell 5,0.
> `MaximumVersion` lades till i Windows PowerShell 5,1.

Ett exempel:

Kräv att `Hyper-V` (version `1.1` eller större) är installerad.

```powershell
#Requires -Modules @{ ModuleName="Hyper-V"; ModuleVersion="1.1" }
```

Kräver att `Hyper-V` ( **endast** version `1.1` ) är installerat.

```powershell
#Requires -Modules @{ ModuleName="Hyper-V"; RequiredVersion="1.1" }
```

Kräver att `Hyper-V` (version `1.1` eller lägre) är installerad.

```powershell
#Requires -Modules @{ ModuleName="Hyper-V"; MaximumVersion="1.1" }
```

Kräver att alla versioner av `PSScheduledJob` och `PSWorkflow` , är installerade.

```powershell
#Requires -Modules PSWorkflow, PSScheduledJob
```

När du använder `RequiredVersion` nyckeln måste du se till att versions strängen exakt matchar den versions sträng som du vill kräva.

```powershell
Get-Module Hyper-V
```

```Output
ModuleType Version    Name     ExportedCommands
---------- -------    ----     ------------------
Binary     2.0.0.0    hyper-v  {Add-VMAssignableDevice, ...}
```

Följande exempel Miss lyckas eftersom **2.0.0** inte exakt matchar **2.0.0.0**.

```powershell
#Requires -Modules @{ ModuleName="Hyper-V"; RequiredVersion="2.0.0" }
```

#### <a name="-psedition-psedition-name"></a>– PSEdition \<PSEdition-Name\>

Anger en PowerShell-utgåva som skriptet kräver. Giltiga värden är **Core** för PowerShell-kärnan och **Desktop** för Windows PowerShell.

Ett exempel:

```powershell
#Requires -PSEdition Core
```

#### <a name="-shellid"></a>-ShellId

Anger det gränssnitt som skriptet kräver. Ange gränssnitts-ID: t. Om du använder parametern **ShellId** måste du också ta med parametern **PSSnapin** .
Du kan hitta den aktuella **ShellId** genom att fråga den `$ShellId` automatiska variabeln.

Ett exempel:

```powershell
#Requires -ShellId MyLocalShell -PSSnapin Microsoft.PowerShell.Core
```

> [!NOTE]
> Den här parametern är avsedd för användning i mini-Shells, som är föråldrad.

#### <a name="-runasadministrator"></a>-RunAsAdministrator

När den här växel parametern läggs till i din `#Requires` instruktion, anger den att den PowerShell-session där du kör skriptet måste startas med utökade användar rättigheter. Parametern **RunAsAdministrator** ignoreras på ett operativ system som inte är från Windows. **RunAsAdministrator** -parametern introducerades i PowerShell 4,0.

Ett exempel:

```powershell
#Requires -RunAsAdministrator
```

### <a name="examples"></a>Exempel

Följande skript har två `#Requires` instruktioner. Om kraven som anges i båda uttrycken inte uppfylls, körs inte skriptet. Varje `#Requires` instruktion måste vara det första objektet på en rad:

```powershell
#Requires -Modules PSWorkflow
#Requires -Version 3
Param
(
    [parameter(Mandatory=$true)]
    [String[]]
    $Path
)
...
```

## <a name="see-also"></a>Se även

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Language_Keywords](about_Language_Keywords.md)

[about_PSSnapins](about_PSSnapins.md)

[Get-PSSnapin](xref:Microsoft.PowerShell.Core.Get-PSSnapin)
