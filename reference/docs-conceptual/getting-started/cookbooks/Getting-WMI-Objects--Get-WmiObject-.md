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
# <a name="getting-wmi-objects-get-wmiobject"></a>Hämta WMI-objekt (Get-WmiObject)

## <a name="getting-wmi-objects-get-wmiobject"></a>Hämta WMI-objekt (Get-WmiObject)

Windows Management Instrumentation (WMI) är en teknik för kärnor för administration av Windows system eftersom den Exponerar en stor mängd information på ett enhetligt sätt. På grund av hur mycket WMI gör möjligt, Windows PowerShell-cmdlet för att komma åt WMI-objekt **Get-WmiObject**, är en av de mest användbara för att göra arbetet. Vi kommer att diskutera hur du använder Get-WmiObject att komma åt WMI-objekt och hur du gör vissa saker med hjälp av WMI-objekt.

### <a name="listing-wmi-classes"></a>Visar en lista över WMI-klasser

Det första problemet uppstår i de flesta WMI-användare försöker att ta reda på vad som kan göras med WMI. WMI-klasser som beskriver de resurser som kan hanteras. Det finns hundratals WMI-klasser, varav några innehåller dussintals egenskaper.

**Get-WmiObject** löser problemet genom att göra WMI kan upptäckas. Du kan hämta en lista över de WMI-klasserna som är tillgängliga på den lokala datorn genom att skriva:

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

Du kan hämta samma information från en fjärrdator med hjälp av parametern ComputerName anger ett datornamn eller IP-adress:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

Klass-listan som returneras av fjärrdatorer kan variera beroende på det aktuella operativsystemet som körs på datorn och viss WMI-tilläggen läggs till av installerade program.

> [!NOTE]
> När du använder Get-WmiObject för att ansluta till en fjärrdator, fjärrdatorn måste köra WMI och under standardkonfigurationen kontot du använder måste vara i den lokala administratörsgruppen på fjärrdatorn. Fjärrsystemet behöver inte ha Windows PowerShell är installerat. På så sätt kan du administrera operativsystem som inte kör Windows PowerShell, men har WMI som är tillgängliga.

Du kan även inkludera ComputerName vid anslutning till det lokala systemet. Du kan använda den lokala datorns namn, IP-adressen (eller loopback-adressen 127.0.0.1) eller WMI-format '.' som datornamn. Om du kör Windows PowerShell på en dator med namnet Admin01 med IP-adress 192.168.1.90 returnerar följande kommandon alla WMI-klassen lista för datorn:

```powershell
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

Get-WmiObject använder root/cimv2-namnområdet som standard. Om du vill ange en annan WMI-namnområde kan använda den **Namespace** parametern och ange motsvarande namnområdessökvägen:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a>Visa information om WMI-klass

Om du redan känner till namnet på en WMI-klassen kan använda du den för att hämta information direkt. Till exempel en WMI-klasser som ofta används för att hämta information om en dator är **Win32_OperatingSystem**.

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

Även om vi visas alla parametrar uttryckas kommandot i en kortfattad fler sätt. Den **ComputerName** parameter är inte nödvändigt när du ansluter till det lokala systemet. Vi visar det mest vanliga fall påvisa och påminna dig om parametern. Den **Namespace** root/cimv2 som standard, men kan utelämnas samt. Slutligen kan de flesta cmdlets du utelämna namnet på gemensamma parametrar. Med Get-WmiObject, om inget namn har angetts för den första parametern, Windows PowerShell behandlas den som den **klassen** parameter. Detta innebär att det sista kommandot har utfärdats genom att skriva:

```powershell
Get-WmiObject Win32_OperatingSystem
```

Den **Win32_OperatingSystem** klassen har många fler egenskaper än de som visas här. Du kan använda Get-medlem för att se alla egenskaper. Egenskaper för WMI-klassen är automatiskt tillgängliga som andra egenskaper för objekt:

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

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a>Visa egenskaper för icke-förvalt med formatet Cmdlets

Om du vill att informationen i den **Win32_OperatingSystem** klassen som inte visas som standard, kan du visa det med hjälp av den **Format** cmdlets. Skriv till exempel om du vill visa data för tillgängligt minne:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> Jokertecken arbeta med egenskapsnamn i **Format-Table**, så det slutliga pipeline-elementet kan minskas till **Format-Table-egenskapen totala*, lediga *

Minnesdata kan vara lättare att läsa om du formaterar som en lista genom att skriva:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```