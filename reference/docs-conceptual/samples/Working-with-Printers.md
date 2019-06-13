---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Arbeta med skrivare
ms.openlocfilehash: 816388325cc3155f1dbd1bc15fc1736155216092
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030672"
---
# <a name="working-with-printers"></a>Arbeta med skrivare

Du kan använda Windows PowerShell för att hantera skrivare med hjälp av WMI och WScript.Network COM-objektet från WSH. Vi använder en blandning av båda verktygen för att demonstrera specifika uppgifter.

## <a name="listing-printer-connections"></a>Visa en lista över anslutningar

Det enklaste sättet att visa en lista över skrivare som är installerad på en dator är att använda WMI **Win32_Printer** klass:

```powershell
Get-WmiObject -Class Win32_Printer
```

Du kan också lista skrivarna med hjälp av den **WScript.Network** COM-objekt som vanligtvis används i WSH skript:

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

Eftersom det här kommandot returnerar en sträng samling portnamn och enheten skrivarnamn utan någon särskiljande etiketter, är det inte enkelt att tolka.

## <a name="adding-a-network-printer"></a>Att lägga till en nätverksskrivare

Om du vill lägga till en ny nätverksskrivare, Använd **WScript.Network**:

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

## <a name="setting-a-default-printer"></a>Ange en standardskrivare

För att du använder WMI för att ange standardskrivaren, hitta i den **Win32_Printer** samling och sedan anropa den **SetDefaultPrinter** metod:

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

**WScript.Network** är lite enklare att använda, eftersom den har en **SetDefaultPrinter** metod som tar endast skrivarnamnet som ett argument:

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

## <a name="removing-a-printer-connection"></a>Ta bort en anslutning

Ta bort en anslutning med den **WScript.Network RemovePrinterConnection** metod:

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```
