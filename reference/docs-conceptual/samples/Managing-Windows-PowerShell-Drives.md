---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Hantera Windows PowerShell-enheter
ms.assetid: bd809e38-8de9-437a-a250-f30a667d11b4
ms.openlocfilehash: cfc5418e9d2efb1a786817e1b941d75e22291742
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405435"
---
# <a name="managing-windows-powershell-drives"></a>Hantera Windows PowerShell-enheter

En *Windows PowerShell-enhet* är en lagringsplats för data som du har åtkomst till som en filsystemets enhet på Windows PowerShell. Windows PowerShell-providers skapa vissa enheter för dig, som filsystemet enheter (inklusive C: och D:), registret enheter (HKCU: och HKLM:), och den certifikat-enheten (Cert:), och du kan skapa egna Windows PowerShell-enheter. Dessa enheter är mycket användbara, men de är tillgängliga i Windows PowerShell. Du kan inte komma åt dem från andra Windows-verktyg, till exempel Utforskaren eller Cmd.exe.

Windows PowerShell använder substantiv, **PSDrive**, för kommandona som fungerar med Windows PowerShell-enheter. En lista med Windows PowerShell-enheter i Windows PowerShell-sessionen, använda den **Get-PSDrive** cmdlet.

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

Även om enheterna i visningen variera med enheter på datorn, på listan ser ut ungefär som utdata från den **Get-PSDrive** kommandot ovan.

Enheter är en delmängd av Windows PowerShell-enheter. Du kan identifiera filen systemenheter av filsystem posten i kolumnen providern. (Filen systemenheter i Windows PowerShell stöds av filsystem för Windows PowerShell-providern.)

Se syntaxen för den **Get-PSDrive** cmdlet, ange ett **Get-Command** med den **Syntax** parameter:

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

Den **PSProvider** parametern kan du visa endast i Windows PowerShell-enheter som stöds av en viss provider. För att visa endast de Windows PowerShell-enheter som stöds av filsystem för Windows PowerShell-providern, exempelvis en **Get-PSDrive** med den **PSProvider** parametern och  **Filsystem** värde:

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

Du kan visa de Windows PowerShell-enheter som representerar registreringsdatafilerna den **PSProvider** att visa endast i Windows PowerShell-enheter som stöds av registerprovidern för Windows PowerShell:

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

Du kan också använda standard-plats-cmdlets med Windows PowerShell-enheter:

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

### <a name="adding-new-windows-powershell-drives-new-psdrive"></a>Att lägga till nya Windows PowerShell-enheter (ny PSDrive)

Du kan lägga till egna Windows PowerShell-enheter med hjälp av den **New PSDrive** kommando. Som hämtar syntaxen för den **New-PSDrive** kommandot, ange den **Get-Command** med den **Syntax** parameter:

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

Om du vill skapa en ny Windows PowerShell-enhet, måste du ange tre parametrar:

- Ett namn för enheten (du kan använda valfritt giltigt namn för Windows PowerShell)

- PSProvider (Använd ”filsystem” i sökvägar för system och ”registret” för registret platser)

- Roten, det vill säga sökväg till roten i den nya enheten

Du kan till exempel skapa en enhet med namnet ”Office” som är mappad till den mapp som innehåller Microsoft Office-program på datorn, till exempel **C:\\programfiler\\Microsoft Office\\OFFICE11**. För att skapa enheten, skriver du följande kommando:

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Micr
osoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> I allmänhet är sökvägar inte skiftlägeskänsliga.

Du refererar till den nya Windows PowerShell-enheten som du gör att alla enheter i Windows PowerShell - efter dess namn följt av ett kolon (**:**).

En Windows PowerShell-enhet kan göra många av de uppgifter som är mycket enklare. Till exempel ha några av de viktigaste nycklarna i Windows-registret extremt långa sökvägar, vilket gör dem krånglig att åtkomst och svårt att komma ihåg. Viktig konfigurationsinformation finns **HKEY_LOCAL_MACHINE\\programvara\\Microsoft\\Windows\\CurrentVersion**. Om du vill visa och ändra objekt i registernyckeln CurrentVersion, kan du skapa en Windows PowerShell-enhet är rotad i nyckeln genom att skriva:

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\W
indows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

Du kan ändra platsen till den **cvkey:** enhet precis som alla andra enheter:''

`PS> cd cvkey:`

eller:

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

Cmdleten New-PsDrive lägger till den nya enheten endast till den aktuella Windows PowerShell-sessionen. Om du stänger Windows PowerShell-fönstret, går den nya enheten förlorad. Använda cmdleten Export-konsolen för att exportera den aktuella Windows PowerShell-sessionen för att spara en Windows PowerShell-enhet, och sedan använda PowerShell.exe **PSConsoleFile** parameter för att importera den. Eller Lägg till den nya enheten i din profil för Windows PowerShell.

### <a name="deleting-windows-powershell-drives-remove-psdrive"></a>Tar bort Windows PowerShell-enheter (Remove-PSDrive)

Du kan ta bort enheter från Windows PowerShell med hjälp av den **Remove-PSDrive** cmdlet. Den **Remove-PSDrive** cmdlet är lätt att använda; om du vill ta bort en specifik Windows PowerShell-enhet måste du bara ange enhetsnamnet för Windows PowerShell.

Exempel: Om du har lagt till den **Office:** Windows PowerShell-enhet, enligt den **New PSDrive** avsnittet, kan du radera den genom att skriva:

```powershell
Remove-PSDrive -Name Office
```

Att ta bort den **cvkey:** Windows PowerShell enhet, även visas i den **New PSDrive** avsnittet använder du följande kommando:

```powershell
Remove-PSDrive -Name cvkey
```

Det är enkelt att ta bort en Windows PowerShell-enhet, men du kan inte ta bort den när du arbetar med enheten. Till exempel:

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

### <a name="adding-and-removing-drives-outside-windows-powershell"></a>Att lägga till och ta bort enheter utanför Windows PowerShell

Windows PowerShell identifierar enheter som läggs till eller tas bort i Windows, inklusive nätverksenheter som är mappade, USB-enheter som är anslutna och enheter som har tagits bort genom att använda antingen den **nätverksanv** kommando eller  **WScript.NetworkMapNetworkDrive** och **RemoveNetworkDrive** metoder från ett skript för Windows Script Host (WSH).