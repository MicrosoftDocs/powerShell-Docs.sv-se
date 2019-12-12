---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Hantera Windows PowerShell-enheter
ms.openlocfilehash: 5d1aba459caeaab2542e17e74534da6713b0faa9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "70215520"
---
# <a name="managing-windows-powershell-drives"></a>Hantera Windows PowerShell-enheter

En *Windows PowerShell-enhet* är en data lager plats som du kan komma åt som en fil system enhet i Windows PowerShell. Windows PowerShell-providern skapar några enheter åt dig, till exempel fil system enheter (inklusive C: och D:), register enheterna (HKCU: och HKLM:) och certifikat enheten (cert:) och du kan skapa egna Windows PowerShell-enheter. De här enheterna är mycket användbara, men de är bara tillgängliga i Windows PowerShell. Du kan inte komma åt dem genom att använda andra Windows-verktyg, till exempel Utforskaren eller cmd. exe.

Windows PowerShell använder substantiv, **PSDrive**, för kommandon som fungerar med Windows PowerShell-enheter. Om du vill ha en lista över Windows PowerShell-enheter i Windows PowerShell-sessionen använder du cmdleten **Get-PSDrive** .

```
PS> Get-PSDrive

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
Alias      Alias
C          FileSystem    C:\                                 ...And Settings\me
cert       Certificate   \
D          FileSystem    D:\
Env        Environment
Function   Function
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
Variable   Variable
```

Även om enheterna i visningen varierar med enheterna i systemet, kommer listan att se ut ungefär som utdata från kommandot **Get-PSDrive** som visas ovan.

Fil Systems enheter är en delmängd av Windows PowerShell-enheterna. Du kan identifiera fil system enheterna med posten FileSystem i kolumnen Provider. (Fil system enheter i Windows PowerShell stöds av Windows PowerShell-providern.)

Om du vill se syntaxen för **Get-PSDrive** -cmdleten skriver du ett **get-kommando-** kommando med parametern **syntax** :

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

Med parametern **PSProvider** kan du bara visa de Windows PowerShell-enheter som stöds av en viss Provider. Om du till exempel bara vill visa de Windows PowerShell-enheter som stöds av Windows PowerShell-filprovidern, skriver du in kommandot **Get-PSDrive** med parametern **PSProvider** och värdet **filesystem** :

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

Om du vill visa de Windows PowerShell-enheter som representerar registreringsdatafiler använder du parametern **PSProvider** för att endast visa de Windows PowerShell-enheter som stöds av Windows PowerShell-registernyckeln:

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

Du kan också använda standard plats-cmdlet: ar med Windows PowerShell-enheter:

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

## <a name="adding-new-windows-powershell-drives-new-psdrive"></a>Lägga till nya Windows PowerShell-enheter (New-PSDrive)

Du kan lägga till egna Windows PowerShell-enheter med kommandot **New-PSDrive** . Hämta syntaxen för kommandot **New-PSDrive** genom att ange kommandot **Get-kommandot** med parametern **syntax** :

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

Om du vill skapa en ny Windows PowerShell-enhet måste du ange tre parametrar:

- Ett namn på enheten (du kan använda alla giltiga Windows PowerShell-namn)

- PSProvider (Använd "FileSystem" för fil system platser och "Registry" för register platser)

- Roten, det vill säga sökvägen till roten för den nya enheten

Du kan till exempel skapa en enhet med namnet "Office" som är mappad till den mapp som innehåller Microsoft Office-program på datorn, till exempel **C:\\programfiler\\Microsoft Office\\Office11**. Skriv följande kommando för att skapa enheten:

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Microsoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> I allmänhet är sökvägar inte Skift läges känsliga.

Du kan referera till den nya Windows PowerShell-enheten på samma sätt som du gör med Windows PowerShell-enheter – efter dess namn följt av ett kolon ( **:** ).

En Windows PowerShell-enhet kan göra många aktiviteter mycket enklare. Några av de viktigaste nycklarna i Windows-registret har till exempel extremt långa sökvägar, vilket gör det svårt att komma åt och svårt att komma ihåg. Viktig konfigurations information finns i **HKEY_LOCAL_MACHINE\\program vara\\Microsoft\\Windows\\CurrentVersion**. Om du vill visa och ändra objekt i register nyckeln CurrentVersion, kan du skapa en Windows PowerShell-enhet som är rotad i nyckeln genom att skriva:

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\Windows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

Du kan sedan ändra plats till **cvkey:** enheten på samma sätt som med andra enheter:

```
PS> cd cvkey:
```

eller:

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

Cmdlet: en New-PsDrive lägger bara till den nya enheten till den aktuella Windows PowerShell-sessionen. Om du stänger Windows PowerShell-fönstret går den nya enheten förlorad. Om du vill spara en Windows PowerShell-enhet använder du cmdleten export-Console för att exportera den aktuella Windows PowerShell-sessionen och använder sedan PowerShell. exe **PSConsoleFile** -parametern för att importera den. Eller Lägg till den nya enheten i Windows PowerShell-profilen.

## <a name="deleting-windows-powershell-drives-remove-psdrive"></a>Ta bort Windows PowerShell-enheter (Remove-PSDrive)

Du kan ta bort enheter från Windows PowerShell med cmdleten **Remove-PSDrive** . Cmdlet: en **Remove-PSDrive** är enkel att använda. Om du vill ta bort en Windows PowerShell-enhet anger du bara namnet på Windows PowerShell-enheten.

Om du till exempel har lagt till **Office:** Windows PowerShell-enheten, som du ser i avsnittet **New-PSDrive** , kan du ta bort den genom att skriva:

```powershell
Remove-PSDrive -Name Office
```

För att ta bort **cvkey:** Windows PowerShell-enheten, som också visas i avsnittet **New-PSDrive** , använder du följande kommando:

```powershell
Remove-PSDrive -Name cvkey
```

Det är enkelt att ta bort en Windows PowerShell-enhet, men du kan inte ta bort den när du befinner dig i enheten. Till exempel:

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

## <a name="adding-and-removing-drives-outside-windows-powershell"></a>Lägga till och ta bort enheter utanför Windows PowerShell

Windows PowerShell identifierar fil Systems enheter som läggs till eller tas bort i Windows, inklusive nätverks enheter som är mappade, USB-enheter som är anslutna och enheter som tas bort med hjälp av kommandot **net use** eller metoden **wscript. NetworkMapNetworkDrive** och **RemoveNetworkDrive** från ett Windows Script Host-skript (WSH).
