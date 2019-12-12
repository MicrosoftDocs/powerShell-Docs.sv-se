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
# <a name="collecting-information-about-computers"></a><span data-ttu-id="378a7-103">Samla in information om datorer</span><span class="sxs-lookup"><span data-stu-id="378a7-103">Collecting Information About Computers</span></span>

<span data-ttu-id="378a7-104">Cmdlets från **CimCmdlets** -modulen är de viktigaste cmdletarna för allmänna system hanterings uppgifter.</span><span class="sxs-lookup"><span data-stu-id="378a7-104">Cmdlets from **CimCmdlets** module are the most important cmdlets for general system management tasks.</span></span>
<span data-ttu-id="378a7-105">Alla inställningar för viktiga under system exponeras via WMI.</span><span class="sxs-lookup"><span data-stu-id="378a7-105">All critical subsystem settings are exposed through WMI.</span></span>
<span data-ttu-id="378a7-106">Dessutom behandlar WMI data som objekt som finns i samlingar av ett eller flera objekt.</span><span class="sxs-lookup"><span data-stu-id="378a7-106">Furthermore, WMI treats data as objects that are in collections of one or more items.</span></span>
<span data-ttu-id="378a7-107">Eftersom Windows PowerShell även fungerar med objekt och har en pipeline som gör att du kan hantera enskilda eller flera objekt på samma sätt, kan du med hjälp av allmän WMI-åtkomst utföra vissa avancerade uppgifter med mycket lite arbete.</span><span class="sxs-lookup"><span data-stu-id="378a7-107">Because Windows PowerShell also works with objects and has a pipeline that allows you to treat single or multiple objects in the same way, generic WMI access allows you to perform some advanced tasks with very little work.</span></span>

<span data-ttu-id="378a7-108">Följande exempel visar hur du samlar in speciell information med hjälp av `Get-CimInstance` mot en godtycklig dator.</span><span class="sxs-lookup"><span data-stu-id="378a7-108">The following examples demonstrate how to collect specific information by using `Get-CimInstance` against an arbitrary computer.</span></span>
<span data-ttu-id="378a7-109">Vi anger parametern **computername** med det punkt värde ( **.** ) som representerar den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="378a7-109">We specify the **ComputerName** parameter with the dot value (**.**), which represents the local computer.</span></span>
<span data-ttu-id="378a7-110">Du kan ange ett namn eller en IP-adress som är kopplad till en dator som du kan komma åt via WMI.</span><span class="sxs-lookup"><span data-stu-id="378a7-110">You can specify a name or IP address associated with any computer you can reach through WMI.</span></span>
<span data-ttu-id="378a7-111">Om du vill hämta information om den lokala datorn kan du utelämna parametern **computername** .</span><span class="sxs-lookup"><span data-stu-id="378a7-111">To retrieve information about the local computer, you could omit the **ComputerName** parameter.</span></span>

## <a name="listing-desktop-settings"></a><span data-ttu-id="378a7-112">Visa Skriv bords inställningar</span><span class="sxs-lookup"><span data-stu-id="378a7-112">Listing Desktop Settings</span></span>

<span data-ttu-id="378a7-113">Vi börjar med ett kommando som samlar in information om Skriv bordets på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="378a7-113">We'll begin with a command that collects information about the desktops on the local computer.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName .
```

<span data-ttu-id="378a7-114">Detta returnerar information för alla skriv bord, oavsett om de används eller inte.</span><span class="sxs-lookup"><span data-stu-id="378a7-114">This returns information for all desktops, whether they are in use or not.</span></span>

> [!NOTE]
> <span data-ttu-id="378a7-115">Information som returneras av vissa WMI-klasser kan vara mycket detaljerad och innehåller ofta metadata om WMI-klassen.</span><span class="sxs-lookup"><span data-stu-id="378a7-115">Information returned by some WMI classes can be very detailed, and often include metadata about the WMI class.</span></span>
<span data-ttu-id="378a7-116">Eftersom de flesta av dessa metadata-egenskaper har namn som börjar med **CIM**kan du filtrera egenskaperna med hjälp av `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="378a7-116">Because most of these metadata properties have names that begin with **Cim**, you can filter the properties using `Select-Object`.</span></span>
<span data-ttu-id="378a7-117">Ange parametern **-ExcludeProperty** med "CIM \*" som värde.</span><span class="sxs-lookup"><span data-stu-id="378a7-117">Specify the **-ExcludeProperty** parameter with "Cim\*" as the value.</span></span>
<span data-ttu-id="378a7-118">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="378a7-118">For example:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="378a7-119">Om du vill filtrera bort metadata använder du en pipeline-operator (|) för att skicka resultatet från kommandot `Get-CimInstance` till `Select-Object -ExcludeProperty "CIM*"`.</span><span class="sxs-lookup"><span data-stu-id="378a7-119">To filter out the metadata, use a pipeline operator (|) to send the results of the `Get-CimInstance` command to `Select-Object -ExcludeProperty "CIM*"`.</span></span>

