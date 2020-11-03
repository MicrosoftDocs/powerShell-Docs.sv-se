---
description: Beskriver hur kopplings operatorn (-JOIN) kombinerar flera strängar till en enda sträng.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_join?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Join
ms.openlocfilehash: 3e5bf4363adbded29dc58facde00f6597abeb697
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271574"
---
# <a name="about-join"></a>Om koppling

## <a name="short-description"></a>KORT BESKRIVNING

Beskriver hur kopplings operatorn (-JOIN) kombinerar flera strängar till en enda sträng.

## <a name="long-description"></a>LÅNG BESKRIVNING

Operatorn Join sammanfogar en uppsättning strängar till en enda sträng. Strängarna läggs till i den resulterande strängen i den ordning som de visas i kommandot.

### <a name="syntax"></a>Syntax

Följande diagram visar syntaxen för operatorn Join.

```powershell
-Join <String[]>
<String[]> -Join <Delimiter>
```

#### <a name="parameters"></a>Parametrar

String []-anger en eller flera strängar som ska anslutas.

Avgränsare – anger ett eller flera tecken som placeras mellan de sammanfogade strängarna. Standardvärdet är ingen avgränsare ("").

Kommentarer

Den unära kopplings operatorn (-JOIN <string [] >) har högre prioritet än ett kommatecken. Om du skickar en kommaavgränsad lista med strängar till den unära kopplings operatorn skickas bara den första strängen (före det första kommatecknet) till kopplings operatorn.

Om du vill använda operatorn enställig koppling, omger du strängarna inom parentes eller lagrar strängarna i en variabel och skickar sedan variabeln till koppling.

Ett exempel:

```powershell
-join "a", "b", "c"
a
b
c

-join ("a", "b", "c")
abc

$z = "a", "b", "c"
-join $z
abc
```

### <a name="examples"></a>Exempel

Följande instruktion ansluter tre strängar:

```powershell
-join ("Windows", "PowerShell", "2.0")
WindowsPowerShell2.0
```

Följande instruktion ansluter tre strängar avgränsade med blank steg:

```powershell
"Windows", "PowerShell", "2.0" -join " "
Windows PowerShell 2.0
```

Följande instruktioner använder en avgränsare med flera tecken för att ansluta till tre strängar:

```powershell
$a = "WIND", "S P", "ERSHELL"
$a -join "OW"
WINDOWS POWERSHELL
```

Följande instruktion kopplar ihop raderna i en här-sträng till en enda sträng. Eftersom en här-sträng är en sträng måste raderna i den här-strängen delas innan de kan anslutas. Du kan använda den här metoden för att återansluta till strängarna i en XML-fil som har sparats i en här-sträng:

```powershell
$a = @'
a
b
c
'@

(-split $a) -join " "
a b c
```

## <a name="see-also"></a>SE ÄVEN

[about_Operators](about_Operators.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Split](about_Split.md)
