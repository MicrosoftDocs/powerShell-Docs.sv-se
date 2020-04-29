---
ms.date: 12/23/2019
keywords: PowerShell, cmdlet
title: Hämta WMI-objekt Hämta CimInstance
ms.openlocfilehash: 4ff47844fd367a49f554c7c05c491bdddf28eabc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "77004696"
---
# <a name="getting-wmi-objects-get-ciminstance"></a><span data-ttu-id="00673-103">Hämta WMI-objekt (Get-CimInstance)</span><span class="sxs-lookup"><span data-stu-id="00673-103">Getting WMI Objects (Get-CimInstance)</span></span>

## <a name="getting-wmi-objects-get-ciminstance"></a><span data-ttu-id="00673-104">Hämta WMI-objekt (Get-CimInstance)</span><span class="sxs-lookup"><span data-stu-id="00673-104">Getting WMI Objects (Get-CimInstance)</span></span>

<span data-ttu-id="00673-105">Windows Management Instrumentation (WMI) är en kärn teknik för administration av Windows-system eftersom det visar en mängd olika information på ett enhetligt sätt.</span><span class="sxs-lookup"><span data-stu-id="00673-105">Windows Management Instrumentation (WMI) is a core technology for Windows system administration because it exposes a wide range of information in a uniform manner.</span></span> <span data-ttu-id="00673-106">På grund av hur mycket WMI gör, är PowerShell-cmdleten för att komma åt `Get-CimInstance`WMI-objekt, en av de mest användbara för att utföra verkligt arbete.</span><span class="sxs-lookup"><span data-stu-id="00673-106">Because of how much WMI makes possible, the PowerShell cmdlet for accessing WMI objects, `Get-CimInstance`, is one of the most useful for doing real work.</span></span> <span data-ttu-id="00673-107">Vi ska diskutera hur du använder CimCmdlets för att komma åt WMI-objekt och sedan använda WMI-objekt för att utföra vissa saker.</span><span class="sxs-lookup"><span data-stu-id="00673-107">We are going to discuss how to use the CimCmdlets to access WMI objects and then how to use WMI objects to do specific things.</span></span>

### <a name="listing-wmi-classes"></a><span data-ttu-id="00673-108">Lista WMI-klasser</span><span class="sxs-lookup"><span data-stu-id="00673-108">Listing WMI Classes</span></span>

<span data-ttu-id="00673-109">Det första problemet som de flesta WMI-användare drabbas av försöker ta reda på vad som kan göras med WMI.</span><span class="sxs-lookup"><span data-stu-id="00673-109">The first problem most WMI users encounter is trying to find out what can be done with WMI.</span></span> <span data-ttu-id="00673-110">WMI-klasser beskriver de resurser som kan hanteras.</span><span class="sxs-lookup"><span data-stu-id="00673-110">WMI classes describe the resources that can be managed.</span></span> <span data-ttu-id="00673-111">Det finns hundratals WMI-klasser, varav vissa innehåller dussin tals egenskaper.</span><span class="sxs-lookup"><span data-stu-id="00673-111">There are hundreds of WMI classes, some of which contain dozens of properties.</span></span>

<span data-ttu-id="00673-112">`Get-CimClass`löser problemet genom att göra WMI synligt.</span><span class="sxs-lookup"><span data-stu-id="00673-112">`Get-CimClass` addresses this problem by making WMI discoverable.</span></span> <span data-ttu-id="00673-113">Du kan hämta en lista över de WMI-klasser som är tillgängliga på den lokala datorn genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="00673-113">You can get a list of the WMI classes available on the local computer by typing:</span></span>

```powershell
Get-CimClass -Namespace root/CIMV2 |
  Where-Object CimClassName -like Win32* |
    Select-Object CimClassName
```

```Output
CimClassName
------------
Win32_DeviceChangeEvent
Win32_SystemConfigurationChangeEvent
Win32_VolumeChangeEvent
Win32_SystemTrace
Win32_ProcessTrace
Win32_ProcessStartTrace
Win32_ProcessStopTrace
Win32_ThreadTrace
Win32_ThreadStartTrace
Win32_ThreadStopTrace
...
```

<span data-ttu-id="00673-114">Du kan hämta samma information från en fjärrdator med hjälp av parametern **computername** , och ange ett dator namn eller en IP-adress:</span><span class="sxs-lookup"><span data-stu-id="00673-114">You can retrieve the same information from a remote computer by using the **ComputerName** parameter, specifying a computer name or IP address:</span></span>

