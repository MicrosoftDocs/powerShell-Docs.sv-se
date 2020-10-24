---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Samla in information om datorer
description: Den här artikeln beskriver hur du samlas information om dator konfiguration med WMI-och CIM-cmdletar.
ms.openlocfilehash: 5088960ab7c049085a9d7c05ec4571b6fd7e3545
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500597"
---
# <a name="collecting-information-about-computers"></a>Samla in information om datorer

Cmdlets från **CimCmdlets** -modulen är de viktigaste cmdletarna för allmänna system hanterings uppgifter. Alla inställningar för viktiga under system exponeras via WMI. Dessutom behandlar WMI data som objekt som finns i samlingar av ett eller flera objekt. Eftersom Windows PowerShell även fungerar med objekt och har en pipeline som gör att du kan hantera enskilda eller flera objekt på samma sätt, kan du med hjälp av allmän WMI-åtkomst utföra vissa avancerade uppgifter med mycket lite arbete.

## <a name="listing-desktop-settings"></a>Visa Skriv bords inställningar

Vi börjar med ett kommando som samlar in information om Skriv bordets på den lokala datorn.

```powershell
Get-CimInstance -ClassName Win32_Desktop
```

Detta returnerar information för alla skriv bord, oavsett om de används eller inte.

> [!NOTE]
> Information som returneras av vissa WMI-klasser kan vara mycket detaljerad och innehåller ofta metadata om WMI-klassen.

Eftersom de flesta av dessa metadata-egenskaper har namn som börjar med **CIM**kan du filtrera egenskaperna med hjälp av `Select-Object` . Ange parametern **-ExcludeProperty** med "CIM *" som värde. Exempel:

```powershell
Get-CimInstance -ClassName Win32_Desktop | Select-Object -ExcludeProperty "CIM*"
```

Om du vill filtrera bort metadata använder du en pipeline-operator (|) för att skicka `Get-CimInstance` kommandots resultat till `Select-Object -ExcludeProperty "CIM*"` .

## <a name="listing-bios-information"></a>Visa BIOS-information

WMI- **Win32_BIOS** -klassen returnerar ganska kompakt och fullständig information om systemets BIOS på den lokala datorn:

```powershell
Get-CimInstance -ClassName Win32_BIOS
```

## <a name="listing-processor-information"></a>Lista processor information

Du kan hämta allmän processor information med hjälp av WMI: s **Win32_Processor** -klass, men du kommer förmodligen att vilja filtrera informationen:

```powershell
Get-CimInstance -ClassName Win32_Processor | Select-Object -ExcludeProperty "CIM*"
```

För en generisk beskrivnings sträng för processor familjen kan du bara returnera egenskapen **SystemType** :

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

## <a name="listing-computer-manufacturer-and-model"></a>Visa dator tillverkare och modell

Information om dator modeller är också tillgänglig från **Win32_ComputerSystem**. De utdata som visas som standard kommer inte att behöva filtreras för att tillhandahålla OEM-data:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```Output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

Dina utdata från kommandon som det här, som returnerar information direkt från viss maskin vara, är bara lika användbara som de data du har. Viss information är inte korrekt konfigurerad av maskin varu tillverkare och kan därför vara otillgänglig.

## <a name="listing-installed-hotfixes"></a>Visar installerade snabb korrigeringar

Du kan visa en lista med alla installerade snabb korrigeringar med **Win32_QuickFixEngineering**:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering
```

Den här klassen returnerar en lista med snabb korrigeringar som ser ut så här:

```Output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

För fler kortfattad-utdata kanske du vill utesluta vissa egenskaper. Även om du kan använda `Get-CimInstance` **egenskapens egenskaps** parameter för att välja endast **HotFixID**så kommer detta faktiskt att returnera mer information, eftersom alla metadata visas som standard:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -Property HotFixID
```

```Output
InstalledOn           :
Caption               :
Description           :
InstallDate           :
Name                  :
Status                :
CSName                :
FixComments           :
HotFixID              : KB4533002
InstalledBy           :
ServicePackInEffect   :
PSComputerName        :
CimClass              : root/cimv2:Win32_QuickFixEngineering
CimInstanceProperties : {Caption, Description, InstallDate, Name…}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
...
```

