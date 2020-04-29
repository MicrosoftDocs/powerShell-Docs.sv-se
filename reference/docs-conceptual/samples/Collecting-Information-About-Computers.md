---
ms.date: 12/23/2019
keywords: PowerShell, cmdlet
title: Samla in information om datorer
ms.openlocfilehash: 9407ff15b3c3ca6b3adab60d4d01d957c599e79e
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75737244"
---
# <a name="collecting-information-about-computers"></a><span data-ttu-id="1fcb4-103">Samla in information om datorer</span><span class="sxs-lookup"><span data-stu-id="1fcb4-103">Collecting Information About Computers</span></span>

<span data-ttu-id="1fcb4-104">Cmdlets från **CimCmdlets** -modulen är de viktigaste cmdletarna för allmänna system hanterings uppgifter.</span><span class="sxs-lookup"><span data-stu-id="1fcb4-104">Cmdlets from **CimCmdlets** module are the most important cmdlets for general system management tasks.</span></span> <span data-ttu-id="1fcb4-105">Alla inställningar för viktiga under system exponeras via WMI.</span><span class="sxs-lookup"><span data-stu-id="1fcb4-105">All critical subsystem settings are exposed through WMI.</span></span> <span data-ttu-id="1fcb4-106">Dessutom behandlar WMI data som objekt som finns i samlingar av ett eller flera objekt.</span><span class="sxs-lookup"><span data-stu-id="1fcb4-106">Furthermore, WMI treats data as objects that are in collections of one or more items.</span></span> <span data-ttu-id="1fcb4-107">Eftersom Windows PowerShell även fungerar med objekt och har en pipeline som gör att du kan hantera enskilda eller flera objekt på samma sätt, kan du med hjälp av allmän WMI-åtkomst utföra vissa avancerade uppgifter med mycket lite arbete.</span><span class="sxs-lookup"><span data-stu-id="1fcb4-107">Because Windows PowerShell also works with objects and has a pipeline that allows you to treat single or multiple objects in the same way, generic WMI access allows you to perform some advanced tasks with very little work.</span></span>

## <a name="listing-desktop-settings"></a><span data-ttu-id="1fcb4-108">Visa Skriv bords inställningar</span><span class="sxs-lookup"><span data-stu-id="1fcb4-108">Listing Desktop Settings</span></span>

<span data-ttu-id="1fcb4-109">Vi börjar med ett kommando som samlar in information om Skriv bordets på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="1fcb4-109">We'll begin with a command that collects information about the desktops on the local computer.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop
```

<span data-ttu-id="1fcb4-110">Detta returnerar information för alla skriv bord, oavsett om de används eller inte.</span><span class="sxs-lookup"><span data-stu-id="1fcb4-110">This returns information for all desktops, whether they are in use or not.</span></span>

> [!NOTE]
> <span data-ttu-id="1fcb4-111">Information som returneras av vissa WMI-klasser kan vara mycket detaljerad och innehåller ofta metadata om WMI-klassen.</span><span class="sxs-lookup"><span data-stu-id="1fcb4-111">Information returned by some WMI classes can be very detailed, and often include metadata about the WMI class.</span></span>

<span data-ttu-id="1fcb4-112">Eftersom de flesta av dessa metadata-egenskaper har namn som börjar med **CIM**kan du filtrera egenskaperna med `Select-Object`hjälp av.</span><span class="sxs-lookup"><span data-stu-id="1fcb4-112">Because most of these metadata properties have names that begin with **Cim**, you can filter the properties using `Select-Object`.</span></span> <span data-ttu-id="1fcb4-113">Ange parametern **-ExcludeProperty** med "CIM \*" som värde.</span><span class="sxs-lookup"><span data-stu-id="1fcb4-113">Specify the **-ExcludeProperty** parameter with "Cim\*" as the value.</span></span> <span data-ttu-id="1fcb4-114">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="1fcb4-114">For example:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="1fcb4-115">Om du vill filtrera bort metadata använder du en pipeline-operator (|) för att skicka `Get-CimInstance` kommandots resultat till `Select-Object -ExcludeProperty "CIM*"`.</span><span class="sxs-lookup"><span data-stu-id="1fcb4-115">To filter out the metadata, use a pipeline operator (|) to send the results of the `Get-CimInstance` command to `Select-Object -ExcludeProperty "CIM*"`.</span></span>

## <a name="listing-bios-information"></a><span data-ttu-id="1fcb4-116">Visa BIOS-information</span><span class="sxs-lookup"><span data-stu-id="1fcb4-116">Listing BIOS Information</span></span>

<span data-ttu-id="1fcb4-117">WMI- **Win32_BIOS** -klassen returnerar ganska kompakt och fullständig information om systemets BIOS på den lokala datorn:</span><span class="sxs-lookup"><span data-stu-id="1fcb4-117">The WMI **Win32_BIOS** class returns fairly compact and complete information about the system BIOS on the local computer:</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS
```

