---
title: Hur du lägger till Cmdlet-namn och sammanfattning för en Cmdlet-hjälpavsnittet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850892"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a>Lägga till cmdlet-namnet och sammanfattningen i ett cmdlet-hjälpavsnitt

Det här avsnittet beskrivs hur du lägger till innehåll som visas i avsnitten namn och en sammanfattning av cmdlet-hjälpen. Det här innehållet har lagts till noden kommando för varje cmdlet i hjälpfilen.

> [!NOTE]
> För en fullständig överblick över en hjälpfilen, öppna en av dll-Help.xml-filerna finns i installationskatalogen för Windows PowerShell. Till exempel innehåller filen Microsoft.PowerShell.Commands.Management.dll Help.xml innehåll för flera av Windows PowerShell-cmdlets.

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a>Du lägger till Cmdlet-namn och en sammanfattning

- Cmdlet: en hjälp kan visa två beskrivningar för cmdleten. Första beskrivningen är en kort beskrivning som kallas sammanfattning. Andra beskrivningen är en mer detaljerad beskrivning som diskuteras i [att lägga till den detaljerade beskrivningen för en Cmdlet-hjälpavsnittet](./how-to-add-a-cmdlet-description.md). Båda dessa beskrivningar ska skrivas som en enda punkt.

- I sammanfattning Upprepa inte cmdlet-namn. Informera användaren att cmdleten Get-Server hämtar en server är kort, men inte informativt. I stället använda synonymer och Lägg till information i beskrivningen.

  Exempel: ”Hämtar ett objekt som representerar en lokal eller fjärransluten dator”.

- Använd enkla verb som ”hämta”, ”skapa” och ”ändra” i sammanfattning. Undvik att använda ”Ange” eftersom det är vaga och avancerad ord som ”ändra”.

  Exempel: ”Hämtar information om Authenticode-signaturen i en fil”.

- Skriv i aktiva rösten. Till exempel ”använda objektet TimeSpan...” är mycket tydligare än ”TimeSpan-objektet kan användas till att...”

- Undvik att verb ”visa” att beskriva cmdletar som hämta objekt. Även om Windows PowerShell visar cmdlet data, är det viktigt att introducera användare till konceptet som cmdleten returnerar .NET Framework-objekt vars data inte visas. Om du betona visningen kanske användaren inte tänka på att cmdlet: en kan ha returnerat många andra användbara egenskaper och metoder som inte visas.

## <a name="see-also"></a>Se även

 [Windows PowerShell SDK](../windows-powershell-reference.md)