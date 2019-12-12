---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Använd flikexpansion
ms.openlocfilehash: d96cbf848f464aff29a7bed9b70d0b6a000aa808
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67031020"
---
# <a name="using-tab-expansion"></a>Använd flikexpansion

Kommando rads gränssnitt ger ofta ett sätt att slutföra namnen på långa filer eller kommandon automatiskt, påskynda kommando posten och tillhandahålla tips. Med PowerShell kan du fylla i fil namn och cmdlet-namn genom att trycka på <kbd>TABB</kbd> -tangenten.

> [!NOTE]
> Fliken utökas av den interna funktionen TabExpansion eller TabExpansion2. Eftersom den här funktionen kan ändras eller åsidosättas, är den här diskussionen en guide till beteendet för standard-PowerShell-konfigurationen.

Om du vill fylla i ett fil namn eller en sökväg från tillgängliga alternativ automatiskt, anger du en del av namnet och trycker på <kbd>TABB</kbd> -tangenten. PowerShell expanderar automatiskt namnet till den första matchning som hittas. Om du trycker på <kbd>tabbtangenten</kbd> flera gånger kommer de tillgängliga alternativen att gå igenom.

Flikens expansion av cmdlet-namn skiljer sig något åt. Om du vill använda TABB-expansion på ett cmdlet-namn skriver du hela den första delen av namnet (verbet) och bindestrecket som följer. Du kan fylla i mer av namnet för en partiell matchning. Om du till exempel skriver `get-co` och sedan trycker på <kbd>tabbtangenten</kbd> , expanderar PowerShell automatiskt detta till `Get-Command`-cmdleten (Observera att det även ändrar Skift läge för bokstäver till deras standard formulär). Om du trycker på <kbd>tabbtangenten</kbd> igen ersätter PowerShell detta med det enda andra matchande cmdlet-namnet, `Get-Content`.

Du kan använda utöka flera gånger på samma rad. Du kan till exempel använda TABB-tillägg på namnet på `Get-Content`-cmdleten genom att ange:

```
PS> Get-Con<Tab>
```

När du trycker på <kbd>TABB</kbd> -tangenten expanderas kommandot till:

```
PS> Get-Content
```

Du kan sedan delvis ange sökvägen till logg filen för Active Setup och använda TABB-expansion igen:

```
PS> Get-Content c:\windows\acts<Tab>
```

När du trycker på <kbd>TABB</kbd> -tangenten expanderas kommandot till:

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> En begränsning av processen för att utöka en flik är att flikarna alltid tolkas som försök att slutföra ett ord. Om du kopierar och klistrar in kommando exempel i en PowerShell-konsol ser du till att exemplet inte innehåller flikar. om det gör det blir resultatet oförutsägbart och det är nästan verkligen inte det du avsåg.
