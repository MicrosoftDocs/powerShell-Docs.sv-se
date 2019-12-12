---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Samla in information om datorer
ms.openlocfilehash: 5dc8fcc5f12fdf9e3fc8151d3e50b8b660262c62
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030846"
---
# <a name="collecting-information-about-computers"></a>Samla in information om datorer

Cmdlets från **CimCmdlets** -modulen är de viktigaste cmdletarna för allmänna system hanterings uppgifter.
Alla inställningar för viktiga under system exponeras via WMI.
Dessutom behandlar WMI data som objekt som finns i samlingar av ett eller flera objekt.
Eftersom Windows PowerShell även fungerar med objekt och har en pipeline som gör att du kan hantera enskilda eller flera objekt på samma sätt, kan du med hjälp av allmän WMI-åtkomst utföra vissa avancerade uppgifter med mycket lite arbete.

Följande exempel visar hur du samlar in speciell information med hjälp av `Get-CimInstance` mot en godtycklig dator.
Vi anger parametern **computername** med det punkt värde ( **.** ) som representerar den lokala datorn.
Du kan ange ett namn eller en IP-adress som är kopplad till en dator som du kan komma åt via WMI.
Om du vill hämta information om den lokala datorn kan du utelämna parametern **computername** .

## <a name="listing-desktop-settings"></a>Visa Skriv bords inställningar

Vi börjar med ett kommando som samlar in information om Skriv bordets på den lokala datorn.

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName .
```

Detta returnerar information för alla skriv bord, oavsett om de används eller inte.

> [!NOTE]
> Information som returneras av vissa WMI-klasser kan vara mycket detaljerad och innehåller ofta metadata om WMI-klassen.
Eftersom de flesta av dessa metadata-egenskaper har namn som börjar med **CIM**kan du filtrera egenskaperna med hjälp av `Select-Object`.
Ange parametern **-ExcludeProperty** med "CIM *" som värde.
Till exempel:

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

Om du vill filtrera bort metadata använder du en pipeline-operator (|) för att skicka resultatet från kommandot `Get-CimInstance` till `Select-Object -ExcludeProperty "CIM*"`.

## <a name="listing-bios-information"></a>Visa BIOS-information

WMI- **Win32_BIOS** -klassen returnerar ganska kompakt och fullständig information om systemets BIOS på den lokala datorn:

```powershell
Get-CimInstance -ClassName Win32_BIOS -ComputerName .
```

## <a name="listing-processor-information"></a>Lista processor information

Du kan hämta allmän processor information med hjälp av WMI: s **Win32_Processor** -klass, men du kommer förmodligen att vilja filtrera informationen:

```powershell
Get-CimInstance -ClassName Win32_Processor -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

För en generisk beskrivnings sträng för processor familjen kan du bara returnera egenskapen **SystemType** :

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

## <a name="listing-computer-manufacturer-and-model"></a>Visa dator tillverkare och modell

Information om dator modeller är också tillgänglig från **Win32_ComputerSystem**.
De utdata som visas som standard kommer inte att behöva filtreras för att tillhandahålla OEM-data:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

Dina utdata från kommandon som det här, som returnerar information direkt från viss maskin vara, är bara lika användbara som de data du har.
Viss information är inte korrekt konfigurerad av maskin varu tillverkare och kan därför vara otillgänglig.

## <a name="listing-installed-hotfixes"></a>Visar installerade snabb korrigeringar

Du kan visa en lista med alla installerade snabb korrigeringar med **Win32_QuickFixEngineering**:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName .
```

Den här klassen returnerar en lista med snabb korrigeringar som ser ut så här:

```output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