```powershell
Get-CimClass -Namespace root/CIMV2 -ComputerName 192.168.1.29
```

<span data-ttu-id="00673-115">De klass listor som returneras av fjärrdatorer kan variera beroende på vilket operativ system som körs på datorn och de specifika WMI-tillägg som har lagts till av installerade program.</span><span class="sxs-lookup"><span data-stu-id="00673-115">The class listing returned by remote computers may vary due to the specific operating system the computer is running and the particular WMI extensions added by installed applications.</span></span>

> [!NOTE]
> <span data-ttu-id="00673-116">När du använder CIM-cmdlets för att ansluta till en fjärrdator måste fjärrdatorn köra WMI och kontot som du använder måste vara i den lokala administratörs gruppen på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="00673-116">When using CIM cmdlets to connect to a remote computer, the remote computer must be running WMI and the account you are using must be in the local administrators group on the remote computer.</span></span>
> <span data-ttu-id="00673-117">Du behöver inte ha PowerShell installerat på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="00673-117">The remote system does not need to have PowerShell installed.</span></span> <span data-ttu-id="00673-118">På så sätt kan du administrera operativ system som inte kör PowerShell, men som har WMI tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="00673-118">This allows you to administer operating systems that are not running PowerShell, but do have WMI available.</span></span>

### <a name="displaying-wmi-class-details"></a><span data-ttu-id="00673-119">Visar information om WMI-klass</span><span class="sxs-lookup"><span data-stu-id="00673-119">Displaying WMI Class Details</span></span>

<span data-ttu-id="00673-120">Om du redan känner till namnet på en WMI-klass kan du använda den för att få information direkt.</span><span class="sxs-lookup"><span data-stu-id="00673-120">If you already know the name of a WMI class, you can use it to get information immediately.</span></span> <span data-ttu-id="00673-121">Till exempel är en av de WMI-klasser som ofta används för att hämta information om en dator **Win32_OperatingSystem**.</span><span class="sxs-lookup"><span data-stu-id="00673-121">For example, one of the WMI classes commonly used for retrieving information about a computer is **Win32_OperatingSystem**.</span></span>

```powershell
Get-CimInstance -Class Win32_OperatingSystem
```

```Output
SystemDirectory     Organization BuildNumber RegisteredUser SerialNumber            Version
---------------     ------------ ----------- -------------- ------------            -------
C:\WINDOWS\system32 Microsoft    18362       USER1          00330-80000-00000-AA175 10.0.18362
```

<span data-ttu-id="00673-122">Även om vi visar alla parametrar kan kommandot uttryckas på ett mer kortfattad sätt.</span><span class="sxs-lookup"><span data-stu-id="00673-122">Although we are showing all of the parameters, the command can be expressed in a more succinct way.</span></span>
<span data-ttu-id="00673-123">Parametern **computername** behövs inte vid anslutning till det lokala systemet.</span><span class="sxs-lookup"><span data-stu-id="00673-123">The **ComputerName** parameter is not necessary when connecting to the local system.</span></span> <span data-ttu-id="00673-124">Vi visar det för att demonstrera det mest generella fallet och påminna dig om parametern.</span><span class="sxs-lookup"><span data-stu-id="00673-124">We show it to demonstrate the most general case and remind you about the parameter.</span></span> <span data-ttu-id="00673-125">**Namn området** `root/CIMV2`är som standard och kan även utelämnas.</span><span class="sxs-lookup"><span data-stu-id="00673-125">The **Namespace** defaults to `root/CIMV2`, and can be omitted as well.</span></span> <span data-ttu-id="00673-126">Slutligen kan du med de flesta cmdlet: ar utesluta namnet på gemensamma parametrar.</span><span class="sxs-lookup"><span data-stu-id="00673-126">Finally, most cmdlets allow you to omit the name of common parameters.</span></span> <span data-ttu-id="00673-127">Med `Get-CimInstance`, om inget namn har angetts för den första parametern, behandlar PowerShell den som **klass** parameter.</span><span class="sxs-lookup"><span data-stu-id="00673-127">With `Get-CimInstance`, if no name is specified for the first parameter, PowerShell treats it as the **Class** parameter.</span></span> <span data-ttu-id="00673-128">Det innebär att det sista kommandot kan ha utfärdats genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="00673-128">This means the last command could have been issued by typing:</span></span>

