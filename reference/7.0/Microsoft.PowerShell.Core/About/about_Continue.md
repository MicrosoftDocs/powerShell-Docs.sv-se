---
description: Beskriver hur `continue` instruktionen omedelbart returnerar program flödet överst i en program slinga, en `switch` instruktion eller en `trap` instruktion.
keywords: powershell,cmdlet
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_continue?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Continue
ms.openlocfilehash: 96758fb110ec1496ebbc073cdacfd3dcc15ae486
ms.sourcegitcommit: 0c31814bed14ff715dc7d4aace07cbdc6df2438e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/17/2020
ms.locfileid: "97614089"
---
# <a name="about-continue"></a>Om Fortsätt

## <a name="short-description"></a>Kort beskrivning

Beskriver hur `continue` instruktionen omedelbart returnerar program flödet överst i en program slinga, en `switch` instruktion eller en `trap` instruktion.

## <a name="long-description"></a>Lång beskrivning

`continue`Instruktionen gör det möjligt att avsluta det aktuella kontroll blocket, men fortsätta att köra, i stället för att avsluta helt. Instruktionen stöder etiketter.
En etikett är ett namn som du tilldelar till en instruktion i ett skript.

## <a name="using-continue-in-loops"></a>Använda Fortsätt i slingor

En omärkt `continue` instruktion returnerar omedelbart program flödet överst i den innersta slingan som styrs av en `for` , `foreach` -, `do` -eller- `while` instruktion. Den aktuella iterationen av loopen avslutas och loopen fortsätter med nästa iteration.

I följande exempel returnerar program Flow överst i `while` slingan om `$ctr` variabeln är lika med 5. Därför visas alla tal mellan 1 och 10 förutom 5:

```powershell
while ($ctr -lt 10)
{
    $ctr += 1
    if ($ctr -eq 5)
    {
        continue
    }

    Write-Host -Object $ctr
}
```

När du använder en `for` loop fortsätter körningen vid `<Repeat>` instruktionen, följt av `<Condition>` testet. I exemplet nedan inträffar inte en oändlig slinga eftersom minskningen av `$i` inträffar efter `continue` nyckelordet.

```powershell
#   <Init>  <Condition> <Repeat>
for ($i = 0; $i -lt 10; $i++)
{
    Write-Host -Object $i
    if ($i -eq 5)
    {
        continue
        # Will not result in an infinite loop.
        $i--
    }
}
```

### <a name="using-a-labeled-continue-in-a-loop"></a>Använda en etikett med etiketten Fortsätt i en slinga

En märkt `continue` instruktion avslutar körningen av upprepnings-och överförings kontrollen till den riktade omslutande upprepnings-eller `switch` instruktions etiketten.

I följande exempel `for` avslutas innersta när `$condition` är **Sant** och upprepningen fortsätter med den andra `for` slingan på `labelB` .

```powershell
:labelA for ($i = 1; $i -le 10; $i++) {
    :labelB for ($j = 1; $j -le 10; $j++) {
        :labelC for ($k = 1; $k -le 10; $k++) {
            if ($condition) {
                continue labelB
            } else {
                $condition = Update-Condition
            }
        }
    }
}
```

## <a name="using-continue-in-a-switch-statement"></a>Använda Continue i en switch-instruktion

En omärkt `continue` instruktion inom en `switch` avslutar körning av den aktuella `switch` upprepnings-och överförings kontrollen överst i `switch` för att hämta nästa inobjekt.

Om det finns ett enskilt inobjekt `continue` avslutar hela `switch` instruktionen.
När `switch` indatatypen är en samling `switch` testar varje element i samlingen. Den `continue` aktuella iterationen avslutas och `switch` fortsätter med nästa element.

```powershell
switch (1,2,3) {
  2 { continue }  # moves on to the next element, 3
  default { $_ }
}
```

```Output
1
3
```

## <a name="using-continue-in-a-trap-statement"></a>Använda Continue i en trap-instruktion

Om den slutliga instruktionen som körs i brödtext a `trap` -instruktionen är `continue` , ignoreras det fångade felet tyst och körningen fortsätter med instruktionen direkt efter den som orsakade problemet `trap` .

## <a name="do-not-use-continue-outside-of-a-loop-switch-or-trap"></a>Använd inte Fortsätt utanför en loop, växel eller trap

När `continue` används utanför en konstruktion som stöder den direkt (loopar, `switch` , `trap` ), letar PowerShell _upp anrops stacken_ för en omsluten konstruktion. Om det inte går att hitta en omsluten konstruktion avslutas den aktuella körnings utrymme tyst.

Det innebär att funktioner och skript som oavsiktligt använder en `continue` utanför en omsluten konstruktion som stöder den, oavsiktligt kan avsluta sina _anropare_.

Om du använder `continue` inuti en pipeline, t. ex. ett `ForEach-Object` skript block, avslutar inte bara pipelinen, utan kan avsluta hela körnings utrymme.

## <a name="see-also"></a>Se även

[about_Break](about_Break.md)

[about_For](about_For.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Throw](about_Throw.md)

[about_Trap](about_Trap.md)

[about_Try_Catch_Finally](about_Try_Catch_Finally.md)
