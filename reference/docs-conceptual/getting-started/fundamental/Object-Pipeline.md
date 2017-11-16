---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Objektet Pipeline
ms.assetid: 523d8ae4-d743-47a4-b79a-806130ca688a
ms.openlocfilehash: 3fa41cc744cf3ab66fc5ef186ead8eb919429a76
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="object-pipeline"></a>Objektet Pipeline
Pipelines fungerar som en serie med anslutna pipe-segment. Artiklar som flyttas längsmed pipelinen släpper igenom varje segment. Om du vill skapa en pipeline i Windows PowerShell måste du ansluta kommandon tillsammans med operatorn ”|”. Utdata från varje kommando används som indata till nästa kommando.

Pipelines är tvekan mest värdefullt begrepp som används i kommandoradsverktyget gränssnitt. Korrekt användning pipelines inte bara minska arbete som ingår i anger komplexa kommandon, men gör det också lättare att se arbetsflödet i kommandona. En relaterad användbar egenskap för pipelines är att eftersom de fungerar på varje objekt separat, du behöver inte ändra dem baserat på om det finns noll, en eller flera objekt i pipelinen. Dessutom kan varje kommando i en pipeline (kallas en pipeline-elementet) vanligtvis skickar utdata till nästa kommando i pipeline objektet objektet. Detta minskar behovet av komplexa kommandon resurs vanligtvis och du kan börja hämta utdata direkt.

I det här kapitlet kommer vi beskriver hur Windows PowerShell-pipeline skiljer sig från pipelines i de flesta populära tankar och demonstrerar några grundläggande verktyg som du kan använda för att kontrollera pipeline utdata och se hur pipeline fungerar.

