---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Arbeta med skrivare
description: I den här artikeln beskrivs hur du hanterar skrivare i Windows med WMI-objekt och COM-gränssnitt.
ms.openlocfilehash: 2606753783043eeae8e9d461e56f0901149cb8e3
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501090"
---
# <a name="working-with-printers-in-windows"></a>Arbeta med skrivare i Windows

Du kan använda PowerShell för att hantera skrivare med hjälp av WMI och com-objektet **wscript. Network** från WSH. Vi kommer att använda en kombination av båda verktygen för att demonstrera vissa uppgifter.

## <a name="listing-printer-connections"></a>Lista skrivar anslutningar

Det enklaste sättet att lista de skrivare som är installerade på en dator är att använda WMI- **Win32_Printer** -klassen:

```powershell
Get-CimInstance -Class Win32_Printer
```

Du kan också lista skrivare med hjälp av **wscript. Network** com-objektet som vanligt vis används i WSH-skript:

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

Eftersom det här kommandot returnerar en enkel sträng samling med port namn och skrivar enhets namn utan att skilja etiketter, är det inte lätt att tolka.

## <a name="adding-a-network-printer"></a>Lägga till en nätverks skrivare

Om du vill lägga till en ny nätverks skrivare använder du **wscript. Network**:

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

## <a name="setting-a-default-printer"></a>Ange en standard skrivare

Om du vill använda WMI för att ange standard skrivare letar du upp skrivaren i den **Win32_Printer** samlingen och anropar sedan metoden **SetDefaultPrinter** :

```powershell
$printer = Get-CimInstance -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'"
Invoke-CimMethod -InputObject $printer -MethodName SetDefaultPrinter
```

**Wscript. Network** är lite enklare att använda, eftersom det har en **SetDefaultPrinter** -metod som bara tar skrivar namnet som ett argument:

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

## <a name="removing-a-printer-connection"></a>Ta bort en skrivar anslutning

Om du vill ta bort en skrivar anslutning använder du metoden **wscript. Network RemovePrinterConnection** :

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```
