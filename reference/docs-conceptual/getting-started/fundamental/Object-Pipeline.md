---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Objektpipeline
ms.assetid: 523d8ae4-d743-47a4-b79a-806130ca688a
ms.openlocfilehash: 6102ec6e8fbf38fdc2bc5fa9c583244ef639dec8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30948218"
---
# <a name="object-pipeline"></a>Objektpipeline
Pipelines fungerar som en serie med anslutna pipe-segment. Artiklar som flyttas längsmed pipelinen släpper igenom varje segment. Om du vill skapa en pipeline i Windows PowerShell måste du ansluta kommandon tillsammans med operatorn ”|”. Utdata från varje kommando används som indata till nästa kommando.

Pipelines är tvekan mest värdefullt begrepp som används i kommandoradsverktyget gränssnitt. Korrekt användning pipelines inte bara minska arbete som ingår i anger komplexa kommandon, men gör det också lättare att se arbetsflödet i kommandona. En relaterad användbar egenskap för pipelines är att eftersom de fungerar på varje objekt separat, du behöver inte ändra dem baserat på om det finns noll, en eller flera objekt i pipelinen. Dessutom kan varje kommando i en pipeline (kallas en pipeline-elementet) vanligtvis skickar utdata till nästa kommando i pipeline objektet objektet. Detta minskar behovet av komplexa kommandon resurs vanligtvis och du kan börja hämta utdata direkt.

I det här kapitlet kommer vi beskriver hur Windows PowerShell-pipeline skiljer sig från pipelines i de flesta populära tankar och demonstrerar några grundläggande verktyg som du kan använda för att kontrollera pipeline utdata och se hur pipeline fungerar.