Ytterligare data returneras, eftersom **egenskaps** parametern i `Get-CimInstance` begränsar egenskaperna som returneras från WMI-klass instanser, inte objektet som returnerades till PowerShell. För att minska utdata använder du `Select-Object` :

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -Property HotFixId | Select-Object -Property HotFixId
```

```Output
HotFixId
--------
KB4048951
```

## <a name="listing-operating-system-version-information"></a>Visar information om operativ systemets version

**Win32_OperatingSystem** klass egenskaper innehåller versions-och service pack information. Du kan uttryckligen välja endast dessa egenskaper för att hämta en versions informations Sammanfattning från **Win32_OperatingSystem**:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem |
  Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

Du kan också använda jokertecken med `Select-Object` **egenskaps** parametern. Eftersom alla egenskaper som börjar med antingen **build** eller **servicepack** är viktiga för användning här kan vi förkorta detta till följande format:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem | Select-Object -Property Build*,OSType,ServicePack*
```

```Output
BuildNumber             : 18362
BuildType               : Multiprocessor Free
OSType                  : 18
ServicePackMajorVersion : 0
ServicePackMinorVersion : 0
```

## <a name="listing-local-users-and-owner"></a>Lista lokala användare och ägare

Lokal allmän användar information – antal licensierade användare, Aktuellt antal användare och ägarnamn – kan hittas med ett val av **Win32_OperatingSystem** klass egenskaper. Du kan uttryckligen välja vilka egenskaper som ska visas:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem |
  Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

En mer kortfattad-version med jokertecken är:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem | Select-Object -Property *user*
```

## <a name="getting-available-disk-space"></a>Hämtar tillgängligt disk utrymme

Om du vill se disk utrymme och ledigt utrymme för lokala enheter kan du använda klassen Win32_LogicalDisk WMI.
Du behöver bara se instanser med en DriveType av 3 – värdet för WMI använder fasta hård diskar.

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3"
```

```Output
DeviceID DriveType ProviderName VolumeName Size         FreeSpace   PSComputerName
-------- --------- ------------ ---------- ----         ---------   --------------
C:       3                      Local Disk 203912880128 65541357568 .
Q:       3                      New Volume 122934034432 44298250240 .
```

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" |
  Measure-Object -Property FreeSpace,Size -Sum |
    Select-Object -Property Property,Sum
```

```Output
Property           Sum
--------           ---
FreeSpace 109839607808
Size      326846914560
```

## <a name="getting-logon-session-information"></a>Hämta information om inloggningssession

Du kan få allmän information om inloggnings sessioner som är associerade med användare via klassen **Win32_LogonSession** WMI:

```powershell
Get-CimInstance -ClassName Win32_LogonSession
```

## <a name="getting-the-user-logged-on-to-a-computer"></a>Få användaren inloggad på en dator

Du kan visa användaren som är inloggad på ett visst dator system med hjälp av Win32_ComputerSystem. Det här kommandot returnerar bara den användare som är inloggad på system Skriv bordet:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName
```

## <a name="getting-local-time-from-a-computer"></a>Hämta lokal tid från en dator

Du kan hämta den aktuella lokala tiden på en speciell dator med hjälp av **Win32_LocalTime** WMI-klassen.

```powershell
Get-CimInstance -ClassName Win32_LocalTime
```

```Output
Day            : 23
DayOfWeek      : 1
Hour           : 8
Milliseconds   :
Minute         : 52
Month          : 12
Quarter        : 4
Second         : 55
WeekInMonth    : 4
Year           : 2019
PSComputerName :
```

## <a name="displaying-service-status"></a>Visar tjänst status

Om du vill visa status för alla tjänster på en speciell dator kan du använda `Get-Service` cmdleten lokalt. För fjärrsystem kan du använda klassen **Win32_Service** WMI. Om du också använder `Select-Object` för att filtrera resultaten till **status**, **namn**och **DisplayName**är utdataformatet nästan identiskt med `Get-Service` :

```powershell
Get-CimInstance -ClassName Win32_Service | Select-Object -Property Status,Name,DisplayName
```

Om du vill tillåta hela visningen av namn för tillfälliga tjänster med extremt långa namn, kan du använda `Format-Table` med parametrarna **AutoSize** och **wrap** för att optimera kolumn bredden och tillåta långa namn att figursättas i stället för att trunkeras:

```powershell
Get-CimInstance -ClassName Win32_Service | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
