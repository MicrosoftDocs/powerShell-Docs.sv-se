---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Arbeta med skrivare
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: 5638629fdf79371c8eff9ee9194b642034250fff
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954508"
---
# <a name="working-with-printers"></a>Arbeta med skrivare

Du kan använda Windows PowerShell för att hantera skrivare med hjälp av WMI och WScript.Network COM-objektet från WSH. Vi använder en blandning av båda verktyg för att visa specifika uppgifter.

### <a name="listing-printer-connections"></a>Visar en lista över skrivaranslutningar

Det enklaste sättet att visa en lista över skrivare installerad på en dator är att använda WMI **Win32_Printer** klass:

```powershell
Get-WmiObject -Class Win32_Printer -ComputerName
```

Du kan också en lista över skrivare med hjälp av den **WScript.Network** COM-objektet som vanligtvis används i WSH-skript:

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

Eftersom det här kommandot returnerar en sträng samling portnamn och skrivare enhetsnamn utan särskiljande etiketter, är det inte enkelt att tolka.

### <a name="adding-a-network-printer"></a>Lägga till en nätverksskrivare

Om du vill lägga till en ny skrivare i nätverket, Använd **WScript.Network**:

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### <a name="setting-a-default-printer"></a>Ange en standardskrivare

Om du vill använda WMI för att ange standardskrivare, hitta skrivaren i den **Win32_Printer** samling och sedan anropa den **SetDefaultPrinter** metod:

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