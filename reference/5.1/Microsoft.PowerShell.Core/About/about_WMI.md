---
description: Windows Management Instrumentation (WMI) använder Common Information Model (CIM) för att representera system, program, nätverk, enheter och andra hanterbara komponenter i det moderna företaget.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wmi?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WMI
ms.openlocfilehash: d24b952ee167e51815d6d9920e95bbc9a6bb9608
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271929"
---
# <a name="about-wmi"></a>Om WMI

## <a name="short-description"></a>KORT BESKRIVNING

Windows Management Instrumentation (WMI) använder Common Information Model (CIM) för att representera system, program, nätverk, enheter och andra hanterbara komponenter i det moderna företaget.

## <a name="long-description"></a>LÅNG BESKRIVNING

Windows Management Instrumentation (WMI) är Microsofts implementering av Web-Based Enterprise Management (WBEM), bransch standard.

Klassisk WMI använder DCOM för att kommunicera med nätverksanslutna enheter för att hantera fjärrsystem. Windows PowerShell 3,0 introducerar en CIM-provider som använder WinRM för att ta bort beroendet av DCOM. Den här CIM-providern använder också nya WMI-providers-API: er som gör att utvecklare kan skriva Windows PowerShell-cmdlets i intern kod (C \+ \+ ).

Blanda inte WMI-providrar med Windows PowerShell-leverantörer. Många Windows-funktioner har en associerad WMI-provider som visar hanterings funktionerna. Om du vill hämta WMI-providers kör du en WMI-fråga som hämtar instanser av klassen __Provider WMI, till exempel följande fråga.

```powershell
Get-WmiObject -Class __Provider
```

## <a name="three-components-of-wmi"></a>TRE KOMPONENTER I WMI

Följande tre komponenter i WMI interagerar med Windows PowerShell: namnrymder, providers och klasser.

WMI-namnområden ordnar WMI-providers och WMI-klasser i grupper av relaterade komponenter. På så sätt liknar de .NET Framework namn områden.
Namn områden är inte fysiska platser, men är mer logiska databaser.
Alla WMI-namnområden är instanser av klassen __Namespace system. Standard namn området för WMI är rot \/ -cimv2 (sedan Microsoft Windows 2000). Använd ett kommando med följande format om du vill använda Windows PowerShell för att hämta WMI-namnrymder i den aktuella sessionen.

```powershell
Get-WmiObject -Class __Namespace
```

Om du vill hämta WMI-namnrymder i andra namn områden använder du parametern namespace för att ändra sökningens plats. Följande kommando hittar WMI-namnrymder som finns i namn området rot/Cimv2/program.

```powershell
Get-WmiObject -Class __Namespace -Namespace root/CIMv2/applications
```

WMI-namnrymder är hierarkiska. Därför kräver en rekursiv fråga som börjar vid rot namn rymden att hämta en lista över alla namn områden i ett visst system.

WMI-providers visar information om Windows-hanterbara objekt. En provider hämtar data från en komponent och skickar dessa data via WMI till ett hanterings program, till exempel Windows PowerShell. De flesta WMI-providers är dynamiska leverantörer, vilket innebär att de hämtar data dynamiskt när de begärs via hanterings programmet.

## <a name="finding-wmi-classes"></a>HITTA WMI-KLASSER

I en standard installation av Windows 8 finns det fler än 1 100 WMI-klasser i rot- \/ Cimv2. Med den här många WMI-klasser identifierar utmaningarna vilken WMI-klass som ska användas för att utföra en speciell uppgift. Windows PowerShell 3,0 erbjuder två sätt att hitta WMI-klasser som är relaterade till ett speciellt ämne.

Om du till exempel vill hitta WMI-klasser i rot \\ cimv2 WMI-namnrymd som är relaterade till diskar, kan du använda en fråga som den som visas här.

```powershell
Get-WmiObject -List *disk*
```

Om du vill hitta WMI-klasser som är relaterade till minne kan du använda en fråga som den som visas här.

```powershell
Get-WmiObject -List *memory*
```

CIM-cmdletarna ger också möjlighet att identifiera WMI-klasser. Använd Get-CIMClass-cmdleten för att göra detta. Kommandot som visas här listar WMI-klasser relaterade till video.

```powershell
Get-CimClass *video*
```

När du anpassar WMI-namnrymder och använder med hjälp av tabb-expansion kan du enkelt identifiera namn områden för underordnade WMI. I följande exempel visar Get-CimClass-cmdleten WMI-klasser relaterade till energi inställningar.
För att hitta den, anger du `root/CIMV2/` namn området och trycker sedan på tabbtangenten flera gånger tills Power namespace visas. Här är kommandot:

```powershell
Get-CimClass *power* -Namespace root/cimv2/power
```
