---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Använd flikexpansion
ms.openlocfilehash: d96cbf848f464aff29a7bed9b70d0b6a000aa808
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67031020"
---
# <a name="using-tab-expansion"></a>Använd flikexpansion

Kommandoradsverktyget gränssnitt är ett sätt att slutföra namnen på lång filer eller kommandon automatiskt, ofta snabbare kommandot posten och ge tips. PowerShell kan du fylla i filnamn och cmdlet-namnen genom att trycka på den <kbd>fliken</kbd> nyckel.

> [!NOTE]
> Flikexpansion styrs av funktionen intern TabExpansion eller TabExpansion2. Eftersom den här funktionen kan ändras eller åsidosätts, är den här diskussionen en guide i beteendet hos PowerShell standardkonfigurationen.

Om du vill fylla i ett filnamn eller sökväg från de olika alternativen automatiskt skriver en del av namn och tryck på den <kbd>fliken</kbd> nyckel. PowerShell kommer automatiskt att expandera namnet till den första matchningen som hittas. Att trycka på den <kbd>fliken</kbd> nyckel upprepade gånger ska gå igenom alla tillgängliga alternativ.

Flikexpansion av cmdlet-namnen är något annorlunda. Om du vill använda flikexpansion på en cmdlet-namn, skriver du hela första delen av namn (verb) och bindestreck som kommer efter. Du kan fylla i mer i namnet på en partiell matchning. Exempel: Om du skriver `get-co` och tryck sedan på den <kbd>fliken</kbd> nyckel, PowerShell kommer automatiskt att expandera den till den `Get-Command` cmdlet (Observera att även ändras i fallet med bokstäver i sina standard formulär). Om du trycker på <kbd>fliken</kbd> viktiga igen, PowerShell ersätter det med det bara andra matchande cmdlet-namnet, `Get-Content`.

Du kan använda flikexpansion upprepade gånger på samma rad. Du kan till exempel använda flikexpansion på namnet på den `Get-Content` cmdlet genom att ange:

```
PS> Get-Con<Tab>
```

När du trycker på den <kbd>fliken</kbd> nyckel, kommandot expanderar till:

```
PS> Get-Content
```

Sedan kan du delvis anger du sökvägen till aktiva installationens loggfil och Använd flikexpansion igen:

```
PS> Get-Content c:\windows\acts<Tab>
```

När du trycker på den <kbd>fliken</kbd> nyckel, kommandot expanderar till:

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> En begränsning med fliken expansionsprocessen är att tolkas alltid flikar som försöker slutföra ett ord. Om du kopierar och klistrar in kommandoexempel i en PowerShell-konsol, kontrollerar du att exemplet inte innehåller flikar; i annat fall resultatet blir oförutsägbara och kommer sannolikt inte som du tänkt.
