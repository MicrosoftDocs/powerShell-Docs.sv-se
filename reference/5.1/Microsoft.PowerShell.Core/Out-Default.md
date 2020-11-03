---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-default?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Default
ms.openlocfilehash: 5e434b6af523da25b0128f6d8e85a196eaf09ff2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264230"
---
# <span data-ttu-id="eec14-103">Out-Default</span><span class="sxs-lookup"><span data-stu-id="eec14-103">Out-Default</span></span>

## <span data-ttu-id="eec14-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="eec14-104">SYNOPSIS</span></span>
<span data-ttu-id="eec14-105">Skickar utdata till standard-formateraren och till standardutdata-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="eec14-105">Sends the output to the default formatter and to the default output cmdlet.</span></span>

## <span data-ttu-id="eec14-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="eec14-106">SYNTAX</span></span>

```
Out-Default [-Transcript] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="eec14-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="eec14-107">DESCRIPTION</span></span>

<span data-ttu-id="eec14-108">PowerShell lägger automatiskt `Out-Default` till i slutet av varje pipeline.</span><span class="sxs-lookup"><span data-stu-id="eec14-108">PowerShell automatically adds `Out-Default` to the end of every pipeline.</span></span> <span data-ttu-id="eec14-109">`Out-Default` bestämmer hur objekt strömmen ska formateras och matas ut.</span><span class="sxs-lookup"><span data-stu-id="eec14-109">`Out-Default` decides how to format and output the object stream.</span></span> <span data-ttu-id="eec14-110">Om objekt strömmen är en data ström med strängar, `Out-Default` rör dessa direkt som `Out-Host` anropar lämpliga API: er som tillhandahålls av värden.</span><span class="sxs-lookup"><span data-stu-id="eec14-110">If the object stream is a stream of strings, `Out-Default` pipes these directly to `Out-Host` which calls the appropriate APIs provided by the host.</span></span> <span data-ttu-id="eec14-111">Om objekt strömmen inte innehåller strängar `Out-Default` kontrollerar objektet objektet för att avgöra vad som ska göras.</span><span class="sxs-lookup"><span data-stu-id="eec14-111">If the object stream does not contain strings, `Out-Default` inspects the object to determine what to do.</span></span>
<span data-ttu-id="eec14-112">Först ser det ut som objekt typ och avgör om det finns en registrerad _vy_ för den här objekt typen.</span><span class="sxs-lookup"><span data-stu-id="eec14-112">First it looks at the object type and determines whether there is a registered _view_ for this object type.</span></span>

<span data-ttu-id="eec14-113">PowerShell definierar XML-schemat och en mekanism ( `Update-FormatData` cmdleten) där vem som helst kan registrera vyer för en objekt typ.</span><span class="sxs-lookup"><span data-stu-id="eec14-113">PowerShell defines XML schema and a mechanism (the `Update-FormatData` cmdlet) where anyone can register views for an object type.</span></span> <span data-ttu-id="eec14-114">Du kan ange **breda** , **lista** , **tabell** eller **anpassade** vyer för valfri objekt typ.</span><span class="sxs-lookup"><span data-stu-id="eec14-114">You can specify **wide** , **list** , **table** , or **custom** views for any object type.</span></span> <span data-ttu-id="eec14-115">Vyerna anger vilka egenskaper som ska visas och hur de ska visas.</span><span class="sxs-lookup"><span data-stu-id="eec14-115">The views specify which properties to display and how they should be displayed.</span></span> <span data-ttu-id="eec14-116">Om en vy är registrerad definierar den vilken formatering som ska användas.</span><span class="sxs-lookup"><span data-stu-id="eec14-116">If a view is registered, it defines which formatter to use.</span></span> <span data-ttu-id="eec14-117">Så om den registrerade vyn är en **tabellvy** , `Out-Default` strömmas objekten till `Format-Table | Out-Host` .</span><span class="sxs-lookup"><span data-stu-id="eec14-117">So if the registered view is a **table** view, `Out-Default` streams the objects to `Format-Table | Out-Host`.</span></span> <span data-ttu-id="eec14-118">`Format-Table` transformerar objekten till en strömmande av formaterings poster (som styrs av data i vydefinitionen) och `Out-Host` transformerar de formaterade posterna till anrop i värd gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="eec14-118">`Format-Table` transforms the objects into a stream of Formatting records (driven by the data in the view definition) and `Out-Host` transforms the formatting records into calls on the Host interface.</span></span>

## <span data-ttu-id="eec14-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="eec14-119">EXAMPLES</span></span>

### <span data-ttu-id="eec14-120">Exempel 1</span><span class="sxs-lookup"><span data-stu-id="eec14-120">Example 1</span></span>

<span data-ttu-id="eec14-121">Även om denna cmdlet inte är avsedd att köras direkt av slutanvändaren kan det vara.</span><span class="sxs-lookup"><span data-stu-id="eec14-121">While this cmdlet is not intended to be run directly by the end user, it can be.</span></span>

```powershell
Get-Process | Select-Object -First 5 | Out-Default
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     12     2.56       5.20       0.00    7376   0 aesm_service
     48    34.32      18.10      26.64    9320  13 AlertusDesktopAlert
     24    13.97      12.74       0.77   12656  13 ApplicationFrameHost
      8     1.79       4.41       0.00    8180   0 AppVShNotify
      9     1.99       5.07       0.19   19320  13 AppVShNotify
