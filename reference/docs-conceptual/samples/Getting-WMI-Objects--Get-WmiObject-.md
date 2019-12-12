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
# <a name="getting-wmi-objects-get-wmiobject"></a>Hämta WMI-objekt (Get-WmiObject)

## <a name="getting-wmi-objects-get-wmiobject"></a>Hämta WMI-objekt (Get-WmiObject)

Windows Management Instrumentation (WMI) är en kärn teknik för administration av Windows-system eftersom det visar en mängd olika information på ett enhetligt sätt. På grund av hur mycket WMI gör kan Windows PowerShell-cmdleten för att komma åt WMI-objekt, **Get-WmiObject**, vara en av de mest användbara för att utföra verkligt arbete. Vi ska diskutera hur du använder Get-WmiObject för att komma åt WMI-objekt och sedan använda WMI-objekt för att utföra vissa saker.

### <a name="listing-wmi-classes"></a>Lista WMI-klasser

Det första problemet som de flesta WMI-användare drabbas av försöker ta reda på vad som kan göras med WMI. WMI-klasser beskriver de resurser som kan hanteras. Det finns hundratals WMI-klasser, varav vissa innehåller dussin tals egenskaper.

**Get-WmiObject** löser problemet genom att göra WMI synligt. Du kan hämta en lista över de WMI-klasser som är tillgängliga på den lokala datorn genom att skriva:

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

Du kan hämta samma information från en fjärrdator med hjälp av parametern ComputerName, och ange ett dator namn eller en IP-adress:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

De klass listor som returneras av fjärrdatorer kan variera beroende på vilket operativ system som körs på datorn och de specifika WMI-tillägg som har lagts till av installerade program.

> [!NOTE]
> När du använder Get-WmiObject för att ansluta till en fjärrdator måste fjärrdatorn köra WMI och, under standard konfigurationen, måste kontot som du använder vara i den lokala administratörs gruppen på fjärrdatorn. Windows PowerShell behöver inte vara installerat på fjärrdatorn. På så sätt kan du administrera operativ system som inte kör Windows PowerShell, men som har WMI tillgängligt.

Du kan till och med ta med dator namnet när du ansluter till det lokala systemet. Du kan använda namnet på den lokala datorn, dess IP-adress (eller loopback-adressen 127.0.0.1) eller WMI-formatet "." som dator namn. Om du kör Windows PowerShell på en dator med namnet Admin01 med IP-192.168.1.90, kommer följande kommandon att returnera WMI-klass listan för datorn:

```powershell
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

Get-WmiObject använder rot-/cimv2-namnområdet som standard. Om du vill ange ett annat WMI-namnområde använder du parametern **namespace** och anger motsvarande sökväg för namn området:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a>Visar information om WMI-klass

Om du redan känner till namnet på en WMI-klass kan du använda den för att få information direkt. Till exempel är en av de WMI-klasser som ofta används för att hämta information om en dator **Win32_OperatingSystem**.

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

Även om vi visar alla parametrar kan kommandot uttryckas på ett mer kortfattad sätt. Parametern **computername** behövs inte vid anslutning till det lokala systemet. Vi visar det för att demonstrera det mest generella fallet och påminna dig om parametern. **Namn området** är som standard rot-cimv2 och kan även utelämnas. Slutligen kan du med de flesta cmdlet: ar utesluta namnet på gemensamma parametrar. Med Get-WmiObject, om inget namn har angetts för den första parametern, behandlar Windows PowerShell den som **klass** parameter. Det innebär att det sista kommandot kan ha utfärdats genom att skriva:

```powershell
Get-WmiObject Win32_OperatingSystem
```

**Win32_OperatingSystem** -klassen har många fler egenskaper än de som visas här. Du kan använda Get-Member för att se alla egenskaper. Egenskaperna för en WMI-klass är automatiskt tillgängliga som andra objekt egenskaper:

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

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a>Visa egenskaper som inte är standard med format-cmdletar

Om du vill ha information som finns i **Win32_OperatingSystem** -klassen som inte visas som standard, kan du Visa den med hjälp av **format** -cmdletar. Om du till exempel vill visa tillgängliga minnes data skriver du:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> Jokertecken fungerar med egenskaps namn i **Format-Table**, så det sista pipeline-elementet kan minskas till `Format-Table -Property Total,Free`

Minnes data kan vara mer läsbara om du formaterar den som en lista genom att skriva:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```
