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
# <a name="getting-wmi-objects-get-ciminstance"></a>Hämta WMI-objekt (Get-CimInstance)

## <a name="getting-wmi-objects-get-ciminstance"></a>Hämta WMI-objekt (Get-CimInstance)

Windows Management Instrumentation (WMI) är en kärn teknik för administration av Windows-system eftersom det visar en mängd olika information på ett enhetligt sätt. På grund av hur mycket WMI gör, är PowerShell-cmdleten för att komma åt `Get-CimInstance`WMI-objekt, en av de mest användbara för att utföra verkligt arbete. Vi ska diskutera hur du använder CimCmdlets för att komma åt WMI-objekt och sedan använda WMI-objekt för att utföra vissa saker.

### <a name="listing-wmi-classes"></a>Lista WMI-klasser

Det första problemet som de flesta WMI-användare drabbas av försöker ta reda på vad som kan göras med WMI. WMI-klasser beskriver de resurser som kan hanteras. Det finns hundratals WMI-klasser, varav vissa innehåller dussin tals egenskaper.

`Get-CimClass`löser problemet genom att göra WMI synligt. Du kan hämta en lista över de WMI-klasser som är tillgängliga på den lokala datorn genom att skriva:

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

Du kan hämta samma information från en fjärrdator med hjälp av parametern **computername** , och ange ett dator namn eller en IP-adress:

```powershell
Get-CimClass -Namespace root/CIMV2 -ComputerName 192.168.1.29
```

De klass listor som returneras av fjärrdatorer kan variera beroende på vilket operativ system som körs på datorn och de specifika WMI-tillägg som har lagts till av installerade program.

> [!NOTE]
> När du använder CIM-cmdlets för att ansluta till en fjärrdator måste fjärrdatorn köra WMI och kontot som du använder måste vara i den lokala administratörs gruppen på fjärrdatorn.
> Du behöver inte ha PowerShell installerat på fjärrdatorn. På så sätt kan du administrera operativ system som inte kör PowerShell, men som har WMI tillgängligt.

### <a name="displaying-wmi-class-details"></a>Visar information om WMI-klass

Om du redan känner till namnet på en WMI-klass kan du använda den för att få information direkt. Till exempel är en av de WMI-klasser som ofta används för att hämta information om en dator **Win32_OperatingSystem**.

```powershell
Get-CimInstance -Class Win32_OperatingSystem
```

```Output
SystemDirectory     Organization BuildNumber RegisteredUser SerialNumber            Version
---------------     ------------ ----------- -------------- ------------            -------
C:\WINDOWS\system32 Microsoft    18362       USER1          00330-80000-00000-AA175 10.0.18362
```

Även om vi visar alla parametrar kan kommandot uttryckas på ett mer kortfattad sätt.
Parametern **computername** behövs inte vid anslutning till det lokala systemet. Vi visar det för att demonstrera det mest generella fallet och påminna dig om parametern. **Namn området** `root/CIMV2`är som standard och kan även utelämnas. Slutligen kan du med de flesta cmdlet: ar utesluta namnet på gemensamma parametrar. Med `Get-CimInstance`, om inget namn har angetts för den första parametern, behandlar PowerShell den som **klass** parameter. Det innebär att det sista kommandot kan ha utfärdats genom att skriva:

```powershell
Get-CimInstance Win32_OperatingSystem
```

**Win32_OperatingSystem** -klassen har många fler egenskaper än de som visas här. Du kan använda Get-Member för att se alla egenskaper. Egenskaperna för en WMI-klass är automatiskt tillgängliga som andra objekt egenskaper:

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

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a>Visa egenskaper som inte är standard med format-cmdletar

Om du vill ha information som finns i **Win32_OperatingSystem** -klassen som inte visas som standard, kan du Visa den med hjälp av **format** -cmdletar. Om du till exempel vill visa tillgängliga minnes data skriver du:

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
> Jokertecken fungerar med egenskaps namn `Format-Table`i, så det sista pipeline-elementet kan minskas till`Format-Table -Property Total*Memory*, Free*`

Minnes data kan vara mer läsbara om du formaterar den som en lista genom att skriva:

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
