---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Arbeta med registerposter
ms.openlocfilehash: c1fd6f57f13240eb2039f2d5756796678800aee0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030730"
---
# <a name="working-with-registry-entries"></a>Arbeta med registerposter

Eftersom register poster är egenskaper för nycklar och inte kan bläddras direkt, måste vi ta en något annorlunda metod när du arbetar med dem.

## <a name="listing-registry-entries"></a>Visar register poster

Det finns många olika sätt att undersöka register poster. Det enklaste sättet är att hämta egenskaps namnen som är associerade med en nyckel. Om du till exempel vill visa namnen på posterna i register nyckeln `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`använder du `Get-Item`. Register nycklar har en egenskap med det generiska namnet "Property" som är en lista över register poster i nyckeln.
Följande kommando väljer egenskapen egenskap och utökar objekten så att de visas i en lista:

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

Om du vill visa register posterna i en mer läsbar form använder du `Get-ItemProperty`:

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

Windows PowerShell-relaterade egenskaper för nyckeln föregås av "PS", till exempel **PSPath**, **PSParentPath**, **PSChildName**och **PSProvider**.

Du kan använda `*.*` notation för att referera till den aktuella platsen. Du kan använda `Set-Location` för att ändra till **CurrentVersion** -registerposten först:

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Du kan också använda den inbyggda HKLM-PSDrive med `Set-Location`:

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Du kan sedan använda `*.*` notation för den aktuella platsen för att lista egenskaperna utan att ange en fullständig sökväg:

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

Ökning av sökvägar fungerar på samma sätt som i fil systemet, så från den här platsen kan du hämta **ItemProperty** -listan för `HKLM:\SOFTWARE\Microsoft\Windows\Help` med hjälp av `Get-ItemProperty -Path ..\Help`.

## <a name="getting-a-single-registry-entry"></a>Hämta en enskild register post

Om du vill hämta en speciell post i en register nyckel kan du använda en av flera olika metoder. I det här exemplet hittas värdet för **DevicePath** i `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.

Använd `Get-ItemProperty`med parametern **Path** för att ange namnet på nyckeln och parametern **Name** för att ange namnet på **DevicePath** -posten.

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

Det här kommandot returnerar standard egenskaperna för Windows PowerShell och egenskapen **DevicePath** .

> [!NOTE]
> Även om `Get-ItemProperty` har **filter**-, **include**-och **exkluderings** parametrar, kan de inte användas för att filtrera efter egenskaps namn. De här parametrarna avser register nycklar, som är objekt Sök vägar och inte register poster. Register poster som är objekt egenskaper.

Ett annat alternativ är att använda kommando rads verktyget REG. exe. Om du vill ha hjälp med REG. exe skriver du `reg.exe /?` i kommando tolken. Du hittar posten DevicePath genom att använda REG. exe, som du ser i följande kommando:

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

Du kan också använda **WshShell** com-objektet för att hitta vissa register poster, men den här metoden fungerar inte med stora binära data eller med register post namn som innehåller tecken som "\\"). Lägg till egenskaps namnet till objekt Sök vägen med en \\ avgränsare:

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

## <a name="setting-a-single-registry-entry"></a>Ange en enskild register post

Om du vill ändra en speciell post i en register nyckel kan du använda en av flera olika metoder. I det här exemplet ändras **Sök vägs** posten under `HKEY_CURRENT_USER\Environment`. I **Sök vägs** posten anges var du hittar körbara filer.

1. Hämta det aktuella värdet för **Sök vägs** posten med `Get-ItemProperty`.
2. Lägg till det nya värdet och skilj det till ett `;`.
3. Använd `Set-ItemProperty` med den angivna nyckeln, post namnet och värdet för att ändra register posten.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> Även om `Set-ItemProperty` har **filter**-, **include**-och **exkluderings** parametrar, kan de inte användas för att filtrera efter egenskaps namn. Dessa parametrar avser register nycklar, som är objekt Sök vägar, och inte register poster, som är objekt egenskaper.

Ett annat alternativ är att använda kommando rads verktyget REG. exe. Om du vill ha hjälp med REG. exe skriver du **reg. exe/?**
i en kommando tolk.

I följande exempel ändras **Sök vägs** posten genom att du tar bort sökvägen som lagts till i exemplet ovan.
`Get-ItemProperty` används fortfarande för att hämta det aktuella värdet för att undvika att behöva parsa strängen som returneras från `reg query`. **Substring** -och **LastIndexOf** -metoderna används för att hämta den senaste sökvägen som lagts till i **Sök vägs** posten.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

## <a name="creating-new-registry-entries"></a>Skapa nya register poster

Om du vill lägga till en ny post med namnet "PowerShellPath" i **CurrentVersion** -nyckeln använder du `New-ItemProperty` med sökvägen till nyckeln, post namnet och värdet för posten. I det här exemplet tar vi värdet för variabeln Windows PowerShell `$PSHome`, som lagrar sökvägen till installations katalogen för Windows PowerShell.

Du kan lägga till den nya posten i nyckeln med hjälp av följande kommando, och kommandot returnerar också information om den nya posten:

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

**PropertyType** måste vara namnet på en **Microsoft. Win32. RegistryValueKind** -uppräknings medlem från följande tabell:

|PropertyType-värde|Innebörd|
|----------------------|-----------|
|Binär|Binära data|
|DWord|Ett tal som är en giltig UInt32|
|ExpandString|En sträng som kan innehålla miljövariabler som expanderas dynamiskt|
|Multisträng|En flerradig sträng|
|Sträng|Valfritt sträng värde|
|QWord|8 byte binära data|

> [!NOTE]
> Du kan lägga till en register post till flera platser genom att ange en matris med värden för parametern **Path** :

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Du kan också skriva över ett befintligt register post värde genom att lägga till parametern **Force** till alla `New-ItemProperty`-kommandon.

## <a name="renaming-registry-entries"></a>Byta namn på register poster

Om du vill byta namn på posten **PowerShellPath** till "PSHome" använder `Rename-ItemProperty`:

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

Om du vill visa det omdöpta värdet lägger du till parametern **Passthru** i kommandot.

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

## <a name="deleting-registry-entries"></a>Tar bort register poster

Om du vill ta bort register posterna PSHome och PowerShellPath använder du `Remove-ItemProperty`:

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
