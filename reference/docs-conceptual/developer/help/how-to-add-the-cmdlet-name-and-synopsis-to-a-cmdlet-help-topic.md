---
title: Så här lägger du till cmdlet-namnet och sammanfattningen i ett hjälp avsnitt för cmdleten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: 5b4c04a14c3d86c7a3b94b768e8fb59116d8c6f5
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560635"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a>Lägga till cmdlet-namnet och sammanfattningen i ett cmdlet-hjälpavsnitt

I det här avsnittet beskrivs hur du lägger till innehåll som visas i avsnitten namn och sammanfattning i cmdlet-hjälpen. I Hjälp filen läggs det här innehållet till i kommando-noden för varje cmdlet.

> [!NOTE]
> Om du vill se en fullständig vy över en hjälpfil öppnar du en av dll-Help. XML-filerna som finns i installations katalogen för Windows PowerShell. Till exempel innehåller filen Microsoft. PowerShell. commands. Management. dll-Help. XML innehåll för flera av Windows PowerShell-cmdlets.

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a>Lägga till cmdlet-namn och en sammanfattning

- Cmdlet-hjälpen kan visa två beskrivningar för cmdleten. Den första beskrivningen är en kort beskrivning som kallas för sammanfattning. Den andra beskrivningen är en mer detaljerad beskrivning som beskrivs i [avsnittet lägga till detaljerad beskrivning i en cmdlet-hjälpfil](./how-to-add-a-cmdlet-description.md). Båda dessa beskrivningar ska vara skrivna som ett enda stycke.

- I sammanfattningen upprepar du inte cmdlet-namnet. Informerar användaren om att cmdleten Get-server hämtar en server, men inte informativ. Använd i stället synonymer och Lägg till information i beskrivningen.

  Exempel: "hämtar ett objekt som representerar en lokal dator eller fjärrdator."

- Använd enkla verb som "Get", "Create" och "Change" i sammanfattningen. Undvik att använda "Set" eftersom det är vagt och snygga ord som "ändra".

  Exempel: "hämtar information om Authenticode-signaturen i en fil."

- Skriv i aktiv röst. Exempel: "Använd TimeSpan-objektet..." är mycket tydligare än "TimeSpan-objektet kan användas för..."

- Undvik verbet "Visa" när du beskriver cmdletar som hämtar objekt. Även om Windows PowerShell visar cmdlet-data är det viktigt att introducera användare till det begrepp som cmdleten returnerar .NET Framework objekt vars data inte kan visas. Om du betonar visningen kanske inte användaren inser att cmdleten kan ha returnerat många andra användbara egenskaper och metoder som inte visas.

## <a name="see-also"></a>Se även

 [Windows PowerShell SDK](../windows-powershell-reference.md)
