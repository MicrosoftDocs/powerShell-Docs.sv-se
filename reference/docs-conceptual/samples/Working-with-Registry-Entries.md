---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Arbeta med registerposter
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: bffdf80931fc4dc570b584623487077dc5d449dc
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405374"
---
# <a name="working-with-registry-entries"></a>Arbeta med registerposter

Eftersom registerposter är egenskaper för nycklar och därför kan inte direkt sökas, behöver vi dra ett något annat sätt när du arbetar med dem.

### <a name="listing-registry-entries"></a>Visa en lista över registerposter

Det finns många olika sätt att undersöka registerposter. Det enklaste sättet är att få de kolumner som är associerade med en nyckel. Till exempel vill visa namnen på de posterna i registernyckeln **HKEY_LOCAL_MACHINE\\programvara\\Microsoft\\Windows\\CurrentVersion**, använda **Get-objekt** . Registernycklar har en egenskap med samlingsnamnet ”Property” som är en lista över registerposter i nyckeln. Följande kommando väljer egenskapen egenskapen och utökar objekt så att de visas i en lista:

```
PS> Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion | Select-Object -ExpandProperty Property
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

Du kan visa registerposterna i ett mer lättläst format **Get-itemproperty-egenskap**:

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

Windows PowerShell-relaterade egenskaperna för nyckeln har alla prefixet ”PS”, till exempel **PSPath**, **PSParentPath**, **PSChildName**, och **PSProvider** .

Du kan använda den ”**.**” notation för att referera till den aktuella platsen. Du kan använda **Set-Location** att ändra till den **CurrentVersion** container registry första:

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

Sökvägen expansion fungerar på samma sätt som i filsystem, så från den här platsen kan du hämta den **itemproperty-egenskap** för **HKLM:\\programvara\\Microsoft\\Windows \\Hjälpa** med hjälp av **Get-itemproperty-egenskap-sökväg... \\Hjälpa**.

### <a name="getting-a-single-registry-entry"></a>Hämta en enda registerpost

Om du vill hämta en viss post i en registernyckel, kan du använda någon av flera möjliga metoder. Det här exemplet efter värdet för **DevicePath** i **HKEY_LOCAL_MACHINE\\programvara\\Microsoft\\Windows\\CurrentVersion**.

Med hjälp av **Get-itemproperty-egenskap**, använda den **sökväg** parametern för att ange namnet på nyckeln, och **namn** parametern för att ange namnet på den **DevicePath** posten.

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

Det här kommandot returnerar standardegenskaper för Windows PowerShell och **DevicePath** egenskapen.

> [!NOTE]
> Även om **Get-itemproperty-egenskap** har **Filter**, **inkludera**, och **undanta** parametrar, de kan inte användas för att filtrera efter egenskapsnamn. De här parametrarna avser registernycklar, som är objektet sökvägar – och inte registerposter – som är egenskaper för konfigurationsobjekt.

Ett annat alternativ är att använda kommandoradsverktyget Reg.exe. Om du vill ha hjälp med reg.exe skriver **reg.exe /?** i Kommandotolken. Använd reg.exe för att hitta posten DevicePath, som visas i följande kommando:

```
PS> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath

! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

Du kan också använda den **WshShell COM** objekt samt för att hitta vissa registerposter, även om den här metoden inte fungerar med stora binära data eller med namn på registret poster som innehåller tecken, till exempel ”\\”). Lägg till egenskapsnamnet till objekt-sökväg med en \\ avgränsare:

```
PS> (New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
%SystemRoot%\inf
```

### <a name="creating-new-registry-entries"></a>Skapar nya registerposter

Att lägga till en ny post med namnet ”PowerShellPath” i den **CurrentVersion** , nyckelanvändningen **New-itemproperty-egenskap** med sökvägen till nyckeln, namnet och värdet för posten. I det här exemplet tar vi värdet för Windows PowerShell-variabel **$PSHome**, som lagrar sökvägen till installationskatalogen för Windows PowerShell.

Du kan lägga till den nya posten till nyckeln med hjälp av följande kommando och kommandot returnerar också information om den nya posten:

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

Den **%d{PropertyType/** måste vara namnet på en **Microsoft.Win32.RegistryValueKind** uppräkningsmedlem i följande tabell:

|%D{PropertyType/ värde|Innebörd|
|----------------------|-----------|
|Binär|Binära data|
|DWord|Ett tal som är en giltig UInt32|
|ExpandString|En sträng som kan innehålla miljövariabler som dynamiskt expanderas|
|Kan|En flerradig sträng|
|Sträng|Ett värde|
|QWord|8 byte av binära data|

> [!NOTE]
> Du kan lägga till en registerpost till flera platser genom att ange en matris med värden för den **sökväg** parameter:

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

Du kan också skriva över en befintlig post registervärdet genom att lägga till den **kraft** parametern till någon **New-itemproperty-egenskap** kommando.

### <a name="renaming-registry-entries"></a>Byta namn på registerposter

Att byta namn på den **PowerShellPath** posten ”PSHome”, Använd **Rename-itemproperty-egenskap**:

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

Om du vill visa omdöpt värdet, lägger du till den **PassThru** parameter i kommandot.

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a>Tar bort registerposter

Ta bort registerposter för både PSHome och PowerShellPath genom att använda **Remove-itemproperty-egenskap**:

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```