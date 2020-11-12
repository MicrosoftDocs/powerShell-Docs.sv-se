---
description: Miljövariabeln PSModulePath innehåller en lista över mappar som genomsöks för att hitta moduler och resurser.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_PSModulePath?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSModulePath
ms.openlocfilehash: 6e0307996bf619bc887b076a1f8c0faa619964fe
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524499"
---
# <a name="about-psmodulepath"></a>Om PSModulePath

`$env:PSModulePath`Miljövariabeln innehåller en lista över mappar som genomsöks för att hitta moduler och resurser. PowerShell söker rekursivt igenom varje mapp efter modul ( `.psd1` eller `.psm1` ) filer.

Som standard är de effektiva platser som `$env:PSModulePath` är tilldelade:

- Platser i hela systemet: dessa mappar innehåller moduler som levereras med PowerShell. Dessa moduler lagras i `$PSHOME\Modules` mappen. Detta är även platsen där Windows Management-moduler är installerade.

- Användare-installerade moduler: de här är moduler som installeras av användaren.
  `Install-Module` har en **omfattnings** parameter som gör att du kan ange om modulen är installerad för den aktuella användaren eller för alla användare. Mer information finns i [install-module](xref:PowerShellGet.Install-Module).

  - I Windows är platsen för det användarspecifika **CurrentUser** -omfånget `$HOME\Documents\PowerShell\Modules` mappen. Platsen för **allusers** -omfattningen är `$env:ProgramFiles\PowerShell\Modules` .
  - På andra datorer än Windows-system är platsen för det användarspecifika **CurrentUser** -omfånget `$HOME/.local/share/powershell/Modules` mappen. Platsen för **allusers** -omfattningen är `/usr/local/share/powershell/Modules` .

Dessutom kan installations program som installerar moduler i andra kataloger, till exempel katalogen program filer, lägga till sina platser till värdet `$env:PSModulePath` .

> [!NOTE]
> På Windows är den användarspecifika platsen den `PowerShell\Modules` mapp som finns i mappen **dokument** i din användar profil. Den angivna sökvägen till platsen varierar efter Windows-version och om du använder mappomdirigering. Microsoft OneDrive kan också ändra platsen för mappen **dokument** . Du kan kontrol lera platsen för mappen **dokument** med hjälp av följande kommando: `[Environment]::GetFolderPath('MyDocuments')` .

## <a name="modifying-psmodulepath"></a>Ändra PSModulePath

Om du vill ändra standardmodulens kataloger för den aktuella sessionen använder du följande kommando format för att ändra värdet för `PSModulePath` miljö variabeln.

Om du till exempel vill lägga till `C:\Program Files\Fabrikam\Modules` katalogen till värdet för PSModulePath-miljövariabeln, skriver du:

```powershell
$Env:PSModulePath = $Env:PSModulePath+";C:\Program Files\Fabrikam\Modules"
```

Semikolon ( `;` ) i kommandot avgränsar den nya sökvägen från den sökväg som föregår den i listan. På andra plattformar än Windows-plattformar `:` separerar kolon () Sök vägarna i miljö variabeln.

Om du vill ändra värdet för `PSModulePath` i varje session lägger du till föregående kommando i din PowerShell-profil eller använder **SetEnvironmentVariable** -metoden i **miljö** klassen.

Följande kommando använder metoden **GetEnvironmentVariable** för att hämta dator inställningen för `PSModulePath` och metoden **SetEnvironmentVariable** för att lägga till `C:\Program Files\Fabrikam\Modules` sökvägen till värdet.

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'Machine')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'Machine')
```

Om du vill lägga till en sökväg till användar inställningen ändrar du värdet för mål till **användare**.

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'User')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'User')
```

Mer information om metoderna i klassen **system. miljö** finns i [miljö metoder](/dotnet/api/system.environment).

## <a name="powershell-psmodulepath-construction"></a>PowerShell-PSModulePath konstruktion

Värdet för `$env:PSModulePath` konstrueras varje gången PowerShell startar.
Värdet varierar efter version av PowerShell och hur det startas.

### <a name="windows-powershell-startup"></a>Windows PowerShell-start

Windows PowerShell använder följande logik för att skapa `PSModulePath` vid start:

- Om `PSModulePath` det inte finns, kombinera **CurrentUser** , **allusers** och `$PSHOME` modulens sökvägar
- IF `PSModulePath` finns:
  - Om `PSModulePath` innehåller en `$PSHOME` sökväg för moduler:
    - Sökvägen till **allusers** -moduler infogas före `$PSHOME` sökvägen till moduler
  - tilläggs
    - Används bara `PSModulePath` enligt definitionen eftersom användaren medvetet tog bort `$PSHOME` platsen

