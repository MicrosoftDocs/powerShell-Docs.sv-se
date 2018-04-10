---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Samla in information om datorer
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: c914a7133a1ac0a05346233db802175f7f29c6b2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="collecting-information-about-computers"></a><span data-ttu-id="6506c-103">Samla in information om datorer</span><span class="sxs-lookup"><span data-stu-id="6506c-103">Collecting Information About Computers</span></span>

<span data-ttu-id="6506c-104">**Get-WmiObject** är den viktigaste cmdleten för allmän system hanteringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="6506c-104">**Get-WmiObject** is the most important cmdlet for general system management tasks.</span></span> <span data-ttu-id="6506c-105">Alla kritiska undersystemet inställningar är tillgängliga via WMI.</span><span class="sxs-lookup"><span data-stu-id="6506c-105">All critical subsystem settings are exposed through WMI.</span></span> <span data-ttu-id="6506c-106">Dessutom behandlas WMI data som objekt i samlingar med ett eller flera objekt.</span><span class="sxs-lookup"><span data-stu-id="6506c-106">Furthermore, WMI treats data as objects that are in collections of one or more items.</span></span> <span data-ttu-id="6506c-107">Eftersom Windows PowerShell kan du också fungerar med objekt och har en pipeline som gör att du kan hantera en eller flera objekt på samma sätt, kan du utföra vissa avancerade med mycket lite av allmänna WMI-åtkomst.</span><span class="sxs-lookup"><span data-stu-id="6506c-107">Because Windows PowerShell also works with objects and has a pipeline that allows you to treat single or multiple objects in the same way, generic WMI access allows you to perform some advanced tasks with very little work.</span></span>

<span data-ttu-id="6506c-108">Följande exempel visar hur du samlar in specifik information med hjälp av **Get-WmiObject** mot en valfri dator.</span><span class="sxs-lookup"><span data-stu-id="6506c-108">The following examples demonstrate how to collect specific information by using **Get-WmiObject** against an arbitrary computer.</span></span> <span data-ttu-id="6506c-109">Anger vi den **ComputerName** parametern med värdet punkt (**.**), som motsvarar den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="6506c-109">We specify the **ComputerName** parameter with the dot value (**.**), which represents the local computer.</span></span> <span data-ttu-id="6506c-110">Du kan ange ett namn eller IP-adress som är associerad med en annan dator som du kan nå via WMI.</span><span class="sxs-lookup"><span data-stu-id="6506c-110">You can specify a name or IP address associated with any computer you can reach through WMI.</span></span> <span data-ttu-id="6506c-111">Om du vill hämta information om den lokala datorn, kan du utelämna den **- ComputerName.**</span><span class="sxs-lookup"><span data-stu-id="6506c-111">To retrieve information about the local computer, you could omit the **-ComputerName.**</span></span>

### <a name="listing-desktop-settings"></a><span data-ttu-id="6506c-112">Visar en lista över inställningar för skrivbord</span><span class="sxs-lookup"><span data-stu-id="6506c-112">Listing Desktop Settings</span></span>

<span data-ttu-id="6506c-113">Vi börjar med ett kommando som samlar in information om de stationära datorer på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="6506c-113">We'll begin with a command that collects information about the desktops on the local computer.</span></span>

```powershell
Get-WmiObject -Class Win32_Desktop -ComputerName .
```

<span data-ttu-id="6506c-114">Detta returnerar information för alla datorer, oavsett om de är används eller inte.</span><span class="sxs-lookup"><span data-stu-id="6506c-114">This returns information for all desktops, whether they are in use or not.</span></span>

> [!NOTE]
> <span data-ttu-id="6506c-115">Information som returneras av vissa WMI-klasser kan vara mycket detaljerad och ofta innehåller metadata om WMI-klassen.</span><span class="sxs-lookup"><span data-stu-id="6506c-115">Information returned by some WMI classes can be very detailed, and often include metadata about the WMI class.</span></span> <span data-ttu-id="6506c-116">Eftersom de flesta av dessa metadataegenskaper har namn som börjar med ett dubbelt understreck, kan du filtrera egenskaper med Select-Object.</span><span class="sxs-lookup"><span data-stu-id="6506c-116">Because most of these metadata properties have names that begin with a double underscore, you can filter the properties using Select-Object.</span></span> <span data-ttu-id="6506c-117">Ange egenskaper som börjar med bokstäver med hjälp av **[a – z]**\* som värde för egenskapen.</span><span class="sxs-lookup"><span data-stu-id="6506c-117">Specify only properties that begin with alphabetic characters by using **[a-z]**\* as the Property value.</span></span> <span data-ttu-id="6506c-118">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="6506c-118">For example:</span></span>

