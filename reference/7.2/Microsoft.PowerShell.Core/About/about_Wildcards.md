---
description: Beskriver hur du använder jokertecken i PowerShell.
Locale: en-US
ms.date: 02/13/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wildcards?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Wildcards
ms.openlocfilehash: 40620e54bb889d683192b346f3ba1c139895e4d0
ms.sourcegitcommit: 9777152e026c47ba8d319593051416054cb62246
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/16/2021
ms.locfileid: "100529982"
---
# <a name="about-wildcards"></a>Om jokertecken

## <a name="short-description"></a>KORT BESKRIVNING

Beskriver hur du använder jokertecken i PowerShell.

## <a name="long-description"></a>LÅNG BESKRIVNING

Jokertecken representerar ett eller flera tecken. Du kan använda dem för att skapa ord mönster i kommandon. Jokertecken används med `-like` operatorn eller med en parameter som accepterar jokertecken.

Om du till exempel vill matcha alla filer i `C:\Techdocs` katalogen med ett `.ppt` fil namns tillägg skriver du:

```powershell
Get-ChildItem C:\Techdocs\*.ppt
```

I det här fallet representerar asterisken ( `*` ) jokertecknet alla tecken som visas före `.ppt` fil namns tillägget.

Jokertecken är enklare än vanliga uttryck. Mer information finns i [about_Regular_Expressions](./about_Regular_Expressions.md).

PowerShell har stöd för följande jokertecken:

|Användning|Beskrivning               |Exempel |Matchning        |Ingen matchning|
|--------|--------------------------|--------|-------------|--------|
|\*      |Matcha inga eller flera tecken | en\*  | aA, AG, Apple | banan |
|?       |Matcha ett Character i den positionen | ? n | en, i, på | kördes |
|\[ \]   |Matcha ett tecken intervall | \[a-l- \] ook | bok, Cook, utseende | skrev |
|\[ \]   |Matcha vissa tecken | \[BC- \] ook | bok, Cook | uttryckt |

Du kan inkludera flera jokertecken i samma ord mönster. Om du till exempel vill söka efter textfiler med namn som börjar med bokstäverna **a** till **l**, skriver du:

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

