---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Hämta WMI-objekt Hämta WmiObject
ms.openlocfilehash: 93276ce12135342af2d6f238976e65e5d8bdde7a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030208"
---
# <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="5df28-103">Hämta WMI-objekt (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="5df28-103">Getting WMI Objects (Get-WmiObject)</span></span>

## <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="5df28-104">Hämta WMI-objekt (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="5df28-104">Getting WMI Objects (Get-WmiObject)</span></span>

<span data-ttu-id="5df28-105">Windows Management Instrumentation (WMI) är en kärn teknik för administration av Windows-system eftersom det visar en mängd olika information på ett enhetligt sätt.</span><span class="sxs-lookup"><span data-stu-id="5df28-105">Windows Management Instrumentation (WMI) is a core technology for Windows system administration because it exposes a wide range of information in a uniform manner.</span></span> <span data-ttu-id="5df28-106">På grund av hur mycket WMI gör kan Windows PowerShell-cmdleten för att komma åt WMI-objekt, **Get-WmiObject**, vara en av de mest användbara för att utföra verkligt arbete.</span><span class="sxs-lookup"><span data-stu-id="5df28-106">Because of how much WMI makes possible, the Windows PowerShell cmdlet for accessing WMI objects, **Get-WmiObject**, is one of the most useful for doing real work.</span></span> <span data-ttu-id="5df28-107">Vi ska diskutera hur du använder Get-WmiObject för att komma åt WMI-objekt och sedan använda WMI-objekt för att utföra vissa saker.</span><span class="sxs-lookup"><span data-stu-id="5df28-107">We are going to discuss how to use Get-WmiObject to access WMI objects and then how to use WMI objects to do specific things.</span></span>

### <a name="listing-wmi-classes"></a><span data-ttu-id="5df28-108">Lista WMI-klasser</span><span class="sxs-lookup"><span data-stu-id="5df28-108">Listing WMI Classes</span></span>

<span data-ttu-id="5df28-109">Det första problemet som de flesta WMI-användare drabbas av försöker ta reda på vad som kan göras med WMI.</span><span class="sxs-lookup"><span data-stu-id="5df28-109">The first problem most WMI users encounter is trying to find out what can be done with WMI.</span></span> <span data-ttu-id="5df28-110">WMI-klasser beskriver de resurser som kan hanteras.</span><span class="sxs-lookup"><span data-stu-id="5df28-110">WMI classes describe the resources that can be managed.</span></span> <span data-ttu-id="5df28-111">Det finns hundratals WMI-klasser, varav vissa innehåller dussin tals egenskaper.</span><span class="sxs-lookup"><span data-stu-id="5df28-111">There are hundreds of WMI classes, some of which contain dozens of properties.</span></span>

<span data-ttu-id="5df28-112">**Get-WmiObject** löser problemet genom att göra WMI synligt.</span><span class="sxs-lookup"><span data-stu-id="5df28-112">**Get-WmiObject** addresses this problem by making WMI discoverable.</span></span> <span data-ttu-id="5df28-113">Du kan hämta en lista över de WMI-klasser som är tillgängliga på den lokala datorn genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="5df28-113">You can get a list of the WMI classes available on the local computer by typing:</span></span>

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

<span data-ttu-id="5df28-114">Du kan hämta samma information från en fjärrdator med hjälp av parametern ComputerName, och ange ett dator namn eller en IP-adress:</span><span class="sxs-lookup"><span data-stu-id="5df28-114">You can retrieve the same information from a remote computer by using the ComputerName parameter, specifying a computer name or IP address:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

<span data-ttu-id="5df28-115">De klass listor som returneras av fjärrdatorer kan variera beroende på vilket operativ system som körs på datorn och de specifika WMI-tillägg som har lagts till av installerade program.</span><span class="sxs-lookup"><span data-stu-id="5df28-115">The class listing returned by remote computers may vary due to the specific operating system the computer is running and the particular WMI extensions added by installed applications.</span></span>

> [!NOTE]
> <span data-ttu-id="5df28-116">När du använder Get-WmiObject för att ansluta till en fjärrdator måste fjärrdatorn köra WMI och, under standard konfigurationen, måste kontot som du använder vara i den lokala administratörs gruppen på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="5df28-116">When using Get-WmiObject to connect to a remote computer, the remote computer must be running WMI and, under the default configuration, the account you are using must be in the local administrators group on the remote computer.</span></span> <span data-ttu-id="5df28-117">Windows PowerShell behöver inte vara installerat på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="5df28-117">The remote system does not need to have Windows PowerShell installed.</span></span> <span data-ttu-id="5df28-118">På så sätt kan du administrera operativ system som inte kör Windows PowerShell, men som har WMI tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="5df28-118">This allows you to administer operating systems that are not running Windows PowerShell, but do have WMI available.</span></span>

<span data-ttu-id="5df28-119">Du kan till och med ta med dator namnet när du ansluter till det lokala systemet.</span><span class="sxs-lookup"><span data-stu-id="5df28-119">You can even include the ComputerName when connecting to the local system.</span></span> <span data-ttu-id="5df28-120">Du kan använda namnet på den lokala datorn, dess IP-adress (eller loopback-adressen 127.0.0.1) eller WMI-formatet "." som dator namn.</span><span class="sxs-lookup"><span data-stu-id="5df28-120">You can use the local computer's name, its IP address (or the loopback address 127.0.0.1), or the WMI-style '.' as the computer name.</span></span> <span data-ttu-id="5df28-121">Om du kör Windows PowerShell på en dator med namnet Admin01 med IP-192.168.1.90, kommer följande kommandon att returnera WMI-klass listan för datorn:</span><span class="sxs-lookup"><span data-stu-id="5df28-121">If you are running Windows PowerShell on a computer named Admin01 with IP address 192.168.1.90, the following commands will all return the WMI class listing for that computer:</span></span>

