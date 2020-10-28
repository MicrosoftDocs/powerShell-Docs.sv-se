---
ms.date: 06/12/2017
title: Syntax för Galleri sökning
description: I den här artikeln beskrivs användar gränssnittet som används för att söka efter innehåll i PowerShell-galleriet.
ms.openlocfilehash: 7ad486095647f99056b37c2ca1a50db099a166c0
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661371"
---
# <a name="gallery-search-syntax"></a>Syntax för Galleri sökning

Du kan söka i PowerShell-galleriet med hjälp av [PowerShell-galleriets webbplats](https://www.powershellgallery.com/). PowerShell-galleriet webbplats innehåller en text Sök ruta där du kan använda uttryck för ord, fraser och nyckelord för att begränsa Sök resultaten.

## <a name="search-by-keywords"></a>Sök med nyckelord

```Syntax
dsc azure sql
```

Sök försöker hitta relevanta dokument som innehåller alla tre nyckelord och returnera matchande dokument.

## <a name="search-using-phrases-and-keywords"></a>Sök med fraser och nyckelord

```Syntax
"azure sql" deployment
```

Ange en fras mellan citat tecken ("") ändra sökningen så att den söker efter den specifika frasen i stället för separata nyckelord. Matchning av dokument bör vanligt vis innehålla den exakta frasen "Azure SQL", inklusive variationer i versaler, t. ex. "Azure SQL" och innehåller vanligt vis ordet "Deployment".

## <a name="filtering-on-fields"></a>Filtrera på fält

Du kan söka efter ett visst paket-ID (eller "ID" eller "ID") eller vissa andra fält genom att förkorrigera Sök termer med fält namnet.

För närvarande är de sökbara fälten "ID", "version", "Tags", "author", "Owner", "Functions", "cmdlets", "DscResources" och "PowerShellVersion".

- ID är det namn som du använder i-konsolen.
- Rubriken är vad som visas överst på sidan paket i Sök resultaten.

## <a name="examples"></a>Exempel

```Syntax
ID:PSReadline
```

söker efter paket med ett ID som innehåller "PSReadline".

```Syntax
Id:"AzureRM.Profile"
```

är ett annat sätt att hitta paket med "AzureRM. profile" i sitt ID-fält.

Filtret "ID" är en del Strängs matchning, så om du söker efter följande:

```Syntax
Id:"azure"
```

Detta ger resultat som inkluderar AzureRM. Profile och Azure. Storage.

Du kan också söka efter flera nyckelord i ett enda fält.

```Syntax
id:azure tags:intellisense
```

Och du kan utföra fras sökningar med dubbla citat tecken:

```Syntax
id:"azure.storage"
```

Om du vill söka i alla paket med DSC-tagg.

```Syntax
Tags:DSC
```

Om du vill söka igenom alla paket med den angivna funktionen.

```Syntax
Functions:Get-TreeSize
```

Om du vill söka igenom alla paket med angiven cmdlet.

```Syntax
Cmdlets:Get-AzureRmEnvironment
```

Om du vill söka igenom alla paket med det angivna DSC-resursnamnet.

```Syntax
DscResources:xArchive
```

Söka igenom alla paket med den angivna PowerShellVersion

```Syntax
PowerShellVersion:2.0
```

Slutligen, om du använder ett fält som vi inte stöder, till exempel "kommandon", så ignorerar vi bara det och söker i alla fält. Så följande fråga

```Syntax
commands:blobs storage
```

Tolkas exakt på samma sätt som den här frågan:

```Syntax
blobs storage
```
