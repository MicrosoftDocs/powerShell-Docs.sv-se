---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Arbeta med registerposter
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: bffdf80931fc4dc570b584623487077dc5d449dc
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952383"
---
# <a name="working-with-registry-entries"></a>Arbeta med registerposter

Eftersom registerposter är egenskaper för nycklar och därför går inte att direkt Bläddra, behöver vi ta ett något annorlunda sätt när du arbetar med dem.

### <a name="listing-registry-entries"></a>Visar en lista över registervärden

Det finns många olika sätt att granska registerposter. Det enklaste sättet är att hämta egenskapsnamn som associeras med en nyckel. Till exempel för att se namnen på poster i registernyckeln **HKEY_LOCAL_MACHINE\\programvara\\Microsoft\\Windows\\CurrentVersion**, Använd **Get-objekt** . Registernycklar har en egenskap med det allmänna namnet för ”egenskapen” som är en lista över registerposter i nyckeln. Följande kommando väljer egenskapen egenskapen och utökar objekt så att de visas i en lista:

```
PS> Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion | Select-Object -ExpandProperty Property
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

Du kan visa registerposterna i ett mer lättläst format **Get-ItemProperty**:

```
PS> Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion

PSPath              : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows\CurrentVersion
PSParentPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows
PSChildName         : CurrentVersion
PSDrive             : HKLM
PSProvider          : Microsoft.PowerShell.Core\Registry
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
CommonFilesDir      : C:\Program Files\Common Files
ProductId           : 76487-338-1167776-22465
WallPaperDir        : C:\WINDOWS\Web\Wallpaper
MediaPath           : C:\WINDOWS\Media
ProgramFilesPath    : C:\Program Files
PF_AccessoriesName  : Accessories
(default)           :
```

Windows PowerShell-relaterade egenskaper för nyckeln är alla med prefixet ”PS”, som **PSPath**, **PSParentPath**, **PSChildName**, och **PSProvider** .

Du kan använda den ”**.**” notation för att referera till den aktuella platsen. Du kan använda **Set-Location** ändra till den **CurrentVersion** registret behållaren första:

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Du kan också använda den inbyggda HKLM PSDrive med **Set-Location**:

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Du kan sedan använda den ”**.**” notation för den aktuella platsen om du vill visa egenskaperna utan att ange en fullständig sökväg:

```
PS> Get-ItemProperty -Path .
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

Sökvägen expansion fungerar på samma sätt som i filsystemet, så du kan hämta från den här platsen i **ItemProperty** lista för **HKLM:\\programvara\\Microsoft\\Windows \\Hjälp** med hjälp av **ItemProperty Get-sökvägen... \\Hjälp**.

### <a name="getting-a-single-registry-entry"></a>Hämta en enda registerpost

Om du vill hämta en post i en registernyckel, kan du använda en av flera möjliga metoder. Det här exemplet returnerar värdet för **DevicePath** i **HKEY_LOCAL_MACHINE\\programvara\\Microsoft\\Windows\\CurrentVersion**.

Med hjälp av **Get-ItemProperty**, använda den **sökväg** parametern för att ange namnet på nyckeln och **namn** parametern för att ange namnet på den **DevicePath** transaktionen.

```
PS> Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath

PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

Det här kommandot returnerar standardegenskaper för Windows PowerShell samt de **DevicePath** egenskapen.

> [!NOTE]
> Även om **Get-ItemProperty** har **Filter**, **inkludera**, och **undanta** parametrar, de kan inte användas för att filtrera efter namn. Parametrarna avser registernycklar, som är objektet sökvägar, och inte registerposter – som är egenskaper.

Ett annat alternativ är att använda kommandoradsverktyget Reg.exe. Hjälp med reg.exe skriver **reg.exe /?** vid en kommandotolk. Använd reg.exe för att hitta posten DevicePath som visas i följande kommando:

```
PS> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath

! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

Du kan också använda den **WshShell COM** objekt samt för att hitta vissa registerposter, även om den här metoden inte fungerar med stora binära data eller registret postnamnen som innehåller tecken, till exempel ”\\”). Lägg till egenskapsnamnet objektsökväg med en \\ avgränsare:

```
PS> (New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
%SystemRoot%\inf
```

### <a name="creating-new-registry-entries"></a>Skapa nya registerposter

Att lägga till en ny post med namnet ”PowerShellPath” i den **CurrentVersion** , nyckelanvändning **ny ItemProperty** med sökvägen till nyckeln, namnet och värdet för posten. I det här exemplet vi tar värdet för Windows PowerShell-variabel **$PSHome**, som lagrar sökvägen till installationskatalogen för Windows PowerShell.

Du kan lägga till den nya posten i nyckeln med hjälp av kommandot och kommandot returnerar även information om den nya posten:

```
PS> New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome

PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

Den **PropertyType** måste vara namnet på en **Microsoft.Win32.RegistryValueKind** uppräkningsmedlem i följande tabell:

|PropertyType värde|Innebörd|
|----------------------|-----------|
|Binär|Binära data|
|DWord|Ett tal som är en giltig UInt32|
|ExpandString|En sträng som kan innehålla miljövariabler som dynamiskt expanderas|
|Längd|En flerradig sträng|
|Sträng|Ett värde|
|QWord|8 byte binära data|

> [!NOTE]
> Du kan lägga till en registerpost till flera platser genom att ange en matris med-värden för den **sökväg** parameter:

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

Du kan också skriva över en befintlig post registervärdet genom att lägga till den **kraft** parameter till någon **ny ItemProperty** kommando.

### <a name="renaming-registry-entries"></a>Byta namn på registerposter

Att byta namn på den **PowerShellPath** post som ”PSHome”, Använd **byta ItemProperty**:

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

Om du vill visa värdet har bytt namn till, lägger du till den **PassThru** parametern för kommandot.

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a>Om du tar bort registerposter

Om du vill ta bort registerposter för både PSHome och PowerShellPath använder **ta bort ItemProperty**:

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```