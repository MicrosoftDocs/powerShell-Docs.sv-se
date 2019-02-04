---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Hämta WMI-objekt Get-WmiObject
ms.assetid: f0ddfc7d-6b5e-4832-82de-2283597ea70d
ms.openlocfilehash: 522822ac3ea6f08b20fa5af6c9accb48b01035d3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688464"
---
# <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="ff09d-103">Hämta WMI-objekt (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="ff09d-103">Getting WMI Objects (Get-WmiObject)</span></span>

## <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="ff09d-104">Hämta WMI-objekt (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="ff09d-104">Getting WMI Objects (Get-WmiObject)</span></span>

<span data-ttu-id="ff09d-105">Windows Management Instrumentation (WMI) är en core-teknik för Windows-systemadministration eftersom den Exponerar en stor mängd information på ett enhetligt sätt.</span><span class="sxs-lookup"><span data-stu-id="ff09d-105">Windows Management Instrumentation (WMI) is a core technology for Windows system administration because it exposes a wide range of information in a uniform manner.</span></span> <span data-ttu-id="ff09d-106">På grund av hur mycket WMI gör det möjligt att, Windows PowerShell-cmdlet för att komma åt WMI-objekt, **Get-WmiObject**, är en av de mest användbara för att göra riktiga arbetet.</span><span class="sxs-lookup"><span data-stu-id="ff09d-106">Because of how much WMI makes possible, the Windows PowerShell cmdlet for accessing WMI objects, **Get-WmiObject**, is one of the most useful for doing real work.</span></span> <span data-ttu-id="ff09d-107">Vi kommer att diskutera hur du använder Get-WmiObject att komma åt WMI-objekt och sedan hur du använder WMI-objekt för att utföra vissa åtgärder.</span><span class="sxs-lookup"><span data-stu-id="ff09d-107">We are going to discuss how to use Get-WmiObject to access WMI objects and then how to use WMI objects to do specific things.</span></span>

### <a name="listing-wmi-classes"></a><span data-ttu-id="ff09d-108">Visa en lista över WMI-klasser</span><span class="sxs-lookup"><span data-stu-id="ff09d-108">Listing WMI Classes</span></span>

<span data-ttu-id="ff09d-109">Det första problemet som uppstår i de flesta WMI-användare försöker att ta reda på vad du kan göra med WMI.</span><span class="sxs-lookup"><span data-stu-id="ff09d-109">The first problem most WMI users encounter is trying to find out what can be done with WMI.</span></span> <span data-ttu-id="ff09d-110">WMI-klasser beskriver de resurser som kan hanteras.</span><span class="sxs-lookup"><span data-stu-id="ff09d-110">WMI classes describe the resources that can be managed.</span></span> <span data-ttu-id="ff09d-111">Det finns hundratals WMI-klasser, vilket innehåller flera egenskaper.</span><span class="sxs-lookup"><span data-stu-id="ff09d-111">There are hundreds of WMI classes, some of which contain dozens of properties.</span></span>

<span data-ttu-id="ff09d-112">**Get-WmiObject** åtgärdar problemet genom att göra WMI identifierbart.</span><span class="sxs-lookup"><span data-stu-id="ff09d-112">**Get-WmiObject** addresses this problem by making WMI discoverable.</span></span> <span data-ttu-id="ff09d-113">Du kan hämta en lista över de WMI-klasserna som är tillgängliga på den lokala datorn genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="ff09d-113">You can get a list of the WMI classes available on the local computer by typing:</span></span>

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

<span data-ttu-id="ff09d-114">Du kan hämta samma information från en fjärrdator med hjälp av parametern ComputerName, om du anger ett datornamn eller IP-adress:</span><span class="sxs-lookup"><span data-stu-id="ff09d-114">You can retrieve the same information from a remote computer by using the ComputerName parameter, specifying a computer name or IP address:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

<span data-ttu-id="ff09d-115">Klass-listan som returneras av fjärrdatorer kan variera beroende på det specifika operativsystemet på datorn och viss WMI-tilläggen har lagts till av installerade program.</span><span class="sxs-lookup"><span data-stu-id="ff09d-115">The class listing returned by remote computers may vary due to the specific operating system the computer is running and the particular WMI extensions added by installed applications.</span></span>

