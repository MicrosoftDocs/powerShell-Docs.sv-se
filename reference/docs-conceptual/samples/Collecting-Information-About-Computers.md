---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Samla in information om datorer
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: 99125ef701705c20d4e955c79eaa3469ce4d58fb
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404804"
---
# <a name="collecting-information-about-computers"></a>Samla in information om datorer

Cmdlet: ar från **CimCmdlets** modul är den viktigaste cmdletar för allmänna aktiviteter på systemnivå.
Alla inställningar för kritiskt undersystem exponeras via WMI.
Dessutom behandlas data som objekt som finns i samlingar med ett eller flera objekt med WMI.
Eftersom Windows PowerShell även fungerar med objekt och har en pipeline som gör att du kan hantera en eller flera objekt på samma sätt kan du utföra vissa avancerade åtgärder med mycket lite av allmän WMI-åtkomst.

Följande exempel visar hur du samlar in specifik information med hjälp av `Get-CimInstance` mot en valfri dator.
Vi anger den **ComputerName** med punkt-värde för parametern (**.**), som representerar den lokala datorn.
Du kan ange ett namn eller IP-adress som är associerade med en annan dator som du kan nå via WMI.
Om du vill hämta information om den lokala datorn, kan du utelämna den **ComputerName** parametern.

### <a name="listing-desktop-settings"></a>Visa en lista över inställningar för fjärrskrivbord

Vi börjar med ett kommando som samlar in information om datorerna på den lokala datorn.

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName .
```

Detta returnerar information för alla datorer, oavsett om de är används eller inte.

> [!NOTE]
> Information som returneras av vissa WMI-klasser kan vara mycket detaljerade och ofta innehålla metadata om WMI-klass.
Eftersom de flesta av dessa metadataegenskaper har namn som börjar med **Cim**, du kan filtrera egenskaper med hjälp av `Select-Object`.
Ange den **- ExcludeProperty** med ”Cim *” som värde för parametern.
Till exempel:

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

Om du vill filtrera bort metadata, använder du en pipelineoperator (|) för att skicka resultatet av den `Get-CimInstance` för att `Select-Object -ExcludeProperty "CIM*"`.

### <a name="listing-bios-information"></a>Visa en lista över BIOS-informationen

WMI **Win32_BIOS** klass returnerar ganska compact och fullständig information om systemets BIOS på den lokala datorn:

```powershell
Get-CimInstance -ClassName Win32_BIOS -ComputerName .
```

### <a name="listing-processor-information"></a>Visa en lista över processorinformation

Du kan hämta information om allmänna med hjälp av WMI **Win32_Processor** class, även om du förmodligen vill filtrera informationen:

```powershell
Get-CimInstance -ClassName Win32_Processor -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

För en allmän beskrivningssträng av processortypen, kan du bara returnera den **SystemType** egenskapen:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

### <a name="listing-computer-manufacturer-and-model"></a>Visa en lista över datortillverkare och modell

Datorinformation för modellen är även tillgänglig från **Win32_ComputerSystem**.
Visad standardutdata behöver inte någon filtrering för att tillhandahålla OEM-data:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

Dina utdata från kommandon som detta tillhandahåller som returnera information direkt från viss maskinvara, är endast lika bra som de data du har.
Viss information är inte korrekt konfigurerad av maskinvarutillverkare och kan därför vara otillgängliga.

### <a name="listing-installed-hotfixes"></a>Lista över installerade snabbkorrigeringar

Du kan lista alla installerade snabbkorrigeringar med hjälp av **Win32_QuickFixEngineering**:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName .
```

Den här klassen returnerar en lista med snabbkorrigeringar som ser ut så här:

```output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

För mer kortfattad utdata du undanta vissa egenskaper.
Även om du kan använda den `Get-CimInstance`'s **egenskapen** parametern för att välja endast de **HotFixID**, göra så kommer att returnera mer information, eftersom alla metadata visas som standard:

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

Ytterligare data returneras, eftersom egenskapen-parametern i `Get-CimInstance` begränsar egenskaperna som returneras från WMI-klassinstanser inte objektet som returneras till Windows PowerShell.
För att minska utdata kan använda `Select-Object`:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId
```

```output
HotFixId
--------
KB4048951
```

### <a name="listing-operating-system-version-information"></a>Visa en lista över versionsinformation för operativsystemet

Den **Win32_OperatingSystem** klassegenskaper inkludera information om version och service pack.
Du kan uttryckligen välja endast de här egenskaperna för att hämta en sammanfattning från **Win32_OperatingSystem**:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

Du kan också använda jokertecken med den `Select-Object`'s **egenskapen** parametern.
Eftersom alla egenskaper från och med antingen **skapa** eller **ServicePack** är viktigt att du använder här kan vi kan förkorta det till följande format:

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

### <a name="listing-local-users-and-owner"></a>Visa en lista över lokala användare och ägare

Lokala Allmänt användarinformation – antalet licensierade användare, aktuellt antal användare och ägarens namn – finns bland ett urval av **Win32_OperatingSystem**' klassegenskaper.
Du kan uttryckligen välja vilka egenskaper som ska visas så här:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

En mer kortfattad version med jokertecken är:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### <a name="getting-available-disk-space"></a>Hämta ledigt diskutrymme

Om du vill se diskutrymme och ledigt utrymme för lokala enheter, kan du använda Win32_LogicalDisk WMI-klass.
Du behöver se bara instanser med en DriveType av 3 – värdet WMI använder för fasta hårddiskar.

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

### <a name="getting-logon-session-information"></a>Hämta inloggningsinformation för Session

Du kan få allmän information om inloggningssessioner som är kopplade till användare via den **Win32_LogonSession** WMI-klass:

```powershell
Get-CimInstance -ClassName Win32_LogonSession -ComputerName .
```

### <a name="getting-the-user-logged-on-to-a-computer"></a>Hämta användaren loggat in på en dator

Du kan visa användare som är anslutna till en viss dator med hjälp av Win32_ComputerSystem.
Det här kommandot returnerar endast användare som är anslutna till systemet skrivbordet:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName -ComputerName .
```

### <a name="getting-local-time-from-a-computer"></a>Hämta lokal tid från en dator

Du kan hämta den aktuella lokala tiden på en specifik dator med hjälp av den **Win32_LocalTime** WMI-klass.

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

### <a name="displaying-service-status"></a>Visa Status för tjänsten

Om du vill visa status för alla tjänster på en specifik dator som du lokalt kan använda den `Get-Service` cmdlet.
För fjärranslutna datorer, kan du använda den **Win32_Service** WMI-klass.
Om du även använder `Select-Object` att filtrera resultaten till **Status**, **namn**, och **DisplayName**, utdataformat blir nästan identisk från `Get-Service`:

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

Om du vill tillåta fullständig visning av namn för tillfällig trafik med mycket långa namn, kanske du vill använda `Format-Table` med den **AutoSize** och **omsluta** parametrar för att optimera kolumnbredd och Tillåt långa namn du omsluter i stället för trunkerades:

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
