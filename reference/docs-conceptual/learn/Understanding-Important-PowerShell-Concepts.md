---
ms.date: 08/23/2018
keywords: PowerShell, cmdlet
title: Förstå viktiga PowerShell-koncept
ms.openlocfilehash: 8f9af370db46ea47dbccbabb7cc90fc27b8f2765
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030979"
---
# <a name="understanding-important-powershell-concepts"></a>Förstå viktiga PowerShell-koncept

PowerShell-designen integrerar koncept från många olika miljöer. Flera av begreppen är bekanta med personer med erfarenhet av gränssnitt eller programmerings miljöer. Det kan dock ta några personer att veta mer om dem. Att titta på några av de här begreppen är en användbar översikt över gränssnittet.

## <a name="output-is-object-based"></a>Utdata är Object-baserad

Till skillnad från traditionella kommando rads gränssnitt är PowerShell-cmdletar utformade för att hantera objekt.
Ett objekt är strukturerad information som är mer än bara den sträng med tecken som visas på skärmen. Kommandoutdata innehåller alltid ytterligare information som du kan använda om du behöver den.

Om du har använt text bearbetnings verktyg för att bearbeta data tidigare kommer du att se att de fungerar annorlunda när de används i PowerShell. I de flesta fall behöver du inte text bearbetnings verktyg för att extrahera speciell information. Du får direkt åtkomst till delar av data med hjälp av standardsyntaxen för PowerShell-objekt.

## <a name="the-command-family-is-extensible"></a>Kommando serien är utöknings bar

Gränssnitt som **cmd. exe** ger dig inte möjlighet att utöka den inbyggda kommando uppsättningen direkt. Du kan skapa externa kommando rads verktyg som körs i **cmd. exe**. Men dessa externa verktyg saknar tjänster, till exempel hjälp integrering. **cmd. exe** vet inte automatiskt att dessa externa verktyg är giltiga kommandon.

Inbyggda kommandon i PowerShell kallas *cmdlets* (uttalat kommando-tillåter). Du kan skapa dina egna cmdlets-moduler och-funktioner med hjälp av kompilerade kod eller skript. Moduler kan lägga till cmdlets och providers i gränssnittet. PowerShell stöder också skript som är likvärdiga med UNIX Shell-skript och kommandofiler för **cmd. exe** .

## <a name="powershell-handles-console-input-and-display"></a>PowerShell hanterar inmatade konsoler och visar

När du skriver ett kommando bearbetar PowerShell alltid kommando rads indatamängden direkt. PowerShell formaterar också utdata som visas på skärmen. Den här skillnaden är viktig eftersom den minskar det arbete som krävs för varje cmdlet. Det garanterar att du alltid kan göra saker på samma sätt med alla cmdletar. Cmdlet-utvecklare behöver inte skriva kod för att parsa kommando rads argumenten eller formatera utdata.

Traditionella kommando rads verktyg har egna scheman för att begära och Visa hjälp. Vissa kommando rads verktyg använder **/?** för att utlösa hjälp visningen. andra använder **-?** , **/h**eller till och med **//** . Vissa visar hjälpen i ett GUI-fönster, i stället för i konsolens visning. Om du använder fel parameter kan verktyget ignorera det du skrev och börja köra en uppgift automatiskt.
Eftersom PowerShell automatiskt tolkar och bearbetar kommando raden **–?** parameter innebär alltid "Visa mig hjälp för det här kommandot".

> [!NOTE]
> Om du kör ett grafiskt program i PowerShell öppnas fönstret för programmet.
> PowerShell inverkar bara vid bearbetning av kommando rads indata som du anger eller programutdata som returneras till konsol fönstret. Det påverkar inte hur programmet fungerar internt.

## <a name="powershell-uses-some-c-syntax"></a>PowerShell använder en C# viss syntax

PowerShell bygger på .NET Framework. Den delar vissa syntax funktioner och nyckelord med C# programmeringsspråket. Med Learning PowerShell kan du göra det mycket enklare C#att lära dig. Om du redan är bekant med C#kan dessa likheter göra det enklare att lära sig PowerShell.