```powershell
Get-WmiObject -Class Win32_Desktop -ComputerName . | Select-Object -Property [a-z]*
```

<span data-ttu-id="6506c-119">Om du vill filtrera bort metadata, använder du en pipelineoperator (|) för att skicka resultatet av kommandot Get-WmiObject till \*\* Select-Object - egenskapen [a – z] \*\*\*.</span><span class="sxs-lookup"><span data-stu-id="6506c-119">To filter out the metadata, use a pipeline operator (|) to send the results of the Get-WmiObject command to \*\*Select-Object -Property [a-z]\*\*\*.</span></span>

### <a name="listing-bios-information"></a><span data-ttu-id="6506c-120">Visar en lista över BIOS-Information</span><span class="sxs-lookup"><span data-stu-id="6506c-120">Listing BIOS Information</span></span>

<span data-ttu-id="6506c-121">Klassen WMI Win32_BIOS returnerar ganska compact och fullständig information om systemets BIOS på den lokala datorn:</span><span class="sxs-lookup"><span data-stu-id="6506c-121">The WMI Win32_BIOS class returns fairly compact and complete information about the system BIOS on the local computer:</span></span>

```powershell
Get-WmiObject -Class Win32_BIOS -ComputerName .
```

### <a name="listing-processor-information"></a><span data-ttu-id="6506c-122">Visar en lista över processorinformation</span><span class="sxs-lookup"><span data-stu-id="6506c-122">Listing Processor Information</span></span>

<span data-ttu-id="6506c-123">Du kan hämta information om allmänna med hjälp av WMI **Win32_Processor** class, även om du förmodligen vill filtrera informationen:</span><span class="sxs-lookup"><span data-stu-id="6506c-123">You can retrieve general processor information by using WMI's **Win32_Processor** class, although you will likely want to filter the information:</span></span>

```powershell
Get-WmiObject -Class Win32_Processor -ComputerName . | Select-Object -Property [a-z]*
```

<span data-ttu-id="6506c-124">För en allmän beskrivning av processortypen sträng kan du bara returnera den **SystemType** egenskapen:</span><span class="sxs-lookup"><span data-stu-id="6506c-124">For a generic description string of the processor family, you can just return the **SystemType** property:</span></span>

```
PS> Get-WmiObject -Class Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

### <a name="listing-computer-manufacturer-and-model"></a><span data-ttu-id="6506c-125">Visar en lista över datortillverkare och modell</span><span class="sxs-lookup"><span data-stu-id="6506c-125">Listing Computer Manufacturer and Model</span></span>

<span data-ttu-id="6506c-126">Datorinformation för modellen är också tillgänglig från **Win32_ComputerSystem**.</span><span class="sxs-lookup"><span data-stu-id="6506c-126">Computer model information is also available from **Win32_ComputerSystem**.</span></span> <span data-ttu-id="6506c-127">Standardutdata visas behöver inte någon filtrering för att tillhandahålla OEM-data:</span><span class="sxs-lookup"><span data-stu-id="6506c-127">The standard displayed output will not need any filtering to provide OEM data:</span></span>

```
PS> Get-WmiObject -Class Win32_ComputerSystem

Domain              : WORKGROUP
Manufacturer        : Compaq Presario 06
Model               : DA243A-ABA 6415cl NA910
Name                : MyPC
PrimaryOwnerName    : Jane Doe
TotalPhysicalMemory : 804765696
```

<span data-ttu-id="6506c-128">Dina utdata från kommandon som den här, som returnerar information direkt från vissa maskinvara är endast lika bra som data som du har.</span><span class="sxs-lookup"><span data-stu-id="6506c-128">Your output from commands such as this, which return information directly from some hardware, is only as good as the data you have.</span></span> <span data-ttu-id="6506c-129">Viss information är inte korrekt konfigurerad av maskinvarutillverkare och kan därför inte tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="6506c-129">Some information is not correctly configured by hardware manufacturers and may therefore be unavailable.</span></span>

### <a name="listing-installed-hotfixes"></a><span data-ttu-id="6506c-130">Lista över installerade snabbkorrigeringar</span><span class="sxs-lookup"><span data-stu-id="6506c-130">Listing Installed Hotfixes</span></span>

<span data-ttu-id="6506c-131">Du kan visa en lista med alla installerade snabbkorrigeringar med hjälp av **Win32_QuickFixEngineering**:</span><span class="sxs-lookup"><span data-stu-id="6506c-131">You can list all installed hotfixes by using **Win32_QuickFixEngineering**:</span></span>

```powershell
Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName .
```

<span data-ttu-id="6506c-132">Den här klassen returnerar en lista med snabbkorrigeringar som ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="6506c-132">This class returns a list of hotfixes that looks like this:</span></span>

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

<span data-ttu-id="6506c-133">För mer koncis utdata kanske du vill undanta vissa egenskaper.</span><span class="sxs-lookup"><span data-stu-id="6506c-133">For more succinct output, you may want to exclude some properties.</span></span> <span data-ttu-id="6506c-134">Även om du kan använda den **Get-WmiObject egenskapen** parametern välja endast den **HotFixID**, göra så kommer att returnera mer, eftersom alla metadata visas som standard:</span><span class="sxs-lookup"><span data-stu-id="6506c-134">Although you can use the **Get-WmiObject's Property** parameter to choose only the **HotFixID**, doing so will actually return more information, because all the metadata is displayed by default:</span></span>

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

<span data-ttu-id="6506c-135">Ytterligare data returneras eftersom egenskapen parameter i **Get-WmiObject** begränsar egenskaperna som returneras från WMI-klassinstanser inte objektet som returneras till Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6506c-135">The additional data is returned, because the Property parameter in **Get-WmiObject** restricts the properties returned from WMI class instances, not the object returned to Windows PowerShell.</span></span> <span data-ttu-id="6506c-136">Om du vill minska utdata, Använd **Select-Object**:</span><span class="sxs-lookup"><span data-stu-id="6506c-136">To reduce the output, use **Select-Object**:</span></span>

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId

HotFixId
--------
KB910437
```