## <a name="listing-bios-information"></a><span data-ttu-id="378a7-120">Visa BIOS-information</span><span class="sxs-lookup"><span data-stu-id="378a7-120">Listing BIOS Information</span></span>

<span data-ttu-id="378a7-121">WMI- **Win32_BIOS** -klassen returnerar ganska kompakt och fullständig information om systemets BIOS på den lokala datorn:</span><span class="sxs-lookup"><span data-stu-id="378a7-121">The WMI **Win32_BIOS** class returns fairly compact and complete information about the system BIOS on the local computer:</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS -ComputerName .
```

## <a name="listing-processor-information"></a><span data-ttu-id="378a7-122">Lista processor information</span><span class="sxs-lookup"><span data-stu-id="378a7-122">Listing Processor Information</span></span>

<span data-ttu-id="378a7-123">Du kan hämta allmän processor information med hjälp av WMI: s **Win32_Processor** -klass, men du kommer förmodligen att vilja filtrera informationen:</span><span class="sxs-lookup"><span data-stu-id="378a7-123">You can retrieve general processor information by using WMI's **Win32_Processor** class, although you will likely want to filter the information:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Processor -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="378a7-124">För en generisk beskrivnings sträng för processor familjen kan du bara returnera egenskapen **SystemType** :</span><span class="sxs-lookup"><span data-stu-id="378a7-124">For a generic description string of the processor family, you can just return the **SystemType** property:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

## <a name="listing-computer-manufacturer-and-model"></a><span data-ttu-id="378a7-125">Visa dator tillverkare och modell</span><span class="sxs-lookup"><span data-stu-id="378a7-125">Listing Computer Manufacturer and Model</span></span>

<span data-ttu-id="378a7-126">Information om dator modeller är också tillgänglig från **Win32_ComputerSystem**.</span><span class="sxs-lookup"><span data-stu-id="378a7-126">Computer model information is also available from **Win32_ComputerSystem**.</span></span>
<span data-ttu-id="378a7-127">De utdata som visas som standard kommer inte att behöva filtreras för att tillhandahålla OEM-data:</span><span class="sxs-lookup"><span data-stu-id="378a7-127">The standard displayed output will not need any filtering to provide OEM data:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

<span data-ttu-id="378a7-128">Dina utdata från kommandon som det här, som returnerar information direkt från viss maskin vara, är bara lika användbara som de data du har.</span><span class="sxs-lookup"><span data-stu-id="378a7-128">Your output from commands such as this, which return information directly from some hardware, is only as good as the data you have.</span></span>
<span data-ttu-id="378a7-129">Viss information är inte korrekt konfigurerad av maskin varu tillverkare och kan därför vara otillgänglig.</span><span class="sxs-lookup"><span data-stu-id="378a7-129">Some information is not correctly configured by hardware manufacturers and may therefore be unavailable.</span></span>

## <a name="listing-installed-hotfixes"></a><span data-ttu-id="378a7-130">Visar installerade snabb korrigeringar</span><span class="sxs-lookup"><span data-stu-id="378a7-130">Listing Installed Hotfixes</span></span>

<span data-ttu-id="378a7-131">Du kan visa en lista med alla installerade snabb korrigeringar med **Win32_QuickFixEngineering**:</span><span class="sxs-lookup"><span data-stu-id="378a7-131">You can list all installed hotfixes by using **Win32_QuickFixEngineering**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName .
```

<span data-ttu-id="378a7-132">Den här klassen returnerar en lista med snabb korrigeringar som ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="378a7-132">This class returns a list of hotfixes that looks like this:</span></span>