## <a name="listing-processor-information"></a><span data-ttu-id="1fcb4-118">Lista processor information</span><span class="sxs-lookup"><span data-stu-id="1fcb4-118">Listing Processor Information</span></span>

<span data-ttu-id="1fcb4-119">Du kan hämta allmän processor information med hjälp av WMI: s **Win32_Processor** -klass, men du kommer förmodligen att vilja filtrera informationen:</span><span class="sxs-lookup"><span data-stu-id="1fcb4-119">You can retrieve general processor information by using WMI's **Win32_Processor** class, although you will likely want to filter the information:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Processor | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="1fcb4-120">För en generisk beskrivnings sträng för processor familjen kan du bara returnera egenskapen **SystemType** :</span><span class="sxs-lookup"><span data-stu-id="1fcb4-120">For a generic description string of the processor family, you can just return the **SystemType** property:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

## <a name="listing-computer-manufacturer-and-model"></a><span data-ttu-id="1fcb4-121">Visa dator tillverkare och modell</span><span class="sxs-lookup"><span data-stu-id="1fcb4-121">Listing Computer Manufacturer and Model</span></span>

<span data-ttu-id="1fcb4-122">Information om dator modeller är också tillgänglig från **Win32_ComputerSystem**.</span><span class="sxs-lookup"><span data-stu-id="1fcb4-122">Computer model information is also available from **Win32_ComputerSystem**.</span></span> <span data-ttu-id="1fcb4-123">De utdata som visas som standard kommer inte att behöva filtreras för att tillhandahålla OEM-data:</span><span class="sxs-lookup"><span data-stu-id="1fcb4-123">The standard displayed output will not need any filtering to provide OEM data:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```Output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

<span data-ttu-id="1fcb4-124">Dina utdata från kommandon som det här, som returnerar information direkt från viss maskin vara, är bara lika användbara som de data du har.</span><span class="sxs-lookup"><span data-stu-id="1fcb4-124">Your output from commands such as this, which return information directly from some hardware, is only as good as the data you have.</span></span> <span data-ttu-id="1fcb4-125">Viss information är inte korrekt konfigurerad av maskin varu tillverkare och kan därför vara otillgänglig.</span><span class="sxs-lookup"><span data-stu-id="1fcb4-125">Some information is not correctly configured by hardware manufacturers and may therefore be unavailable.</span></span>

## <a name="listing-installed-hotfixes"></a><span data-ttu-id="1fcb4-126">Visar installerade snabb korrigeringar</span><span class="sxs-lookup"><span data-stu-id="1fcb4-126">Listing Installed Hotfixes</span></span>

<span data-ttu-id="1fcb4-127">Du kan visa en lista med alla installerade snabb korrigeringar med **Win32_QuickFixEngineering**:</span><span class="sxs-lookup"><span data-stu-id="1fcb4-127">You can list all installed hotfixes by using **Win32_QuickFixEngineering**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering
```

<span data-ttu-id="1fcb4-128">Den här klassen returnerar en lista med snabb korrigeringar som ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="1fcb4-128">This class returns a list of hotfixes that looks like this:</span></span>

