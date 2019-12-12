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
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353258"
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