```output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

<span data-ttu-id="378a7-133">För fler kortfattad-utdata kanske du vill utesluta vissa egenskaper.</span><span class="sxs-lookup"><span data-stu-id="378a7-133">For more succinct output, you may want to exclude some properties.</span></span>
<span data-ttu-id="378a7-134">Även om du kan använda `Get-CimInstance`ens **egenskaps** parameter för att välja endast **HotFixID**, returnerar faktiskt mer information, eftersom alla metadata visas som standard:</span><span class="sxs-lookup"><span data-stu-id="378a7-134">Although you can use the `Get-CimInstance`'s **Property** parameter to choose only the **HotFixID**, doing so will actually return more information, because all the metadata is displayed by default:</span></span>

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

<span data-ttu-id="378a7-135">Ytterligare data returneras, eftersom egenskaps parametern i `Get-CimInstance` begränsar egenskaperna som returneras från WMI-klass instanser, inte det objekt som returneras till Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="378a7-135">The additional data is returned, because the Property parameter in `Get-CimInstance` restricts the properties returned from WMI class instances, not the object returned to Windows PowerShell.</span></span>
<span data-ttu-id="378a7-136">Använd `Select-Object`för att minska utdata:</span><span class="sxs-lookup"><span data-stu-id="378a7-136">To reduce the output, use `Select-Object`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId
```

```output
HotFixId
--------
KB4048951
```

## <a name="listing-operating-system-version-information"></a><span data-ttu-id="378a7-137">Visar information om operativ systemets version</span><span class="sxs-lookup"><span data-stu-id="378a7-137">Listing Operating System Version Information</span></span>

<span data-ttu-id="378a7-138">**Win32_OperatingSystem** klass egenskaper innehåller versions-och service pack information.</span><span class="sxs-lookup"><span data-stu-id="378a7-138">The **Win32_OperatingSystem** class properties include version and service pack information.</span></span>
<span data-ttu-id="378a7-139">Du kan uttryckligen välja endast dessa egenskaper för att hämta en versions informations Sammanfattning från **Win32_OperatingSystem**:</span><span class="sxs-lookup"><span data-stu-id="378a7-139">You can explicitly select only these properties to get a version information summary from **Win32_OperatingSystem**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

<span data-ttu-id="378a7-140">Du kan också använda jokertecken med `Select-Object`**egenskaps** parameter.</span><span class="sxs-lookup"><span data-stu-id="378a7-140">You can also use wildcards with the `Select-Object`'s **Property** parameter.</span></span>
<span data-ttu-id="378a7-141">Eftersom alla egenskaper som börjar med antingen **build** eller **servicepack** är viktiga för användning här kan vi förkorta detta till följande format:</span><span class="sxs-lookup"><span data-stu-id="378a7-141">Because all the properties beginning with either **Build** or **ServicePack** are important to use here, we can shorten this to the following form:</span></span>

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

## <a name="listing-local-users-and-owner"></a><span data-ttu-id="378a7-142">Lista lokala användare och ägare</span><span class="sxs-lookup"><span data-stu-id="378a7-142">Listing Local Users and Owner</span></span>

<span data-ttu-id="378a7-143">Lokal allmän användar information – antal licensierade användare, Aktuellt antal användare och ägarnamn – kan hittas med ett val av **Win32_OperatingSystem** klass egenskaper.</span><span class="sxs-lookup"><span data-stu-id="378a7-143">Local general user information — number of licensed users, current number of users, and owner name — can be found with a selection of **Win32_OperatingSystem** class' properties.</span></span>
<span data-ttu-id="378a7-144">Du kan uttryckligen välja vilka egenskaper som ska visas:</span><span class="sxs-lookup"><span data-stu-id="378a7-144">You can explicitly select the properties to display like this:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

<span data-ttu-id="378a7-145">En mer kortfattad-version med jokertecken är:</span><span class="sxs-lookup"><span data-stu-id="378a7-145">A more succinct version using wildcards is:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

## <a name="getting-available-disk-space"></a><span data-ttu-id="378a7-146">Hämtar tillgängligt disk utrymme</span><span class="sxs-lookup"><span data-stu-id="378a7-146">Getting Available Disk Space</span></span>

