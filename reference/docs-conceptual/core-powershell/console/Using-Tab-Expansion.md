---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Med fliken expanderades
ms.assetid: c8730471-bf6a-43b8-ab1d-f9ef5a74f04e
ms.openlocfilehash: 8412bd97a95719f07b16c6671d3b8801bbfab8e3
ms.sourcegitcommit: 4807ab554d55fdee499980835bcc279368b1df68
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2017
---
# <a name="using-tab-expansion"></a>Med fliken expanderades
Kommandoradsverktyget tankar tillhandahåller ofta ett sätt att slutföra namnen på långa filer eller kommandon automatiskt, snabba på kommando-post och ge. Windows PowerShell kan du fylla i namn på filen och cmdlet genom att trycka på **fliken** nyckel.

> [!NOTE]
> Fliken expansion styrs av funktionen interna TabExpansion eller TabExpansion2. Eftersom den här funktionen kan ändras eller åsidosätts, är den här diskussionen en guide som beteendet för PowerShell standardkonfigurationen.

Om du vill fylla i ett filnamn eller sökväg från de tillgängliga alternativen automatiskt skriver en del av namn och klicka på den **fliken** nyckel. PowerShell kommer automatiskt att expandera namnet till den första matchningen som hittas. När du trycker på den **fliken** nyckel upprepade gånger att växla mellan alla tillgängliga alternativ.

Fliken expandering av cmdlet-namnen är något annorlunda. För att använda fliken expansion på en cmdlet-namn, skriver du hela första delen av namn (verb) och bindestreck som följer den. Du kan fylla i flera namn för en delvis matchning. Om du skriver till exempel **get-co** och tryck sedan på den **fliken** nyckeln, PowerShell kommer automatiskt att expandera den till den **Get-Command** cmdlet (Observera att ändrar du även fallet för att deras standardformulär). Om du trycker på **fliken** nyckeln igen och PowerShell ersätter det med endast andra matchande namn, **Get-innehåll**.

Du kan använda fliken expansion upprepade gånger på samma linje. Du kan till exempel använda fliken expansion på namnet på den **Get-innehåll** cmdlet genom att ange:

```
PS> Get-Con<Tab>
```

När du trycker på den **fliken** nyckeln, kommandot expanderar till:

```
PS> Get-Content
```

Du kan sedan delvis ange sökvägen till loggfilen Active Setup och använda fliken expansion igen:

```
PS> Get-Content c:\windows\acts<Tab>
```

När du trycker på den **fliken** nyckeln, kommandot expanderar till:

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> En begränsning med den flik utvidgas är flikar tolkas alltid som försöker slutföra ett ord. Om du kopierar och klistrar in kommandoexempel i PowerShell-konsolen, kontrollera att provet inte innehåller flikar. Om resultatet blir oförutsägbara och sannolikt inte som du tänkt.
