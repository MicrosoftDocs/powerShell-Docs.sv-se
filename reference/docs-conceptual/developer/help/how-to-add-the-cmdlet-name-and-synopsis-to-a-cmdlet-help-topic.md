---
ms.date: 09/13/2016
ms.topic: reference
title: Lägga till cmdlet-namnet och sammanfattningen i ett cmdlet-hjälpavsnitt
description: Lägga till cmdlet-namnet och sammanfattningen i ett cmdlet-hjälpavsnitt
ms.openlocfilehash: aeeb0cdd1d6d17b88067928ff952dc57a9441917
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659063"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a>Lägga till cmdlet-namnet och sammanfattningen i ett cmdlet-hjälpavsnitt

I det här avsnittet beskrivs hur du lägger till innehåll som visas i avsnitten **namn** och **Sammanfattning** i cmdlet-hjälpen. I Hjälp filen läggs det här innehållet till i kommando-noden för varje cmdlet.

> [!NOTE]
> Om du vill se en fullständig vy över en hjälpfil öppnar du en av `dll-Help.xml` filerna som finns i installations katalogen för PowerShell. Filen innehåller till exempel `Microsoft.PowerShell.Commands.Management.dll-Help.xml` innehåll för flera av PowerShell-cmdletarna.

## <a name="to-add-the-cmdlet-name-and-a-synopsis"></a>Lägga till cmdlet-namn och en sammanfattning

- Cmdlet-hjälpen kan visa två beskrivningar för cmdleten. Den första beskrivningen är en kort beskrivning som kallas för sammanfattning. Den andra beskrivningen är en mer detaljerad beskrivning som beskrivs i [avsnittet lägga till detaljerad beskrivning i en cmdlet-hjälpfil](./how-to-add-a-cmdlet-description.md).
  Båda dessa beskrivningar ska vara skrivna som ett enda stycke.

- I sammanfattningen upprepar du inte cmdlet-namnet. Informerar användaren om att `Get-Server` cmdleten hämtar en server, men inte informativ. Använd i stället synonymer och Lägg till information i beskrivningen.

  Exempel: "hämtar ett objekt som representerar en lokal dator eller fjärrdator."

- Använd enkla verb som "Get", "Create" och "Change" i sammanfattningen. Undvik att använda "Set" eftersom det är vagt och snygga ord som "ändra".

  Exempel: "hämtar information om Authenticode-signaturen i en fil."

- Skriv i aktiv röst. Exempel: "Använd TimeSpan-objektet..." är mycket tydligare än "TimeSpan-objektet kan användas för..."

- Undvik verbet "Visa" när du beskriver cmdletar som hämtar objekt. Även om Windows PowerShell visar cmdlet-data är det viktigt att introducera användare till det begrepp som cmdleten returnerar .NET Framework objekt vars data inte kan visas. Om du betonar visningen kanske inte användaren inser att cmdleten kan ha returnerat många andra användbara egenskaper och metoder som inte visas.

## <a name="see-also"></a>Se även

[Windows PowerShell SDK](../windows-powershell-reference.md)