> [!NOTE]
> <span data-ttu-id="ff09d-116">När du använder Get-WmiObject för att ansluta till en fjärrdator, fjärrdatorn måste köra WMI och under standardkonfigurationen kontot du använder måste vara i gruppen lokala administratörer på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="ff09d-116">When using Get-WmiObject to connect to a remote computer, the remote computer must be running WMI and, under the default configuration, the account you are using must be in the local administrators group on the remote computer.</span></span> <span data-ttu-id="ff09d-117">Fjärrsystemet behöver inte ha Windows PowerShell installerad.</span><span class="sxs-lookup"><span data-stu-id="ff09d-117">The remote system does not need to have Windows PowerShell installed.</span></span> <span data-ttu-id="ff09d-118">På så sätt kan du administrera operativsystem som inte kör Windows PowerShell, men har WMI som är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="ff09d-118">This allows you to administer operating systems that are not running Windows PowerShell, but do have WMI available.</span></span>

<span data-ttu-id="ff09d-119">Du kan även inkludera datornamn när du ansluter till det lokala systemet.</span><span class="sxs-lookup"><span data-stu-id="ff09d-119">You can even include the ComputerName when connecting to the local system.</span></span> <span data-ttu-id="ff09d-120">Du kan använda den lokala datorns namn, dess IP-adress (eller loopback-adressen 127.0.0.1) eller WMI-formatet '.' som datornamn.</span><span class="sxs-lookup"><span data-stu-id="ff09d-120">You can use the local computer's name, its IP address (or the loopback address 127.0.0.1), or the WMI-style '.' as the computer name.</span></span> <span data-ttu-id="ff09d-121">Om du använder Windows PowerShell på en dator med namnet Admin01 med IP-adress 192.168.1.90 returnerar följande kommandon för alla WMI-klass för datorn:</span><span class="sxs-lookup"><span data-stu-id="ff09d-121">If you are running Windows PowerShell on a computer named Admin01 with IP address 192.168.1.90, the following commands will all return the WMI class listing for that computer:</span></span>

