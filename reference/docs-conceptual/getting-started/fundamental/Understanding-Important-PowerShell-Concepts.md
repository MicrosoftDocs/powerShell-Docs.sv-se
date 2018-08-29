---
ms.date: 08/23/2018
keywords: PowerShell cmdlet
title: Förstå viktiga PowerShell-koncept
ms.assetid: 3e601e38-4520-4578-a48d-b6779f1d35ee
ms.openlocfilehash: 5f8192f962cebb8ee5e5384e39b48de811b11003
ms.sourcegitcommit: 59727f71dc204785a1bcdedc02716d8340a77aeb
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/28/2018
ms.locfileid: "43134243"
---
# <a name="understanding-important-powershell-concepts"></a>Förstå viktiga PowerShell-koncept

PowerShell-design integrerar begrepp från många olika miljöer. Flera av begrepp som är välkända för personer med erfarenhet av gränssnitt eller programmeringsmiljöer. Men vet många om alla. Titta på några av de här koncepten ger en bra översikt över gränssnittet.

## <a name="output-is-object-based"></a>Utdata är objektbaserad

Till skillnad från traditionella command-line gränssnitt, har PowerShell-cmdletarna utformats utan objekt.
Ett objekt är strukturerad information som är mer än bara sträng med tecken som visas på skärmen. Kommandoutdata alltid har extra information som du kan använda om du behöver den.

Om du har använt text-bearbetning verktyg för att bearbeta data som tidigare, hittar du att de fungerar annorlunda när de används i PowerShell. I de flesta fall behöver du inte text-process-verktyg för att extrahera specifik information. Du har direkt åtkomst till delar av data med standard syntax för PowerShell-objekt.

## <a name="the-command-family-is-extensible"></a>I kommando-familjen kan utökas

Gränssnitt, till exempel Cmd.exe gör inte det möjligt för dig att utöka den inbyggda kommandouppsättningen direkt.
Du kan skapa externa kommandoradsverktyg som körs i Cmd.exe. Men dessa externa verktyg har inte tjänster, till exempel hjälp-integrering. Cmd.exe inte automatiskt att visa att dessa externa verktyg är giltiga kommandon.

Inbyggda kommandona i PowerShell kallas *cmdletar* (uttalas Commando-lets). Du kan skapa egna moduler med cmdletar och funktioner med hjälp av kompilerad kod eller skript. Moduler kan lägga till cmdlets och providers i gränssnittet. PowerShell har även stöd för skript som kan jämföras med UNIX-kommandoskript och Cmd.exe batch-filer.

## <a name="powershell-handles-console-input-and-display"></a>PowerShell hanterar konsolindata och visa

När du skriver ett kommando bearbetar PowerShell alltid kommandoradsverktyget indata direkt. PowerShell också formaterar utdata som visas på skärmen. Den här skillnaden är betydande, eftersom det arbete som krävs för varje cmdlet. Det innebär att du kan alltid göra saker på samma sätt med en cmdlet. Cmdlet: en utvecklare behöver inte skriva kod för att parsa kommandoradsargument eller formatera utdata.

Traditionella kommandoradsverktyg har egna scheman för att begära och visa hjälp. Vissa kommandoradsverktyg använder **/?** att utlösa det bidrar till att visa; andra använda **-?**, **/H**, eller till och med **//**. Vissa visas hjälp i ett GUI-fönster i stället för i konsolen visas. Om du använder parametern fel, kan verktyget Ignorera vad du har angett och köra en uppgift automatiskt.
Eftersom PowerShell automatiskt tolkar och bearbetar command line den **-?** Parametern innebär alltid ”visa hjälp för det här kommandot”.

> [!NOTE]
> Om du kör en grafisk programmet i PowerShell, öppnas fönstret för programmet.
> PowerShell intervenes endast när bearbetning av kommandoraden indata du anger eller programutdata som returneras till konsolfönstret. Den påverkar inte hur programmet fungerar internt.

## <a name="powershell-uses-some-c-syntax"></a>PowerShell använder vissa C#-syntax

PowerShell bygger på .NET Framework. Den delar vissa syntaxfunktioner och nyckelord med programmeringsspråket C#. Lära sig PowerShell kan göra det enklare att lära dig C#. Om du redan är bekant med C#, göra dessa likheter lära sig PowerShell enklare.