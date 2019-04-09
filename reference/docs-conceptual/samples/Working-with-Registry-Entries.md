---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Arbeta med registerposter
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: 667d17d0d62745a27ffef5f1912336b72f74c2a9
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293086"
---
# <a name="working-with-registry-entries"></a>Arbeta med registerposter

Eftersom registerposter är egenskaper för nycklar och därför kan inte direkt sökas, behöver vi dra ett något annat sätt när du arbetar med dem.

## <a name="listing-registry-entries"></a>Visa en lista över registerposter

Det finns många olika sätt att undersöka registerposter. Det enklaste sättet är att få de kolumner som är associerade med en nyckel. Till exempel vill visa namnen på de posterna i registernyckeln `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, använda `Get-Item`. Registernycklar har en egenskap med samlingsnamnet ”Property” som är en lista över registerposter i nyckeln.
Följande kommando väljer egenskapen egenskapen och utökar objekt så att de visas i en lista:

```powershell
Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion |
  Select-Object -ExpandProperty Property
```

```Output
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

Du kan visa registerposterna i ett mer lättläst format `Get-ItemProperty`:

```powershell
Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

```Output
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

Du kan använda den `*.*` notation för att referera till den aktuella platsen. Du kan använda `Set-Location` att ändra till den **CurrentVersion** container registry första:

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Du kan också använda den inbyggda HKLM PSDrive med `Set-Location`:

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Du kan sedan använda den `*.*` notation för den aktuella platsen om du vill visa egenskaperna utan att ange en fullständig sökväg:

```powershell
Get-ItemProperty -Path .
```

```Output
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

Sökvägen expansion fungerar på samma sätt som i filsystem, så från den här platsen kan du hämta den **itemproperty-egenskap** för `HKLM:\SOFTWARE\Microsoft\Windows\Help` med hjälp av `Get-ItemProperty -Path ..\Help`.

## <a name="getting-a-single-registry-entry"></a>Hämta en enda registerpost

Om du vill hämta en viss post i en registernyckel, kan du använda någon av flera möjliga metoder. Det här exemplet efter värdet för **DevicePath** i `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.

Med hjälp av `Get-ItemProperty`, använda den **sökväg** parametern för att ange namnet på nyckeln, och **namn** parametern för att ange namnet på den **DevicePath** posten.

```powershell
Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath
```

```Output
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
> Även om `Get-ItemProperty` har **Filter**, **inkludera**, och **undanta** parametrar, de kan inte användas för att filtrera efter egenskapsnamn. De här parametrarna avser registernycklar som är objektet sökvägar och inte registerposter. Registerposter som är egenskaper för konfigurationsobjekt.

Ett annat alternativ är att använda kommandoradsverktyget Reg.exe. Om du vill ha hjälp med reg.exe skriver `reg.exe /?` i Kommandotolken. Använd reg.exe för att hitta posten DevicePath, som visas i följande kommando:

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

Du kan också använda den **WshShell** COM-objekt samt att hitta vissa registerposter, även om den här metoden inte fungerar med stora binära data eller med namn på registret poster som innehåller tecken, till exempel ”\\”). Lägg till egenskapsnamnet till objekt-sökväg med en \\ avgränsare:

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

## <a name="setting-a-single-registry-entry"></a>Ange en enda registerpost

Om du vill ändra en viss post i en registernyckel, kan du använda någon av flera möjliga metoder. Det här exemplet ändrar den **sökväg** posten under `HKEY_CURRENT_USER\Environment`. Den **sökväg** posten anger var du hittar körbara filer.

1. Hämta det aktuella värdet för den **sökväg** post med hjälp av `Get-ItemProperty`.
2. Lägg till det nya värdet, att avgränsa dem med en `;`.
3. Använd `Set-ItemProperty` med angiven nyckel, postens namn och värde för att ändra registerposten.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> Även om `Set-ItemProperty` har **Filter**, **inkludera**, och **undanta** parametrar, de kan inte användas för att filtrera efter egenskapsnamn. De här parametrarna avser registernycklar, som är objektet sökvägar – och inte registerposter – som är egenskaper för konfigurationsobjekt.

Ett annat alternativ är att använda kommandoradsverktyget Reg.exe. Om du vill ha hjälp med reg.exe skriver **reg.exe /?**
i Kommandotolken.

Följande exempel ändringar i **sökväg** post genom att ta bort sökvägen som har lagts till i exemplet ovan.
`Get-ItemProperty` fortfarande används för att hämta det aktuella värdet för att undvika att behöva Parsar då strängen som returnerades från `reg query`. Den **delsträngen** och **LastIndexOf** metoder används för att hämta den senaste sökvägen som lagts till i den **sökväg** posten.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

## <a name="creating-new-registry-entries"></a>Skapar nya registerposter

Att lägga till en ny post med namnet ”PowerShellPath” i den **CurrentVersion** , nyckelanvändningen `New-ItemProperty` med sökvägen till nyckeln, namnet och värdet för posten. I det här exemplet tar vi värdet för Windows PowerShell-variabel `$PSHome`, som lagrar sökvägen till installationskatalogen för Windows PowerShell.

Du kan lägga till den nya posten till nyckeln med hjälp av följande kommando och kommandot returnerar också information om den nya posten:

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

```Output
PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows
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
|MultiString|En flerradig sträng|
|Sträng|ett värde|
|QWord|8 byte av binära data|

> [!NOTE]
> Du kan lägga till en registerpost till flera platser genom att ange en matris med värden för den **sökväg** parameter:

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Du kan också skriva över en befintlig post registervärdet genom att lägga till den **kraft** parametern till någon `New-ItemProperty` kommando.

## <a name="renaming-registry-entries"></a>Renaming Registry Entries

Att byta namn på den **PowerShellPath** posten ”PSHome”, Använd `Rename-ItemProperty`:

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

Om du vill visa omdöpt värdet, lägger du till den **PassThru** parameter i kommandot.

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

## <a name="deleting-registry-entries"></a>Tar bort registerposter

Ta bort registerposter för både PSHome och PowerShellPath genom att använda `Remove-ItemProperty`:

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
