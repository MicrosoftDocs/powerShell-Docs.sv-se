---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Samla in information om datorer
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: 7f5a5f6accd57a84e2bcb3d20c14640a8e028791
ms.sourcegitcommit: a9aa5e8d0fab0cbb3e4e6cff0e3ca8c0339ab4e6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/27/2018
---
# <a name="collecting-information-about-computers"></a>Samla in information om datorer

**Get-WmiObject** är den viktigaste cmdleten för allmän system hanteringsuppgifter. Alla kritiska undersystemet inställningar är tillgängliga via WMI. Dessutom behandlas WMI data som objekt i samlingar med ett eller flera objekt. Eftersom Windows PowerShell kan du också fungerar med objekt och har en pipeline som gör att du kan hantera en eller flera objekt på samma sätt, kan du utföra vissa avancerade med mycket lite av allmänna WMI-åtkomst.

Följande exempel visar hur du samlar in specifik information med hjälp av **Get-WmiObject** mot en valfri dator. Anger vi den **ComputerName** parametern med värdet punkt (**.**), som motsvarar den lokala datorn. Du kan ange ett namn eller IP-adress som är associerad med en annan dator som du kan nå via WMI. Om du vill hämta information om den lokala datorn, kan du utelämna den **- ComputerName.**

### <a name="listing-desktop-settings"></a>Visar en lista över inställningar för skrivbord

Vi börjar med ett kommando som samlar in information om de stationära datorer på den lokala datorn.

```powershell
Get-WmiObject -Class Win32_Desktop -ComputerName .
```

Detta returnerar information för alla datorer, oavsett om de är används eller inte.

> [!NOTE]
> Information som returneras av vissa WMI-klasser kan vara mycket detaljerad och ofta innehåller metadata om WMI-klassen. Eftersom de flesta av dessa metadataegenskaper har namn som börjar med ett dubbelt understreck, kan du filtrera egenskaper med Select-Object. Ange egenskaper som börjar med bokstäver med hjälp av **[a – z]*** som värde för egenskapen. Till exempel:

```powershell
Get-WmiObject -Class Win32_Desktop -ComputerName . | Select-Object -Property [a-z]*
```

Om du vill filtrera bort metadata, använder du en pipelineoperator (|) för att skicka resultatet av kommandot Get-WmiObject till `Select-Object -Property [a-z]*`.

### <a name="listing-bios-information"></a>Visar en lista över BIOS-Information

Klassen WMI Win32_BIOS returnerar ganska compact och fullständig information om systemets BIOS på den lokala datorn:

```powershell
Get-WmiObject -Class Win32_BIOS -ComputerName .
```

### <a name="listing-processor-information"></a>Visar en lista över processorinformation

Du kan hämta information om allmänna med hjälp av WMI **Win32_Processor** class, även om du förmodligen vill filtrera informationen:

```powershell
Get-WmiObject -Class Win32_Processor -ComputerName . | Select-Object -Property [a-z]*
```

För en allmän beskrivning av processortypen sträng kan du bara returnera den **SystemType** egenskapen:

```
PS> Get-WmiObject -Class Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

### <a name="listing-computer-manufacturer-and-model"></a>Visar en lista över datortillverkare och modell

Datorinformation för modellen är också tillgänglig från **Win32_ComputerSystem**. Standardutdata visas behöver inte någon filtrering för att tillhandahålla OEM-data:

```
PS> Get-WmiObject -Class Win32_ComputerSystem

Domain              : WORKGROUP
Manufacturer        : Compaq Presario 06
Model               : DA243A-ABA 6415cl NA910
Name                : MyPC
PrimaryOwnerName    : Jane Doe
TotalPhysicalMemory : 804765696
```

Dina utdata från kommandon som den här, som returnerar information direkt från vissa maskinvara är endast lika bra som data som du har. Viss information är inte korrekt konfigurerad av maskinvarutillverkare och kan därför inte tillgänglig.

### <a name="listing-installed-hotfixes"></a>Lista över installerade snabbkorrigeringar

Du kan visa en lista med alla installerade snabbkorrigeringar med hjälp av **Win32_QuickFixEngineering**:

```powershell
Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName .
```

Den här klassen returnerar en lista med snabbkorrigeringar som ser ut så här:

```output
Description         : Update for Windows XP (KB910437)
FixComments         : Update
HotFixID            : KB910437
Install Date        :
InstalledBy         : Administrator
InstalledOn         : 12/16/2005
Name                :
ServicePackInEffect : SP3
Status              :
```

För mer koncis utdata kanske du vill undanta vissa egenskaper. Även om du kan använda den **Get-WmiObject egenskapen** parametern välja endast den **HotFixID**, göra så kommer att returnera mer, eftersom alla metadata visas som standard:

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property HotFixID

HotFixID         : KB910437
__GENUS          : 2
__CLASS          : Win32_QuickFixEngineering
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
```

