---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Samla in information om datorer
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: d837684108656e17ebf26189bd4841c5de01051c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058343"
---
# <a name="collecting-information-about-computers"></a><span data-ttu-id="62203-103">Samla in information om datorer</span><span class="sxs-lookup"><span data-stu-id="62203-103">Collecting Information About Computers</span></span>

<span data-ttu-id="62203-104">Cmdlet: ar från **CimCmdlets** modul är den viktigaste cmdletar för allmänna aktiviteter på systemnivå.</span><span class="sxs-lookup"><span data-stu-id="62203-104">Cmdlets from **CimCmdlets** module are the most important cmdlets for general system management tasks.</span></span>
<span data-ttu-id="62203-105">Alla inställningar för kritiskt undersystem exponeras via WMI.</span><span class="sxs-lookup"><span data-stu-id="62203-105">All critical subsystem settings are exposed through WMI.</span></span>
<span data-ttu-id="62203-106">Dessutom behandlas data som objekt som finns i samlingar med ett eller flera objekt med WMI.</span><span class="sxs-lookup"><span data-stu-id="62203-106">Furthermore, WMI treats data as objects that are in collections of one or more items.</span></span>
<span data-ttu-id="62203-107">Eftersom Windows PowerShell även fungerar med objekt och har en pipeline som gör att du kan hantera en eller flera objekt på samma sätt kan du utföra vissa avancerade åtgärder med mycket lite av allmän WMI-åtkomst.</span><span class="sxs-lookup"><span data-stu-id="62203-107">Because Windows PowerShell also works with objects and has a pipeline that allows you to treat single or multiple objects in the same way, generic WMI access allows you to perform some advanced tasks with very little work.</span></span>

<span data-ttu-id="62203-108">Följande exempel visar hur du samlar in specifik information med hjälp av `Get-CimInstance` mot en valfri dator.</span><span class="sxs-lookup"><span data-stu-id="62203-108">The following examples demonstrate how to collect specific information by using `Get-CimInstance` against an arbitrary computer.</span></span>
<span data-ttu-id="62203-109">Vi anger den **ComputerName** med punkt-värde för parametern (**.**), som representerar den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="62203-109">We specify the **ComputerName** parameter with the dot value (**.**), which represents the local computer.</span></span>
<span data-ttu-id="62203-110">Du kan ange ett namn eller IP-adress som är associerade med en annan dator som du kan nå via WMI.</span><span class="sxs-lookup"><span data-stu-id="62203-110">You can specify a name or IP address associated with any computer you can reach through WMI.</span></span>
<span data-ttu-id="62203-111">Om du vill hämta information om den lokala datorn, kan du utelämna den **ComputerName** parametern.</span><span class="sxs-lookup"><span data-stu-id="62203-111">To retrieve information about the local computer, you could omit the **ComputerName** parameter.</span></span>

## <a name="listing-desktop-settings"></a><span data-ttu-id="62203-112">Visa en lista över inställningar för fjärrskrivbord</span><span class="sxs-lookup"><span data-stu-id="62203-112">Listing Desktop Settings</span></span>

<span data-ttu-id="62203-113">Vi börjar med ett kommando som samlar in information om datorerna på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="62203-113">We'll begin with a command that collects information about the desktops on the local computer.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName .
```

<span data-ttu-id="62203-114">Detta returnerar information för alla datorer, oavsett om de är används eller inte.</span><span class="sxs-lookup"><span data-stu-id="62203-114">This returns information for all desktops, whether they are in use or not.</span></span>

> [!NOTE]
> <span data-ttu-id="62203-115">Information som returneras av vissa WMI-klasser kan vara mycket detaljerade och ofta innehålla metadata om WMI-klass.</span><span class="sxs-lookup"><span data-stu-id="62203-115">Information returned by some WMI classes can be very detailed, and often include metadata about the WMI class.</span></span>
<span data-ttu-id="62203-116">Eftersom de flesta av dessa metadataegenskaper har namn som börjar med **Cim**, du kan filtrera egenskaper med hjälp av `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="62203-116">Because most of these metadata properties have names that begin with **Cim**, you can filter the properties using `Select-Object`.</span></span>
<span data-ttu-id="62203-117">Ange den **- ExcludeProperty** med ”Cim \*” som värde för parametern.</span><span class="sxs-lookup"><span data-stu-id="62203-117">Specify the **-ExcludeProperty** parameter with "Cim\*" as the value.</span></span>
<span data-ttu-id="62203-118">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="62203-118">For example:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="62203-119">Om du vill filtrera bort metadata, använder du en pipelineoperator (|) för att skicka resultatet av den `Get-CimInstance` för att `Select-Object -ExcludeProperty "CIM*"`.</span><span class="sxs-lookup"><span data-stu-id="62203-119">To filter out the metadata, use a pipeline operator (|) to send the results of the `Get-CimInstance` command to `Select-Object -ExcludeProperty "CIM*"`.</span></span>

