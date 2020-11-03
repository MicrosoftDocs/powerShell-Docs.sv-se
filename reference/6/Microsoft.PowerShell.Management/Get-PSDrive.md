---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psdrive?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSDrive
ms.openlocfilehash: f5000ec88defda441d5f31f6ead5d8c37412857b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266798"
---
# Get-PSDrive

## SAMMANFATTNING
Hämtar enheter i den aktuella sessionen.

## SYNTAX

### Namn (standard)

```
Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [<CommonParameters>]
```

### LiteralName

```
Get-PSDrive [-LiteralName] <String[]> [-Scope <String>] [-PSProvider <String[]>] [<CommonParameters>]
```

## BESKRIVNING

`Get-PSDrive`Cmdlet: en hämtar enheterna i den aktuella sessionen. Du kan hämta en viss enhet eller alla enheter i sessionen.

Denna cmdlet hämtar följande typer av enheter:

- Logiska Windows-enheter på datorn, inklusive enheter som är mappade till nätverks resurser.
- Enheter som exponeras av PowerShell-leverantörer (till exempel certifikatet:, funktion:, och alias: enheter) och HKLM: och HKCU: enheter som exponeras av Windows PowerShell-registernyckeln.
- Temporära enheter och beständiga mappade nätverks enheter som du skapar med hjälp av New-PSDrive-cmdlet: en.

Från och med Windows PowerShell 3,0 kan parametern **persist** för `New-PSDrive` cmdleten skapa mappade nätverks enheter som sparas på den lokala datorn och som är tillgängliga i andra sessioner. Mer information finns i New-PSDrive.

Med början i Windows PowerShell 3,0, när en extern enhet är ansluten till datorn, lägger Windows PowerShell automatiskt till en PSDrive i fil systemet som representerar den nya enheten.
Du behöver inte starta om Windows PowerShell. När en extern enhet kopplas bort från datorn tar Windows PowerShell automatiskt bort PSDrive som representerar den borttagna enheten.

## EXEMPEL

### Exempel 1: Hämta enheter i den aktuella sessionen

```
PS C:\> Get-PSDrive

Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
Alias                                  Alias
C                 202.06      23718.91 FileSystem    C:\
Cert                                   Certificate   \
D                1211.06     123642.32 FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
Variable                               Variable
```

Det här kommandot hämtar enheterna i den aktuella sessionen.

Utdata visar hård disken (C:), CD-ROM-enhet (D:) och de enheter som exponeras av Windows PowerShell-providern (alias:, cert:, kuvert:, funktion:, HKCU:, HKLM: och variabel:).

### Exempel 2: Hämta en enhet på datorn

```
PS C:\foo> Get-PSDrive D

Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
D                1211.06     123642.32 FileSystem    D:\
```

Det här kommandot hämtar enhets beteckningen D: på datorn. Observera att enhets beteckningen i kommandot inte följs av ett kolon.

### Exempel 3: Hämta alla enheter som stöds av Windows PowerShell-filsystem-providern

```
PS C:\> Get-PSDrive -PSProvider FileSystem
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                                    A:\
C                 202.06      23718.91 FileSystem    C:\
D                1211.06     123642.32 FileSystem    D:\
G                 202.06        710.91 FileSystem    \\Music\GratefulDead
```

Det här kommandot hämtar alla enheter som stöds av Windows PowerShell-providern. Detta inkluderar fasta enheter, logiska partitioner, mappade nätverks enheter och temporära enheter som du skapar med hjälp av New-PSDrive-cmdleten.

### Exempel 4: kontrol lera om en enhet används som namn på en Windows PowerShell-enhet

```powershell
if (Get-PSDrive X -ErrorAction SilentlyContinue) {
    Write-Host 'The X: drive is already in use.'
} else {
    New-PSDrive -Name X -PSProvider Registry -Root HKLM:\SOFTWARE
}
```

Det här kommandot kontrollerar om X-enheten redan används som namnet på Windows PowerShell-enheten.
Om den inte är det använder kommandot `New-PSDrive` cmdleten för att skapa en tillfällig enhet som är mappad till HKLM: \ program register nyckel.

### Exempel 5: jämför typerna av filer system enheter

