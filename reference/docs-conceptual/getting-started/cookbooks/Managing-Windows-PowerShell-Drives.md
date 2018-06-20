---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Hantera Windows PowerShell-enheter
ms.assetid: bd809e38-8de9-437a-a250-f30a667d11b4
ms.openlocfilehash: cfc5418e9d2efb1a786817e1b941d75e22291742
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951876"
---
# <a name="managing-windows-powershell-drives"></a>Hantera Windows PowerShell-enheter

En *Windows PowerShell-enhet* är en lagringsplats för data som du kan använda som en filsystemets enhet i Windows PowerShell. Windows PowerShell-providers skapa vissa enheter, som filsystemet enheter (inklusive C: och D:), registret enheter (HKCU: och HKLM:), och certifikat-enhet (Cert:), och du kan skapa egna enheter för Windows PowerShell. Dessa enheter är mycket användbara, men de är tillgängliga i Windows PowerShell. Du kan inte komma åt dem med andra Windows-verktyg, till exempel Utforskaren eller Cmd.exe.

Windows PowerShell använder substantiv, **PSDrive**, för kommandon som fungerar med Windows PowerShell-enheter. För en lista över Windows PowerShell-enheter i Windows PowerShell-sessionen, använder den **Get-PSDrive** cmdlet.

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

Även om enheterna i visas varierar beroende på enheter i systemet, listan ser ut ungefär som utdata från den **Get-PSDrive** kommandot ovan.

Enheter är en delmängd av Windows PowerShell-enheter. Du kan identifiera filen systemenheter av filsystem posten i kolumnen providern. (Filen systemenheter i Windows PowerShell stöds av filsystem för Windows PowerShell-providern.)

Syntaxen för den **Get-PSDrive** cmdlet, ange en **Get-Command** kommandot med den **Syntax** parameter:

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

Den **PSProvider** parameter kan du visa endast Windows PowerShell-enheter som stöds av en viss provider. Skriv till exempel för att visa endast de Windows PowerShell-enheter som stöds av filsystem för Windows PowerShell-providern, en **Get-PSDrive** kommandot med de **PSProvider** parameter och  **Filsystem** värde:

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

Använd för att visa Windows PowerShell-enheter som representerar registreringsdatafilerna den **PSProvider** parametern visas bara i Windows PowerShell-enheter som stöds av registret för Windows PowerShell-providern:

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

### <a name="adding-new-windows-powershell-drives-new-psdrive"></a>Lägga till nya Windows PowerShell-enheter (ny PSDrive)

Du kan lägga till egna Windows PowerShell-enheter med hjälp av den **ny PSDrive** kommando. Få syntaxen för den **ny PSDrive** kommandot, anger du den **Get-Command** kommandot med den **Syntax** parameter:

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

Om du vill skapa en ny Windows PowerShell-enhet, måste du ange tre parametrar:

- Ett namn för enheten (du kan använda valfritt giltigt namn för Windows PowerShell)

- PSProvider (Använd ”filsystem” för systemet sökvägar och ”registret” för platser i registret)

- Rot, som är sökvägen till roten för den nya enheten

Du kan till exempel skapa en enhet med namnet ”Office” som är mappad till den mapp som innehåller Microsoft Office-program på datorn, som **C:\\programfiler\\Microsoft Office\\OFFICE11**. Skriv följande kommando för att skapa enheten:

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Micr
osoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> I allmänhet är sökvägar inte skiftlägeskänsliga.

Du refererar till den nya Windows PowerShell-enheten som du har alla enheter i Windows PowerShell - med namnet följt av ett kolon (**:**).

En Windows PowerShell-enhet kan göra många av de uppgifter som är mycket enklare. Till exempel ha några av de viktigaste nycklarna i Windows-registret extremt långa sökvägar, vilket gör dem krånglig att åtkomst och svårt att komma ihåg. Viktig konfigurationsinformation finns **HKEY_LOCAL_MACHINE\\programvara\\Microsoft\\Windows\\CurrentVersion**. Om du vill visa och ändra objekt i registernyckeln CurrentVersion kan skapa du en Windows PowerShell-enhet är rotad i nyckeln genom att skriva:

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

Cmdlet New-PsDrive lägger till den nya enheten endast den aktuella Windows PowerShell-sessionen. Om du stänger fönstret Windows PowerShell, går den nya enheten förlorad. Använd cmdleten Export-konsolen för att exportera den aktuella Windows PowerShell-sessionen om du vill spara en Windows PowerShell-enhet, och sedan använda PowerShell.exe **PSConsoleFile** parameter för att importera den. Eller Lägg till den nya enheten i Windows PowerShell-profilen.

### <a name="deleting-windows-powershell-drives-remove-psdrive"></a>Ta bort Windows PowerShell-enheter (ta bort PSDrive)

Du kan ta bort enheter från Windows PowerShell med hjälp av den **ta bort PSDrive** cmdlet. Den **ta bort PSDrive** cmdlet är enkel att använda; för att ta bort en viss Windows PowerShell-enhet du bara ange namnet för Windows PowerShell-enhet.

Om du har lagt till exempelvis den **Office:** Windows PowerShell-enhet, som visas i den **ny PSDrive** avsnittet, du kan ta bort den genom att skriva:

```powershell
Remove-PSDrive -Name Office
```

Ta bort den **cvkey:** Windows PowerShell enhet, även visas i den **ny PSDrive** avsnittet använder du följande kommando:

```powershell
Remove-PSDrive -Name cvkey
```

Det är lätt att ta bort en Windows PowerShell-enhet, men du kan inte ta bort den när du arbetar med enheten. Till exempel:

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

### <a name="adding-and-removing-drives-outside-windows-powershell"></a>Lägga till och ta bort enheter utanför Windows PowerShell

Windows PowerShell identifierar enheter som lagts till eller tas bort i Windows, inklusive nätverksenheter som är mappade, USB-enheter som är anslutna och enheter som tas bort med hjälp av antingen den **net Använd** kommando eller  **WScript.NetworkMapNetworkDrive** och **RemoveNetworkDrive** metoder från ett skript med Windows Script Host (WSH).