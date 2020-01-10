---
ms.date: 12/23/2019
keywords: PowerShell, cmdlet
title: Arbeta med skrivare
ms.openlocfilehash: 47c4f230d023ad93e2b65080feaa1dbfae803d08
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736870"
---
# <a name="working-with-printers-in-windows"></a><span data-ttu-id="02281-103">Arbeta med skrivare i Windows</span><span class="sxs-lookup"><span data-stu-id="02281-103">Working with Printers in Windows</span></span>

<span data-ttu-id="02281-104">Du kan använda PowerShell för att hantera skrivare med hjälp av WMI och com-objektet **wscript. Network** från WSH.</span><span class="sxs-lookup"><span data-stu-id="02281-104">You can use PowerShell to manage printers by using WMI and the **WScript.Network** COM object from WSH.</span></span> <span data-ttu-id="02281-105">Vi kommer att använda en kombination av båda verktygen för att demonstrera vissa uppgifter.</span><span class="sxs-lookup"><span data-stu-id="02281-105">We will use a mix of both tools to demonstrate specific tasks.</span></span>

## <a name="listing-printer-connections"></a><span data-ttu-id="02281-106">Lista skrivar anslutningar</span><span class="sxs-lookup"><span data-stu-id="02281-106">Listing Printer Connections</span></span>

<span data-ttu-id="02281-107">Det enklaste sättet att lista de skrivare som är installerade på en dator är att använda WMI- **Win32_Printer** -klassen:</span><span class="sxs-lookup"><span data-stu-id="02281-107">The simplest way to list the printers installed on a computer is to use the WMI **Win32_Printer** class:</span></span>

```powershell
Get-CimInstance -Class Win32_Printer
```

<span data-ttu-id="02281-108">Du kan också lista skrivare med hjälp av **wscript. Network** com-objektet som vanligt vis används i WSH-skript:</span><span class="sxs-lookup"><span data-stu-id="02281-108">You can also list the printers by using the **WScript.Network** COM object that is typically used in WSH scripts:</span></span>

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

<span data-ttu-id="02281-109">Eftersom det här kommandot returnerar en enkel sträng samling med port namn och skrivar enhets namn utan att skilja etiketter, är det inte lätt att tolka.</span><span class="sxs-lookup"><span data-stu-id="02281-109">Because this command returns a simple string collection of port names and printer device names without any distinguishing labels, it is not easy to interpret.</span></span>

## <a name="adding-a-network-printer"></a><span data-ttu-id="02281-110">Lägga till en nätverks skrivare</span><span class="sxs-lookup"><span data-stu-id="02281-110">Adding a Network Printer</span></span>

<span data-ttu-id="02281-111">Om du vill lägga till en ny nätverks skrivare använder du **wscript. Network**:</span><span class="sxs-lookup"><span data-stu-id="02281-111">To add a new network printer, use **WScript.Network**:</span></span>

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

## <a name="setting-a-default-printer"></a><span data-ttu-id="02281-112">Ange en standard skrivare</span><span class="sxs-lookup"><span data-stu-id="02281-112">Setting a Default Printer</span></span>

<span data-ttu-id="02281-113">Om du vill använda WMI för att ange standard skrivare letar du upp skrivaren i den **Win32_Printer** samlingen och anropar sedan metoden **SetDefaultPrinter** :</span><span class="sxs-lookup"><span data-stu-id="02281-113">To use WMI to set the default printer, find the printer in the **Win32_Printer** collection and then invoke the **SetDefaultPrinter** method:</span></span>

```powershell
(Get-CimInstance -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

<span data-ttu-id="02281-114">**Wscript. Network** är lite enklare att använda, eftersom det har en **SetDefaultPrinter** -metod som bara tar skrivar namnet som ett argument:</span><span class="sxs-lookup"><span data-stu-id="02281-114">**WScript.Network** is a little simpler to use, because it has a **SetDefaultPrinter** method that takes only the printer name as an argument:</span></span>

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

## <a name="removing-a-printer-connection"></a><span data-ttu-id="02281-115">Ta bort en skrivar anslutning</span><span class="sxs-lookup"><span data-stu-id="02281-115">Removing a Printer Connection</span></span>

<span data-ttu-id="02281-116">Om du vill ta bort en skrivar anslutning använder du metoden **wscript. Network RemovePrinterConnection** :</span><span class="sxs-lookup"><span data-stu-id="02281-116">To remove a printer connection, use the **WScript.Network RemovePrinterConnection** method:</span></span>

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```
