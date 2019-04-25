---
title: Skrivhjälp för PowerShell-cmdletar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083169"
---
# <a name="writing-help-for-powershell-cmdlets"></a>Skriva hjälp för PowerShell-cmdletar

PowerShell-cmdlets kan vara användbart, men om inte din hjälpavsnitt Förklara tydligt vad cmdleten gör och hur du använder det, kan inte hämta används cmdleten eller, värsta fall kan det vara frustrerande användare.
Filformat för XML-baserade cmdlet-hjälpen förbättrar konsekvens, men bra kräver mycket mer.

Om du aldrig har skrivit cmdlet hjälp, kan du läsa följande riktlinjer.
XML-schema som krävs för att skapa cmdlet-hjälpavsnittet beskrivs i följande avsnitt.
Börja med [skapar Cmdlet hjälpfilen](./how-to-create-the-cmdlet-help-file.md).
Avsnittet innehåller en beskrivning av de översta XML-noderna.

## <a name="writing-guidelines-for-cmdlet-help"></a>Skriva riktlinjer för Cmdlet-hjälpen

### <a name="write-well"></a>Skriva bra
Inget ersätter ett välskriven ämne.
Om du inte är en professionell skrivare, hitta en skrivare eller en redigerare som hjälper dig att.
Ett annat alternativ är att kopiera dina hjälptext till Microsoft Word och använda grammatik och stavning kontrollerar för att förbättra ditt arbete.

### <a name="write-simply"></a>Skriv bara
Använd enkla ord och fraser.
Undvik jargong.
Överväg att många läsare är utrustade endast med en ordlista för andra språk och det aktuella hjälpavsnittet.

### <a name="write-consistently"></a>Skriva konsekvent
Hjälp för relaterade cmdlets bör likna (till exempel get-x och set-x).
Använder standard beskrivningarna för standard parametrar, t.ex **kraft** och **InputObject**.
(Kopiera dem från hjälp för core-cmdletarna.) Använda allmänna villkor.
Till exempel, Använd ”parametern”, inte ”argumentet” och Använd ”cmdlet” inte ”kommandot” eller ”command-let”.

### <a name="start-the-synopsis-with-a-verb"></a>Starta sammanfattning med ett verb
Fältet Sammanfattning informerar användaren vilka cmdleten, inte vad det är eller hur det fungerar.
Verb skapa en uppgiftsbaserad instruktion som informerar användarna om denna cmdlet uppfyller deras behov.
Använda enkla verb som ”hämta”, ”skapa” och ”ändra”.
Undvika (set), vilket kan vara vaga och avancerad ord som ”ändra”.

### <a name="focus-on-objects"></a>Fokusera på objekt
De flesta ”hämta” cmdletar visas något, men deras primära funktion är att hämta ett objekt.
I din hjälp att fokusera på objektet, så att användarna förstår att standardvisningen är ett av flera och att de kan använda metoder och egenskaper i objektet som du hämtade för dem på olika sätt.

### <a name="write-detailed-descriptions"></a>Skriva detaljerade beskrivningar
Kort lista allt som cmdlet: en kan göra i den detaljerade beskrivningen.
Om den huvudsakliga funktionen är att ändra en egenskap, men cmdlet: en kan ändra alla egenskaper, lista du detta i den detaljerade beskrivningen.

### <a name="use-conventional-syntax"></a>Använd konventionella syntax
Använd standard Backus Naur formatet som är gemensamt för Windows och UNIX-hjälpen.

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a>Använd Microsoft .NET Framework-typer för parametervärden
Platshållare för värden (i syntax och parameteralternativ beskrivningarna) visar .NET Framework-typer av objekt som ska ta emot parametern.
PowerShell-teamet utvecklade denna konvention för att lära ut användare om .NET Framework.

### <a name="write-complete-parameter-descriptions"></a>Skriva fullständiga beskrivningar
Beskrivningar av parametern måste informera användare om två saker: vilka parametern gör (dess effekt) och de måste skriva för parametervärdena.

### <a name="write-practical-examples"></a>Skriva praktiska exempel
Exemplen ska visa hur du använder alla parametrar, men viktigaste är att visa hur du använder cmdlet: en i verkliga uppgifter.
Börja med ett enkelt exempel och skriva allt mer komplexa exempel.
I det sista exemplet visa hur du använder cmdleten i en pipeline.

### <a name="use-the-notes-field"></a>Använd fältet Anteckningar
Använd fältet Anteckningar för att förklara begreppen att användarna måste förstå cmdlet: en.
Du kan också använda anteckningar för att hjälpa användarna att undvika vanliga fel.
Undvik att URL: er när den ändras.
I stället ange villkor för användarna att söka efter.

### <a name="test-your-help"></a>Testa din hjälp
Testa hjälp precis som du testar din kod.
Har vänner och kollegor läsa hjälpinnehåll och ge feedback.
Du kan också samla in feedback från diskussionsgrupper.

## <a name="see-also"></a>Se även

 [Så här skapar du filen Cmdlet-hjälpen](./how-to-create-the-cmdlet-help-file.md)

 [Hur du lägger till Cmdlet-namn och sammanfattning för en Cmdlet-hjälpavsnittet](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Hur du lägger till den detaljerade beskrivningen för en Cmdlet-hjälpavsnittet](./how-to-add-a-cmdlet-description.md)

 [Lägga till Syntax i en Cmdlet-hjälpavsnittet](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Lägga till parametrar i en Cmdlet-hjälpavsnittet](./how-to-add-parameter-information.md)

 [Hur du lägger till indata-typer till en Cmdlet-hjälpavsnittet](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Hur du lägger till returvärden för en Cmdlet-hjälpavsnittet](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Lägga till kommentarer om en Cmdlet-hjälpavsnittet](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Hur du lägger till exempel att en Cmdlet-hjälpavsnittet](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Lägga till länkarna till Cmdlet-hjälpavsnittet](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)