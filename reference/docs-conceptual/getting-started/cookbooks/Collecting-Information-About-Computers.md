---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Samla in information om datorer
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: ca92474eaf6fa546c3d6450f5a282e45157018a8
ms.sourcegitcommit: 4a841ebda3339ae2477e0f5f5be8c01740221232
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/07/2018
---
# <a name="collecting-information-about-computers"></a>Samla in information om datorer

Cmdlet: ar från **CimCmdlets** modul är den viktigaste cmdlets för allmänna aktiviteter på systemnivå.
Alla kritiska undersystemet inställningar är tillgängliga via WMI.
Dessutom behandlas WMI data som objekt i samlingar med ett eller flera objekt.
Eftersom Windows PowerShell kan du också fungerar med objekt och har en pipeline som gör att du kan hantera en eller flera objekt på samma sätt, kan du utföra vissa avancerade med mycket lite av allmänna WMI-åtkomst.

Följande exempel visar hur du samlar in specifik information med hjälp av `Get-CimInstance` mot en valfri dator.
Anger vi den **ComputerName** parametern med värdet punkt (**.**), som motsvarar den lokala datorn.
Du kan ange ett namn eller IP-adress som är associerad med en annan dator som du kan nå via WMI.
Om du vill hämta information om den lokala datorn, kan du utelämna den **ComputerName** parameter.

### <a name="listing-desktop-settings"></a>Visar en lista över inställningar för skrivbord

Vi börjar med ett kommando som samlar in information om de stationära datorer på den lokala datorn.

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName .
```

Detta returnerar information för alla datorer, oavsett om de är används eller inte.

> [!NOTE]
> Information som returneras av vissa WMI-klasser kan vara mycket detaljerad och ofta innehåller metadata om WMI-klassen.
Eftersom de flesta av dessa metadataegenskaper har namn som börjar med **Cim**, kan du filtrera egenskaper med hjälp av `Select-Object`.
Ange den **- ExcludeProperty** parametern med ”Cim *” som värde.
Till exempel:

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

För att filtrera ut metadata, använder du en pipelineoperator (|) för att skicka resultaten av den `Get-CimInstance` kommandot till `Select-Object -ExcludeProperty "CIM*"`.

### <a name="listing-bios-information"></a>Visar en lista över BIOS-Information

WMI **Win32_BIOS** klassen returnerar ganska compact och fullständig information om systemets BIOS på den lokala datorn:

```powershell
Get-CimInstance -ClassName Win32_BIOS -ComputerName .
```

### <a name="listing-processor-information"></a>Visar en lista över processorinformation

Du kan hämta information om allmänna med hjälp av WMI **Win32_Processor** class, även om du förmodligen vill filtrera informationen:

```powershell
Get-CimInstance -ClassName Win32_Processor -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

För en allmän beskrivning av processortypen sträng kan du bara returnera den **SystemType** egenskapen:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

### <a name="listing-computer-manufacturer-and-model"></a>Visar en lista över datortillverkare och modell

Datorinformation för modellen är också tillgänglig från **Win32_ComputerSystem**.
Standardutdata visas behöver inte någon filtrering för att tillhandahålla OEM-data:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

Dina utdata från kommandon som den här, som returnerar information direkt från vissa maskinvara är endast lika bra som data som du har.
Viss information är inte korrekt konfigurerad av maskinvarutillverkare och kan därför inte tillgänglig.

### <a name="listing-installed-hotfixes"></a>Lista över installerade snabbkorrigeringar

Du kan visa en lista med alla installerade snabbkorrigeringar med hjälp av **Win32_QuickFixEngineering**:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName .
```

Den här klassen returnerar en lista med snabbkorrigeringar som ser ut så här:

```output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

För mer koncis utdata kanske du vill undanta vissa egenskaper.
Även om du kan använda den `Get-CimInstance`'s **egenskapen** parametern välja endast den **HotFixID**, göra så kommer att returnera mer, eftersom alla metadata visas som standard:

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

Ytterligare data returneras eftersom egenskapen parameter i `Get-CimInstance` begränsar egenskaperna som returneras från WMI-klassinstanser inte objektet som returneras till Windows PowerShell.
Om du vill minska utdata, Använd `Select-Object`:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId
```

```output
HotFixId
--------
KB4048951
```

### <a name="listing-operating-system-version-information"></a>Visar en lista över versionsinformation för operativsystemet

Den **Win32_OperatingSystem** klassegenskaper inkludera version och service pack.
Du kan uttryckligen välja endast dessa egenskaper att hämta versionsinformation om en sammanfattande från **Win32_OperatingSystem**:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

Du kan också använda jokertecken med den `Select-Object`'s **egenskapen** parameter.
Eftersom alla egenskaper som börjar med antingen **skapa** eller **ServicePack** är viktigt att du använder här, kan vi förkorta det till följande format:

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

### <a name="listing-local-users-and-owner"></a>Visar en lista över lokala användare och ägare

Lokala allmän användarinformation, antalet licensierade användare, aktuellt antal användare och ägarens namn – kan hittas med ett urval av **Win32_OperatingSystem**' klassegenskaper.
Du kan uttryckligen välja egenskaper som ska visas så här:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

En mer koncis version med jokertecken är:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### <a name="getting-available-disk-space"></a>Hämtning av ledigt diskutrymme

Du kan använda Win32_LogicalDisk WMI-klassen om du vill se diskutrymme och ledigt utrymme för lokala enheter.
Du behöver se endast instanser med en DriveType av 3 – värdet WMI använder för fasta hårddiskar.

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

### <a name="getting-logon-session-information"></a>Hämtning av inloggningsinformationen för Session

Du kan hämta allmän information om inloggningssessioner som är kopplade till användare via den **Win32_LogonSession** WMI-klassen:

```powershell
Get-CimInstance -ClassName Win32_LogonSession -ComputerName .
```

### <a name="getting-the-user-logged-on-to-a-computer"></a>Att användaren loggat in på en dator

Du kan visa användare som är anslutna till en viss dator med hjälp av Win32_ComputerSystem.
Detta kommando returnerar bara den användaren loggat in på systemet skrivbordet:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName -ComputerName .
```

### <a name="getting-local-time-from-a-computer"></a>Hämta lokal tid från en dator

Du kan hämta den aktuella lokala tiden på en specifik dator med hjälp av den **Win32_LocalTime** WMI-klassen.

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

Om du vill visa status för alla tjänster på en specifik dator du lokalt kan använda den `Get-Service` cmdlet.
För fjärranslutna datorer, kan du använda den **Win32_Service** WMI-klassen.
Om du också använda `Select-Object` att filtrera resultaten till **Status**, **namn**, och **DisplayName**, utdataformatet kommer att nästan identisk från `Get-Service`:

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

Om du vill tillåta fullständig visningen av namn för tillfällig trafik med mycket långa namn, kanske du vill använda `Format-Table` med den **AutoSize** och **omsluter** parametrar för att optimera kolumnbredden och Tillåt långa namn du omsluter i stället för trunkerades:

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