Ytterligare data returneras eftersom egenskapen parameter i **Get-WmiObject** begränsar egenskaperna som returneras från WMI-klassinstanser inte objektet som returneras till Windows PowerShell. Om du vill minska utdata, Använd **Select-Object**:

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId

HotFixId
--------
KB910437
```

### <a name="listing-operating-system-version-information"></a>Visar en lista över versionsinformation för operativsystemet

Den **Win32_OperatingSystem** klassegenskaper inkludera version och service pack. Du kan uttryckligen välja endast dessa egenskaper att hämta versionsinformation om en sammanfattande från **Win32_OperatingSystem**:

```powershell
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

Du kan också använda jokertecken med den **Select-Object-egenskapen** parameter. Eftersom alla egenskaper som börjar med antingen **skapa** eller **ServicePack** är viktigt att du använder här, kan vi förkorta det till följande format:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*

BuildNumber             : 2600
BuildType               : Uniprocessor Free
OSType                  : 18
ServicePackMajorVersion : 2
ServicePackMinorVersion : 0
```

### <a name="listing-local-users-and-owner"></a>Visar en lista över lokala användare och ägare

Lokala allmän användarinformation, antalet licensierade användare, aktuellt antal användare och ägarens namn – kan hittas med ett urval av **Win32_OperatingSystem** egenskaper. Du kan uttryckligen välja egenskaper som ska visas så här:

```powershell
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

En mer koncis version med jokertecken är:

```powershell
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### <a name="getting-available-disk-space"></a>Hämtning av ledigt diskutrymme

Du kan använda WMI Win32_LogicalDisk klassen om du vill se diskutrymme och ledigt utrymme för lokala enheter. Du behöver se endast instanser med en DriveType av 3 – värdet WMI använder för fasta hårddiskar.

```
PS> Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName .

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 65541357568
Size         : 203912880128
VolumeName   : Local Disk

DeviceID     : Q:
DriveType    : 3
ProviderName :
FreeSpace    : 44298250240
Size         : 122934034432
VolumeName   : New Volume

PS> Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum

Property           Sum
--------           ---
FreeSpace 109839607808
Size      326846914560
```

### <a name="getting-logon-session-information"></a>Hämtning av inloggningsinformationen för Session

Du kan få allmän information om inloggningssessioner som är kopplade till användare via Win32_LogonSession WMI-klassen:

```powershell
Get-WmiObject -Class Win32_LogonSession -ComputerName .
```

### <a name="getting-the-user-logged-on-to-a-computer"></a>Att användaren loggat in på en dator

Du kan visa användare som är anslutna till en viss dator med hjälp av Win32_ComputerSystem. Detta kommando returnerar bara den användaren loggat in på systemet skrivbordet:

```powershell
Get-WmiObject -Class Win32_ComputerSystem -Property UserName -ComputerName .
```

### <a name="getting-local-time-from-a-computer"></a>Hämta lokal tid från en dator

Du kan hämta den aktuella lokala tiden på en specifik dator med hjälp av Win32_LocalTime för WMI-klassen. Eftersom den här klassen som standard visas alla metadata, kanske du vill filtrera den med hjälp av **Select-Object**:

```
PS> Get-WmiObject -Class Win32_LocalTime -ComputerName . | Select-Object -Property [a-z]*

Day          : 15
DayOfWeek    : 4
Hour         : 12
Milliseconds :
Minute       : 11
Month        : 6
Quarter      : 2
Second       : 52
WeekInMonth  : 3
Year         : 2006
```

### <a name="displaying-service-status"></a>Visa Status för tjänsten

Om du vill visa status för alla tjänster på en specifik dator du lokalt kan använda den **Get-Service** cmdlet som tidigare nämnts. Du kan använda WMI Win32_Service-klassen för fjärranslutna system. Om du också använda **Select-Object** att filtrera resultaten till **Status**, **namn**, och **DisplayName**, utdataformatet blir nästan identisk från **Get-Service**:

```powershell
Get-WmiObject -Class Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

Om du vill tillåta fullständig visningen av namn för tillfällig trafik med mycket långa namn, kanske du vill använda **Format-Table** med den **AutoSize** och **omsluter** parametrar , att optimera kolumnbredden och tillåta långa namn du omsluter i stället för trunkerades:

```powershell
Get-WmiObject -Class Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