## <a name="listing-bios-information"></a><span data-ttu-id="62203-120">Visa en lista över BIOS-informationen</span><span class="sxs-lookup"><span data-stu-id="62203-120">Listing BIOS Information</span></span>

<span data-ttu-id="62203-121">WMI **Win32_BIOS** klass returnerar ganska compact och fullständig information om systemets BIOS på den lokala datorn:</span><span class="sxs-lookup"><span data-stu-id="62203-121">The WMI **Win32_BIOS** class returns fairly compact and complete information about the system BIOS on the local computer:</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS -ComputerName .
```

## <a name="listing-processor-information"></a><span data-ttu-id="62203-122">Visa en lista över processorinformation</span><span class="sxs-lookup"><span data-stu-id="62203-122">Listing Processor Information</span></span>

<span data-ttu-id="62203-123">Du kan hämta information om allmänna med hjälp av WMI **Win32_Processor** class, även om du förmodligen vill filtrera informationen:</span><span class="sxs-lookup"><span data-stu-id="62203-123">You can retrieve general processor information by using WMI's **Win32_Processor** class, although you will likely want to filter the information:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Processor -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="62203-124">För en allmän beskrivningssträng av processortypen, kan du bara returnera den **SystemType** egenskapen:</span><span class="sxs-lookup"><span data-stu-id="62203-124">For a generic description string of the processor family, you can just return the **SystemType** property:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

## <a name="listing-computer-manufacturer-and-model"></a><span data-ttu-id="62203-125">Visa en lista över datortillverkare och modell</span><span class="sxs-lookup"><span data-stu-id="62203-125">Listing Computer Manufacturer and Model</span></span>

<span data-ttu-id="62203-126">Datorinformation för modellen är även tillgänglig från **Win32_ComputerSystem**.</span><span class="sxs-lookup"><span data-stu-id="62203-126">Computer model information is also available from **Win32_ComputerSystem**.</span></span>
<span data-ttu-id="62203-127">Visad standardutdata behöver inte någon filtrering för att tillhandahålla OEM-data:</span><span class="sxs-lookup"><span data-stu-id="62203-127">The standard displayed output will not need any filtering to provide OEM data:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

<span data-ttu-id="62203-128">Dina utdata från kommandon som detta tillhandahåller som returnera information direkt från viss maskinvara, är endast lika bra som de data du har.</span><span class="sxs-lookup"><span data-stu-id="62203-128">Your output from commands such as this, which return information directly from some hardware, is only as good as the data you have.</span></span>
<span data-ttu-id="62203-129">Viss information är inte korrekt konfigurerad av maskinvarutillverkare och kan därför vara otillgängliga.</span><span class="sxs-lookup"><span data-stu-id="62203-129">Some information is not correctly configured by hardware manufacturers and may therefore be unavailable.</span></span>

## <a name="listing-installed-hotfixes"></a><span data-ttu-id="62203-130">Lista över installerade snabbkorrigeringar</span><span class="sxs-lookup"><span data-stu-id="62203-130">Listing Installed Hotfixes</span></span>

<span data-ttu-id="62203-131">Du kan lista alla installerade snabbkorrigeringar med hjälp av **Win32_QuickFixEngineering**:</span><span class="sxs-lookup"><span data-stu-id="62203-131">You can list all installed hotfixes by using **Win32_QuickFixEngineering**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName .
```

<span data-ttu-id="62203-132">Den här klassen returnerar en lista med snabbkorrigeringar som ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="62203-132">This class returns a list of hotfixes that looks like this:</span></span>