```Output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

<span data-ttu-id="1fcb4-129">För fler kortfattad-utdata kanske du vill utesluta vissa egenskaper.</span><span class="sxs-lookup"><span data-stu-id="1fcb4-129">For more succinct output, you may want to exclude some properties.</span></span> <span data-ttu-id="1fcb4-130">Även om du kan använda `Get-CimInstance` **egenskapens egenskaps** parameter för att välja endast **HotFixID**så kommer detta faktiskt att returnera mer information, eftersom alla metadata visas som standard:</span><span class="sxs-lookup"><span data-stu-id="1fcb4-130">Although you can use the `Get-CimInstance`'s **Property** parameter to choose only the **HotFixID**, doing so will actually return more information, because all the metadata is displayed by default:</span></span>

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

<span data-ttu-id="1fcb4-131">Ytterligare data returneras, eftersom **egenskaps** parametern i `Get-CimInstance` begränsar egenskaperna som returneras från WMI-klass instanser, inte objektet som returnerades till PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1fcb4-131">The additional data is returned, because the **Property** parameter in `Get-CimInstance` restricts the properties returned from WMI class instances, not the object returned to PowerShell.</span></span> <span data-ttu-id="1fcb4-132">För att minska utdata använder `Select-Object`du:</span><span class="sxs-lookup"><span data-stu-id="1fcb4-132">To reduce the output, use `Select-Object`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -Property HotFixId | Select-Object -Property HotFixId
```

```Output
HotFixId
--------
KB4048951
```

## <a name="listing-operating-system-version-information"></a><span data-ttu-id="1fcb4-133">Visar information om operativ systemets version</span><span class="sxs-lookup"><span data-stu-id="1fcb4-133">Listing Operating System Version Information</span></span>

<span data-ttu-id="1fcb4-134">**Win32_OperatingSystem** klass egenskaper innehåller versions-och service pack information.</span><span class="sxs-lookup"><span data-stu-id="1fcb4-134">The **Win32_OperatingSystem** class properties include version and service pack information.</span></span> <span data-ttu-id="1fcb4-135">Du kan uttryckligen välja endast dessa egenskaper för att hämta en versions informations Sammanfattning från **Win32_OperatingSystem**:</span><span class="sxs-lookup"><span data-stu-id="1fcb4-135">You can explicitly select only these properties to get a version information summary from **Win32_OperatingSystem**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem |
  Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

<span data-ttu-id="1fcb4-136">Du kan också använda jokertecken med `Select-Object` **egenskaps** parametern.</span><span class="sxs-lookup"><span data-stu-id="1fcb4-136">You can also use wildcards with the `Select-Object`'s **Property** parameter.</span></span> <span data-ttu-id="1fcb4-137">Eftersom alla egenskaper som börjar med antingen **build** eller **servicepack** är viktiga för användning här kan vi förkorta detta till följande format:</span><span class="sxs-lookup"><span data-stu-id="1fcb4-137">Because all the properties beginning with either **Build** or **ServicePack** are important to use here, we can shorten this to the following form:</span></span>

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

## <a name="listing-local-users-and-owner"></a><span data-ttu-id="1fcb4-138">Lista lokala användare och ägare</span><span class="sxs-lookup"><span data-stu-id="1fcb4-138">Listing Local Users and Owner</span></span>

<span data-ttu-id="1fcb4-139">Lokal allmän användar information – antal licensierade användare, Aktuellt antal användare och ägarnamn – kan hittas med ett val av **Win32_OperatingSystem** klass egenskaper.</span><span class="sxs-lookup"><span data-stu-id="1fcb4-139">Local general user information — number of licensed users, current number of users, and owner name — can be found with a selection of **Win32_OperatingSystem** class properties.</span></span> <span data-ttu-id="1fcb4-140">Du kan uttryckligen välja vilka egenskaper som ska visas:</span><span class="sxs-lookup"><span data-stu-id="1fcb4-140">You can explicitly select the properties to display like this:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem |
  Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