```
PS C:\> Get-PSDrive -PSProvider FileSystem
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                                    A:\
C                 202.06      23718.91 FileSystem    C:\
D                1211.06     123642.32 FileSystem    D:\
G                 202.06        710.91 FileSystem    \\Music\GratefulDead
X                                      Registry      HKLM:\Network

PS C:\> net use
New connections will be remembered.
Status       Local     Remote                    Network
-------------------------------------------------------------------------------
OK           G:        \\Server01\Public         Microsoft Windows Network

PS C:\> [System.IO.DriveInfo]::GetDrives() | Format-Table
Name DriveType DriveFormat IsReady AvailableFreeSpace TotalFreeSpace TotalSize     RootDirectory VolumeLabel
---- --------- ----------- ------- ------------------ -------------- ---------     ------------- -----------
A:\    Network               False                                                 A:\
C:\      Fixed NTFS          True  771920580608       771920580608   988877418496  C:\           Windows
D:\      Fixed NTFS          True  689684144128       689684144128   1990045179904 D:\           Big Drive
E:\      CDRom               False                                                 E:\
G:\    Network NTFS          True      69120000           69120000       104853504 G:\           GratefulDead

PS N:\> Get-CimInstance -Class Win32_LogicalDisk

DeviceID DriveType ProviderName   VolumeName         Size          FreeSpace
-------- --------- ------------   ----------         ----          ---------
A:       4
C:       3                        Windows            988877418496  771926069248
D:       3                        Big!              1990045179904  689684144128
E:       5
G:       4         \\Music\GratefulDead              988877418496  771926069248


PS C:\> Get-CimInstance -Class Win32_NetworkConnection
LocalName RemoteName            ConnectionState Status
--------- ----------            --------------- ------
G:        \\Music\GratefulDead  Connected       OK
```

I det här exemplet jämförs de typer av fil Systems enheter som visas av `Get-PSDrive` till de som visas med hjälp av andra metoder. Det här exemplet visar olika sätt att visa enheter i Windows PowerShell, och det visar att sessionsbaserade enheter som skapats med hjälp av New-PSDrive-cmdleten endast är tillgängliga i Windows PowerShell.

Det första kommandot använder `Get-PSDrive` för att hämta alla fil system enheter i sessionen. Detta inkluderar de fasta enheterna (C: och D:), en mappad nätverks enhet (G:) som skapats med hjälp av **persist** -parametern i `New-PSDrive` och en PowerShell-enhet (T:) som skapats med hjälp av `New-PSDrive` utan **persist** -parametern.

Kommandot **net use** visar Windows-anslutna nätverks enheter, i det här fallet visas endast G-enheten. Den visar inte X: enheten som skapades av `New-PSDrive` . Det visar att enheten G: även mappas till \\ \\ musik \\ GratefulDead.

Det tredje kommandot använder metoden **GetDrives** i klassen Microsoft .NET Framework **system. io. DriveInfo** . Det här kommandot hämtar Windows fil system enheter, inklusive enhet G:, men den hämtar inte enheterna som skapats av `New-PSDrive` .

Det fjärde kommandot använder `Get-CimInstance` cmdleten för att hämta instanserna av klassen **Win32_LogicalDisk** . Den returnerar enheterna A:, C:, D:, E:, och G:, men inte enheterna som skapats av `New-PSDrive` .

Det sista kommandot använder `Get-CimInstance` cmdleten för att Visa instanserna av klassen **Win32_NetworkConnection** . Som **net use** returnerar den bara den permanenta G: enheten som skapats av `New-PSDrive` .

## PARAMETRAR

### -LiteralName

Anger namnet på enheten.

Värdet för **LiteralName** används exakt som det har angetts. Inga tecken tolkas som jokertecken. Om namnet innehåller escape-tecken, omger du det med enkla citat tecken. Enkla citat tecken anger att Windows PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String[]
Parameter Sets: LiteralName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Anger, som en sträng mat ris, namnet eller namnet på de enheter som denna cmdlet hämtar i åtgärden.
Ange enhets namnet eller bokstaven utan kolon (:).

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PSProvider

Anger, som en sträng mat ris, Windows PowerShell-providern. Denna cmdlet hämtar bara de enheter som stöds av den här providern. Skriv namnet på en provider, till exempel fil system, register eller certifikat.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Omfattning

Anger omfånget där denna cmdlet hämtar enheterna.

De acceptabla värdena för den här parametern är:

- Global
- Lokal
- Skript
- ett tal i förhållande till det aktuella omfånget (0 till antalet omfattningar, där 0 är det aktuella omfånget och 1 är överordnat). "Local" är standardvärdet.

Mer information finns i [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Det går inte att skicka pipe-objekt till denna cmdlet.

## UTDATA

### System.Management.Automation.PSDriveInfo

Denna cmdlet returnerar objekt som representerar enheterna i sessionen.

## ANTECKNINGAR

* Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst. Om du vill visa en lista över tillgängliga providers i sessionen använder du `Get-PSProvider` cmdleten. Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).
* Mappade nätverks enheter som skapas med hjälp av parametern **persist** i New-PSDrive-cmdlet är bara knutna till ett användar konto. Mappade nätverks enheter som du skapar i sessioner som startas med alternativet Kör som administratör eller med autentiseringsuppgifterna för en annan användare visas inte i sessioner som startas utan uttryckliga autentiseringsuppgifter eller med autentiseringsuppgifterna för den aktuella användaren.

## RELATERADE LÄNKAR

[New-PSDrive](New-PSDrive.md)

[Remove-PSDrive](Remove-PSDrive.md)

[Get-PSProvider](Get-PSProvider.md)