```output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

<span data-ttu-id="62203-133">För mer kortfattad utdata du undanta vissa egenskaper.</span><span class="sxs-lookup"><span data-stu-id="62203-133">For more succinct output, you may want to exclude some properties.</span></span>
<span data-ttu-id="62203-134">Även om du kan använda den `Get-CimInstance`'s **egenskapen** parametern för att välja endast de **HotFixID**, göra så kommer att returnera mer information, eftersom alla metadata visas som standard:</span><span class="sxs-lookup"><span data-stu-id="62203-134">Although you can use the `Get-CimInstance`'s **Property** parameter to choose only the **HotFixID**, doing so will actually return more information, because all the metadata is displayed by default:</span></span>

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

<span data-ttu-id="62203-135">Ytterligare data returneras, eftersom egenskapen-parametern i `Get-CimInstance` begränsar egenskaperna som returneras från WMI-klassinstanser inte objektet som returneras till Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="62203-135">The additional data is returned, because the Property parameter in `Get-CimInstance` restricts the properties returned from WMI class instances, not the object returned to Windows PowerShell.</span></span>
<span data-ttu-id="62203-136">För att minska utdata kan använda `Select-Object`:</span><span class="sxs-lookup"><span data-stu-id="62203-136">To reduce the output, use `Select-Object`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId
```

```output
HotFixId
--------
KB4048951
```

## <a name="listing-operating-system-version-information"></a><span data-ttu-id="62203-137">Visa en lista över versionsinformation för operativsystemet</span><span class="sxs-lookup"><span data-stu-id="62203-137">Listing Operating System Version Information</span></span>

<span data-ttu-id="62203-138">Den **Win32_OperatingSystem** klassegenskaper inkludera information om version och service pack.</span><span class="sxs-lookup"><span data-stu-id="62203-138">The **Win32_OperatingSystem** class properties include version and service pack information.</span></span>
<span data-ttu-id="62203-139">Du kan uttryckligen välja endast de här egenskaperna för att hämta en sammanfattning från **Win32_OperatingSystem**:</span><span class="sxs-lookup"><span data-stu-id="62203-139">You can explicitly select only these properties to get a version information summary from **Win32_OperatingSystem**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

<span data-ttu-id="62203-140">Du kan också använda jokertecken med den `Select-Object`'s **egenskapen** parametern.</span><span class="sxs-lookup"><span data-stu-id="62203-140">You can also use wildcards with the `Select-Object`'s **Property** parameter.</span></span>
<span data-ttu-id="62203-141">Eftersom alla egenskaper från och med antingen **skapa** eller **ServicePack** är viktigt att du använder här kan vi kan förkorta det till följande format:</span><span class="sxs-lookup"><span data-stu-id="62203-141">Because all the properties beginning with either **Build** or **ServicePack** are important to use here, we can shorten this to the following form:</span></span>

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

## <a name="listing-local-users-and-owner"></a><span data-ttu-id="62203-142">Visa en lista över lokala användare och ägare</span><span class="sxs-lookup"><span data-stu-id="62203-142">Listing Local Users and Owner</span></span>

<span data-ttu-id="62203-143">Lokala Allmänt användarinformation – antalet licensierade användare, aktuellt antal användare och ägarens namn – finns bland ett urval av **Win32_OperatingSystem**' klassegenskaper.</span><span class="sxs-lookup"><span data-stu-id="62203-143">Local general user information — number of licensed users, current number of users, and owner name — can be found with a selection of **Win32_OperatingSystem** class' properties.</span></span>
<span data-ttu-id="62203-144">Du kan uttryckligen välja vilka egenskaper som ska visas så här:</span><span class="sxs-lookup"><span data-stu-id="62203-144">You can explicitly select the properties to display like this:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

<span data-ttu-id="62203-145">En mer kortfattad version med jokertecken är:</span><span class="sxs-lookup"><span data-stu-id="62203-145">A more succinct version using wildcards is:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

## <a name="getting-available-disk-space"></a><span data-ttu-id="62203-146">Hämta ledigt diskutrymme</span><span class="sxs-lookup"><span data-stu-id="62203-146">Getting Available Disk Space</span></span>

