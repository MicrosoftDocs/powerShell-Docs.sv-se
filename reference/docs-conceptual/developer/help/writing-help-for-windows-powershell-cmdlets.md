---
title: Skriva hjälp för PowerShell-cmdletar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: fd565e8bf8429d91d785664c8cc69d1843439219
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560601"
---
# <a name="writing-help-for-powershell-cmdlets"></a>Skriva hjälp för PowerShell-cmdletar

PowerShell-cmdletar kan vara användbara, men om inte hjälp avsnitten tydligt förklarar vad cmdleten gör och hur du använder den, kan cmdleten inte användas eller, till och med sämre, vara frustrerande användare.
Hjälp fil formatet för XML-baserad cmdlet förbättrar konsekvensen, men den fantastiska hjälpen kräver mycket mer.

Om du aldrig har skrivit cmdlet-hjälpen kan du läsa följande rikt linjer.
Det XML-schema som krävs för att redigera cmdlet-hjälp avsnittet beskrivs i följande avsnitt.
Börja med att [skapa cmdlet-hjälp filen](./how-to-create-the-cmdlet-help-file.md).
Avsnittet innehåller en beskrivning av XML-noder på översta nivån.

## <a name="writing-guidelines-for-cmdlet-help"></a>Skriv rikt linjer för cmdlet-hjälp

### <a name="write-well"></a>Skriva bra
Ingenting ersätter ett välskrivet ämne.
Om du inte är en professionell skrivare kan du söka efter en skrivare eller redigerare som hjälper dig.
Ett annat alternativ är att kopiera din hjälp text till Microsoft Word och använda grammatik-och stavnings kontrollerna för att förbättra ditt arbete.

### <a name="write-simply"></a>Skriv bara
Använd enkla ord och fraser.
Undvik jargong.
Tänk på att många läsare bara är utrustade med en ord lista för främmande språk och ditt hjälp avsnitt.

### <a name="write-consistently"></a>Skriv konsekvent
Hjälp för relaterade cmdlets bör vara liknande (till exempel get-x och set-x).
Använd standard beskrivningarna för standard parametrar som **Force** och **InputObject**.
(Kopiera dem från hjälp för Core-cmdletar.) Använd standard villkor.
Använd till exempel "parameter", inte "argument" och Använd "cmdlet" inte "Command" eller "kommando-let".

### <a name="start-the-synopsis-with-a-verb"></a>Starta sammanfattningen med ett verb
I fältet Sammanfattning informerar du användaren vad cmdleten gör, inte vad det är eller hur det fungerar.
Verben skapar ett uppgifts baserat uttryck som informerar användare om denna cmdlet uppfyller deras krav.
Använd enkla verb som "Get", "skapa" och "ändra".
Undvik "Set", som kan vara vagt och snygga ord som "ändra".

### <a name="focus-on-objects"></a>Fokusera på objekt
De flesta "Get"-cmdletar visar något, men deras primära funktion är att hämta ett objekt.
I hjälpen fokuserar du på objektet så att användarna förstår att standard visningen är ett av många, och att de kan använda metoderna och egenskaperna för objektet som du har hämtat för dem på olika sätt.

### <a name="write-detailed-descriptions"></a>Skriv detaljerade beskrivningar
Visa en kort lista över allt som cmdleten kan göra i den detaljerade beskrivningen.
Om huvud funktionen är att ändra en egenskap, men cmdleten kan ändra alla egenskaper, visar du detta i den detaljerade beskrivningen.

### <a name="use-conventional-syntax"></a>Använd konventionell syntax
Använd det vanliga Naur-formatet som är vanligt för kommando rads hjälpen för Windows och UNIX.

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a>Använd Microsoft .NET Framework-typer för parameter värden
Plats hållarna för parameter värden (i beskrivningarna syntax och parameter) visar de .NET Framework typer av objekt som parametern accepterar.
PowerShell-teamet utvecklade denna konvention för att hjälpa att lära användare om .NET Framework.

### <a name="write-complete-parameter-descriptions"></a>Skriv fullständiga parameter beskrivningar
Parameter beskrivningar måste informera användare av två saker: vad parametern gör (dess funktion) och vad de måste ange för parameter värden.

### <a name="write-practical-examples"></a>Skriv praktiska exempel
Exemplen bör visa hur du använder alla parametrar, men det viktigaste är att visa hur du använder cmdleten i verkliga uppgifter.
Börja med ett enkelt exempel och skriv allt fler komplexa exempel.
I det sista exemplet visar vi hur du använder cmdleten i en pipeline.

### <a name="use-the-notes-field"></a>Använd fältet Anteckningar
Använd fältet Anteckningar om du vill förklara de koncept som användarna behöver för att förstå cmdleten.
Du kan också använda kommentarer för att hjälpa användarna att undvika vanliga fel.
Undvik URL: er när de ändras.
Ange i stället användar villkor för att söka efter.

### <a name="test-your-help"></a>Testa din hjälp
Testa hjälpen precis som du testar koden.
Låt vänner och kollegor läsa ditt hjälp innehåll och ge feedback.
Du kan också begära feedback från diskussions grupper.

## <a name="see-also"></a>Se även

 [Skapa cmdlet-hjälpfilen](./how-to-create-the-cmdlet-help-file.md)

 [Lägga till cmdlet-namnet och sammanfattningen i ett cmdlet-hjälpavsnitt](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Så här lägger du till den detaljerade beskrivningen i ett hjälp avsnitt för cmdlet](./how-to-add-a-cmdlet-description.md)

 [Lägga till syntax till ett cmdlet-hjälpavsnitt](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Så här lägger du till parametrar i ett hjälp avsnitt för cmdlet](./how-to-add-parameter-information.md)

 [Så här lägger du till indatatyper i ett hjälp avsnitt för cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Lägga till returvärden i ett cmdlet-hjälpavsnitt](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Lägga till anteckningar i ett cmdlet-hjälpavsnitt](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Lägga till exempel i ett cmdlet-hjälpavsnitt](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Lägga till relaterade länkar i ett cmdlet-hjälpavsnitt](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)