<span data-ttu-id="1fcb4-141">En mer kortfattad-version med jokertecken är:</span><span class="sxs-lookup"><span data-stu-id="1fcb4-141">A more succinct version using wildcards is:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem | Select-Object -Property *user*
```

## <a name="getting-available-disk-space"></a><span data-ttu-id="1fcb4-142">Hämtar tillgängligt disk utrymme</span><span class="sxs-lookup"><span data-stu-id="1fcb4-142">Getting Available Disk Space</span></span>

<span data-ttu-id="1fcb4-143">Om du vill se disk utrymme och ledigt utrymme för lokala enheter kan du använda klassen Win32_LogicalDisk WMI.</span><span class="sxs-lookup"><span data-stu-id="1fcb4-143">To see the disk space and free space for local drives, you can use the Win32_LogicalDisk WMI class.</span></span>
<span data-ttu-id="1fcb4-144">Du behöver bara se instanser med en DriveType av 3 – värdet för WMI använder fasta hård diskar.</span><span class="sxs-lookup"><span data-stu-id="1fcb4-144">You need to see only instances with a DriveType of 3 — the value WMI uses for fixed hard disks.</span></span>

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

## <a name="getting-logon-session-information"></a><span data-ttu-id="1fcb4-145">Hämta information om inloggningssession</span><span class="sxs-lookup"><span data-stu-id="1fcb4-145">Getting Logon Session Information</span></span>

<span data-ttu-id="1fcb4-146">Du kan få allmän information om inloggnings sessioner som är associerade med användare via klassen **Win32_LogonSession** WMI:</span><span class="sxs-lookup"><span data-stu-id="1fcb4-146">You can get general information about logon sessions associated with users through the **Win32_LogonSession** WMI class:</span></span>

```powershell
Get-CimInstance -ClassName Win32_LogonSession
```

## <a name="getting-the-user-logged-on-to-a-computer"></a><span data-ttu-id="1fcb4-147">Få användaren inloggad på en dator</span><span class="sxs-lookup"><span data-stu-id="1fcb4-147">Getting the User Logged on to a Computer</span></span>

<span data-ttu-id="1fcb4-148">Du kan visa användaren som är inloggad på ett visst dator system med hjälp av Win32_ComputerSystem.</span><span class="sxs-lookup"><span data-stu-id="1fcb4-148">You can display the user logged on to a particular computer system using Win32_ComputerSystem.</span></span> <span data-ttu-id="1fcb4-149">Det här kommandot returnerar bara den användare som är inloggad på system Skriv bordet:</span><span class="sxs-lookup"><span data-stu-id="1fcb4-149">This command returns only the user logged on to the system desktop:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName
```

## <a name="getting-local-time-from-a-computer"></a><span data-ttu-id="1fcb4-150">Hämta lokal tid från en dator</span><span class="sxs-lookup"><span data-stu-id="1fcb4-150">Getting Local Time from a Computer</span></span>

<span data-ttu-id="1fcb4-151">Du kan hämta den aktuella lokala tiden på en speciell dator med hjälp av **Win32_LocalTime** WMI-klassen.</span><span class="sxs-lookup"><span data-stu-id="1fcb4-151">You can retrieve the current local time on a specific computer by using the **Win32_LocalTime** WMI class.</span></span>

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

## <a name="displaying-service-status"></a><span data-ttu-id="1fcb4-152">Visar tjänst status</span><span class="sxs-lookup"><span data-stu-id="1fcb4-152">Displaying Service Status</span></span>

<span data-ttu-id="1fcb4-153">Om du vill visa status för alla tjänster på en speciell dator kan du använda `Get-Service` cmdleten lokalt.</span><span class="sxs-lookup"><span data-stu-id="1fcb4-153">To view the status of all services on a specific computer, you can locally use the `Get-Service` cmdlet.</span></span> <span data-ttu-id="1fcb4-154">För fjärrsystem kan du använda klassen **Win32_Service** WMI.</span><span class="sxs-lookup"><span data-stu-id="1fcb4-154">For remote systems, you can use the **Win32_Service** WMI class.</span></span> <span data-ttu-id="1fcb4-155">Om du också använder `Select-Object` för att filtrera resultaten till **status**, **namn**och **DisplayName**är utdataformatet nästan identiskt med `Get-Service`:</span><span class="sxs-lookup"><span data-stu-id="1fcb4-155">If you also use `Select-Object` to filter the results to **Status**, **Name**, and **DisplayName**, the output format will be almost identical to that from `Get-Service`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service | Select-Object -Property Status,Name,DisplayName
```

<span data-ttu-id="1fcb4-156">Om du vill tillåta hela visningen av namn för tillfälliga tjänster med extremt långa namn, kan du använda `Format-Table` med parametrarna **AutoSize** och **wrap** för att optimera kolumn bredden och tillåta långa namn att figursättas i stället för att trunkeras:</span><span class="sxs-lookup"><span data-stu-id="1fcb4-156">To allow the complete display of names for the occasional services with extremely long names, you may want to use `Format-Table` with the **AutoSize** and **Wrap** parameters, to optimize column width and allow long names to wrap instead of being truncated:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
