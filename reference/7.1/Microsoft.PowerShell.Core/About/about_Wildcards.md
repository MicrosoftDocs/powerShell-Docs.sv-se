---
description: Beskriver hur du använder jokertecken i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 3/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wildcards?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Wildcards
ms.openlocfilehash: 4778de5022f35f354e7783cedc5019198d11604b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272493"
---
# <a name="about-wildcards"></a>Om jokertecken

## <a name="short-description"></a>KORT BESKRIVNING

Beskriver hur du använder jokertecken i PowerShell.

## <a name="long-description"></a>LÅNG BESKRIVNING

Jokertecken representerar ett eller flera tecken. Du kan använda dem för att skapa ord mönster i kommandon. Om du till exempel vill hämta alla filer i `C:\Techdocs` katalogen med ett `.ppt` fil namns tillägg skriver du:

```powershell
Get-ChildItem C:\Techdocs\*.ppt
```

I det här fallet representerar asterisken ( `*` ) jokertecknet alla tecken som visas före `.ppt` fil namns tillägget.

PowerShell har stöd för följande jokertecken:

|Användning|Beskrivning               |Exempel |Matchning        |Ingen matchning|
|--------|--------------------------|--------|-------------|--------|
|\*      |Matcha inga eller flera tecken | en\*  | aA, AG, Apple | banan |
|?       |Matcha ett Character i den positionen | ? n | en, i, på | kördes |
|\[ \]   |Matcha ett tecken intervall | \[a-l- \] ook | bok, Cook, utseende | skrev |
|\[ \]   |Matcha vissa tecken | \[BC- \] ook | bok, Cook | uttryckt |

Du kan inkludera flera jokertecken i samma ord mönster. Om du till exempel vill söka efter textfiler med namn som börjar med bokstäverna **a** till **l** , skriver du:

```powershell
Get-ChildItem C:\Techdocs\[a-l]*.txt
```

Många cmdlets accepterar jokertecken i parameter värden. I hjälp avsnittet för varje cmdlet beskrivs vilka parametrar som accepterar jokertecken. För parametrar som accepterar jokertecken är deras användning Skift läges okänslig.

Du kan använda jokertecken i kommandon och skript block, till exempel för att skapa ett ord mönster som representerar egenskaps värden. Följande kommando hämtar till exempel tjänster där egenskap svärdet **ServiceType** inkluderar **Interactive**.

```powershell
Get-Service | Where-Object {$_.ServiceType -Like "*Interactive*"}
```

I följande exempel `If` innehåller instruktionen ett villkor som använder jokertecken för att hitta egenskaps värden. Om återställnings punktens **Beskrivning** innehåller **PowerShell** lägger kommandot till värdet för återställnings punktens **CreationTime** -egenskap till en loggfil.

```powershell
$p = Get-ComputerRestorePoint
foreach ($point in $p) {
  if ($point.description -like "*PowerShell*") {
    Add-Content -Path C:\TechDocs\RestoreLog.txt "$($point.CreationTime)"
  }
}
```

## <a name="see-also"></a>SE ÄVEN

[about_Language_Keywords](about_Language_Keywords.md)

[about_If](about_If.md)

[about_Script_Blocks](about_Script_Blocks.md)