```

## <span data-ttu-id="eec14-122">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="eec14-122">PARAMETERS</span></span>

### <span data-ttu-id="eec14-123">– InputObject</span><span class="sxs-lookup"><span data-stu-id="eec14-123">-InputObject</span></span>

<span data-ttu-id="eec14-124">Accepterar ininformation till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="eec14-124">Accepts input to the cmdlet.</span></span>

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

### <span data-ttu-id="eec14-125">-Avskrift</span><span class="sxs-lookup"><span data-stu-id="eec14-125">-Transcript</span></span>

<span data-ttu-id="eec14-126">Anger om utdata ska skickas till PowerShell: s avskrifts tjänster.</span><span class="sxs-lookup"><span data-stu-id="eec14-126">Determines whether the output should be sent to PowerShell's transcription services.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eec14-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="eec14-127">CommonParameters</span></span>

<span data-ttu-id="eec14-128">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="eec14-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="eec14-129">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="eec14-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="eec14-130">INDATA</span><span class="sxs-lookup"><span data-stu-id="eec14-130">INPUTS</span></span>

## <span data-ttu-id="eec14-131">UTDATA</span><span class="sxs-lookup"><span data-stu-id="eec14-131">OUTPUTS</span></span>

## <span data-ttu-id="eec14-132">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="eec14-132">NOTES</span></span>

## <span data-ttu-id="eec14-133">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="eec14-133">RELATED LINKS</span></span>

[<span data-ttu-id="eec14-134">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="eec14-134">Format-Custom</span></span>](../Microsoft.PowerShell.Utility/Format-Custom.md)

[<span data-ttu-id="eec14-135">Format-List</span><span class="sxs-lookup"><span data-stu-id="eec14-135">Format-List</span></span>](../Microsoft.PowerShell.Utility/Format-List.md)

[<span data-ttu-id="eec14-136">Format-Table</span><span class="sxs-lookup"><span data-stu-id="eec14-136">Format-Table</span></span>](../Microsoft.PowerShell.Utility/Format-Table.md)

[<span data-ttu-id="eec14-137">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="eec14-137">Format-Wide</span></span>](../Microsoft.PowerShell.Utility/Format-Wide.md)

[<span data-ttu-id="eec14-138">about_Format.ps1XML</span><span class="sxs-lookup"><span data-stu-id="eec14-138">about_Format.ps1xml</span></span>](About/about_Format.ps1xml.md)

[<span data-ttu-id="eec14-139">Hur PowerShell-formatering och utmatning fungerar</span><span class="sxs-lookup"><span data-stu-id="eec14-139">How PowerShell Formatting and Outputting REALLY works</span></span>](https://devblogs.microsoft.com/powershell/how-powershell-formatting-and-outputting-really-works/)