```powershell
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

<span data-ttu-id="5df28-122">Get-WmiObject använder rot-/cimv2-namnområdet som standard.</span><span class="sxs-lookup"><span data-stu-id="5df28-122">Get-WmiObject uses the root/cimv2 namespace by default.</span></span> <span data-ttu-id="5df28-123">Om du vill ange ett annat WMI-namnområde använder du parametern **namespace** och anger motsvarande sökväg för namn området:</span><span class="sxs-lookup"><span data-stu-id="5df28-123">If you want to specify another WMI namespace, use the **Namespace** parameter and specify the corresponding namespace path:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a><span data-ttu-id="5df28-124">Visar information om WMI-klass</span><span class="sxs-lookup"><span data-stu-id="5df28-124">Displaying WMI Class Details</span></span>

<span data-ttu-id="5df28-125">Om du redan känner till namnet på en WMI-klass kan du använda den för att få information direkt.</span><span class="sxs-lookup"><span data-stu-id="5df28-125">If you already know the name of a WMI class, you can use it to get information immediately.</span></span> <span data-ttu-id="5df28-126">Till exempel är en av de WMI-klasser som ofta används för att hämta information om en dator **Win32_OperatingSystem**.</span><span class="sxs-lookup"><span data-stu-id="5df28-126">For example, one of the WMI classes commonly used for retrieving information about a computer is **Win32_OperatingSystem**.</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

<span data-ttu-id="5df28-127">Även om vi visar alla parametrar kan kommandot uttryckas på ett mer kortfattad sätt.</span><span class="sxs-lookup"><span data-stu-id="5df28-127">Although we are showing all of the parameters, the command can be expressed in a more succinct way.</span></span> <span data-ttu-id="5df28-128">Parametern **computername** behövs inte vid anslutning till det lokala systemet.</span><span class="sxs-lookup"><span data-stu-id="5df28-128">The **ComputerName** parameter is not necessary when connecting to the local system.</span></span> <span data-ttu-id="5df28-129">Vi visar det för att demonstrera det mest generella fallet och påminna dig om parametern.</span><span class="sxs-lookup"><span data-stu-id="5df28-129">We show it to demonstrate the most general case and remind you about the parameter.</span></span> <span data-ttu-id="5df28-130">**Namn området** är som standard rot-cimv2 och kan även utelämnas.</span><span class="sxs-lookup"><span data-stu-id="5df28-130">The **Namespace** defaults to root/cimv2, and can be omitted as well.</span></span> <span data-ttu-id="5df28-131">Slutligen kan du med de flesta cmdlet: ar utesluta namnet på gemensamma parametrar.</span><span class="sxs-lookup"><span data-stu-id="5df28-131">Finally, most cmdlets allow you to omit the name of common parameters.</span></span> <span data-ttu-id="5df28-132">Med Get-WmiObject, om inget namn har angetts för den första parametern, behandlar Windows PowerShell den som **klass** parameter.</span><span class="sxs-lookup"><span data-stu-id="5df28-132">With Get-WmiObject, if no name is specified for the first parameter, Windows PowerShell treats it as the **Class** parameter.</span></span> <span data-ttu-id="5df28-133">Det innebär att det sista kommandot kan ha utfärdats genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="5df28-133">This means the last command could have been issued by typing:</span></span>

```powershell
Get-WmiObject Win32_OperatingSystem
```

<span data-ttu-id="5df28-134">**Win32_OperatingSystem** -klassen har många fler egenskaper än de som visas här.</span><span class="sxs-lookup"><span data-stu-id="5df28-134">The **Win32_OperatingSystem** class has many more properties than those displayed here.</span></span> <span data-ttu-id="5df28-135">Du kan använda Get-Member för att se alla egenskaper.</span><span class="sxs-lookup"><span data-stu-id="5df28-135">You can use Get-Member to see all the properties.</span></span> <span data-ttu-id="5df28-136">Egenskaperna för en WMI-klass är automatiskt tillgängliga som andra objekt egenskaper:</span><span class="sxs-lookup"><span data-stu-id="5df28-136">The properties of a WMI class are automatically available like other object properties:</span></span>

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

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a><span data-ttu-id="5df28-137">Visa egenskaper som inte är standard med format-cmdletar</span><span class="sxs-lookup"><span data-stu-id="5df28-137">Displaying Non-Default Properties with Format Cmdlets</span></span>

<span data-ttu-id="5df28-138">Om du vill ha information som finns i **Win32_OperatingSystem** -klassen som inte visas som standard, kan du Visa den med hjälp av **format** -cmdletar.</span><span class="sxs-lookup"><span data-stu-id="5df28-138">If you want information contained in the **Win32_OperatingSystem** class that is not displayed by default, you can display it by using the **Format** cmdlets.</span></span> <span data-ttu-id="5df28-139">Om du till exempel vill visa tillgängliga minnes data skriver du:</span><span class="sxs-lookup"><span data-stu-id="5df28-139">For example, if you want to display available memory data, type:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> <span data-ttu-id="5df28-140">Jokertecken fungerar med egenskaps namn i **Format-Table**, så det sista pipeline-elementet kan minskas till `Format-Table -Property Total,Free`</span><span class="sxs-lookup"><span data-stu-id="5df28-140">Wildcards work with property names in **Format-Table**, so the final pipeline element can be reduced to `Format-Table -Property Total,Free`</span></span>

<span data-ttu-id="5df28-141">Minnes data kan vara mer läsbara om du formaterar den som en lista genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="5df28-141">The memory data might be more readable if you format it as a list by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```