**CurrentUser** module-sökvägen är för fast fast endast om användar omfånget `$env:PSModulePath` inte finns. Annars används användar omfånget `$env:PSModulePath` enligt definitionen.

### <a name="powershell-core-6-startup"></a>PowerShell Core 6-start

PowerShell Core 6 använder inte innehåll i `$env:PSModulePath` om den upptäcker att den har startats från PowerShell. Den skriver över den med:

- **CurrentUser** modules sökväg + **allusers** modules sökväg + `$PSHOME` moduler sökväg + sökväg för Windows PowerShell- `$PSHOME` moduler.

### <a name="powershell-7-startup"></a>PowerShell 7-Start

I Windows, för de flesta miljövariabler, använder en ny process bara det värdet även om det finns en dator som omfattas av samma namn för de flesta miljövariabler.

I PowerShell 7 `PSModulePath` behandlas liknande hur `Path` miljövariabeln behandlas i Windows. I Windows `Path` behandlas det annorlunda jämfört med andra miljövariabler. När en process startas kombinerar Windows den användare som omfattas av `Path` datorns omfång `Path` .

- Hämta användar omfattningen `PSModulePath`
- Jämför med att bearbeta en ärvd `PSModulePath` miljö variabel
  - Om samma:
    - Lägg till **allusers** `PSModulePath` till slutet efter semantiken för `Path` miljö variabeln
    - Windows- `System32` sökvägen kommer från den dator som definierats `PSModulePath` så behöver inte uttryckligen läggas till
  - Om det skiljer sig, behandla som om användaren uttryckligen ändrade den och inte lägger till **allusers**`PSModulePath`
- Prefix med PS7-användare, system och `$PSHOME` sökvägar i den ordningen
  - Om `powershell.config.json` innehåller en användare `PSModulePath` som är begränsad använder du den i stället för standardvärdet för användaren
  - Om `powershell.config.json` innehåller ett system område `PSModulePath` använder du det i stället för standardvärdet för systemet

UNIX-system har ingen åtskillnad mellan användar-och systemmiljövariabler.
`PSModulePath` ärvs och PS7 sökvägar är före fast om de inte redan har definierats.

### <a name="starting-windows-powershell-from-powershell-7"></a>Starta Windows PowerShell från PowerShell 7

I den här diskussionen innebär _Windows PowerShell_ både `powershell.exe` och `powershell_ise.exe` .

Värdet för `$env:PSModulePath` kopieras till `WinPSModulePath` med följande ändringar:

- Ta bort PS7 sökväg till användar modulen
- Ta bort PS7-sökvägen till system-modulen
- Ta bort PS7 `$PSHOME`

PS7-sökvägarna tas bort så att PS7-moduler inte kan läsas in i Windows PowerShell. `WinPSModulePath`Värdet används när du startar Windows PowerShell.

### <a name="starting-powershell-7-from-windows-powershell"></a>Starta PowerShell 7 från Windows PowerShell

PowerShell 7-starten fortsätter i befintligt skick med att ärva sökvägar som har lagts till i Windows PowerShell. Eftersom PS7 sökvägar är i förväg finns det inget funktionellt problem.

### <a name="starting-powershell-6-from-powershell-7"></a>Starta PowerShell 6 från PowerShell 7

PowerShell Core 6 skriver över `$env:PSModulePath` . Inga ändringar har gjorts.

### <a name="starting-powershell-7-from-powershell-6"></a>Starta PowerShell 7 från PowerShell 6

PowerShell 7-starten fortsätter i befintligt skick med att ärva sökvägar som PowerShell Core 6 lagt till. Eftersom PS7 sökvägar är i förväg finns det inget funktionellt problem.

## <a name="module-search-behavior"></a>Beteende för modul sökning

PowerShell söker rekursivt igenom varje mapp i **PSModulePath** efter modul ( `.psd1` eller `.psm1` ) filer. Med det här Sök mönstret kan flera versioner av samma modul installeras i olika mappar. Exempel:

```Output
    Directory: C:\Program Files\WindowsPowerShell\Modules\PowerShellGet

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d----           8/14/2020  5:56 PM                1.0.0.1
d----           9/13/2019  3:53 PM                2.1.2
```

Som standard laddar PowerShell det högsta versions numret för en modul när flera versioner hittas. Om du vill läsa in en speciell version använder `Import-Module` du med parametern **FullyQualifiedName** . Mer information finns i [import-module](xref:Microsoft.PowerShell.Core.Import-Module).

## <a name="see-also"></a>Se även

- [about_Modules](about_Modules.md)
- [Miljö metoder](/dotnet/api/system.environment)
