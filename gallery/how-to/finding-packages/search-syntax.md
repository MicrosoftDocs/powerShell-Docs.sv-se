---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Gallerisökning
ms.openlocfilehash: 9aadb6771c85845cc3fa05cb56f0194b060d1c1b
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004147"
---
# <a name="gallery-search-syntax"></a>Gallerisökning

PowerShell-galleriet erbjuder en text searchbox där du kan använda ord och fraser nyckelordet uttryck för att begränsa sökresultaten.

## <a name="search-by-keywords"></a>Sök efter nyckelord

    dsc azure sql

Sök gör sitt bästa för att hitta relevant dokument som innehåller alla 3 nyckelord och returnera matchande dokument.

## <a name="search-using-phrases-and-keywords"></a>Söka med fraser och nyckelord

    "azure sql" deployment

Att ange en fras mellan citattecken (””) Ändra söker efter en viss fras i stället för separata nyckelord.
Matchande dokument ska vanligtvis innehålla exakt fras ”azure sql”, inklusive varianter på förtroendeingivande t.ex. ”Azure SQL”, och även vanligtvis innehåller ordet ”distribution”.

## <a name="filtering-on-fields"></a>Filtrering på fält

Du kan söka efter en viss paket-ID (eller ”Id” eller ”id”) eller vissa andra fält genom Sök villkor med fältnamnet.

De sökbara fälten är för närvarande ”Id”, ”Version”, ”-taggar”, ”författare”, 'Owner', 'Funktioner', 'Cmdletar', 'DscResources' och 'PowerShellVersion'.

[Vad är skillnaden mellan ID och rubrik? ID: T är det namn som du använder i konsolen. Rubriken är vad som ska visas överst på sidan package i sökresultaten.]

## <a name="examples"></a>Exempel

    ID:"PSReadline"
    id:"AzureRM.Profile"

söker efter paket med ”PSReadline” eller ”AzureRM.Profile” i ID-fältet respektive.

    Id:"AzureRM.Profile"

är ett annat sätt att hitta paket med ”AzureRM.Profile” i ID-fältet.

”Id”-filtret är en understräng matchar, så om du söker efter följande:

    Id:"azure"

Du får resultat som 'AzureRM.Profile' och 'Azure.Storage'.

Du kan också söka efter flera nyckelord i ett enda fält. Eller blanda och matcha fält.

    id:azure tags:intellisense
    id:azure id:storage

Och du kan utföra frasen sökningar:

    id:"azure.storage"


Att söka efter alla paket med DSC-tagg.

    Tags:"DSC"

Att söka efter alla paket med den angivna funktionen.

    Functions:"Update-AzureRM"

Att söka efter alla paket med angivna cmdlet.

    Cmdlets:"Get-AzureRmEnvironment"

Att söka efter alla paket med det angivna namnet för DSC-resurs.

    DscResources:"xArchive"

Att söka efter alla paket med den angivna PowerShellVersion

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


Slutligen, om du använder ett fält som inte stöds, till exempel kommandon, vi bara ignorera det och söka i alla fält. Så följande fråga

    commands:blobs storage

Är tolkas exakt samma som den här frågan:

    blobs storage