```powershell
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

<span data-ttu-id="ff09d-122">Get-WmiObject använder root/cimv2-namnområdet som standard.</span><span class="sxs-lookup"><span data-stu-id="ff09d-122">Get-WmiObject uses the root/cimv2 namespace by default.</span></span> <span data-ttu-id="ff09d-123">Om du vill ange en annan WMI-namnområde kan använda den **Namespace** parametern och ange namnområdessökvägen för motsvarande:</span><span class="sxs-lookup"><span data-stu-id="ff09d-123">If you want to specify another WMI namespace, use the **Namespace** parameter and specify the corresponding namespace path:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a><span data-ttu-id="ff09d-124">Visa information om WMI-klass</span><span class="sxs-lookup"><span data-stu-id="ff09d-124">Displaying WMI Class Details</span></span>

<span data-ttu-id="ff09d-125">Om du redan känner till namnet på en WMI-klass, kan du använda den för att få information direkt.</span><span class="sxs-lookup"><span data-stu-id="ff09d-125">If you already know the name of a WMI class, you can use it to get information immediately.</span></span> <span data-ttu-id="ff09d-126">Till exempel en WMI-klasser som ofta används för att hämta information om en dator är **Win32_OperatingSystem**.</span><span class="sxs-lookup"><span data-stu-id="ff09d-126">For example, one of the WMI classes commonly used for retrieving information about a computer is **Win32_OperatingSystem**.</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

<span data-ttu-id="ff09d-127">Även om vi visar alla parametrar, kan kommandot uttryckas i ett mer kortfattad sätt.</span><span class="sxs-lookup"><span data-stu-id="ff09d-127">Although we are showing all of the parameters, the command can be expressed in a more succinct way.</span></span> <span data-ttu-id="ff09d-128">Den **ComputerName** parametern är inte nödvändigt när du ansluter till det lokala systemet.</span><span class="sxs-lookup"><span data-stu-id="ff09d-128">The **ComputerName** parameter is not necessary when connecting to the local system.</span></span> <span data-ttu-id="ff09d-129">Vi visar den för att demonstrera mest vanliga fall och påminna dig om parametern.</span><span class="sxs-lookup"><span data-stu-id="ff09d-129">We show it to demonstrate the most general case and remind you about the parameter.</span></span> <span data-ttu-id="ff09d-130">Den **Namespace** root/cimv2 som standard, men kan utelämnas också.</span><span class="sxs-lookup"><span data-stu-id="ff09d-130">The **Namespace** defaults to root/cimv2, and can be omitted as well.</span></span> <span data-ttu-id="ff09d-131">Slutligen, de flesta cmdletar kan du utelämna namnet på gemensamma parametrar.</span><span class="sxs-lookup"><span data-stu-id="ff09d-131">Finally, most cmdlets allow you to omit the name of common parameters.</span></span> <span data-ttu-id="ff09d-132">Med Get-WmiObject, om inget namn har angetts för den första parametern, Windows PowerShell behandlas den som den **klass** parametern.</span><span class="sxs-lookup"><span data-stu-id="ff09d-132">With Get-WmiObject, if no name is specified for the first parameter, Windows PowerShell treats it as the **Class** parameter.</span></span> <span data-ttu-id="ff09d-133">Det innebär att det sista kommandot har utfärdats genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="ff09d-133">This means the last command could have been issued by typing:</span></span>

```powershell
Get-WmiObject Win32_OperatingSystem
```

<span data-ttu-id="ff09d-134">Den **Win32_OperatingSystem** klassen har många fler egenskaper än de som visas här.</span><span class="sxs-lookup"><span data-stu-id="ff09d-134">The **Win32_OperatingSystem** class has many more properties than those displayed here.</span></span> <span data-ttu-id="ff09d-135">Du kan använda Get-Member för att visa alla egenskaper.</span><span class="sxs-lookup"><span data-stu-id="ff09d-135">You can use Get-Member to see all the properties.</span></span> <span data-ttu-id="ff09d-136">Egenskaperna för en WMI-klass är automatiskt tillgängliga som andra objektegenskaper:</span><span class="sxs-lookup"><span data-stu-id="ff09d-136">The properties of a WMI class are automatically available like other object properties:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Get-Member -MemberType Property

   TypeName: System.Management.ManagementObject#root\cimv2\Win32_OperatingSyste
m

Name                                      MemberType Definition
----                                      ---------- ----------
__CLASS                                   Property   System.String __CLASS {...
...
BootDevice                                Property   System.String BootDevic...
BuildNumber                               Property   System.String BuildNumb...
...
```

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a><span data-ttu-id="ff09d-137">Visa icke-standard-egenskaper med Format-cmdletar</span><span class="sxs-lookup"><span data-stu-id="ff09d-137">Displaying Non-Default Properties with Format Cmdlets</span></span>

<span data-ttu-id="ff09d-138">Om du vill att informationen i den **Win32_OperatingSystem** klassen som inte visas som standard, kan du visa den med hjälp av den **Format** cmdletar.</span><span class="sxs-lookup"><span data-stu-id="ff09d-138">If you want information contained in the **Win32_OperatingSystem** class that is not displayed by default, you can display it by using the **Format** cmdlets.</span></span> <span data-ttu-id="ff09d-139">Till exempel om du vill visa data för tillgängligt minne, skriver du:</span><span class="sxs-lookup"><span data-stu-id="ff09d-139">For example, if you want to display available memory data, type:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> <span data-ttu-id="ff09d-140">Jokertecken fungerar med egenskapsnamn i **Format-Table**, så det slutliga pipeline-elementet kan minskas till `Format-Table -Property Total,Free`</span><span class="sxs-lookup"><span data-stu-id="ff09d-140">Wildcards work with property names in **Format-Table**, so the final pipeline element can be reduced to `Format-Table -Property Total,Free`</span></span>

<span data-ttu-id="ff09d-141">Minnesdata kan vara lättare att läsa om du formatera den som en lista genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="ff09d-141">The memory data might be more readable if you format it as a list by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```
