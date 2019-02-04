---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Arbeta med skrivare
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: 5638629fdf79371c8eff9ee9194b642034250fff
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686959"
---
# <a name="working-with-printers"></a>Arbeta med skrivare

Du kan använda Windows PowerShell för att hantera skrivare med hjälp av WMI och WScript.Network COM-objektet från WSH. Vi använder en blandning av båda verktygen för att demonstrera specifika uppgifter.

### <a name="listing-printer-connections"></a>Visa en lista över anslutningar

Det enklaste sättet att visa en lista över skrivare som är installerad på en dator är att använda WMI **Win32_Printer** klass:

```powershell
Get-WmiObject -Class Win32_Printer -ComputerName
```

Du kan också lista skrivarna med hjälp av den **WScript.Network** COM-objekt som vanligtvis används i WSH skript:

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

Eftersom det här kommandot returnerar en sträng samling portnamn och enheten skrivarnamn utan någon särskiljande etiketter, är det inte enkelt att tolka.

### <a name="adding-a-network-printer"></a>Att lägga till en nätverksskrivare

Om du vill lägga till en ny nätverksskrivare, Använd **WScript.Network**:

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### <a name="setting-a-default-printer"></a>Ange en standardskrivare

För att du använder WMI för att ange standardskrivaren, hitta i den **Win32_Printer** samling och sedan anropa den **SetDefaultPrinter** metod:

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

**WScript.Network** är lite enklare att använda, eftersom den har en **SetDefaultPrinter** metod som tar endast skrivarnamnet som ett argument:

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

### <a name="removing-a-printer-connection"></a>Ta bort en anslutning

Ta bort en anslutning med den **WScript.Network RemovePrinterConnection** metod:

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```