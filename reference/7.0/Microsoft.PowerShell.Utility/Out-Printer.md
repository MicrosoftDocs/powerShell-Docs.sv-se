---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-printer?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Printer
ms.openlocfilehash: 552ccc39cc19d625c5173df360fa20a10c6040c1
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262353"
---
# <span data-ttu-id="fbbdb-103">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="fbbdb-103">Out-Printer</span></span>

## <span data-ttu-id="fbbdb-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="fbbdb-104">SYNOPSIS</span></span>
<span data-ttu-id="fbbdb-105">Skickar utdata till en skrivare.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-105">Sends output to a printer.</span></span>

## <span data-ttu-id="fbbdb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fbbdb-106">SYNTAX</span></span>

```
Out-Printer [[-Name] <String>] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="fbbdb-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="fbbdb-107">DESCRIPTION</span></span>

<span data-ttu-id="fbbdb-108">`Out-Printer`Cmdleten skickar utdata till standard skrivaren eller till en alternativ skrivare, om en sådan finns angiven.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-108">The `Out-Printer` cmdlet sends output to the default printer or to an alternate printer, if one is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="fbbdb-109">Den här cmdleten introducerades om i PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-109">This cmdlet was reintroduced in PowerShell 7.</span></span> <span data-ttu-id="fbbdb-110">Den här cmdleten är endast tillgänglig på Windows-system som stöder Windows-skrivbordet.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-110">This cmdlet is only available on Windows systems that support the Windows Desktop.</span></span>

## <span data-ttu-id="fbbdb-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="fbbdb-111">EXAMPLES</span></span>

### <span data-ttu-id="fbbdb-112">Exempel 1 – skicka en fil som ska skrivas ut på standard skrivaren</span><span class="sxs-lookup"><span data-stu-id="fbbdb-112">Example 1 - Send a file to be printed on the default printer</span></span>

<span data-ttu-id="fbbdb-113">Det här exemplet visar hur du skriver ut en fil, även om inte `Out-Printer` har en **Sök vägs** parameter.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-113">This example shows how to print a file, even though `Out-Printer` does not have a **Path** parameter.</span></span>

```powershell
Get-Content -Path ./readme.txt | Out-Printer
```

<span data-ttu-id="fbbdb-114">`Get-Content`hämtar innehållet i `readme.txt` filen i den aktuella katalogen och skickar den till `Out-Printer` , som skickar den till standard skrivaren.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-114">`Get-Content`gets the contents of the `readme.txt` file in the current directory and pipes it to `Out-Printer`, which sends it to the default printer.</span></span>

### <span data-ttu-id="fbbdb-115">Exempel 2: skriva ut en sträng till en fjärran sluten skrivare</span><span class="sxs-lookup"><span data-stu-id="fbbdb-115">Example 2: Print a string to a remote printer</span></span>

<span data-ttu-id="fbbdb-116">Det här exemplet skriver ut `Hello, World` till **färg skrivaren PRT-6b** på Server01.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-116">This example prints `Hello, World` to the **Prt-6B Color** printer on Server01.</span></span>

```powershell
"Hello, World" | Out-Printer -Name "\\Server01\Prt-6B Color"
```

<span data-ttu-id="fbbdb-117">Parametern **Name** väljer en speciell skrivare istället för standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-117">The **Name** parameter selects a specific printer, rather than the default.</span></span>

### <span data-ttu-id="fbbdb-118">Exempel 3 – Skriv ut ett hjälp avsnitt till standard skrivaren</span><span class="sxs-lookup"><span data-stu-id="fbbdb-118">Example 3 - Print a help topic to the default printer</span></span>

<span data-ttu-id="fbbdb-119">I det här exemplet skrivs den fullständiga versionen av hjälp avsnittet för `Get-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="fbbdb-119">This example prints the full version of the Help topic for `Get-CimInstance`.</span></span>

```powershell
$H = Get-Help -Full Get-CimInstance
Out-Printer -InputObject $H
```