### <a name="listing-operating-system-version-information"></a><span data-ttu-id="6506c-137">Visar en lista över versionsinformation för operativsystemet</span><span class="sxs-lookup"><span data-stu-id="6506c-137">Listing Operating System Version Information</span></span>

<span data-ttu-id="6506c-138">Den **Win32_OperatingSystem** klassegenskaper inkludera version och service pack.</span><span class="sxs-lookup"><span data-stu-id="6506c-138">The **Win32_OperatingSystem** class properties include version and service pack information.</span></span> <span data-ttu-id="6506c-139">Du kan uttryckligen välja endast dessa egenskaper att hämta versionsinformation om en sammanfattande från **Win32_OperatingSystem**:</span><span class="sxs-lookup"><span data-stu-id="6506c-139">You can explicitly select only these properties to get a version information summary from **Win32_OperatingSystem**:</span></span>

```powershell
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

<span data-ttu-id="6506c-140">Du kan också använda jokertecken med den **Select-Object-egenskapen** parameter.</span><span class="sxs-lookup"><span data-stu-id="6506c-140">You can also use wildcards with the **Select-Object's Property** parameter.</span></span> <span data-ttu-id="6506c-141">Eftersom alla egenskaper som börjar med antingen **skapa** eller **ServicePack** är viktigt att du använder här, kan vi förkorta det till följande format:</span><span class="sxs-lookup"><span data-stu-id="6506c-141">Because all the properties beginning with either **Build** or **ServicePack** are important to use here, we can shorten this to the following form:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*

BuildNumber             : 2600
BuildType               : Uniprocessor Free
OSType                  : 18
ServicePackMajorVersion : 2
ServicePackMinorVersion : 0
```

### <a name="listing-local-users-and-owner"></a><span data-ttu-id="6506c-142">Visar en lista över lokala användare och ägare</span><span class="sxs-lookup"><span data-stu-id="6506c-142">Listing Local Users and Owner</span></span>

<span data-ttu-id="6506c-143">Lokala allmän användarinformation, antalet licensierade användare, aktuellt antal användare och ägarens namn – kan hittas med ett urval av **Win32_OperatingSystem** egenskaper.</span><span class="sxs-lookup"><span data-stu-id="6506c-143">Local general user information—number of licensed users, current number of users, and owner name—can be found with a selection of **Win32_OperatingSystem** properties.</span></span> <span data-ttu-id="6506c-144">Du kan uttryckligen välja egenskaper som ska visas så här:</span><span class="sxs-lookup"><span data-stu-id="6506c-144">You can explicitly select the properties to display like this:</span></span>

```powershell
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

<span data-ttu-id="6506c-145">En mer koncis version med jokertecken är:</span><span class="sxs-lookup"><span data-stu-id="6506c-145">A more succinct version using wildcards is:</span></span>

```powershell
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### <a name="getting-available-disk-space"></a><span data-ttu-id="6506c-146">Hämtning av ledigt diskutrymme</span><span class="sxs-lookup"><span data-stu-id="6506c-146">Getting Available Disk Space</span></span>

<span data-ttu-id="6506c-147">Du kan använda WMI Win32_LogicalDisk klassen om du vill se diskutrymme och ledigt utrymme för lokala enheter.</span><span class="sxs-lookup"><span data-stu-id="6506c-147">To see the disk space and free space for local drives, you can use the WMI Win32_LogicalDisk class.</span></span> <span data-ttu-id="6506c-148">Du behöver se endast instanser med en DriveType av 3 – värdet WMI använder för fasta hårddiskar.</span><span class="sxs-lookup"><span data-stu-id="6506c-148">You need to see only instances with a DriveType of 3—the value WMI uses for fixed hard disks.</span></span>

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