```powershell
Get-CimInstance Win32_OperatingSystem
```

<span data-ttu-id="00673-129">**Win32_OperatingSystem** -klassen har många fler egenskaper än de som visas här.</span><span class="sxs-lookup"><span data-stu-id="00673-129">The **Win32_OperatingSystem** class has many more properties than those displayed here.</span></span> <span data-ttu-id="00673-130">Du kan använda Get-Member för att se alla egenskaper.</span><span class="sxs-lookup"><span data-stu-id="00673-130">You can use Get-Member to see all the properties.</span></span> <span data-ttu-id="00673-131">Egenskaperna för en WMI-klass är automatiskt tillgängliga som andra objekt egenskaper:</span><span class="sxs-lookup"><span data-stu-id="00673-131">The properties of a WMI class are automatically available like other object properties:</span></span>

```powershell
Get-CimInstance -Class Win32_OperatingSystem | Get-Member -MemberType Property
```

```Output
   TypeName: Microsoft.Management.Infrastructure.CimInstance#root/cimv2/Win32_OperatingSystem
Name                                      MemberType Definition
----                                      ---------- ----------
BootDevice                                Property   string BootDevice {get;}
BuildNumber                               Property   string BuildNumber {get;}
BuildType                                 Property   string BuildType {get;}
Caption                                   Property   string Caption {get;}
CodeSet                                   Property   string CodeSet {get;}
CountryCode                               Property   string CountryCode {get;}
CreationClassName                         Property   string CreationClassName {get;}
CSCreationClassName                       Property   string CSCreationClassName {get;}
CSDVersion                                Property   string CSDVersion {get;}
CSName                                    Property   string CSName {get;}
CurrentTimeZone                           Property   short CurrentTimeZone {get;}
DataExecutionPrevention_32BitApplications Property   bool DataExecutionPrevention_32BitApplications {get;}
DataExecutionPrevention_Available         Property   bool DataExecutionPrevention_Available {get;}
...
```

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a><span data-ttu-id="00673-132">Visa egenskaper som inte är standard med format-cmdletar</span><span class="sxs-lookup"><span data-stu-id="00673-132">Displaying Non-Default Properties with Format Cmdlets</span></span>

<span data-ttu-id="00673-133">Om du vill ha information som finns i **Win32_OperatingSystem** -klassen som inte visas som standard, kan du Visa den med hjälp av **format** -cmdletar.</span><span class="sxs-lookup"><span data-stu-id="00673-133">If you want information contained in the **Win32_OperatingSystem** class that is not displayed by default, you can display it by using the **Format** cmdlets.</span></span> <span data-ttu-id="00673-134">Om du till exempel vill visa tillgängliga minnes data skriver du:</span><span class="sxs-lookup"><span data-stu-id="00673-134">For example, if you want to display available memory data, type:</span></span>

```powershell
Get-CimInstance -Class Win32_OperatingSystem |
  Format-Table -Property TotalVirtualMemorySize, TotalVisibleMemorySize,
    FreePhysicalMemory, FreeVirtualMemory, FreeSpaceInPagingFiles
```

```Output
TotalVirtualMemorySize TotalVisibleMemorySize FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------------- ------------------ ----------------- ----------------------
              33449088               16671872            6451868          18424496               16285032
```

> [!NOTE]
> <span data-ttu-id="00673-135">Jokertecken fungerar med egenskaps namn `Format-Table`i, så det sista pipeline-elementet kan minskas till`Format-Table -Property Total*Memory*, Free*`</span><span class="sxs-lookup"><span data-stu-id="00673-135">Wildcards work with property names in `Format-Table`, so the final pipeline element can be reduced to `Format-Table -Property Total*Memory*, Free*`</span></span>

<span data-ttu-id="00673-136">Minnes data kan vara mer läsbara om du formaterar den som en lista genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="00673-136">The memory data might be more readable if you format it as a list by typing:</span></span>

```powershell
Get-CimInstance -Class Win32_OperatingSystem | Format-List Total*Memory*, Free*
```

```Output
TotalVirtualMemorySize : 33449088
TotalVisibleMemorySize : 16671872
FreePhysicalMemory     : 6524456
FreeSpaceInPagingFiles : 16285808
FreeVirtualMemory      : 18393668
Name                   : Microsoft Windows 10 Pro|C:\WINDOWS|\Device\Harddisk0\Partition2
```