<span data-ttu-id="62203-147">Om du vill se diskutrymme och ledigt utrymme för lokala enheter, kan du använda Win32_LogicalDisk WMI-klass.</span><span class="sxs-lookup"><span data-stu-id="62203-147">To see the disk space and free space for local drives, you can use the Win32_LogicalDisk WMI class.</span></span>
<span data-ttu-id="62203-148">Du behöver se bara instanser med en DriveType av 3 – värdet WMI använder för fasta hårddiskar.</span><span class="sxs-lookup"><span data-stu-id="62203-148">You need to see only instances with a DriveType of 3 — the value WMI uses for fixed hard disks.</span></span>

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

## <a name="getting-logon-session-information"></a><span data-ttu-id="62203-149">Hämta inloggningsinformation för Session</span><span class="sxs-lookup"><span data-stu-id="62203-149">Getting Logon Session Information</span></span>

<span data-ttu-id="62203-150">Du kan få allmän information om inloggningssessioner som är kopplade till användare via den **Win32_LogonSession** WMI-klass:</span><span class="sxs-lookup"><span data-stu-id="62203-150">You can get general information about logon sessions associated with users through the **Win32_LogonSession** WMI class:</span></span>

```powershell
Get-CimInstance -ClassName Win32_LogonSession -ComputerName .
```

## <a name="getting-the-user-logged-on-to-a-computer"></a><span data-ttu-id="62203-151">Hämta användaren loggat in på en dator</span><span class="sxs-lookup"><span data-stu-id="62203-151">Getting the User Logged on to a Computer</span></span>

<span data-ttu-id="62203-152">Du kan visa användare som är anslutna till en viss dator med hjälp av Win32_ComputerSystem.</span><span class="sxs-lookup"><span data-stu-id="62203-152">You can display the user logged on to a particular computer system using Win32_ComputerSystem.</span></span>
<span data-ttu-id="62203-153">Det här kommandot returnerar endast användare som är anslutna till systemet skrivbordet:</span><span class="sxs-lookup"><span data-stu-id="62203-153">This command returns only the user logged on to the system desktop:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName -ComputerName .
```

## <a name="getting-local-time-from-a-computer"></a><span data-ttu-id="62203-154">Hämta lokal tid från en dator</span><span class="sxs-lookup"><span data-stu-id="62203-154">Getting Local Time from a Computer</span></span>

<span data-ttu-id="62203-155">Du kan hämta den aktuella lokala tiden på en specifik dator med hjälp av den **Win32_LocalTime** WMI-klass.</span><span class="sxs-lookup"><span data-stu-id="62203-155">You can retrieve the current local time on a specific computer by using the **Win32_LocalTime** WMI class.</span></span>

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

## <a name="displaying-service-status"></a><span data-ttu-id="62203-156">Visa Status för tjänsten</span><span class="sxs-lookup"><span data-stu-id="62203-156">Displaying Service Status</span></span>

<span data-ttu-id="62203-157">Om du vill visa status för alla tjänster på en specifik dator som du lokalt kan använda den `Get-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="62203-157">To view the status of all services on a specific computer, you can locally use the `Get-Service` cmdlet.</span></span>
<span data-ttu-id="62203-158">För fjärranslutna datorer, kan du använda den **Win32_Service** WMI-klass.</span><span class="sxs-lookup"><span data-stu-id="62203-158">For remote systems, you can use the **Win32_Service** WMI class.</span></span>
<span data-ttu-id="62203-159">Om du även använder `Select-Object` att filtrera resultaten till **Status**, **namn**, och **DisplayName**, utdataformat blir nästan identisk från `Get-Service`:</span><span class="sxs-lookup"><span data-stu-id="62203-159">If you also use `Select-Object` to filter the results to **Status**, **Name**, and **DisplayName**, the output format will be almost identical to that from `Get-Service`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

<span data-ttu-id="62203-160">Om du vill tillåta fullständig visning av namn för tillfällig trafik med mycket långa namn, kanske du vill använda `Format-Table` med den **AutoSize** och **omsluta** parametrar för att optimera kolumnbredd och Tillåt långa namn du omsluter i stället för trunkerades:</span><span class="sxs-lookup"><span data-stu-id="62203-160">To allow the complete display of names for the occasional services with extremely long names, you may want to use `Format-Table` with the **AutoSize** and **Wrap** parameters, to optimize column width and allow long names to wrap instead of being truncated:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
