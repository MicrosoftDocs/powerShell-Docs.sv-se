---
description: Innehåller viktig information om objekt i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/30/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_objects?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Objects
ms.openlocfilehash: b845dc8b55a19bb642c194398b0c9f5f13d24cb3
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272271"
---
# <a name="about-objects"></a>Om objekt

## <a name="short-description"></a>Kort beskrivning
Innehåller viktig information om objekt i PowerShell.

## <a name="long-description"></a>Lång beskrivning

Varje åtgärd som du utför i PowerShell sker inom kontexten för objekt. När data flyttas från ett kommando till nästa, flyttas det som ett eller flera identifierbara objekt. Ett objekt är en samling data som representerar ett objekt. Ett objekt består av tre typer av data: objekt typ, dess metoder och dess egenskaper.

## <a name="types-methods-and-properties"></a>Typer, metoder och egenskaper

Objekt typen visar vilken typ av objekt den är. Ett objekt som representerar en fil är till exempel ett FileInfo-objekt.

Objekt metoderna är åtgärder som du kan utföra på objektet.
FileInfo-objekt har till exempel en CopyTo-metod som du kan använda för att kopiera filen.

Objekt egenskaper lagrar information om objektet. FileInfo-objekt har till exempel en LastWriteTime-egenskap som lagrar datum och tid då filen senast öppnades.

När du arbetar med objekt kan du använda deras metoder och egenskaper i kommandon för att vidta åtgärder och hantera data.

## <a name="objects-in-pipelines"></a>Objekt i pipelines

När kommandon kombineras i en pipeline skickar de information till varandra som objekt. När det första kommandot körs skickar det ett eller flera objekt nedåt i pipelinen till det andra kommandot. Det andra kommandot tar emot objekten från det första kommandot, bearbetar objekten och skickar sedan nya eller ändrade objekt till nästa kommando i pipelinen.
Detta fortsätter tills alla kommandon i pipelinen har körts.

Följande exempel visar hur objekt skickas från ett kommando till nästa:

```powershell
Get-ChildItem C: | where { $_.PsIsContainer -eq $false } | Format-List
```

Det första kommandot `Get-ChildItem C:` returnerar ett fil-eller katalog objekt för varje objekt i rot katalogen i fil systemet. Filen och katalog-objekten har passerat pipelinen till det andra kommandot.

Det andra kommandot `where { $_.PsIsContainer -eq $false }` använder egenskapen PsIsContainer för alla fil system objekt för att välja filer, som har värdet FALSKT ( \$ falskt) i sin PsIsContainer-egenskap. Mappar, som är behållare och har därför värdet sant ( \$ sant) i sin PsIsContainer-egenskap, inte markerade.

Det andra kommandot skickar bara filobjekten till det tredje kommandot `Format-List` , som visar fil objekt i en lista.

## <a name="see-also"></a>Se även

[about_Methods](about_Methods.md)

[about_Object_Creation](about_Object_Creation.md)

[about_Properties](about_Properties.md)

[about_Pipelines](about_Pipelines.md)

[Hämta medlem](xref:Microsoft.PowerShell.Utility.Get-Member)
