---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: galleriet, powershell, cmdlet, psgallery
title: psgallery_search_syntax
ms.openlocfilehash: 409ae607557af760f9cec4e3c54f39e51b5fac18
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="gallery-search-syntax"></a>Galleriet Söksyntax

PowerShell-galleriet erbjuder en text searchbox där du kan använda ord och fraser nyckelordet uttryck för att begränsa sökresultatet.

## <a name="search-by-keywords"></a>Sök efter nyckelord

    dsc azure sql

Sök gör sitt bästa för att hitta relevanta dokument som innehåller alla 3 nyckelord och returnera matchande dokument.

## <a name="search-using-phrases-and-keywords"></a>Sökningen med fraser och nyckelord

    "azure sql" deployment

Ange en fras inom citattecken (””) Ändra söker efter en viss fras i stället för separata nyckelord.
Matchande dokument ska vanligtvis innehålla frasen ”azure sql”, inklusive på versaler t.ex. ”Azure SQL”, och även vanligtvis innehåller ordet ”distribution”.

## <a name="filtering-on-fields"></a>Filtrering på fält

Du kan söka efter ett specifikt objekt-ID (eller ”Id” eller ”id”) eller vissa fält med Sök villkor med fältnamnet.

Sökbara fält är för närvarande ”Id”, ”Version”, ”-taggar', 'Författare',” ägare ”,” funktioner', 'Cmdlets', 'DscResources' och 'PowerShellVersion'.

[Vad är skillnaden mellan ID och titel? ID: T är det namn som du använder i konsolen. Rubriken är vad som visas överst på sidan objektet i sökresultaten.]

## <a name="examples"></a>Exempel

    ID:"PSReadline"
    id:"AzureRM.Profile"

Sök efter objekt med ”PSReadline” eller ”AzureRM.Profile” i ID-fältet respektive.

    Id:"AzureRM.Profile"

är ett annat sätt att hitta objekt med ”AzureRM.Profile” i ID-fältet.

”Id”-filtret är en understräng matchar, så om du söker efter följande:

    Id:"azure"
    
Du får resultat som 'AzureRM.Profile' och 'Azure.Storage'.

Du kan också söka efter flera nyckelord i ett enda fält. Eller blanda och matcha fält.

    id:azure tags:intellisense
    id:azure id:storage

Och du kan utföra sökningar fras:

    id:"azure.storage"


För att söka alla objekt med DSC-tagg.

    Tags:"DSC"

För att söka alla objekt med angiven funktion.

    Functions:"Update-AzureRM"

För att söka alla objekt med den angivna cmdleten.
    
    Cmdlets:"Get-AzureRmEnvironment"

För att söka alla objekt med det angivna namnet för DSC-resurs.

    DscResources:"xArchive"

Att söka efter alla objekt med den angivna PowerShellVersion

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


Slutligen, om du använder ett fält inte stöds, till exempel kommandon, vi bara ignorera det och söka i alla fält. Därför följande fråga

    commands:blobs storage
    
Är tolkas exakt samma sätt som den här frågan:

    blobs storage