<span data-ttu-id="fbbdb-120">`Get-Help` hämtar den fullständiga versionen av hjälp avsnittet för `Get-CimInstance` och lagrar den i `$H` variabeln.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-120">`Get-Help` gets the full version of the Help topic for `Get-CimInstance` and stores it in the `$H` variable.</span></span> <span data-ttu-id="fbbdb-121">Parametern **InputObject** skickar värdet `$H` till `Out-Printer` .</span><span class="sxs-lookup"><span data-stu-id="fbbdb-121">The **InputObject** parameter passes the value of `$H` to `Out-Printer`.</span></span>

## <span data-ttu-id="fbbdb-122">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="fbbdb-122">PARAMETERS</span></span>

### <span data-ttu-id="fbbdb-123">– InputObject</span><span class="sxs-lookup"><span data-stu-id="fbbdb-123">-InputObject</span></span>

<span data-ttu-id="fbbdb-124">Anger de objekt som ska skickas till skrivaren.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-124">Specifies the objects to be sent to the printer.</span></span> <span data-ttu-id="fbbdb-125">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-125">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="fbbdb-126">-Name</span><span class="sxs-lookup"><span data-stu-id="fbbdb-126">-Name</span></span>

<span data-ttu-id="fbbdb-127">Skickar utdata till den angivna skrivaren.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-127">Sends the output to the specified printer.</span></span> <span data-ttu-id="fbbdb-128">Parameter namnets **namn** är valfritt.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-128">The parameter name **Name** is optional.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PrinterName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fbbdb-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fbbdb-129">CommonParameters</span></span>

<span data-ttu-id="fbbdb-130">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fbbdb-131">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="fbbdb-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fbbdb-132">INDATA</span><span class="sxs-lookup"><span data-stu-id="fbbdb-132">INPUTS</span></span>

### <span data-ttu-id="fbbdb-133">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="fbbdb-133">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="fbbdb-134">Du kan skicka vidare alla objekt till `Out-Printer` .</span><span class="sxs-lookup"><span data-stu-id="fbbdb-134">You can pipe any object to `Out-Printer`.</span></span>

## <span data-ttu-id="fbbdb-135">UTDATA</span><span class="sxs-lookup"><span data-stu-id="fbbdb-135">OUTPUTS</span></span>

### <span data-ttu-id="fbbdb-136">Inget</span><span class="sxs-lookup"><span data-stu-id="fbbdb-136">None</span></span>

<span data-ttu-id="fbbdb-137">`Out-Printer` returnerar inga objekt.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-137">`Out-Printer` does not return any objects.</span></span>

## <span data-ttu-id="fbbdb-138">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="fbbdb-138">NOTES</span></span>

<span data-ttu-id="fbbdb-139">Cmdletarna som innehåller `Out` verbet formaterar inte objekt.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-139">The cmdlets that contain the `Out` verb do not format objects.</span></span> <span data-ttu-id="fbbdb-140">De återger dem bara och skickar dem till det angivna visnings målet.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-140">They just render them and send them to the specified display destination.</span></span> <span data-ttu-id="fbbdb-141">Om du skickar ett oformaterat objekt till en `Out` cmdlet skickar cmdleten den till en formaterings-cmdlet innan du återger den.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-141">If you send an unformatted object to an `Out` cmdlet, the cmdlet sends it to a formatting cmdlet before rendering it.</span></span>

<span data-ttu-id="fbbdb-142">`Out-Printer` skickar data till skrivaren, men genererar inga utdata-objekt till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-142">`Out-Printer` sends data to the printer, but does not emit any output objects to the pipeline.</span></span> <span data-ttu-id="fbbdb-143">Om du skickar utdata från `Out-Printer` till `Get-Member` , rapporterar det `Get-Member` att inga objekt har angetts.</span><span class="sxs-lookup"><span data-stu-id="fbbdb-143">If you pipe the output of `Out-Printer` to `Get-Member`, `Get-Member` reports that no objects have been specified.</span></span>

## <span data-ttu-id="fbbdb-144">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="fbbdb-144">RELATED LINKS</span></span>

[<span data-ttu-id="fbbdb-145">Ut-fil</span><span class="sxs-lookup"><span data-stu-id="fbbdb-145">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="fbbdb-146">Out-sträng</span><span class="sxs-lookup"><span data-stu-id="fbbdb-146">Out-String</span></span>](Out-String.md)
