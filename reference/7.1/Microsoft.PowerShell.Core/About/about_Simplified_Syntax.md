---
description: Beskriver enklare, mer naturligt språk sätt för skript filter för objekt samlingar.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_simplified_syntax?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Simplified_Syntax
ms.openlocfilehash: 0a5d0059c6fd318fc9ddf2f49489fc2ae8aee291
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271809"
---
# <a name="about_simplified_syntax"></a>about_Simplified_Syntax

## <a name="short-description"></a>KORT BESKRIVNING
Beskriver enklare, mer naturligt språk sätt för skript filter för objekt samlingar.

## <a name="long-description"></a>LÅNG BESKRIVNING

Förenklad syntax, som introducerades i Windows PowerShell 3,0, gör att du kan bygga vissa filter kommandon utan att använda skript block. Den förenklade syntaxen påminner mer om naturligt språk och är i första hand användbart med samlingar av objekt som får skickas i kommandon `Where-Object` och `ForEach-Object` deras motsvarande alias `where` och `foreach` .

Du kan använda en metod för medlemmarna i en samling (oftast en matris) utan att referera till den automatiska variabeln `$_` i ett-skript block.

Tänk på följande två anrop:

### <a name="standard-syntax"></a>Standardsyntax

```powershell
dir Cert:\LocalMachine\Root | where { $_.FriendlyName -eq 'Verisign' }
dir Cert:\ -Recurse | foreach { $_.GetKeyAlgorithm() }
```

### <a name="simplified-syntax"></a>Förenklad syntax

Under den förenklade syntaxen behandlas jämförelse operatorer som fungerar på medlemmar av objekt i en samling som parametrar. Du kan anropa en metod för objekt i en samling utan att referera till den automatiska variabeln i `$_` ett-skript block.
Jämför följande två anrop till dem i föregående exempel:

```powershell
dir Cert:\LocalMachine\Root | where FriendlyName -eq 'Verisign'
dir Cert:\ -Recurse | foreach GetKeyAlgorithm
```

När båda syntaxerna fungerar returnerar den förenklade syntaxen resultat utan att referera till den automatiska variabeln `$_` i ett-skript block.
Metod namnet `GetKeyAlgorithm` behandlas som en parameter för `ForEach-Object` .
Det andra kommandot returnerar samma resultat, men utan fel, eftersom den förenklade syntaxen inte försöker returnera resultat för objekt för vilka det angivna argumentet inte tillämpades.

I det här exemplet `Process` skickas egenskapen `Description` som medlems namn parameter till `ForEach-Object` kommandot. Resultaten är beskrivningar av aktiva processer.

```powershell
Get-Process | foreach Description
```

I det här exemplet `DirectoryInfo` skickas metoden `GetFiles` som kommandots medlems namn parameter `ForEach-Object` .  
Metoden anropas med Sök mönster parametern `.*` .  
Resultaten är `FileInfo` poster för alla dolda filer i UNIX-format i användar arbets kataloger. 

```powershell
Get-ChildItem /home -Directory | foreach GetFiles .*
```

## <a name="see-also"></a>SE ÄVEN

- [about_Comparison_Operators](about_Comparison_Operators.md)
- [about_Foreach](about_Foreach.md)
- [Where-objekt](xref:Microsoft.PowerShell.Core.Where-Object)
- [-Objekt](xref:Microsoft.PowerShell.Core.ForEach-Object)

