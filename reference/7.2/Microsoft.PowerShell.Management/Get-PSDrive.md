---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psdrive?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSDrive
ms.openlocfilehash: aa83b6318b8e3b07d17cbb3e511bc7ab4aa9a774
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708387"
---
# <span data-ttu-id="e0d30-102">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="e0d30-102">Get-PSDrive</span></span>

## <span data-ttu-id="e0d30-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="e0d30-103">SYNOPSIS</span></span>
<span data-ttu-id="e0d30-104">Hämtar enheter i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="e0d30-104">Gets drives in the current session.</span></span>

## <span data-ttu-id="e0d30-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e0d30-105">SYNTAX</span></span>

### <span data-ttu-id="e0d30-106">Namn (standard)</span><span class="sxs-lookup"><span data-stu-id="e0d30-106">Name (Default)</span></span>

```
Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="e0d30-107">LiteralName</span><span class="sxs-lookup"><span data-stu-id="e0d30-107">LiteralName</span></span>

```
Get-PSDrive [-LiteralName] <String[]> [-Scope <String>] [-PSProvider <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="e0d30-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e0d30-108">DESCRIPTION</span></span>

<span data-ttu-id="e0d30-109">`Get-PSDrive`Cmdlet: en hämtar enheterna i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="e0d30-109">The `Get-PSDrive` cmdlet gets the drives in the current session.</span></span> <span data-ttu-id="e0d30-110">Du kan hämta en viss enhet eller alla enheter i sessionen.</span><span class="sxs-lookup"><span data-stu-id="e0d30-110">You can get a particular drive or all drives in the session.</span></span>

<span data-ttu-id="e0d30-111">Denna cmdlet hämtar följande typer av enheter:</span><span class="sxs-lookup"><span data-stu-id="e0d30-111">This cmdlet gets the following types of drives:</span></span>

- <span data-ttu-id="e0d30-112">Logiska Windows-enheter på datorn, inklusive enheter som är mappade till nätverks resurser.</span><span class="sxs-lookup"><span data-stu-id="e0d30-112">Windows logical drives on the computer, including drives mapped to network shares.</span></span>
- <span data-ttu-id="e0d30-113">Enheter som exponeras av PowerShell-leverantörer (till exempel certifikatet:, funktion:, och alias: enheter) och HKLM: och HKCU: enheter som exponeras av Windows PowerShell-registernyckeln.</span><span class="sxs-lookup"><span data-stu-id="e0d30-113">Drives exposed by PowerShell providers (such as the Certificate:, Function:, and Alias: drives) and the HKLM: and HKCU: drives that are exposed by the Windows PowerShell Registry provider.</span></span>
- <span data-ttu-id="e0d30-114">Temporära enheter och beständiga mappade nätverks enheter som du skapar med hjälp av New-PSDrive-cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="e0d30-114">Session-specified temporary drives and persistent mapped network drives that you create by using the New-PSDrive cmdlet.</span></span>

<span data-ttu-id="e0d30-115">Från och med Windows PowerShell 3,0 kan parametern **persist** för `New-PSDrive` cmdleten skapa mappade nätverks enheter som sparas på den lokala datorn och som är tillgängliga i andra sessioner.</span><span class="sxs-lookup"><span data-stu-id="e0d30-115">Beginning in Windows PowerShell 3.0, the **Persist** parameter of the `New-PSDrive` cmdlet can create mapped network drives that are saved on the local computer and are available in other sessions.</span></span> <span data-ttu-id="e0d30-116">Mer information finns i New-PSDrive.</span><span class="sxs-lookup"><span data-stu-id="e0d30-116">For more information, see New-PSDrive.</span></span>

<span data-ttu-id="e0d30-117">Med början i Windows PowerShell 3,0, när en extern enhet är ansluten till datorn, lägger Windows PowerShell automatiskt till en PSDrive i fil systemet som representerar den nya enheten.</span><span class="sxs-lookup"><span data-stu-id="e0d30-117">Also, beginning in Windows PowerShell 3.0, when an external drive is connected to the computer, Windows PowerShell automatically adds a PSDrive to the file system that represents the new drive.</span></span>
<span data-ttu-id="e0d30-118">Du behöver inte starta om Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0d30-118">You do not need to restart Windows PowerShell.</span></span> <span data-ttu-id="e0d30-119">När en extern enhet kopplas bort från datorn tar Windows PowerShell automatiskt bort PSDrive som representerar den borttagna enheten.</span><span class="sxs-lookup"><span data-stu-id="e0d30-119">Similarly, when an external drive is disconnected from the computer, Windows PowerShell automatically deletes the PSDrive that represents the removed drive.</span></span>

## <span data-ttu-id="e0d30-120">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e0d30-120">EXAMPLES</span></span>

### <span data-ttu-id="e0d30-121">Exempel 1: Hämta enheter i den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="e0d30-121">Example 1: Get drives in the current session</span></span>

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

<span data-ttu-id="e0d30-122">Det här kommandot hämtar enheterna i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="e0d30-122">This command gets the drives in the current session.</span></span>

<span data-ttu-id="e0d30-123">Utdata visar hård disken (C:), CD-ROM-enhet (D:) och de enheter som exponeras av Windows PowerShell-providern (alias:, cert:, kuvert:, funktion:, HKCU:, HKLM: och variabel:).</span><span class="sxs-lookup"><span data-stu-id="e0d30-123">The output shows the hard drive (C:), CD-ROM drive (D:), and the drives exposed by the Windows PowerShell providers (Alias:, Cert:, Env:, Function:, HKCU:, HKLM:, and Variable:).</span></span>

### <span data-ttu-id="e0d30-124">Exempel 2: Hämta en enhet på datorn</span><span class="sxs-lookup"><span data-stu-id="e0d30-124">Example 2: Get a drive on the computer</span></span>

```
PS C:\foo> Get-PSDrive D

Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
D                1211.06     123642.32 FileSystem    D:\
```

<span data-ttu-id="e0d30-125">Det här kommandot hämtar enhets beteckningen D: på datorn.</span><span class="sxs-lookup"><span data-stu-id="e0d30-125">This command gets the D: drive on the computer.</span></span> <span data-ttu-id="e0d30-126">Observera att enhets beteckningen i kommandot inte följs av ett kolon.</span><span class="sxs-lookup"><span data-stu-id="e0d30-126">Note that the drive letter in the command is not followed by a colon.</span></span>

### <span data-ttu-id="e0d30-127">Exempel 3: Hämta alla enheter som stöds av Windows PowerShell-filsystem-providern</span><span class="sxs-lookup"><span data-stu-id="e0d30-127">Example 3: Get all the drives that are supported by the Windows PowerShell file system provider</span></span>

```
PS C:\> Get-PSDrive -PSProvider FileSystem
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                                    A:\
C                 202.06      23718.91 FileSystem    C:\
D                1211.06     123642.32 FileSystem    D:\
G                 202.06        710.91 FileSystem    \\Music\GratefulDead
```

<span data-ttu-id="e0d30-128">Det här kommandot hämtar alla enheter som stöds av Windows PowerShell-providern.</span><span class="sxs-lookup"><span data-stu-id="e0d30-128">This command gets all of the drives that are supported by the Windows PowerShell FileSystem provider.</span></span> <span data-ttu-id="e0d30-129">Detta inkluderar fasta enheter, logiska partitioner, mappade nätverks enheter och temporära enheter som du skapar med hjälp av New-PSDrive-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e0d30-129">This includes fixed drives, logical partitions, mapped network drives, and temporary drives that you create by using the New-PSDrive cmdlet.</span></span>

### <span data-ttu-id="e0d30-130">Exempel 4: kontrol lera om en enhet används som namn på en Windows PowerShell-enhet</span><span class="sxs-lookup"><span data-stu-id="e0d30-130">Example 4: Check to see if a drive is in use as a Windows PowerShell drive name</span></span>

```powershell
if (Get-PSDrive X -ErrorAction SilentlyContinue) {
    Write-Host 'The X: drive is already in use.'
} else {
    New-PSDrive -Name X -PSProvider Registry -Root HKLM:\SOFTWARE
}
```

<span data-ttu-id="e0d30-131">Det här kommandot kontrollerar om X-enheten redan används som namnet på Windows PowerShell-enheten.</span><span class="sxs-lookup"><span data-stu-id="e0d30-131">This command checks to see whether the X drive is already in use as a Windows PowerShell drive name.</span></span>
<span data-ttu-id="e0d30-132">Om den inte är det använder kommandot `New-PSDrive` cmdleten för att skapa en tillfällig enhet som är mappad till HKLM: \ program register nyckel.</span><span class="sxs-lookup"><span data-stu-id="e0d30-132">If it is not, the command uses the `New-PSDrive` cmdlet to create a temporary drive that is mapped to the HKLM:\SOFTWARE registry key.</span></span>

### <span data-ttu-id="e0d30-133">Exempel 5: jämför typerna av filer system enheter</span><span class="sxs-lookup"><span data-stu-id="e0d30-133">Example 5: Compare the types of files system drives</span></span>

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

<span data-ttu-id="e0d30-134">I det här exemplet jämförs de typer av fil Systems enheter som visas av `Get-PSDrive` till de som visas med hjälp av andra metoder.</span><span class="sxs-lookup"><span data-stu-id="e0d30-134">This example compares the types of file system drives that are displayed by `Get-PSDrive` to those displayed by using other methods.</span></span> <span data-ttu-id="e0d30-135">Det här exemplet visar olika sätt att visa enheter i Windows PowerShell, och det visar att sessionsbaserade enheter som skapats med hjälp av New-PSDrive-cmdleten endast är tillgängliga i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e0d30-135">This example demonstrates different ways to display drives in Windows PowerShell, and it shows that session-specific drives created by using the New-PSDrive cmdlet are accessible only in Windows PowerShell.</span></span>

<span data-ttu-id="e0d30-136">Det första kommandot använder `Get-PSDrive` för att hämta alla fil system enheter i sessionen.</span><span class="sxs-lookup"><span data-stu-id="e0d30-136">The first command uses `Get-PSDrive` to get all of the file system drives in the session.</span></span> <span data-ttu-id="e0d30-137">Detta inkluderar de fasta enheterna (C: och D:), en mappad nätverks enhet (G:) som skapats med hjälp av **persist** -parametern i `New-PSDrive` och en PowerShell-enhet (T:) som skapats med hjälp av `New-PSDrive` utan **persist** -parametern.</span><span class="sxs-lookup"><span data-stu-id="e0d30-137">This includes the fixed drives (C: and D:), a mapped network drive (G:) that was created by using the **Persist** parameter of `New-PSDrive`, and a PowerShell drive (T:) that was created by using `New-PSDrive` without the **Persist** parameter.</span></span>

<span data-ttu-id="e0d30-138">Kommandot **net use** visar Windows-anslutna nätverks enheter, i det här fallet visas endast G-enheten.</span><span class="sxs-lookup"><span data-stu-id="e0d30-138">The **net use** command displays Windows mapped network drives, in this case it displays only the G drive.</span></span> <span data-ttu-id="e0d30-139">Den visar inte X: enheten som skapades av `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="e0d30-139">It does not display the X: drive that was created by `New-PSDrive`.</span></span> <span data-ttu-id="e0d30-140">Det visar att enheten G: även mappas till \\ \\ musik \\ GratefulDead.</span><span class="sxs-lookup"><span data-stu-id="e0d30-140">It shows that the G: drive is also mapped to \\\\Music\\GratefulDead.</span></span>

<span data-ttu-id="e0d30-141">Det tredje kommandot använder metoden **GetDrives** i klassen Microsoft .NET Framework **system. io. DriveInfo** .</span><span class="sxs-lookup"><span data-stu-id="e0d30-141">The third command uses the **GetDrives** method of the Microsoft .NET Framework **System.IO.DriveInfo** class.</span></span> <span data-ttu-id="e0d30-142">Det här kommandot hämtar Windows fil system enheter, inklusive enhet G:, men den hämtar inte enheterna som skapats av `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="e0d30-142">This command gets the Windows file system drives, including drive G:, but it does not get the drives created by `New-PSDrive`.</span></span>

<span data-ttu-id="e0d30-143">Det fjärde kommandot använder `Get-CimInstance` cmdleten för att hämta instanserna av klassen **Win32_LogicalDisk** .</span><span class="sxs-lookup"><span data-stu-id="e0d30-143">The fourth command uses the `Get-CimInstance` cmdlet to get the instances of the **Win32_LogicalDisk** class.</span></span> <span data-ttu-id="e0d30-144">Den returnerar enheterna A:, C:, D:, E:, och G:, men inte enheterna som skapats av `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="e0d30-144">It returns the A:, C:, D:, E:, and G: drives, but not the drives created by `New-PSDrive`.</span></span>

<span data-ttu-id="e0d30-145">Det sista kommandot använder `Get-CimInstance` cmdleten för att Visa instanserna av klassen **Win32_NetworkConnection** .</span><span class="sxs-lookup"><span data-stu-id="e0d30-145">The last command uses the `Get-CimInstance` cmdlet to display the instances of the **Win32_NetworkConnection** class.</span></span> <span data-ttu-id="e0d30-146">Som **net use** returnerar den bara den permanenta G: enheten som skapats av `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="e0d30-146">Like **net use**, it returns only the persistent G: drive created by `New-PSDrive`.</span></span>

## <span data-ttu-id="e0d30-147">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="e0d30-147">PARAMETERS</span></span>

### <span data-ttu-id="e0d30-148">-LiteralName</span><span class="sxs-lookup"><span data-stu-id="e0d30-148">-LiteralName</span></span>

<span data-ttu-id="e0d30-149">Anger namnet på enheten.</span><span class="sxs-lookup"><span data-stu-id="e0d30-149">Specifies the name of the drive.</span></span>

<span data-ttu-id="e0d30-150">Värdet för **LiteralName** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="e0d30-150">The value of **LiteralName** is used exactly as it is typed.</span></span> <span data-ttu-id="e0d30-151">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="e0d30-151">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="e0d30-152">Om namnet innehåller escape-tecken, omger du det med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="e0d30-152">If the name includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="e0d30-153">Enkla citat tecken anger att Windows PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="e0d30-153">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="e0d30-154">-Name</span><span class="sxs-lookup"><span data-stu-id="e0d30-154">-Name</span></span>

<span data-ttu-id="e0d30-155">Anger, som en sträng mat ris, namnet eller namnet på de enheter som denna cmdlet hämtar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="e0d30-155">Specifies, as a string array, the name or name of drives that this cmdlet gets in the operation.</span></span>
<span data-ttu-id="e0d30-156">Ange enhets namnet eller bokstaven utan kolon (:).</span><span class="sxs-lookup"><span data-stu-id="e0d30-156">Type the drive name or letter without a colon (:).</span></span>

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

### <span data-ttu-id="e0d30-157">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="e0d30-157">-PSProvider</span></span>

<span data-ttu-id="e0d30-158">Anger, som en sträng mat ris, Windows PowerShell-providern.</span><span class="sxs-lookup"><span data-stu-id="e0d30-158">Specifies, as a string array, the Windows PowerShell provider.</span></span> <span data-ttu-id="e0d30-159">Denna cmdlet hämtar bara de enheter som stöds av den här providern.</span><span class="sxs-lookup"><span data-stu-id="e0d30-159">This cmdlet gets only the drives supported by this provider.</span></span> <span data-ttu-id="e0d30-160">Skriv namnet på en provider, till exempel fil system, register eller certifikat.</span><span class="sxs-lookup"><span data-stu-id="e0d30-160">Type the name of a provider, such as FileSystem, Registry, or Certificate.</span></span>

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

### <span data-ttu-id="e0d30-161">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="e0d30-161">-Scope</span></span>

<span data-ttu-id="e0d30-162">Anger omfånget där denna cmdlet hämtar enheterna.</span><span class="sxs-lookup"><span data-stu-id="e0d30-162">Specifies the scope in which this cmdlet gets the drives.</span></span>

<span data-ttu-id="e0d30-163">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="e0d30-163">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="e0d30-164">Global</span><span class="sxs-lookup"><span data-stu-id="e0d30-164">Global</span></span>
- <span data-ttu-id="e0d30-165">Lokal</span><span class="sxs-lookup"><span data-stu-id="e0d30-165">Local</span></span>
- <span data-ttu-id="e0d30-166">Skript</span><span class="sxs-lookup"><span data-stu-id="e0d30-166">Script</span></span>
- <span data-ttu-id="e0d30-167">ett tal i förhållande till det aktuella omfånget (0 till antalet omfattningar, där 0 är det aktuella omfånget och 1 är överordnat).</span><span class="sxs-lookup"><span data-stu-id="e0d30-167">a number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span> <span data-ttu-id="e0d30-168">"Local" är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="e0d30-168">"Local" is the default.</span></span>

<span data-ttu-id="e0d30-169">Mer information finns i [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="e0d30-169">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

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

### <span data-ttu-id="e0d30-170">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e0d30-170">CommonParameters</span></span>

<span data-ttu-id="e0d30-171">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e0d30-171">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e0d30-172">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e0d30-172">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e0d30-173">INDATA</span><span class="sxs-lookup"><span data-stu-id="e0d30-173">INPUTS</span></span>

### <span data-ttu-id="e0d30-174">Inga</span><span class="sxs-lookup"><span data-stu-id="e0d30-174">None</span></span>

<span data-ttu-id="e0d30-175">Det går inte att skicka pipe-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e0d30-175">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="e0d30-176">UTDATA</span><span class="sxs-lookup"><span data-stu-id="e0d30-176">OUTPUTS</span></span>

### <span data-ttu-id="e0d30-177">System.Management.Automation.PSDriveInfo</span><span class="sxs-lookup"><span data-stu-id="e0d30-177">System.Management.Automation.PSDriveInfo</span></span>

<span data-ttu-id="e0d30-178">Denna cmdlet returnerar objekt som representerar enheterna i sessionen.</span><span class="sxs-lookup"><span data-stu-id="e0d30-178">This cmdlet returns objects that represent the drives in the session.</span></span>

## <span data-ttu-id="e0d30-179">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="e0d30-179">NOTES</span></span>

* <span data-ttu-id="e0d30-180">Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="e0d30-180">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="e0d30-181">Om du vill visa en lista över tillgängliga providers i sessionen använder du `Get-PSProvider` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e0d30-181">To list the providers available in your session, use the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="e0d30-182">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="e0d30-182">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
* <span data-ttu-id="e0d30-183">Mappade nätverks enheter som skapas med hjälp av parametern **persist** i New-PSDrive-cmdlet är bara knutna till ett användar konto.</span><span class="sxs-lookup"><span data-stu-id="e0d30-183">Mapped network drives that are created by using the **Persist** parameter of the New-PSDrive cmdlet are specific to a user account.</span></span> <span data-ttu-id="e0d30-184">Mappade nätverks enheter som du skapar i sessioner som startas med alternativet Kör som administratör eller med autentiseringsuppgifterna för en annan användare visas inte i sessioner som startas utan uttryckliga autentiseringsuppgifter eller med autentiseringsuppgifterna för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="e0d30-184">Mapped network drives that you create in sessions that are started with the Run as administrator option or with the credentials of another user are not visible in sessions that are started without explicit credentials or with the credentials of the current user.</span></span>

## <span data-ttu-id="e0d30-185">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="e0d30-185">RELATED LINKS</span></span>

[<span data-ttu-id="e0d30-186">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="e0d30-186">New-PSDrive</span></span>](New-PSDrive.md)

[<span data-ttu-id="e0d30-187">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="e0d30-187">Remove-PSDrive</span></span>](Remove-PSDrive.md)

[<span data-ttu-id="e0d30-188">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="e0d30-188">Get-PSProvider</span></span>](Get-PSProvider.md)