### <a name="getting-logon-session-information"></a><span data-ttu-id="6506c-149">Hämtning av inloggningsinformationen för Session</span><span class="sxs-lookup"><span data-stu-id="6506c-149">Getting Logon Session Information</span></span>

<span data-ttu-id="6506c-150">Du kan få allmän information om inloggningssessioner som är kopplade till användare via Win32_LogonSession WMI-klassen:</span><span class="sxs-lookup"><span data-stu-id="6506c-150">You can get general information about logon sessions associated with users through the WMI Win32_LogonSession class:</span></span>

```powershell
Get-WmiObject -Class Win32_LogonSession -ComputerName .
```

### <a name="getting-the-user-logged-on-to-a-computer"></a><span data-ttu-id="6506c-151">Att användaren loggat in på en dator</span><span class="sxs-lookup"><span data-stu-id="6506c-151">Getting the User Logged on to a Computer</span></span>

<span data-ttu-id="6506c-152">Du kan visa användare som är anslutna till en viss dator med hjälp av Win32_ComputerSystem.</span><span class="sxs-lookup"><span data-stu-id="6506c-152">You can display the user logged on to a particular computer system using Win32_ComputerSystem.</span></span> <span data-ttu-id="6506c-153">Detta kommando returnerar bara den användaren loggat in på systemet skrivbordet:</span><span class="sxs-lookup"><span data-stu-id="6506c-153">This command returns only the user logged on to the system desktop:</span></span>

```powershell
Get-WmiObject -Class Win32_ComputerSystem -Property UserName -ComputerName .
```

### <a name="getting-local-time-from-a-computer"></a><span data-ttu-id="6506c-154">Hämta lokal tid från en dator</span><span class="sxs-lookup"><span data-stu-id="6506c-154">Getting Local Time from a Computer</span></span>

<span data-ttu-id="6506c-155">Du kan hämta den aktuella lokala tiden på en specifik dator med hjälp av Win32_LocalTime för WMI-klassen.</span><span class="sxs-lookup"><span data-stu-id="6506c-155">You can retrieve the current local time on a specific computer by using the WMI Win32_LocalTime class.</span></span> <span data-ttu-id="6506c-156">Eftersom den här klassen som standard visas alla metadata, kanske du vill filtrera den med hjälp av **Select-Object**:</span><span class="sxs-lookup"><span data-stu-id="6506c-156">Because this class by default displays all metadata, you may want to filter it using **Select-Object**:</span></span>

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

### <a name="displaying-service-status"></a><span data-ttu-id="6506c-157">Visa Status för tjänsten</span><span class="sxs-lookup"><span data-stu-id="6506c-157">Displaying Service Status</span></span>

<span data-ttu-id="6506c-158">Om du vill visa status för alla tjänster på en specifik dator du lokalt kan använda den **Get-Service** cmdlet som tidigare nämnts.</span><span class="sxs-lookup"><span data-stu-id="6506c-158">To view the status of all services on a specific computer, you can locally use the **Get-Service** cmdlet as mentioned earlier.</span></span> <span data-ttu-id="6506c-159">Du kan använda WMI Win32_Service-klassen för fjärranslutna system.</span><span class="sxs-lookup"><span data-stu-id="6506c-159">For remote systems, you can use the WMI Win32_Service class.</span></span> <span data-ttu-id="6506c-160">Om du också använda **Select-Object** att filtrera resultaten till **Status**, **namn**, och **DisplayName**, utdataformatet blir nästan identisk från **Get-Service**:</span><span class="sxs-lookup"><span data-stu-id="6506c-160">If you also use **Select-Object** to filter the results to **Status**, **Name**, and **DisplayName**, the output format will be almost identical to that from **Get-Service**:</span></span>

```powershell
Get-WmiObject -Class Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

<span data-ttu-id="6506c-161">Om du vill tillåta fullständig visningen av namn för tillfällig trafik med mycket långa namn, kanske du vill använda **Format-Table** med den **AutoSize** och **omsluter** parametrar , att optimera kolumnbredden och tillåta långa namn du omsluter i stället för trunkerades:</span><span class="sxs-lookup"><span data-stu-id="6506c-161">To allow the complete display of names for the occasional services with extremely long names, you may want to use **Format-Table** with the **AutoSize** and **Wrap** parameters, to optimize column width and allow long names to wrap instead of being truncated:</span></span>

```powershell
Get-WmiObject -Class Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```