---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Hämta WMI-objekt Get-WmiObject
ms.openlocfilehash: 93276ce12135342af2d6f238976e65e5d8bdde7a
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030208"
---
# <a name="getting-wmi-objects-get-wmiobject"></a>Hämta WMI-objekt (Get-WmiObject)

## <a name="getting-wmi-objects-get-wmiobject"></a>Hämta WMI-objekt (Get-WmiObject)

Windows Management Instrumentation (WMI) är en core-teknik för Windows-systemadministration eftersom den Exponerar en stor mängd information på ett enhetligt sätt. På grund av hur mycket WMI gör det möjligt att, Windows PowerShell-cmdlet för att komma åt WMI-objekt, **Get-WmiObject**, är en av de mest användbara för att göra riktiga arbetet. Vi kommer att diskutera hur du använder Get-WmiObject att komma åt WMI-objekt och sedan hur du använder WMI-objekt för att utföra vissa åtgärder.

### <a name="listing-wmi-classes"></a>Visa en lista över WMI-klasser

Det första problemet som uppstår i de flesta WMI-användare försöker att ta reda på vad du kan göra med WMI. WMI-klasser beskriver de resurser som kan hanteras. Det finns hundratals WMI-klasser, vilket innehåller flera egenskaper.

**Get-WmiObject** åtgärdar problemet genom att göra WMI identifierbart. Du kan hämta en lista över de WMI-klasserna som är tillgängliga på den lokala datorn genom att skriva:

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

Du kan hämta samma information från en fjärrdator med hjälp av parametern ComputerName, om du anger ett datornamn eller IP-adress:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

Klass-listan som returneras av fjärrdatorer kan variera beroende på det specifika operativsystemet på datorn och viss WMI-tilläggen har lagts till av installerade program.

> [!NOTE]
> När du använder Get-WmiObject för att ansluta till en fjärrdator, fjärrdatorn måste köra WMI och under standardkonfigurationen kontot du använder måste vara i gruppen lokala administratörer på fjärrdatorn. Fjärrsystemet behöver inte ha Windows PowerShell installerad. På så sätt kan du administrera operativsystem som inte kör Windows PowerShell, men har WMI som är tillgängliga.

Du kan även inkludera datornamn när du ansluter till det lokala systemet. Du kan använda den lokala datorns namn, dess IP-adress (eller loopback-adressen 127.0.0.1) eller WMI-formatet '.' som datornamn. Om du använder Windows PowerShell på en dator med namnet Admin01 med IP-adress 192.168.1.90 returnerar följande kommandon för alla WMI-klass för datorn:

```powershell
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

Get-WmiObject använder root/cimv2-namnområdet som standard. Om du vill ange en annan WMI-namnområde kan använda den **Namespace** parametern och ange namnområdessökvägen för motsvarande:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a>Visa information om WMI-klass

Om du redan känner till namnet på en WMI-klass, kan du använda den för att få information direkt. Till exempel en WMI-klasser som ofta används för att hämta information om en dator är **Win32_OperatingSystem**.

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

Även om vi visar alla parametrar, kan kommandot uttryckas i ett mer kortfattad sätt. Den **ComputerName** parametern är inte nödvändigt när du ansluter till det lokala systemet. Vi visar den för att demonstrera mest vanliga fall och påminna dig om parametern. Den **Namespace** root/cimv2 som standard, men kan utelämnas också. Slutligen, de flesta cmdletar kan du utelämna namnet på gemensamma parametrar. Med Get-WmiObject, om inget namn har angetts för den första parametern, Windows PowerShell behandlas den som den **klass** parametern. Det innebär att det sista kommandot har utfärdats genom att skriva:

```powershell
Get-WmiObject Win32_OperatingSystem
```

Den **Win32_OperatingSystem** klassen har många fler egenskaper än de som visas här. Du kan använda Get-Member för att visa alla egenskaper. Egenskaperna för en WMI-klass är automatiskt tillgängliga som andra objektegenskaper:

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

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a>Visa icke-standard-egenskaper med Format-cmdletar

Om du vill att informationen i den **Win32_OperatingSystem** klassen som inte visas som standard, kan du visa den med hjälp av den **Format** cmdletar. Till exempel om du vill visa data för tillgängligt minne, skriver du:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> Jokertecken fungerar med egenskapsnamn i **Format-Table**, så det slutliga pipeline-elementet kan minskas till `Format-Table -Property Total,Free`

Minnesdata kan vara lättare att läsa om du formatera den som en lista genom att skriva:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```