<span data-ttu-id="378a7-147">Om du vill se disk utrymme och ledigt utrymme för lokala enheter kan du använda klassen Win32_LogicalDisk WMI.</span><span class="sxs-lookup"><span data-stu-id="378a7-147">To see the disk space and free space for local drives, you can use the Win32_LogicalDisk WMI class.</span></span>
<span data-ttu-id="378a7-148">Du behöver bara se instanser med en DriveType av 3 – värdet för WMI använder fasta hård diskar.</span><span class="sxs-lookup"><span data-stu-id="378a7-148">You need to see only instances with a DriveType of 3 — the value WMI uses for fixed hard disks.</span></span>

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

## <a name="getting-logon-session-information"></a><span data-ttu-id="378a7-149">Hämta information om inloggningssession</span><span class="sxs-lookup"><span data-stu-id="378a7-149">Getting Logon Session Information</span></span>

<span data-ttu-id="378a7-150">Du kan få allmän information om inloggnings sessioner som är associerade med användare via klassen **Win32_LogonSession** WMI:</span><span class="sxs-lookup"><span data-stu-id="378a7-150">You can get general information about logon sessions associated with users through the **Win32_LogonSession** WMI class:</span></span>

```powershell
Get-CimInstance -ClassName Win32_LogonSession -ComputerName .
```

## <a name="getting-the-user-logged-on-to-a-computer"></a><span data-ttu-id="378a7-151">Få användaren inloggad på en dator</span><span class="sxs-lookup"><span data-stu-id="378a7-151">Getting the User Logged on to a Computer</span></span>

<span data-ttu-id="378a7-152">Du kan visa användaren som är inloggad på ett visst dator system med hjälp av Win32_ComputerSystem.</span><span class="sxs-lookup"><span data-stu-id="378a7-152">You can display the user logged on to a particular computer system using Win32_ComputerSystem.</span></span>
<span data-ttu-id="378a7-153">Det här kommandot returnerar bara den användare som är inloggad på system Skriv bordet:</span><span class="sxs-lookup"><span data-stu-id="378a7-153">This command returns only the user logged on to the system desktop:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName -ComputerName .
```

## <a name="getting-local-time-from-a-computer"></a><span data-ttu-id="378a7-154">Hämta lokal tid från en dator</span><span class="sxs-lookup"><span data-stu-id="378a7-154">Getting Local Time from a Computer</span></span>

<span data-ttu-id="378a7-155">Du kan hämta den aktuella lokala tiden på en speciell dator med hjälp av **Win32_LocalTime** WMI-klassen.</span><span class="sxs-lookup"><span data-stu-id="378a7-155">You can retrieve the current local time on a specific computer by using the **Win32_LocalTime** WMI class.</span></span>

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

## <a name="displaying-service-status"></a><span data-ttu-id="378a7-156">Visar tjänst status</span><span class="sxs-lookup"><span data-stu-id="378a7-156">Displaying Service Status</span></span>

<span data-ttu-id="378a7-157">Om du vill visa status för alla tjänster på en speciell dator kan du använda `Get-Service`-cmdlet: en lokalt.</span><span class="sxs-lookup"><span data-stu-id="378a7-157">To view the status of all services on a specific computer, you can locally use the `Get-Service` cmdlet.</span></span>
<span data-ttu-id="378a7-158">För fjärrsystem kan du använda klassen **Win32_Service** WMI.</span><span class="sxs-lookup"><span data-stu-id="378a7-158">For remote systems, you can use the **Win32_Service** WMI class.</span></span>
<span data-ttu-id="378a7-159">Om du också använder `Select-Object` för att filtrera resultaten till **status**, **namn**och **DisplayName**, är utdataformatet nästan identiskt med `Get-Service`:</span><span class="sxs-lookup"><span data-stu-id="378a7-159">If you also use `Select-Object` to filter the results to **Status**, **Name**, and **DisplayName**, the output format will be almost identical to that from `Get-Service`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

<span data-ttu-id="378a7-160">Om du vill tillåta hela visningen av namn för tillfälliga tjänster med extremt långa namn, kanske du vill använda `Format-Table` med parametrarna **AutoSize** och **wrap** för att optimera kolumn bredden och tillåta långa namn att figursättas i stället för att trunkeras:</span><span class="sxs-lookup"><span data-stu-id="378a7-160">To allow the complete display of names for the occasional services with extremely long names, you may want to use `Format-Table` with the **AutoSize** and **Wrap** parameters, to optimize column width and allow long names to wrap instead of being truncated:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
