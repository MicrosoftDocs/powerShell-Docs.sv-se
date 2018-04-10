---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Hämta WMI-objekt får WMI-objekt
ms.assetid: f0ddfc7d-6b5e-4832-82de-2283597ea70d
ms.openlocfilehash: 67922426ae3f13ef5f4c70bc70bb3ce1594d3d05
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="79577-103">Hämta WMI-objekt (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="79577-103">Getting WMI Objects (Get-WmiObject)</span></span>

## <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="79577-104">Hämta WMI-objekt (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="79577-104">Getting WMI Objects (Get-WmiObject)</span></span>

<span data-ttu-id="79577-105">Windows Management Instrumentation (WMI) är en teknik för kärnor för administration av Windows system eftersom den Exponerar en stor mängd information på ett enhetligt sätt.</span><span class="sxs-lookup"><span data-stu-id="79577-105">Windows Management Instrumentation (WMI) is a core technology for Windows system administration because it exposes a wide range of information in a uniform manner.</span></span> <span data-ttu-id="79577-106">På grund av hur mycket WMI gör möjligt, Windows PowerShell-cmdlet för att komma åt WMI-objekt **Get-WmiObject**, är en av de mest användbara för att göra arbetet.</span><span class="sxs-lookup"><span data-stu-id="79577-106">Because of how much WMI makes possible, the Windows PowerShell cmdlet for accessing WMI objects, **Get-WmiObject**, is one of the most useful for doing real work.</span></span> <span data-ttu-id="79577-107">Vi kommer att diskutera hur du använder Get-WmiObject att komma åt WMI-objekt och hur du gör vissa saker med hjälp av WMI-objekt.</span><span class="sxs-lookup"><span data-stu-id="79577-107">We are going to discuss how to use Get-WmiObject to access WMI objects and then how to use WMI objects to do specific things.</span></span>

### <a name="listing-wmi-classes"></a><span data-ttu-id="79577-108">Visar en lista över WMI-klasser</span><span class="sxs-lookup"><span data-stu-id="79577-108">Listing WMI Classes</span></span>

<span data-ttu-id="79577-109">Det första problemet uppstår i de flesta WMI-användare försöker att ta reda på vad som kan göras med WMI.</span><span class="sxs-lookup"><span data-stu-id="79577-109">The first problem most WMI users encounter is trying to find out what can be done with WMI.</span></span> <span data-ttu-id="79577-110">WMI-klasser som beskriver de resurser som kan hanteras.</span><span class="sxs-lookup"><span data-stu-id="79577-110">WMI classes describe the resources that can be managed.</span></span> <span data-ttu-id="79577-111">Det finns hundratals WMI-klasser, varav några innehåller dussintals egenskaper.</span><span class="sxs-lookup"><span data-stu-id="79577-111">There are hundreds of WMI classes, some of which contain dozens of properties.</span></span>

<span data-ttu-id="79577-112">**Get-WmiObject** löser problemet genom att göra WMI kan upptäckas.</span><span class="sxs-lookup"><span data-stu-id="79577-112">**Get-WmiObject** addresses this problem by making WMI discoverable.</span></span> <span data-ttu-id="79577-113">Du kan hämta en lista över de WMI-klasserna som är tillgängliga på den lokala datorn genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="79577-113">You can get a list of the WMI classes available on the local computer by typing:</span></span>

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

<span data-ttu-id="79577-114">Du kan hämta samma information från en fjärrdator med hjälp av parametern ComputerName anger ett datornamn eller IP-adress:</span><span class="sxs-lookup"><span data-stu-id="79577-114">You can retrieve the same information from a remote computer by using the ComputerName parameter, specifying a computer name or IP address:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

<span data-ttu-id="79577-115">Klass-listan som returneras av fjärrdatorer kan variera beroende på det aktuella operativsystemet som körs på datorn och viss WMI-tilläggen läggs till av installerade program.</span><span class="sxs-lookup"><span data-stu-id="79577-115">The class listing returned by remote computers may vary due to the specific operating system the computer is running and the particular WMI extensions added by installed applications.</span></span>

> [!NOTE]
> <span data-ttu-id="79577-116">När du använder Get-WmiObject för att ansluta till en fjärrdator, fjärrdatorn måste köra WMI och under standardkonfigurationen kontot du använder måste vara i den lokala administratörsgruppen på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="79577-116">When using Get-WmiObject to connect to a remote computer, the remote computer must be running WMI and, under the default configuration, the account you are using must be in the local administrators group on the remote computer.</span></span> <span data-ttu-id="79577-117">Fjärrsystemet behöver inte ha Windows PowerShell är installerat.</span><span class="sxs-lookup"><span data-stu-id="79577-117">The remote system does not need to have Windows PowerShell installed.</span></span> <span data-ttu-id="79577-118">På så sätt kan du administrera operativsystem som inte kör Windows PowerShell, men har WMI som är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="79577-118">This allows you to administer operating systems that are not running Windows PowerShell, but do have WMI available.</span></span>

<span data-ttu-id="79577-119">Du kan även inkludera ComputerName vid anslutning till det lokala systemet.</span><span class="sxs-lookup"><span data-stu-id="79577-119">You can even include the ComputerName when connecting to the local system.</span></span> <span data-ttu-id="79577-120">Du kan använda den lokala datorns namn, IP-adressen (eller loopback-adressen 127.0.0.1) eller WMI-format '.' som datornamn.</span><span class="sxs-lookup"><span data-stu-id="79577-120">You can use the local computer's name, its IP address (or the loopback address 127.0.0.1), or the WMI-style '.' as the computer name.</span></span> <span data-ttu-id="79577-121">Om du kör Windows PowerShell på en dator med namnet Admin01 med IP-adress 192.168.1.90 returnerar följande kommandon alla WMI-klassen lista för datorn:</span><span class="sxs-lookup"><span data-stu-id="79577-121">If you are running Windows PowerShell on a computer named Admin01 with IP address 192.168.1.90, the following commands will all return the WMI class listing for that computer:</span></span>

```powershell
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

<span data-ttu-id="79577-122">Get-WmiObject använder root/cimv2-namnområdet som standard.</span><span class="sxs-lookup"><span data-stu-id="79577-122">Get-WmiObject uses the root/cimv2 namespace by default.</span></span> <span data-ttu-id="79577-123">Om du vill ange en annan WMI-namnområde kan använda den **Namespace** parametern och ange motsvarande namnområdessökvägen:</span><span class="sxs-lookup"><span data-stu-id="79577-123">If you want to specify another WMI namespace, use the **Namespace** parameter and specify the corresponding namespace path:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a><span data-ttu-id="79577-124">Visa information om WMI-klass</span><span class="sxs-lookup"><span data-stu-id="79577-124">Displaying WMI Class Details</span></span>

<span data-ttu-id="79577-125">Om du redan känner till namnet på en WMI-klassen kan använda du den för att hämta information direkt.</span><span class="sxs-lookup"><span data-stu-id="79577-125">If you already know the name of a WMI class, you can use it to get information immediately.</span></span> <span data-ttu-id="79577-126">Till exempel en WMI-klasser som ofta används för att hämta information om en dator är **Win32_OperatingSystem**.</span><span class="sxs-lookup"><span data-stu-id="79577-126">For example, one of the WMI classes commonly used for retrieving information about a computer is **Win32_OperatingSystem**.</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

<span data-ttu-id="79577-127">Även om vi visas alla parametrar uttryckas kommandot i en kortfattad fler sätt.</span><span class="sxs-lookup"><span data-stu-id="79577-127">Although we are showing all of the parameters, the command can be expressed in a more succinct way.</span></span> <span data-ttu-id="79577-128">Den **ComputerName** parameter är inte nödvändigt när du ansluter till det lokala systemet.</span><span class="sxs-lookup"><span data-stu-id="79577-128">The **ComputerName** parameter is not necessary when connecting to the local system.</span></span> <span data-ttu-id="79577-129">Vi visar det mest vanliga fall påvisa och påminna dig om parametern.</span><span class="sxs-lookup"><span data-stu-id="79577-129">We show it to demonstrate the most general case and remind you about the parameter.</span></span> <span data-ttu-id="79577-130">Den **Namespace** root/cimv2 som standard, men kan utelämnas samt.</span><span class="sxs-lookup"><span data-stu-id="79577-130">The **Namespace** defaults to root/cimv2, and can be omitted as well.</span></span> <span data-ttu-id="79577-131">Slutligen kan de flesta cmdlets du utelämna namnet på gemensamma parametrar.</span><span class="sxs-lookup"><span data-stu-id="79577-131">Finally, most cmdlets allow you to omit the name of common parameters.</span></span> <span data-ttu-id="79577-132">Med Get-WmiObject, om inget namn har angetts för den första parametern, Windows PowerShell behandlas den som den **klassen** parameter.</span><span class="sxs-lookup"><span data-stu-id="79577-132">With Get-WmiObject, if no name is specified for the first parameter, Windows PowerShell treats it as the **Class** parameter.</span></span> <span data-ttu-id="79577-133">Detta innebär att det sista kommandot har utfärdats genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="79577-133">This means the last command could have been issued by typing:</span></span>

```powershell
Get-WmiObject Win32_OperatingSystem
```

<span data-ttu-id="79577-134">Den **Win32_OperatingSystem** klassen har många fler egenskaper än de som visas här.</span><span class="sxs-lookup"><span data-stu-id="79577-134">The **Win32_OperatingSystem** class has many more properties than those displayed here.</span></span> <span data-ttu-id="79577-135">Du kan använda Get-medlem för att se alla egenskaper.</span><span class="sxs-lookup"><span data-stu-id="79577-135">You can use Get-Member to see all the properties.</span></span> <span data-ttu-id="79577-136">Egenskaper för WMI-klassen är automatiskt tillgängliga som andra egenskaper för objekt:</span><span class="sxs-lookup"><span data-stu-id="79577-136">The properties of a WMI class are automatically available like other object properties:</span></span>

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

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a><span data-ttu-id="79577-137">Visa egenskaper för icke-förvalt med formatet Cmdlets</span><span class="sxs-lookup"><span data-stu-id="79577-137">Displaying Non-Default Properties with Format Cmdlets</span></span>

<span data-ttu-id="79577-138">Om du vill att informationen i den **Win32_OperatingSystem** klassen som inte visas som standard, kan du visa det med hjälp av den **Format** cmdlets.</span><span class="sxs-lookup"><span data-stu-id="79577-138">If you want information contained in the **Win32_OperatingSystem** class that is not displayed by default, you can display it by using the **Format** cmdlets.</span></span> <span data-ttu-id="79577-139">Skriv till exempel om du vill visa data för tillgängligt minne:</span><span class="sxs-lookup"><span data-stu-id="79577-139">For example, if you want to display available memory data, type:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> <span data-ttu-id="79577-140">Jokertecken arbeta med egenskapsnamn i **Format-Table**, så det slutliga pipeline-elementet kan minskas till **Format-Table-egenskapen totala*, lediga *</span><span class="sxs-lookup"><span data-stu-id="79577-140">Wildcards work with property names in **Format-Table**, so the final pipeline element can be reduced to **Format-Table -Property Total*,Free*</span></span>

<span data-ttu-id="79577-141">Minnesdata kan vara lättare att läsa om du formaterar som en lista genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="79577-141">The memory data might be more readable if you format it as a list by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```