För fler kortfattad-utdata kanske du vill utesluta vissa egenskaper.
Även om du kan använda `Get-CimInstance`ens **egenskaps** parameter för att välja endast **HotFixID**, returnerar faktiskt mer information, eftersom alla metadata visas som standard:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixID
```

```output
PSShowComputerName    : True
InstalledOn           :
Caption               :
Description           :
InstallDate           :
Name                  :
Status                :
CSName                :
FixComments           :
HotFixID              : KB4048951
InstalledBy           :
ServicePackInEffect   :
PSComputerName        : .
CimClass              : root/cimv2:Win32_QuickFixEngineering
CimInstanceProperties : {Caption, Description, InstallDate, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

Ytterligare data returneras, eftersom egenskaps parametern i `Get-CimInstance` begränsar egenskaperna som returneras från WMI-klass instanser, inte det objekt som returneras till Windows PowerShell.
Använd `Select-Object`för att minska utdata:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId
```

```output
HotFixId
--------
KB4048951
```

## <a name="listing-operating-system-version-information"></a>Visar information om operativ systemets version

**Win32_OperatingSystem** klass egenskaper innehåller versions-och service pack information.
Du kan uttryckligen välja endast dessa egenskaper för att hämta en versions informations Sammanfattning från **Win32_OperatingSystem**:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

Du kan också använda jokertecken med `Select-Object`**egenskaps** parameter.
Eftersom alla egenskaper som börjar med antingen **build** eller **servicepack** är viktiga för användning här kan vi förkorta detta till följande format:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*
```

```output
BuildNumber             : 16299
BuildType               : Multiprocessor Free
OSType                  : 18
ServicePackMajorVersion : 0
ServicePackMinorVersion : 0
```

## <a name="listing-local-users-and-owner"></a>Lista lokala användare och ägare

Lokal allmän användar information – antal licensierade användare, Aktuellt antal användare och ägarnamn – kan hittas med ett val av **Win32_OperatingSystem** klass egenskaper.
Du kan uttryckligen välja vilka egenskaper som ska visas:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

En mer kortfattad-version med jokertecken är:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

## <a name="getting-available-disk-space"></a>Hämtar tillgängligt disk utrymme

Om du vill se disk utrymme och ledigt utrymme för lokala enheter kan du använda klassen Win32_LogicalDisk WMI.
Du behöver bara se instanser med en DriveType av 3 – värdet för WMI använder fasta hård diskar.

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" -ComputerName .

DeviceID DriveType ProviderName VolumeName Size         FreeSpace   PSComputerName
-------- --------- ------------ ---------- ----         ---------   --------------
C:       3                      Local Disk 203912880128 65541357568 .
Q:       3                      New Volume 122934034432 44298250240 .

Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum

Property           Sum
--------           ---
FreeSpace 109839607808
Size      326846914560
```

## <a name="getting-logon-session-information"></a>Hämta information om inloggningssession

Du kan få allmän information om inloggnings sessioner som är associerade med användare via klassen **Win32_LogonSession** WMI:

```powershell
Get-CimInstance -ClassName Win32_LogonSession -ComputerName .
```

## <a name="getting-the-user-logged-on-to-a-computer"></a>Få användaren inloggad på en dator

Du kan visa användaren som är inloggad på ett visst dator system med hjälp av Win32_ComputerSystem.
Det här kommandot returnerar bara den användare som är inloggad på system Skriv bordet:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName -ComputerName .
```

## <a name="getting-local-time-from-a-computer"></a>Hämta lokal tid från en dator

Du kan hämta den aktuella lokala tiden på en speciell dator med hjälp av **Win32_LocalTime** WMI-klassen.

```powershell
Get-CimInstance -ClassName Win32_LocalTime -ComputerName .

Day          : 15
DayOfWeek    : 4
Hour         : 12
Milliseconds :
Minute       : 11
Month        : 6
Quarter      : 2
Second       : 52
WeekInMonth  : 3
Year         : 2017
PSComputerName : .
```

## <a name="displaying-service-status"></a>Visar tjänst status

Om du vill visa status för alla tjänster på en speciell dator kan du använda `Get-Service`-cmdlet: en lokalt.
För fjärrsystem kan du använda klassen **Win32_Service** WMI.
Om du också använder `Select-Object` för att filtrera resultaten till **status**, **namn**och **DisplayName**, är utdataformatet nästan identiskt med `Get-Service`:

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

Om du vill tillåta hela visningen av namn för tillfälliga tjänster med extremt långa namn, kanske du vill använda `Format-Table` med parametrarna **AutoSize** och **wrap** för att optimera kolumn bredden och tillåta långa namn att figursättas i stället för att trunkeras:

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
