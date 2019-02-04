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
# <a name="working-with-printers"></a><span data-ttu-id="43941-103">Arbeta med skrivare</span><span class="sxs-lookup"><span data-stu-id="43941-103">Working with Printers</span></span>

<span data-ttu-id="43941-104">Du kan använda Windows PowerShell för att hantera skrivare med hjälp av WMI och WScript.Network COM-objektet från WSH.</span><span class="sxs-lookup"><span data-stu-id="43941-104">You can use Windows PowerShell to manage printers by using WMI and the WScript.Network COM object from WSH.</span></span> <span data-ttu-id="43941-105">Vi använder en blandning av båda verktygen för att demonstrera specifika uppgifter.</span><span class="sxs-lookup"><span data-stu-id="43941-105">We will use a mix of both tools to demonstrate specific tasks.</span></span>

### <a name="listing-printer-connections"></a><span data-ttu-id="43941-106">Visa en lista över anslutningar</span><span class="sxs-lookup"><span data-stu-id="43941-106">Listing Printer Connections</span></span>

<span data-ttu-id="43941-107">Det enklaste sättet att visa en lista över skrivare som är installerad på en dator är att använda WMI **Win32_Printer** klass:</span><span class="sxs-lookup"><span data-stu-id="43941-107">The simplest way to list the printers installed on a computer is to use the WMI **Win32_Printer** class:</span></span>

```powershell
Get-WmiObject -Class Win32_Printer -ComputerName
```

<span data-ttu-id="43941-108">Du kan också lista skrivarna med hjälp av den **WScript.Network** COM-objekt som vanligtvis används i WSH skript:</span><span class="sxs-lookup"><span data-stu-id="43941-108">You can also list the printers by using the **WScript.Network** COM object that is typically used in WSH scripts:</span></span>

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

<span data-ttu-id="43941-109">Eftersom det här kommandot returnerar en sträng samling portnamn och enheten skrivarnamn utan någon särskiljande etiketter, är det inte enkelt att tolka.</span><span class="sxs-lookup"><span data-stu-id="43941-109">Because this command returns a simple string collection of port names and printer device names without any distinguishing labels, it is not easy to interpret.</span></span>

### <a name="adding-a-network-printer"></a><span data-ttu-id="43941-110">Att lägga till en nätverksskrivare</span><span class="sxs-lookup"><span data-stu-id="43941-110">Adding a Network Printer</span></span>

<span data-ttu-id="43941-111">Om du vill lägga till en ny nätverksskrivare, Använd **WScript.Network**:</span><span class="sxs-lookup"><span data-stu-id="43941-111">To add a new network printer, use **WScript.Network**:</span></span>

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### <a name="setting-a-default-printer"></a><span data-ttu-id="43941-112">Ange en standardskrivare</span><span class="sxs-lookup"><span data-stu-id="43941-112">Setting a Default Printer</span></span>

<span data-ttu-id="43941-113">För att du använder WMI för att ange standardskrivaren, hitta i den **Win32_Printer** samling och sedan anropa den **SetDefaultPrinter** metod:</span><span class="sxs-lookup"><span data-stu-id="43941-113">To use WMI to set the default printer, find the printer in the **Win32_Printer** collection and then invoke the **SetDefaultPrinter** method:</span></span>

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

<span data-ttu-id="43941-114">**WScript.Network** är lite enklare att använda, eftersom den har en **SetDefaultPrinter** metod som tar endast skrivarnamnet som ett argument:</span><span class="sxs-lookup"><span data-stu-id="43941-114">**WScript.Network** is a little simpler to use, because it has a **SetDefaultPrinter** method that takes only the printer name as an argument:</span></span>

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

### <a name="removing-a-printer-connection"></a><span data-ttu-id="43941-115">Ta bort en anslutning</span><span class="sxs-lookup"><span data-stu-id="43941-115">Removing a Printer Connection</span></span>

<span data-ttu-id="43941-116">Ta bort en anslutning med den **WScript.Network RemovePrinterConnection** metod:</span><span class="sxs-lookup"><span data-stu-id="43941-116">To remove a printer connection, use the **WScript.Network RemovePrinterConnection** method:</span></span>

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```